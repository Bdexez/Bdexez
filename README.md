<p align="center">
  <img src="./assets/header.svg?v=4" width="100%" alt="Bdex — Python, artificial intelligence, neural networks, C/C++, graphics and systems.">
</p>

<p align="center">
  <a href="#python-artificial-intelligence--neural-networks">Python &amp; AI</a>
  &nbsp; · &nbsp;
  <a href="#real-time-graphics--systems">Graphics &amp; systems</a>
  &nbsp; · &nbsp;
  <a href="#full-stack-development">Full-stack</a>
  &nbsp; · &nbsp;
  <a href="#technical-stack">Technical stack</a>
</p>

<br>

I'm **Bdex**. I develop in **Python, C/C++ and TypeScript**, with projects in **artificial intelligence, neural networks, local LLM agents, real-time graphics and full-stack software**.

My work ranges from implementing learning algorithms and building AI assistants to generating frames on the GPU and developing business applications. Below is what each project does and how I approach its implementation.

## Python, artificial intelligence & neural networks

### Sensai — Local AI tutor and study assistant

`Python` · `LLMs` · `Ollama` · `RAG` · `SQLite`

A language-learning assistant available in the terminal and through its **Duolingoy** web interface. It generates short exercises, corrects mistakes, remembers learner progress and can turn course material into revision sheets and Python quizzes.

- **Local LLM integration:** direct calls to Ollama's HTTP API, streamed responses, conversation history and a managed context budget, without an LLM orchestration framework.
- **Document-grounded answers:** a RAG pipeline indexes lessons and retrieves relevant passages using embeddings, cosine similarity, BM25, metadata filters and reranking.
- **Persistent learning memory:** SQLite stores sessions, vocabulary, recurring mistakes and spaced-repetition progress.
- **Agent capabilities:** a ReAct loop can read permitted files, prepare materials and test generated Python exercises, with action confirmations, execution limits and observability.

### MyTorch — Neural-network library from scratch

`Python` · `NumPy` · `Neural networks` · **In progress**

A neural-network library implemented from first principles to deepen my understanding of machine learning. The focus is on implementing the underlying mechanisms and understanding how models are built and evaluated.

This work combines **Python/NumPy implementation** with study of the machine-learning literature. It is an ongoing project focused on neural-network fundamentals, alongside my application-oriented AI projects.

### cs2edge — Calibrated CS2 match prediction

`Python` · `NumPy` · `Machine learning` · `Probability calibration`

A probabilistic model that estimates the outcome of professional CS2 matches. Its central question is whether its stated confidence matches observed outcomes: predictions around 70% should correspond to wins around 70% of the time.

- **Model implemented by hand:** ridge logistic regression solved with IRLS, followed by temperature calibration, using a NumPy-only core.
- **Consistent probabilities:** the model enforces the relationship between the two opposing outcomes, so their probabilities sum to one.
- **Chronological evaluation:** walk-forward backtesting trains on earlier matches and evaluates later ones, preserving the order in which information becomes available.
- **Selective predictions:** the system can abstain when confidence is insufficient and records its predictions to compare announced probabilities with actual results.

### BAD — Linux telemetry for hardware anomaly detection

`Python` · `SQLite` · `Linux` · `Data collection`

A hardware telemetry collector designed to build labelled datasets for anomaly detection: obstructed airflow, cooling problems or unstable overclocks. The implemented collection stage supplies the contextual data needed before training a detection model.

- **Multi-source collection:** independent readers gather sensor values, hardware counters and kernel events through Linux interfaces such as `/proc` and `/sys`.
- **Resilient acquisition:** unavailable sources disable themselves; the collector keeps running when a sensor is missing.
- **Error analysis:** kernel classification rules and hardware counters capture complementary evidence of faults.
- **Explicit coverage:** a diagnostic command explains which sources the machine exposes and which problems can or cannot be observed. The collector has no mandatory third-party dependencies.

## Real-time graphics & systems

### bdex-framegen — Frame generation for Vulkan games on Linux

`C++20` · `Vulkan` · `GLSL` · `Linux`

An implicit Vulkan layer that sits between a game and the graphics driver. It estimates motion between rendered frames and synthesizes intermediate images to improve displayed fluidity, without changing the game's code. It targets native Vulkan games and Direct3D games translated through DXVK or VKD3D-Proton.

- **Presentation control:** a virtual swapchain separates the images the game renders from the real swapchain presented to the display.
- **GPU image processing:** compute shaders build a luma pyramid, estimate optical flow with hierarchical block matching, refine motion and synthesize images with bidirectional warping.
- **Separate presentation work:** a dedicated thread handles presentation and pacing; a separate compute queue is used when available.
- **Quality and correctness:** generated frames are compared with real frames and simple baselines; Vulkan validation, synchronization checks and scene-cut handling help identify rendering errors and interpolation limits.

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
| **Python** | Python · NumPy · pandas · SQLite · Streamlit |
| **Artificial intelligence** | Neural networks · Machine learning · Probabilistic modelling · Calibration · Walk-forward evaluation |
| **LLMs & agents** | Ollama · RAG · Embeddings · BM25 · Reranking · ReAct · Context management |
| **Systems & graphics** | C · C++ · Vulkan · GLSL compute · Linux · CMake |
| **Web & backend** | TypeScript · React · NestJS · Node.js · Prisma · PostgreSQL · REST APIs |
| **Tools** | Git · Docker · systemd |

<sub>Project descriptions are provided here while their source repositories remain private.</sub>
