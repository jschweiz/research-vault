# MedGemma 1.5 Technical Report

- alphaXiv: https://www.alphaxiv.org/abs/2604.05081
- Source paper: https://arxiv.org/abs/2604.05081

The MedGemma 1.5 Technical Report details the development and evaluation of an expanded collection of open-weight medical foundation models. While previous iterations established capabilities in 2D medical imaging and text-based clinical reasoning, MedGemma 1.5 is designed to address more complex, high-dimensional modalities. This includes volumetric 3D imaging, histopathology whole slide images (WSIs), and the temporal analysis of longitudinal patient records. By integrating these capabilities into a single $4\text{B}$ parameter architecture, the project provides a unified resource for medical AI development.

## 1. Introduction to MedGemma 1.5

Modern healthcare relies on a diverse array of data types, many of which extend beyond the simple 2D images typically used in computer vision research. Volumetric data from Computed Tomography (CT) and Magnetic Resonance Imaging (MRI), along with massive gigapixel-scale whole slide images from pathology, represent the bulk of diagnostic information in many clinical workflows. MedGemma 1.5 aims to bridge the gap between general-purpose multimodal models and the specific requirements of complex medical data.

![Overview of the MedGemma Collection and the capabilities of MedGemma 1.5](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05081v1/x1.png)
*Figure 1: The MedGemma collection landscape, highlighting the transition from 2D imaging and text to advanced modalities like 3D radiology, whole slide pathology, and anatomical localization in MedGemma 1.5.*

The primary motivation for this work is to provide the open-source community with a model capable of spatiotemporal awareness and fine-grained anatomical localization. Unlike previous versions, MedGemma 1.5 is specifically trained to recognize structures within 3D volumes and track disease progression across multiple timepoints. This advancement is achieved within an efficient $4\text{B}$ parameter framework, making the model accessible for local deployment and fine-tuning by researchers and developers.

## 2. Architectural Foundations

The architecture of MedGemma 1.5 is built upon the Gemma 3 foundation model. It employs a decoder-only transformer as its core language and reasoning engine, paired with a specialized vision encoder. The vision component uses a $400\text{M}$ parameter MedSigLIP encoder, which was pretrained on a vast corpus of medical image-text pairs to ensure a deep understanding of clinical visual semantics.

During the training of MedGemma 1.5, the MedSigLIP vision encoder was kept frozen to preserve its representational strengths, while the language decoder underwent extensive pretraining and instruction tuning. This allows the model to map complex visual features from the encoder into the linguistic space required for generating reports, answering clinical questions, and performing structured data extraction.

## 3. Bridging the Dimensionality Gap: 3D Radiology

One of the most significant technical hurdles in medical AI is the transition from 2D slices to 3D volumes. Standard vision encoders are designed for 2D RGB images, whereas CT and MRI scans consist of hundreds of grayscale axial slices. MedGemma 1.5 addresses this through a specific preprocessing and windowing strategy.

### 3.1. Volumetric Slicing and Tokenization
To process 3D data, volumes are converted into sequences of 2D axial images. Each slice is rescaled to the encoder’s input dimension of $896 \times 896$ pixels. To manage computational constraints and memory, the model enforces a slice cap. During training and evaluation, the number of axial slices per query is limited to a maximum of 85. This results in a substantial vision token budget:
$$
\text{Vision Tokens} = 85 \text{ slices} \times \text{tokens per slice} = 21,760
$$
If a volume exceeds this limit, the model employs equidistant sampling to ensure the entire anatomical region is represented within the token budget.

### 3.2. Multi-Channel Windowing for CT
CT scans use Hounsfield Units (HU) to represent tissue density, ranging from the very low density of air to the very high density of bone. To maximize the information captured by the 3D RGB encoder, MedGemma 1.5 uses multi-channel windowing, where different tissue density ranges are mapped to the Red, Green, and Blue channels:
*   **Red Channel**: A broad range of $(-1024, 1024)$ HU to capture general morphological boundaries and the contrast between air and bone.
*   **Green Channel**: A narrow soft-tissue window of $(-135, 215)$ HU to emphasize subtle textures in organs.
*   **Blue Channel**: A specific window of $(0, 80)$ HU designed for brain parenchyma, acute hemorrhages, and vascular calcifications.

This technique allows the model to "see" various clinical features simultaneously within a single RGB representation, despite the source data being grayscale.

## 4. Analyzing the Microscopic: Whole Slide Imaging (WSI)

Histopathology involves the examination of tissue slides at extreme resolutions. A single WSI can be gigapixels in size, far exceeding the input capacity of any standard neural network. MedGemma 1.5 implements a "patch-based" approach to process these slides.

First, a tissue segmentation algorithm identifies relevant regions on the slide at a lower magnification. Then, non-overlapping patches of $896 \times 896$ pixels are extracted. To provide the model with a comprehensive view, the pipeline stochastically selects a magnification level ($5\text{x}$, $10\text{x}$, or $20\text{x}$) for patch extraction.

The model enforces a cap of 126 patches per slide, totaling $32,256$ vision tokens. Crucially, these patches are presented to the model in their original spatial order. This preserves the relative positional context, allowing the language model to understand the architectural arrangement of the tissue, which is vital for cancer grading and diagnosis.

## 5. Enhancing Clinical Context: Localization and Longitudinal Tracking

Beyond classification, MedGemma 1.5 introduces fine-grained anatomical localization. This capability allows the model to output bounding boxes for specific structures or abnormalities on X-rays. In training, this is treated as a coordinate-generation task, where the model learns to identify regions of interest within the $896 \times 896$ coordinate space.

Furthermore, the model is trained on multi-timepoint radiology data. By taking a sequence of images from the same patient at different dates, the model can perform longitudinal analysis. It can identify if a nodule has grown, if a pleural effusion has resolved, or if a treatment is showing efficacy. This shift from "snapshot" analysis to "sequence" analysis mimics the actual workflow of clinical radiologists.

## 6. Training Methodology and Alignment

The development of MedGemma 1.5 involved three distinct stages: pretraining, distillation, and reinforcement learning (RL).

1.  **Pretraining**: The model was exposed to a massive mixture of general and medical-specific data. This included radiology reports, electronic health records (EHRs), and lab reports.
2.  **Distillation**: To boost the performance of the $4\text{B}$ model, knowledge was transferred from larger "teacher" models. This included domain-specific teachers specialized in CT, MRI, and pathology. The student model (MedGemma 1.5) was trained to match the output distribution (logits) of these specialized teachers.
3.  **Reinforcement Learning**: RL was used to align the model with human clinical preferences. This stage focused on improving the accuracy of medical document understanding and ensuring that the model's visual interpretations matched the reasoning patterns of clinical experts.

## 7. Performance Analysis and Comparative Benchmarking

MedGemma 1.5 was evaluated against its predecessor and other state-of-the-art models. The results demonstrate substantial gains in the newly introduced multimodal tasks.

![Comparison of MedGemma 1.5 and MedGemma 1.0 across various tasks](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05081v1/x2.png)
*Figure 2: Performance comparison between MedGemma 1.5 4B and MedGemma 1.0 4B across text-based reasoning and complex imaging tasks.*

### 7.1. Multimodal Gains
On the internal MRI and CT classification datasets, MedGemma 1.5 showed absolute accuracy improvements of $11\%$ and $3\%$, respectively, over the $4\text{B}$ parameter baseline. The impact was even more pronounced in histopathology; for WSI report generation, the model achieved a ROUGE-L score of $49.4$, compared to just $4.1$ for the previous version.

In anatomical localization, the Mean Intersection over Union (IoU) on the Chest ImaGenome dataset increased from $3.1$ to $38.0$. This indicates a much more precise ability to identify and bound anatomical structures.

### 7.2. Clinical Knowledge and Document Understanding
The model also saw improvements in text-centric benchmarks:
*   **MedQA**: Accuracy rose from $64.4\%$ to $69.1\%$.
*   **EHRQA**: Accuracy increased significantly from $67.6\%$ to $89.6\%$.
*   **Lab Report Extraction**: The Macro F1 score on EHR lab report datasets improved dramatically, with one dataset seeing a jump from $25\%$ to $64\%$.

### 7.3. Trade-offs and Limitations
The report notes that specializing a $4\text{B}$ parameter model for intensive medical tasks can lead to "catastrophic forgetting" in general domains. For example, performance on the MMLU Pro benchmark (a measure of general knowledge) dropped from $39.1\%$ to $33.8\%$. Additionally, minor regressions were observed in some legacy Visual Question Answering (VQA) benchmarks like SLAKE, where scores fell from $72.3$ to $59.8$. These trade-offs suggest that the model's capacity is being redirected toward specialized clinical reasoning.

## 8. Qualitative Analysis

To understand the model's practical utility, the report provides examples of its reasoning process. Figure 3 illustrates a scenario where the model analyzes a 3D CT volume to identify a liver mass.

![Qualitative example of MedGemma 1.5 analyzing a CT volume](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05081v1/x3.png)
*Figure 3: A qualitative demonstration showing MedGemma 1.5's ability to analyze multiple slices of a CT scan, provide a reasoning-based response, and have its output evaluated by a board-certified radiologist.*

In this example, the model identifies a "large, irregular mass in the right lobe of the liver" and describes its heterogeneity. While a board-certified radiologist agreed with the primary diagnosis, they noted that the model incorrectly identified biliary ductal dilation. This highlights the model's role as a foundational data processing tool that still requires clinical oversight, rather than a standalone diagnostic system.

## 9. Significance and Concluding Observations

MedGemma 1.5 represents a move toward more comprehensive medical foundation models. By providing an open-weight model that natively supports 3D volumes, gigapixel pathology slides, and longitudinal tracking, Google Research and Google DeepMind have provided a tool for the broader research community.

The model’s significance lies in its ability to:
1.  **Process High-Dimensional Data**: It successfully adapts 2D vision architectures to handle 3D and high-resolution clinical data through clever preprocessing and tokenization.
2.  **Enable Complex Clinical Tasks**: Capabilities like anatomical localization and longitudinal analysis move medical AI closer to real-world clinical workflows.
3.  **Provide an Open Foundation**: As an open-weight $4\text{B}$ model, it serves as an accessible baseline that researchers can fine-tune for specific, niche clinical applications.

While the model shows clear improvements in specialized medical tasks, the observed trade-offs in general reasoning highlight the challenges of model specialization. MedGemma 1.5 is presented not as a final clinical solution, but as a robust foundational component designed to accelerate the development of next-generation healthcare AI.

## Relevant Citations

- Medgemma technical report: This is the technical report for MedGemma 1, the direct predecessor model. The main paper introduces MedGemma 1.5 as an update and makes numerous direct comparisons in architecture, training data, and performance benchmarks to this original work, making it fundamentally important for context.
- Gemma 3 technical report: The main paper explicitly states that MedGemma 1.5 is based on the Gemma 3 architecture. This citation is crucial as it details the foundational text model that MedGemma 1.5 adapts and specializes for the medical domain.
- Learning to exploit temporal structure for biomedical vision-language processing: This paper introduces the MS-CXR-T dataset, which MedGemma 1.5 uses to evaluate its new capability for multi-timepoint (longitudinal) chest X-ray analysis. This citation is directly relevant to validating one of the key novel contributions of the MedGemma 1.5 model.
- Chest imagenome dataset: This paper provides the dataset used to evaluate anatomical localization, a major new capability introduced in MedGemma 1.5. The model's significant improvement in Intersection over Union (IoU) on this dataset is a key result highlighted in the report.
- Polypath: Adapting a large multimodal model for multi-slide pathology report generation: This work is central to the new whole-slide image (WSI) pathology capabilities of MedGemma 1.5. It is cited for the custom tissue segmentation algorithm used in preprocessing and as the state-of-the-art performance benchmark against which MedGemma 1.5 is compared for pathology report generation.
