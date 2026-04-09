# Gym-Anything: Turn any Software into an Agent Environment

- alphaXiv: https://www.alphaxiv.org/abs/2604.06126
- Source paper: https://arxiv.org/abs/2604.06126

The development of computer-use agents (CUAs)—AI systems capable of navigating graphical user interfaces (GUIs) to perform digital tasks—is a major focus in artificial intelligence. However, current research is often limited by the scope of existing benchmarks. Most current environments focus on short-horizon tasks in a small number of consumer applications, such as changing a desktop background or filling out a simple web form. These tasks do not reflect the complexity of professional software used in the global economy, where workflows may involve hundreds of steps and specialized domain knowledge.

The primary barrier to progress is the high cost of environment creation. Manually installing software, configuring it with realistic data, and designing verifiable tasks can take weeks of expert human effort per application. Gym-Anything addresses this scalability bottleneck by introducing a framework for the automated creation of interactive environments and tasks across a wide array of software, grounded in their economic relevance.

## The Gym-Anything Framework

At the core of this work is the Gym-Anything library, which standardizes the process of turning software into an interactive agent environment. To ensure modularity and scalability, the framework abstracts environment creation into three sequential setup scripts: $install$, $configure$, and $task\_setup$. These are accompanied by a declarative configuration file, $env.json$.

The $install$ script handles the base installation of the software. The $configure$ script populates the environment with domain-specific, realistic data (e.g., medical records for a healthcare app or financial logs for accounting software). Finally, the $task\_setup$ script prepares the environment for a specific goal. This separation allows researchers to reuse the installation and configuration logic across thousands of different tasks.

Gym-Anything provides a unified Gymnasium-style API that handles complex backend operations across multiple operating systems, including Linux, Windows, and Android. It manages container orchestration (using Docker or Apptainer), display forwarding, and checkpointing. Agents interact with these environments through a standard interface: they receive visual observations (screenshots) and execute actions via keyboard and mouse inputs.

## Grounding Software Selection in Economic Value

To ensure that the research contributes to solving real-world problems, the authors developed a systematic approach to selecting software based on its contribution to the Gross Domestic Product (GDP). Rather than choosing software based on popularity or ease of automation, they identified applications that drive significant economic activity.

The selection process involves several steps:
1.  **GDP Estimation:** Using data from O*NET and the Bureau of Labor Statistics, the authors estimated the GDP attributed to approximately 900 U.S. occupations.
2.  **Software Discovery:** For each occupation, large language models (LLMs) with web-search capabilities identified relevant software categories and specific applications.
3.  **GDP Attribution:** The GDP of an occupation was decomposed and attributed to specific software based on the fraction of computer-based work and the software's market share within its category.
4.  **Filtering:** The software was filtered to ensure it could be "sandboxable"—meaning it is self-hostable, has a GUI, and does not require specialized hardware that cannot be simulated.

This resulted in a tiered selection of 200 software applications covering all 22 major U.S. Standard Occupational Classification groups, including high-GDP software in healthcare, STEM, and finance.

## The Multi-Agent Creation Pipeline

The most labor-intensive part of building environments—writing the setup scripts and verifying the installation—is automated through a multi-agent "Creation-Audit" loop. This process uses two distinct agents to reduce bias and ensure quality.

The Creation Agent, $Agent_C$, is responsible for researching the software, downloading data, implementing the setup scripts, and launching the environment. Crucially, $Agent_C$ is tasked with providing "evidence" of a successful setup, such as specific execution logs or screenshots of the GUI in its configured state.

The Audit Agent, $Agent_{audit}$, acts as an independent reviewer. It evaluates the evidence produced by $Agent_C$ against a predefined quality checklist. If the environment fails the audit, $Agent_{audit}$ provides feedback, and $Agent_C$ attempts to fix the issues. This adversarial relationship helps prevent "self-confirmation bias," where a single agent might overlook its own mistakes.

To improve efficiency over time, the system uses a shared memory $M$. $Agent_C$ stores specific learnings in $M_{soft}$ (software-specific) and $M_{general}$ (general principles). A Memory Summarization Agent, $Agent_{summ}$, periodically condenses these logs to help the system learn general rules for environment creation, such as how to handle common installation errors or how to bypass specific GUI configuration prompts.

## Scaling Task Generation: Propose-and-Amplify

Once an environment is established, it needs diverse and realistic tasks. The researchers use a two-step "Propose-and-Amplify" strategy to generate these tasks at scale.

In the **Propose** phase, a high-capability agentive model explores the software GUI to create a small set of "seed tasks." These tasks are designed to be difficult and representative of professional use cases. Because the agent actually interacts with the software, the tasks are grounded in functional reality.

In the **Amplify** phase, a more cost-effective, non-agentive model uses these seed tasks as in-context examples to generate thousands of additional tasks. To maintain diversity, the model generates tasks sequentially while considering previously generated instructions. Finally, an automated filtering step uses a Vision-Language Model (VLM) to verify that the initial state of the software actually matches the task description.

## Robust and Granular Task Verification

Evaluating an agent on a 500-step task is more difficult than evaluating it on a 5-step task. A simple success/failure binary is often insufficient for long-horizon work. Gym-Anything implements a robust verification system based on three components:

1.  **Privileged Information ($I$):** This consists of ground-truth data extracted directly from the environment setup scripts (e.g., a specific database entry or a file hidden in a directory). This information is used by the verifier but remains hidden from the agent performing the task.
2.  **Checklist-based VLM Verifier:** A VLM uses the task instructions and $I$ to generate a checklist $C$. It then reviews the agent's trajectory $\tau$ and assigns partial credit based on how many sub-goals were completed. This approach achieved a 93.3% agreement rate with human annotators.
3.  **Integrity Checklist ($C_{int}$):** To prevent agents from "cheating" by bypassing the GUI (e.g., using a terminal to move a file instead of using the software's internal menu), an integrity check ensures the agent followed the intended workflow. If an agent fails $C_{int}$, it receives a zero score regardless of whether the final goal was achieved.

## CUA-World Benchmarks and Agent Performance

The application of this framework resulted in two major benchmarks: **CUA-World** (over 10,000 tasks across 200 apps) and **CUA-World-Long** (200 extremely long-horizon tasks).

The performance of state-of-the-art models on these benchmarks reveals the current limitations of AI agents. On CUA-World-Test, frontier models like Gemini 3 Flash achieve a pass rate of approximately 22.6%. On the more challenging CUA-World-Long, where tasks can require over 500 steps, the pass rate drops significantly to 7.5% under standard constraints.

The research also explored "Distillation," where successful trajectories from a strong teacher model were used to train a smaller 2B parameter student model. This training led to a significant improvement in the student's performance, allowing it to outperform models twice its size. This suggests that the CUA-World dataset provides a valuable training signal for improving the reasoning and execution capabilities of smaller, more efficient agents.

## Insights and Behavioral Analysis

The study provides several insights into how agents succeed or fail in complex environments:
*   **Retry Loops:** Failed trajectories are characterized by high levels of "retry loops," where an agent repeats the same unsuccessful action multiple times.
*   **Self-Verification:** Successful agents are more likely to perform "verification checks" (e.g., checking if a file saved correctly) during their workflow.
*   **Test-Time Auditing (TTA):** The researchers found that using an independent VLM to audit the agent's progress during execution—and providing feedback if a sub-task was missed—improved pass rates. This helps mitigate "premature stopping," a common issue where agents believe they have finished a task when they have actually missed a crucial step.

## Significance of the Work

Gym-Anything provides the first scalable pipeline for creating interactive, economically grounded environments for computer-use agents. By automating the environment setup and task generation process, it allows the research community to move beyond simplified web tasks and toward the complex, long-horizon workflows that define professional digital work. The release of the CUA-World benchmark provides a rigorous testing ground for the next generation of AI agents, highlighting the need for better planning, more robust self-verification, and improved visual reasoning in complex software interfaces.

## Relevant Citations

- OSWorld: Benchmarking multimodal agents for open-ended tasks in real computer environments.: This paper introduced OSWorld, a key prior interactive benchmark for computer-use agents on desktop operating systems. Gym-Anything directly compares its CUA-World benchmark against OSWorld to demonstrate its significant improvements in scale, task diversity, economic coverage, and automated environment creation.
- WebArena: A realistic web environment for building autonomous agents.: WebArena is cited as a prominent example of existing interactive benchmarks that focus on a narrow set of web-based tasks. The Gym-Anything paper uses it as a point of contrast to highlight its own framework's ability to create environments from a much broader and more economically significant range of software beyond web browsers.
- Mind2Web: Towards a generalist agent for the web.: This paper is referenced as a large-scale static dataset for web agents. The Gym-Anything paper contrasts its interactive, execution-based evaluation approach with the action-matching evaluation used in static datasets like Mind2Web, arguing that interactive environments provide a more faithful assessment of an agent's capabilities.
- AndroidWorld: A dynamic benchmarking environment for autonomous agents.: AndroidWorld is a key interactive benchmark for agents on the Android platform. It is used as a direct comparison point in Table 2 to demonstrate CUA-World's superior scale in software diversity and task count, and to show that Gym-Anything's framework can handle multiple operating systems, including mobile.
