# General Multimodal Protein Design Enables DNA-Encoding of Chemistry

- alphaXiv: https://www.alphaxiv.org/abs/2604.05181
- Source paper: https://arxiv.org/abs/2604.05181

## Expanding the Reach of Biocatalysis

Nature has evolved an extraordinary array of enzymes to facilitate the chemical reactions necessary for life. However, the scope of these natural catalysts represents only a small fraction of the theoretically possible chemical space. Many synthetically useful transformations, termed "new-to-nature" chemistries, lack biological precedents, leaving protein engineers without a natural starting point for directed evolution. 

Traditional enzyme engineering typically begins with a protein that already displays some level of the desired activity. For reactions like carbene-transfer or specific carbon-hydrogen insertions, identifying such an "ancestor" in nature is often impossible. Computational methods have attempted to fill this gap by designing *de novo* proteins. Historically, these methods rely on "theozymes"—predefined geometric arrangements of amino acids optimized to stabilize a transition state. This approach is limited by its dependence on fixed active-site geometries and the requirement for precise mechanistic understanding. Furthermore, existing generative models often separate the creation of the protein's backbone from its sequence, a decoupled process that can lead to structural instabilities or sequences that fail to fold into the intended shape.

DISCO (DIffusion for Sequence-structure CO-design) addresses these challenges by generating protein sequences and 3D structures simultaneously. By conditioning the generative process on arbitrary biomolecules, DISCO enables the systematic design of functional enzymes for novel transformations without requiring pre-specified catalytic motifs.

## Multimodal Diffusion: Simultaneous Sequence and Structure Co-design

At the heart of DISCO is a multimodal generative framework that treats the protein sequence and its 3D coordinates as a joint distribution. While many existing models generate a 3D backbone and subsequently use an inverse folding model to determine the amino acid sequence, DISCO performs these tasks in parallel using a joint diffusion process.

The model utilizes two types of diffusion: a discrete masked diffusion process for the amino acid sequence and a continuous diffusion process for the 3D atomic coordinates. During training, noise is added to both the sequence and the structure. The model then learns a joint reverse process to recover the clean data from the noisy inputs. This is achieved using a combination of unimodal diffusion losses:

$$
\mathcal{L}_{\text{total}} = \mathcal{L}_{\text{coord}} + \lambda \mathcal{L}_{\text{mask}}
$$

where $\mathcal{L}_{\text{coord}}$ represents the denoising score matching loss for coordinates and $\mathcal{L}_{\text{mask}}$ represents the masked language model loss for sequences. By optimizing these together, the model learns the dependencies between specific amino acid identities and their spatial arrangements.

The architecture is built upon components from AlphaFold 3, including a Pairformer stack and a Joint Diffusion Module that leverages atom-level attention. Instead of a multiple sequence alignment (MSA) module, DISCO incorporates a frozen protein language model (pLM) to provide evolutionary context for partial sequences. Crucially, the model incorporates $SE(3)$ symmetries through data augmentation, ensuring that the generated structures are invariant to rotation and translation in 3D space.

## Cross-Modal Recycling and Inference Optimization

A primary difficulty in co-designing sequence and structure is ensuring they remain consistent throughout the generative trajectory. DISCO introduces "cross-modal recycling" to solve this. At each step $t$ of the diffusion process, the model is conditioned on four pieces of information: the current noisy sequence $s_t$, the current noisy structure $x_t$, and the model’s own predicted "clean" versions of the sequence and structure from the previous step. This feedback loop allows sequence predictions to adapt to the emerging backbone and vice versa.

To further improve the quality of generated proteins, the researchers implemented several inference-time enhancements:

1.  **Sequence Self-Correction:** Standard masked diffusion models often "commit" to a residue once it is unmasked, even if subsequent structural changes make that residue a poor fit. DISCO employs a random remasking strategy during inference, allowing the model to reconsider and correct its sequence choices as the structure matures.
2.  **Entropy-Adaptive Sequence Temperature:** Early in the generative process, models can become overly confident in certain residues. DISCO uses an adaptive temperature scheme that flattens the distribution of tokens when entropy is high, preventing premature commitment and maintaining flexibility during co-design.
3.  **Noisy Guidance:** This is a variation of classifier-free guidance. Instead of using a completely unconditioned model, DISCO uses a model conditioned on a partially noised target. This allows the guidance signal to be more subtle and effective during the early stages of generation.

## Multimodal Steering with Feynman-Kac Correctors

While standard diffusion models excel at sampling from a learned distribution, they do not inherently allow for the optimization of specific properties. To address this, the researchers introduced Multimodal Feynman-Kac Correctors (FKC). These correctors allow the model to steer the generative process toward proteins that satisfy specific rewards or constraints.

FKC-MM (Multimodal) allows for joint optimization of objectives defined over both sequence and structure. For example, if a designer wants to increase the number of disulfide bonds or cation-π interactions, FKC-MM "tilts" the diffusion trajectory to favor those outcomes. Experimental results showed that this method could generate proteins with six disulfide bonds in a 100-residue chain, a density found in only 0.2% of natural proteins.

Another variant, FKC-SG (Specificity Guidance), steers the model toward binding a specific target while simultaneously "repelling" a structurally similar decoy. This is achieved by penalizing the likelihood of the generated design under an off-target model. In tests, this approach successfully distinguished between very similar molecules, such as the amino acids valine and proline, or the steroid hormones aldosterone and cortisone.

## Benchmarking and Structural Realism

In computational evaluations, DISCO demonstrated significant improvements over existing protein design methods. When generating proteins unconditionally, approximately 90% of the sequences were predicted to refold to their designed backbones with an $\text{RMSD} < 2\text{ \AA}$. Compared to models like RFDiffusion or BoltzGen, DISCO achieved higher sequence and structural diversity without sacrificing this "co-designability."

The proteins generated by DISCO exhibit high physicochemical realism. They possess natural amino acid compositions, diverse secondary structures (alpha helices and beta sheets), and native-like surface properties, such as charge distribution and hydrophobicity. 

When conditioned on small molecules, DISCO creates ligand-responsive pockets. The model's binding sites naturally correlate in lipophilicity with the hydrophobicity of the ligand. Furthermore, DISCO is capable of sampling valid ligand conformers, exploring rotatable bonds while maintaining the rigid core geometries of the conditioning molecules. Analysis of the generated binding motifs using structural search tools revealed that the majority of DISCO's active sites are novel; over 80% showed an $\text{RMSD} > 3\text{ \AA}$ when compared to the five nearest residues in known natural proteins.

## Designing New-to-Nature Enzymes for Carbene-Transfer Reactions

The most rigorous test of DISCO's capabilities was the design of functional enzymes for carbene-transfer reactions. These are non-biological reactions involving highly reactive intermediates that are prized in organic synthesis but difficult to control.

The researchers conditioned DISCO on the geometry of an iron-carbenoid intermediate (a heme-cofactor bound to a reactive carbenoid). Notably, they did not provide theozymes or pre-specify which residues should coordinate the reaction. From $10^4$ initial designs, 90 were selected for experimental validation in *Escherichia coli*. The designs were tested against four reactions:
1.  **Alkene cyclopropanation:** One design achieved a 72% yield and a total turnover number ($\text{TTN}$) of 4,050, with a $99:1$ diastereomeric ratio, outperforming previous enzymes developed through rounds of directed evolution.
2.  **B–H insertion:** The top design reached a 98% yield and 5,170 $\text{TTN}$.
3.  **C(sp^3)\text{--}H$ insertion:** One design achieved 2,360 $\text{TTN}$, comparable to performance levels that previously required 14 rounds of directed evolution to achieve in natural variants.
4.  **Spirocyclopropanation:** This challenging reaction yielded multiple active variants with modest turnover.

The successful designs were structurally diverse and often based on protein folds unrelated to catalysis. For example, one of the most active enzymes for spirocyclopropanation was structurally similar to a TetR-family transcription factor that has no known catalytic function in nature. This demonstrates DISCO's ability to repurpose entire protein architectures for completely new chemical tasks.

## Evolvability and the Future of Programmable Proteins

Beyond initial activity, a critical feature of a designed enzyme is its "evolvability"—the ability to be further improved through laboratory evolution. The researchers subjected a DISCO-designed enzyme to a single round of error-prone PCR. This simple evolutionary step led to variants with improved enantioselectivity, with one variant increasing its enantiomeric excess from $35\%$ to $49\%$. The mutations that provided these improvements were scattered throughout the protein, suggesting that the designed enzymes occupy stable, evolvable regions of the sequence-structure landscape.

The significance of this work lies in its ability to bypass the "initial activity" bottleneck that has long hindered the development of biocatalysts for new-to-nature chemistry. By treating protein sequence and structure as a single, co-designed unit and conditioning them on arbitrary chemical targets, DISCO provides a general platform for creating functional biological molecules. This moves the field closer to a "DNA-encoding of chemistry," where any synthetic transformation could potentially be facilitated by a custom-designed, genetically encodable enzyme.

## Relevant Citations

- De novo design of protein structure and function with RFdiffusion: This paper introduces RFdiffusion, a state-of-the-art generative model for protein design. It serves as a crucial baseline and point of comparison throughout the main paper, which aims to improve upon such models by enabling joint sequence-structure co-design and flexible conditioning without pre-specified motifs.
- Accurate structure prediction of biomolecular interactions with AlphaFold 3: The DISCO model's architecture is explicitly based on AlphaFold 3, adapting its core components for the task of generative co-design. Furthermore, AlphaFold 3 is used as a key computational filter to validate the generated designs in silico, making it a foundational tool for both the model's construction and its evaluation pipeline.
- Feynman-Kac correctors in diffusion: Annealing, guidance, and product of experts: This work provides the theoretical framework for the Feynman-Kac Corrector (FKC), which the main paper adapts to develop its novel multimodal inference steering methods (FKC-MM and FKC-SG). This is a core methodological contribution of DISCO, enabling controllable generation of proteins with desired properties like specificity or high disulfide bond content.
- Enzymatic assembly of carbon–carbon bonds via iron-catalysed sp 3 C–H functionalization: This paper describes a landmark directed evolution campaign for a challenging new-to-nature C(sp3)–H insertion reaction. The DISCO-designed enzymes are shown to rival the performance of the highly evolved catalysts from this study, providing a powerful experimental benchmark that validates DISCO's ability to generate highly active enzymes for complex transformations without prior experimental screening or evolution.
