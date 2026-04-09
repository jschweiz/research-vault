# BiDexGrasp: Coordinated Bimanual Dexterous Grasps across Object Geometries and Sizes

- alphaXiv: https://www.alphaxiv.org/abs/2604.06589
- Source paper: https://arxiv.org/abs/2604.06589

## The Challenge of Bimanual Dexterous Grasping

Robotic dexterous grasping aims to replicate the human ability to manipulate objects using multi-fingered hands. While significant progress has been made in single-hand grasping, many real-world objects—due to their substantial size, heavy weight, or complex geometries—require the use of two hands. Transitioning from single-hand to bimanual (two-handed) manipulation introduces several complexities. The search space for valid hand configurations grows quadratically, and the system must ensure precise coordination between both hands to maintain stability and avoid collisions.

![BiDexGrasp Generation Framework](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06589v1/x2.png)
*Figure 1: The BiDexGrasp generation framework, illustrating the Bimanual Coordination Module, Scale-Adaptive Anchor strategy, and Geometry-Adaptive Features.*

Existing approaches often struggle with objects of varying scales and shapes. Models trained on small, single-handed objects frequently fail when applied to larger items like crates or stools. Furthermore, current bimanual datasets lack the diversity and scale necessary to train robust, generalizable models. BiDexGrasp addresses these issues by providing a large-scale dataset and a generative framework specifically designed for coordinated, geometry-adaptive bimanual grasping.

## The BiDexGrasp Dataset: Diversity Across Scales

A central contribution of this research is the BiDexGrasp dataset, which encompasses 6,351 unique objects sourced from the Objaverse and DexGraspNet collections. Unlike previous datasets that might focus on a narrow range of object sizes, BiDexGrasp explicitly incorporates scale diversity. Each object in the dataset is scaled to 11 discrete sizes, ranging from 30 cm to 80 cm.

The final dataset contains 9.7 million annotated grasp instances. This scale and variety are intended to allow models to learn how grasping strategies must change as an object grows from something that might fit in a single palm to something that requires a wide, two-handed embrace. To create such a massive amount of high-quality data, the authors developed a specialized synthesis pipeline.

## High-Efficiency Data Synthesis Pipeline

Generating millions of physically feasible bimanual grasps manually is impossible, and traditional random sampling is highly inefficient. The researchers developed a three-stage automated pipeline to generate the BiDexGrasp dataset.

![Data Synthesis Pipeline](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06589v1/x1.png)
*Figure 2: The automated data synthesis pipeline featuring region-based initialization and decoupled optimization.*

### Bimanual Region-Constraint Initialization
To avoid the "needle in a haystack" problem of random initialization, the pipeline first identifies promising grasping regions on the object surface. It uses a Grasp Wrench Space (GWS) estimator to evaluate pairs of surface regions. Only region pairs that offer high potential for stable, force-closure grasps are selected for initial hand placement. This step significantly increases the success rate of the subsequent optimization.

### Decoupled Force-Closure Optimization
Once the hands are initialized, their poses are refined through optimization. A common problem in bimanual optimization is that one hand might dominate the stability score, leading to a "lazy" second hand that doesn't actually contribute to the grasp. To prevent this, the authors propose a decoupled energy function:

$$ \min_{G_{bi}} (w_{Q-left} Q(G_{left}) + w_{Q-right} Q(G_{right}) + w_{dis} E_{dis} + w_{region} E_{region}) $$

In this formulation, $Q(G_{left})$ and $Q(G_{right})$ represent the force-closure quality for the left and right hands individually. By optimizing these terms alongside a distance term $E_{dis}$ and a region consistency term $E_{region}$, the framework ensures that both hands actively participate in a stable, coordinated grasp.

### Kinematics-Aware Filtering
Finally, the synthesized "floating" hand poses are converted into realistic tabletop configurations. This involves solving inverse kinematics for robotic arms to ensure that the generated grasps are actually reachable by a physical robot on a flat surface without collisions.

## The BiDexGrasp Generation Framework

With a large-scale dataset in hand, the authors developed a generative model to predict bimanual grasps for unseen objects. The framework takes an object point cloud as input and produces coordinated hand poses. It relies on three primary modules to handle coordination, scale, and geometry.

### Bimanual Coordination Module (BCM)
The BCM ensures that the two hands work together rather than as two independent agents. It samples various "grasp views" (approaching directions) and predicts the probability $p_i$ of a single view being successful, as well as the joint probability $p_{bi,i,j}$ of a pair of views working in harmony. This allows the model to select two approach directions that are globally stable and unlikely to result in inter-hand collisions.

### Scale-Adaptive Grasp Anchor (SAGA)
Predicting the absolute position of a hand in 3D space is difficult when object sizes vary from 30 cm to 80 cm. To simplify this task, SAGA introduces a relative coordinate system. It defines a grasp anchor $g_{anchor}$ at the intersection of the chosen approach view and the object's bounding sphere. The model then predicts the relative translation $\Delta t$ and rotation $\Delta r$ of the wrist with respect to this anchor. This normalization makes the learning process much more robust to changes in object scale.

### Geometry-Adaptive Object Feature (GAF)
To handle complex shapes, the framework combines global object features with local geometric details. GAF extracts local point cloud features specifically around the predicted grasp anchors. This ensures that the model "pays attention" to the fine-grained surface geometry where the fingers will actually make contact, filtering out irrelevant parts of the object.

### Relative Dexterous Grasp Diffusion
The final hand poses are generated using a Denoising Diffusion Probabilistic Model (DDPM). The diffusion process iteratively refines a noise-filled hand pose into a precise configuration $G_{bi,rela,0:T}$ based on the condition $F_{ga-obj}$ (the combined global and local geometry features). The model's objective is to learn the distribution:

$$ p_{\theta}(G_{bi,rela,0:T} | F_{ga-obj}) $$

This probabilistic approach allows the model to generate a diverse set of valid grasps for any given object.

## Experimental Results and Performance

The BiDexGrasp framework was evaluated in both simulation and real-world environments, showing significant improvements over existing methods like SceneDiffuser and DGTR.

### Simulation Success Rates
In large-scale simulation tests, the proposed framework achieved a lift success rate of 66.78%, more than 25% higher than previous state-of-the-art bimanual methods. It also showed much lower object penetration (1.53 cm) and self-penetration (0.01 cm), indicating that the generated grasps were not only successful but also physically realistic.

![Generated Grasp Samples](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06589v1/x4.png)
*Figure 3: Samples of generated grasps demonstrating the framework's ability to handle diverse geometries and large scales.*

### Generalization and Adaptability
One of the strengths of this work is its ability to generalize. The data synthesis pipeline was successfully applied to different hand models, such as the Leap Hand, without structural changes. This suggests the principles of bimanual coordination and decoupled optimization are hand-agnostic.

### Real-World Deployment
The framework was deployed on two different physical robotic systems:
1.  A dual-arm setup with Piper arms and Brainco dexterous hands.
2.  A Unitree G1 humanoid robot with Inspire hands.

![Real World Experiments](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06589v1/x8.png)
*Figure 4: Real-world experimental setup using the Unitree G1 robot and dual Piper arms to grasp unseen objects.*

Despite being trained entirely in simulation, the model successfully generalized to real-world objects including a stool, a large plush watermelon, and a storage bin. Success rates in the real world ranged from $33.3\%$ to $100\%$, depending on the object complexity and the specific hardware used. The experiments confirmed that the scale-adaptive anchors and coordination modules are effective in bridging the gap between simulation and reality.

## Summary of Contributions

BiDexGrasp provides a comprehensive approach to bimanual dexterous grasping by addressing the two most significant bottlenecks in the field: the lack of diverse, large-scale data and the difficulty of coordinating high-dimensional action spaces across different scales.

By introducing a dataset of 9.7 million grasps and a framework that explicitly models bimanual coordination and scale adaptation, this work establishes a baseline for future research. The move away from absolute pose prediction toward relative, anchor-based regression, combined with decoupled optimization for data synthesis, offers a practical path toward robots that can reliably manipulate the large and complex objects found in human environments.

## Relevant Citations

- Bimanual grasp synthesis for dexterous robot hands: This paper is the primary point of comparison for the BiDexGrasp data synthesis pipeline. The authors explicitly state they compare their results against BimanGrasp, identifying it as the "only publicly available open-source bimanual grasp synthesis pipeline" and demonstrating significant improvements in grasp success rate and synthesis speed.
- Bodex: Scalable and efficient robotic dexterous grasp synthesis using bilevel optimization: This work is foundational to the methodology of the main paper. The BiDexGrasp synthesis pipeline is described as an extension of the framework proposed in BoDex, and the baseline for the ablation studies is a direct bimanual adaptation of this single-hand synthesis method.
- Dexgraspnet: A large-scale robotic dexterous grasp dataset for general objects based on simulation: DexGraspNet is a major large-scale single-hand dexterous grasping dataset that provides crucial context for the contributions of BiDexGrasp. The paper uses objects from DexGraspNet and directly compares its dataset statistics (e.g., number of objects, grasp count) against it in Table I to highlight its own scale and advancements in the bimanual domain.
- Dhagrasp: Synthesizing affordance-aware dual-hand grasps with text instructions: This is another key contemporary work on bimanual grasp synthesis that helps establish the state of the art. The BiDexGrasp paper compares its dataset against DHAGrasp in Table I to differentiate its contributions, particularly concerning the diversity of object sizes and the total number of grasps.
