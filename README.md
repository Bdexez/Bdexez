<p align="center">
  <img src="./assets/header.svg?v=4" width="100%" alt="Bdex — Python, artificial intelligence, neural networks, C/C++, graphics and systems.">
</p>

<p align="center">
  <a href="#real-time-graphics--systems">Framegen</a>
  &nbsp; · &nbsp;
  <a href="#python-artificial-intelligence--neural-networks">Python &amp; AI</a>
  &nbsp; · &nbsp;
  <a href="#full-stack-development">Full-stack</a>
  &nbsp; · &nbsp;
  <a href="#technical-stack">Technical stack</a>
</p>

<br>

I'm **Bdex**. I develop in **Python, C/C++ and TypeScript**, with projects in **artificial intelligence, neural networks, local LLM agents, real-time graphics and full-stack software**.

My work ranges from implementing learning algorithms and building AI assistants to generating frames on the GPU and developing business applications. Below is what each project does and how I approach its implementation.

## Projects at a glance

| Project | Focus | Source |
| :--- | :--- | :--- |
| [**bdex-framegen**](https://github.com/Bdexez/bdex_frame_gen) | GPU frame generation, Vulkan injection and capture | Public |
| [**bdex Game Engine**](https://github.com/Bdexez/bdex_game_engine) | Modular 3D engine, ECS and Vulkan rendering | Public |
| [**CHIMERA**](https://github.com/Bdexez/Neural_Network_November) | Multimodal neural network for text, vision and time series | Public · experimental |
| [**Sensai**](#sensai--local-ai-tutor-and-study-assistant) | Local LLM tutor, RAG and learning agents | Private |
| [**MyTorch**](#mytorch--neural-network-library-and-chess-analyzer-in-c17) | C17 neural-network library, chess analysis and learning demos | Private · completed |
| [**cs2edge**](https://github.com/Bdexez/Cs2edge) | Probabilistic CS2 modelling and calibration | Public |
| [**BAD**](https://github.com/Bdexez/BAD_-Bdex_Anomaly_Detector-) | Linux telemetry and labelled anomaly datasets | Public |
| [**Up Network**](#up-network--multi-company-erp--crm) | Multi-company ERP / CRM | Private |

## Real-time graphics & systems

### bdex-framegen — Frame generation for Vulkan games on Linux

`C++20` · `Vulkan` · `GLSL` · `Linux` · `Windows capture`

[**Explore the repository →**](https://github.com/Bdexez/bdex_frame_gen)

An implicit Vulkan layer that sits between a game and the graphics driver. It estimates motion between rendered frames and synthesizes intermediate images to improve displayed fluidity, without changing the game's code. It targets native Vulkan games and Direct3D games translated through DXVK or VKD3D-Proton. The shared GPU engine also supports capture-based output, with interpolation, extrapolation and hybrid generation modes.

- **Presentation control:** a virtual swapchain separates the images the game renders from the real swapchain presented to the display.
- **GPU image processing:** compute shaders build a luma pyramid, estimate optical flow with hierarchical block matching, refine motion and synthesize images with bidirectional warping.
- **Separate presentation work:** a dedicated thread handles presentation and pacing; a separate compute queue is used when available.
- **Quality and correctness:** generated frames are compared with real frames and simple baselines; Vulkan validation, synchronization checks and scene-cut handling help identify rendering errors and interpolation limits.

### bdex Game Engine — Modular 3D engine with a Vulkan backend

`C++23` · `Vulkan 1.3` · `GLSL` · `ECS` · `CMake` · **In development**

[**Explore the repository →**](https://github.com/Bdexez/bdex_game_engine)

A 3D engine built around a small kernel and replaceable modules. Windowing, graphics backends and rendering implement separate interfaces, so the same application can run in a window, render offscreen or execute its simulation without a GPU.

- **Module architecture:** runtime plugins, dependency resolution, a service registry and an event bus connect engine components through explicit interfaces.
- **Simulation and scenes:** an entity component system with generational handles, hierarchical transforms, fixed-timestep updates and a multithreaded job system.
- **Vulkan rendering:** dynamic rendering, synchronization2, Vulkan Memory Allocator and an extensible forward renderer provide textured meshes, materials and directional lighting.
- **Assets and validation:** OBJ/TGA/SPIR-V loading, procedural geometry, a 3D sandbox and GoogleTest unit/integration tests; offscreen Vulkan and a null backend support headless execution.

## Python, artificial intelligence & neural networks

### CHIMERA — Multimodal neural network for text, vision and time series

`Python` · `PyTorch` · `Mixture of Experts` · `Multimodal learning` · **Experimental**

[**Explore the repository →**](https://github.com/Bdexez/Neural_Network_November)

A trainable neural architecture that combines text generation, image classification and time-series forecasting in one model. Image and temporal encoders feed a shared decoder, and the three input modalities can be used individually, in pairs or together. The repository documents joint training of a **549M-parameter configuration on synthetic data**.

- **Multimodal fusion:** cross-attention compresses visual and temporal features into learned latents that condition the decoder and task heads.
- **Attention and expert routing:** grouped-query attention, rotary positions, gated causal convolutions and top-k routing combine specialized SwiGLU experts with a shared expert branch.
- **Task-specific outputs:** byte-level text generation, classification and ordered forecast quantiles, with masking for missing temporal values.
- **Training and reproducibility:** gradient accumulation, activation checkpointing, validation and early stopping, resumable optimizer/RNG state and distributed training support. The repository includes synthetic benchmarks and tests for causality, gradients and single-process resume equivalence.

### Sensai — Local AI tutor and study assistant

`Python` · `LLMs` · `Ollama` · `RAG` · `SQLite`

A language-learning assistant available in the terminal and through its **Duolingoy** web interface. It generates short exercises, corrects mistakes, remembers learner progress and can turn course material into revision sheets and Python quizzes.

- **Local LLM integration:** direct calls to Ollama's HTTP API, streamed responses, conversation history and a managed context budget, without an LLM orchestration framework.
- **Document-grounded answers:** a RAG pipeline indexes lessons and retrieves relevant passages using embeddings, cosine similarity, BM25, metadata filters and reranking.
- **Persistent learning memory:** SQLite stores sessions, vocabulary, recurring mistakes and spaced-repetition progress.
- **Agent capabilities:** a ReAct loop can read permitted files, prepare materials and test generated Python exercises, with action confirmations, execution limits and observability.

### MyTorch — Neural-network library and chess analyzer in C17

`C17` · `Neural networks` · `Backpropagation` · `Adam` · **Completed**

A completed C17 implementation of a neural-network library, a chess-position classifier and AND/XOR/tic-tac-toe learning demos. Forward propagation, backpropagation, Adam optimization, data generation and SVG plots are implemented in C, with shell scripts automating the workflow. The reusable API is packaged as `libmytorch.a`.

- **Configurable learning core:** multilayer networks, ReLU/tanh/sigmoid hidden activations, softmax or sigmoid outputs, mini-batch training, L2 regularization and early stopping. Optional CBLAS accelerates matrix products, with a built-in C fallback.
- **Chess analysis:** parses six-field FEN positions and classifies `Nothing`, `Check` and `Checkmate`; output also identifies the side giving check or mate.
- **Reproducible evaluation:** normalized positions are deduplicated before a stratified 70/15/15 training/validation/test split. The project benchmark reports **100% accuracy on its 16,044-position held-out chess test set**.
- **Learning demonstrations:** a perceptron for AND, a multilayer network for XOR and a tic-tac-toe classifier built from all **5,478 legal board states**, with separate data partitions.
- **Engineering and validation:** atomic model serialization, hyperparameter search, CSV/SVG reports, numerical gradient checks and CLI tests, plus AddressSanitizer and UndefinedBehaviorSanitizer build targets.

### cs2edge — Calibrated CS2 match prediction

`Python` · `NumPy` · `Machine learning` · `Probability calibration`

[**Explore the repository →**](https://github.com/Bdexez/Cs2edge)

A probabilistic model that estimates the outcome of professional CS2 matches. Its central question is whether its stated confidence matches observed outcomes: predictions around 70% should correspond to wins around 70% of the time. The bundled examples and tests use synthetic match history.

- **Model implemented by hand:** ridge logistic regression solved with IRLS, followed by temperature calibration, using a NumPy-only core.
- **Consistent probabilities:** the model enforces the relationship between the two opposing outcomes, so their probabilities sum to one.
- **Chronological evaluation:** walk-forward backtesting trains on earlier matches and evaluates later ones, preserving the order in which information becomes available.
- **Selective predictions:** the system can abstain when confidence is insufficient and records its predictions to compare announced probabilities with actual results.

### BAD — Linux telemetry for hardware anomaly detection

`Python` · `SQLite` · `Linux` · `Data collection`

[**Explore the repository →**](https://github.com/Bdexez/BAD_-Bdex_Anomaly_Detector-)

A hardware telemetry collector designed to build labelled datasets for anomaly detection: obstructed airflow, cooling problems or unstable overclocks. The implemented collection stage supplies the contextual data needed before training a detection model.

- **Multi-source collection:** independent readers gather sensor values, hardware counters and kernel events through Linux interfaces such as `/proc` and `/sys`.
- **Resilient acquisition:** unavailable sources disable themselves; the collector keeps running when a sensor is missing.
- **Error analysis:** kernel classification rules and hardware counters capture complementary evidence of faults.
- **Explicit coverage:** a diagnostic command explains which sources the machine exposes and which problems can or cannot be observed. The collector has no mandatory third-party dependencies.
- **Dataset workflow:** experiment labels, consistent CSV exports, data-quality reports and online SQLite backups support collection and analysis.

## Full-stack development

### Up Network — Multi-company ERP / CRM

`TypeScript` · `NestJS` · `React` · `Prisma` · `PostgreSQL`

A management suite for SMEs, developed during a six-month internship. It covers customer relationships, sales, purchasing, inventory, projects, HR and accounting reports, with several companies operating within the same application.

- **Complete business workflows:** quotes progress into orders, invoices and payments, with credit notes and multi-currency support.
- **Backend access control:** permissions are enforced server-side and the active company comes from the authenticated token.
- **Data consistency:** PostgreSQL and Prisma model the business entities; optimistic locking protects finalized documents against conflicting changes.
- **Delivery and validation:** a React interface, documented REST API, unit tests and reporting features including aged balances, VAT breakdowns and FEC export.

## Technical stack

| Area | Technologies & concepts |
| :--- | :--- |
| **Python** | Python · NumPy · PyTorch · pandas · SQLite · Streamlit |
| **Artificial intelligence** | Neural networks · Multimodal learning · Mixture of Experts · Machine learning · Probabilistic modelling · Calibration · Walk-forward evaluation |
| **LLMs & agents** | Ollama · RAG · Embeddings · BM25 · Reranking · ReAct · Context management |
| **Systems & graphics** | C17 · C++20/23 · Vulkan · GLSL compute · ECS · Linux · CMake |
| **Web & backend** | TypeScript · React · NestJS · Node.js · Prisma · PostgreSQL · REST APIs |
| **Tools** | Git · Docker · systemd · Make · AddressSanitizer · UndefinedBehaviorSanitizer |

<sub>Public projects link directly to their source repositories. Sensai, MyTorch and Up Network are presented here with private source code.</sub>
