# Full-Duplex-Bench-v3: Benchmarking Tool Use for Full-Duplex Voice Agents Under Real-World Disfluency

- alphaXiv: https://www.alphaxiv.org/abs/2604.04847
- Source paper: https://arxiv.org/abs/2604.04847

## The Evolution of Spoken AI Agents

The transition of Artificial Intelligence from text-based interfaces to interactive voice assistants represents a shift toward more natural human-computer interaction. While Large Language Models (LLMs) have become proficient at using external tools—such as checking a bank balance or booking a flight—through Application Programming Interfaces (APIs), bringing these capabilities to real-time voice agents introduces significant technical hurdles. Most existing voice systems operate in a "half-duplex" mode, where the user and the machine take turns speaking in a rigid sequence. In contrast, "full-duplex" agents can listen and speak simultaneously, allowing for interruptions and a more fluid conversational flow.

![Full-Duplex-Bench-v3 Overview](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04847v1/FDBv3.drawio.png)
*Figure 1: The Full-Duplex-Bench-v3 (FDB-v3) framework evaluates voice agents on their ability to execute multi-step tool calls while handling natural human speech phenomena such as fillers and self-corrections.*

This research introduces Full-Duplex-Bench-v3 (FDB-v3), a benchmark designed to evaluate how modern voice agents handle tool use under real-world conditions. Unlike previous benchmarks that often relied on synthetic, computer-generated voices, FDB-v3 utilizes authentic human audio recordings. These recordings include "disfluencies"—the natural stammers, pauses, and corrections that characterize human speech—to test the robustness of an agent's reasoning and its ability to execute complex tasks in real-time.

## Bridging the Gap: From Textual Logic to Verbal Interaction

In text-based environments, AI agents have ample time to process a prompt, reason through steps, and call tools. The input is usually clean and finalized. However, when an agent moves into the realm of spoken dialogue, it faces two primary challenges: latency and acoustic ambiguity. To feel natural, a voice agent must respond within milliseconds, yet it must also be accurate enough to avoid making permanent mistakes, such as booking a non-refundable ticket based on an incomplete sentence.

Current approaches to building voice agents typically fall into two categories. The "cascaded" approach pipes several models together: a Speech-to-Text (STT) model transcribes the audio, an LLM processes the text and decides on an action, and a Text-to-Speech (TTS) model generates the reply. While reliable, this chain introduces significant delays. The emerging "end-to-end" or speech-to-speech (S2S) models process audio signals directly into spoken responses. While these models are faster and can capture emotional nuances, they are often less transparent and can be more susceptible to errors caused by the messy nature of human speech. FDB-v3 provides a structured way to compare these different architectures.

## The Complexity of Human Speech: Disfluencies

One of the defining features of FDB-v3 is its focus on disfluencies. In a controlled laboratory setting, a user might say, "Please book me a flight to New York." In reality, a user might say, "Um, can you book me a flight to... let's see... New York? No, wait, I mean Boston." 

FDB-v3 categorizes these phenomena into five specific types to pinpoint where AI models fail:
*   **False Starts**: When a user begins a thought, abandons it, and starts a completely different request. The agent must discard the initial context to avoid executing incorrect tools.
*   **Self-Corrections**: When a user changes a specific detail (like a destination or a price range) mid-sentence. This requires "state rollback," where the agent must update its internal plan before calling an API.
*   **Fillers**: Words like "um" or "uh" that convey no information but maintain the floor. These can confuse some models, causing them to hallucinate tool parameters or delay their response.
*   **Pauses**: Silent intervals within a turn. A model that is too "eager" might interpret a pause as the end of the turn and interrupt the user.
*   **Hesitations**: Combinations of fillers and repetitions that test whether the agent can maintain focus on the core request.

By annotating 100 scenarios with these disfluencies across a variety of speakers, the benchmark creates a rigorous testbed for "dynamic state updates," ensuring that agents are not just following instructions but are actively listening and adapting to the user's evolving intent.

## Designing Realistic Agentic Tasks

To evaluate an agent’s practical utility, FDB-v3 employs a set of mock APIs across four distinct domains: Travel & Identity, Finance & Billing, Housing & Location, and E-Commerce Support. These APIs are deterministic—meaning they provide consistent, predictable outputs—which allows for objective scoring of the agent's decisions.

The benchmark organizes tasks into three levels of difficulty:
1.  **Easy**: Single-step tool calls with clear instructions.
2.  **Medium**: Two-step tasks requiring the agent to use the output of one tool as the input for another.
3.  **Hard**: Complex, multi-step chains with conflicting constraints or multiple required entity lookups.

For example, a "Hard" task in the Finance domain might involve checking a user's account balance, verifying their identification, and then authorizing a multi-part payment, all while the user is providing the information disfluently. This setup ensures that the benchmark tests not only the speech processing but also the underlying logical reasoning of the agent.

## Multi-Dimensional Evaluation Framework

Evaluating a voice agent requires more than just checking if it got the right answer. FDB-v3 uses a comprehensive set of metrics to capture the nuances of the interaction.

**Tool-Use Performance**
The core of the evaluation is based on whether the agent invoked the correct tools with the correct parameters. This is measured via:
*   **Tool Selection F1**: A balance between correctly identifying the needed tools and avoiding unnecessary ones.
*   **Argument Accuracy**: A measure of how well the agent extracted specific details (like dates or account numbers) from the audio.
*   **Task Completion ($\text{Pass@1}$)**: A strict binary metric. A scenario is only marked successful if every tool call and every argument is perfect.

**Turn-Taking and Latency**
In a full-duplex conversation, timing is everything. The benchmark measures:
*   **Turn-take rate**: How often the agent successfully provides a relevant response when the user stops speaking.
*   **Interruption rate**: How often the agent speaks over the user before they have finished their thought.
*   **Latency Decomposition**: To understand why an agent is slow, FDB-v3 breaks down the time spent into three parts:
    *   **First Word Latency**: The time until the agent makes any sound.
    *   **Tool Call Latency**: The time until the agent initiates the API call.
    *   **Task Completion Latency**: The total time until the agent delivers the final, factual result to the user.

If we denote the start time of the agent's response as $t_{\text{agent\_start}}$ and the end of the user's utterance as $t_{\text{user\_end}}$, the base latency is calculated as:
$$\Delta t = t_{\text{agent\_start}} - t_{\text{user\_end}}$$
If $\Delta t$ is negative, it indicates an interruption.

## Comparative Performance Analysis

The researchers tested several prominent models, including OpenAI's GPT-Realtime, Google's Gemini Live (versions 2.5 and 3.1), and open-weight models like Ultravox. They also included a "Cascaded" baseline using Whisper for transcription and GPT-4o for reasoning.

The results highlighted a clear trade-off between speed and correctness. GPT-Realtime emerged as the most accurate model, leading in tool selection and task completion ($\text{Pass@1}$ of $0.600$). However, Gemini Live 3.1 was significantly faster, achieving the lowest task completion latency ($4.25$ seconds compared to GPT-Realtime's $6.89$ seconds). 

A critical finding was the shared difficulty across all models in handling self-corrections. Even the most advanced models frequently "locked in" an incorrect parameter if the user corrected themselves late in the sentence. For instance, in a scenario where a user changed a travel destination, many agents had already initiated the search for the first destination before the user finished the correction. This "eagerness" is a byproduct of trying to minimize latency, but it leads to errors in dynamic environments.

The "Cascaded" system proved to be the most reliable at taking turns (a $100\%$ turn-take rate) but was by far the slowest, with a latency of over $10$ seconds. This confirms that while modular pipelines are robust, they struggle to meet the real-time demands of fluid conversation.

## Implications for Future Voice AI

The FDB-v3 benchmark reveals that the current frontier of voice AI is not just about making models faster, but about making them more flexible listeners. The "silent worker" phenomenon—where a model like Gemini Live 3.1 executes tools correctly but fails to speak to the user in complex situations—points to a disconnect between an agent's reasoning and its communicative layers.

Furthermore, the high interruption and filler rates seen in models like Ultravox suggest that using "filler speech" (saying things like "Let me check that for you...") is a common strategy to mask processing time. However, if these fillers are deployed incorrectly, they can disrupt the user and degrade the overall experience.

In conclusion, FDB-v3 provides a rigorous framework for identifying these specific failure modes. By moving the evaluation of voice agents into the messy, disfluent reality of human speech, the benchmark sets a standard for the next generation of assistants that must balance the need for speed with the necessity of being a careful, adaptive listener. Success in this domain will require agents that can not only understand what we say but also recognize when we change our minds.

## Relevant Citations

- Full-duplex-bench-v2: A multi-turn evaluation framework for duplex dialogue systems with an automated examiner: This paper is the direct predecessor to the work being presented. FDB-v3 is an explicit extension of the Full-Duplex-Bench series, and this citation provides the necessary context for the new version's contributions, which are adding real human audio and multi-step tool use.
- Voiceagentbench: Are voice assistants ready for agentic tasks?: This citation is used as a key point of contrast to highlight a gap in existing research. The authors mention that VoiceAgentBench evaluates complex tool-use but relies on synthetic audio, which justifies their paper's focus on using authentic, disfluent human speech.
- Audio multichallenge: A multi-turn evaluation of spoken dialogue systems on natural human interaction: This paper is cited to demonstrate the limitations of benchmarks that use real speech but lack tool-use evaluation. By referencing this work, the authors establish the novelty of FDB-v3, which uniquely combines authentic human speech with complex, multi-step tool-use scenarios.
- Pauses, gaps and overlaps in conversations: This foundational paper is cited in the introduction to provide the scientific rationale for why latency is a critical evaluation metric. It establishes that a spoken reply must arrive within a narrow time window to feel natural, grounding the paper's focus on latency and turn-taking in established research.
