<p align="center">
  <img src="./assets/header.svg?v=4" width="100%" alt="Bdex — Python, artificial intelligence, neural networks, C/C++, graphics and systems.">
</p>

<p align="center"><a href="#python--artificial-intelligence">Python &amp; AI</a> &nbsp; · &nbsp; <a href="#projects">Projects</a> &nbsp; · &nbsp; <a href="#technical-stack">Technical stack</a></p>

<br>

I'm **Bdex**. I develop in **Python, C/C++ and TypeScript**, working on **artificial intelligence, neural networks, Linux systems, real-time graphics and full-stack applications**.

## Python & artificial intelligence

My work includes **two AI projects, including a neural-network project**. Python is a core language in my work, from probabilistic modelling and model evaluation to hardware data collection.

## Projects

<sub>The source repositories for the projects below are currently private.</sub>

### bdex-framegen — Frame generation for Vulkan

`C++20` · `Vulkan` · `GLSL` · `Linux`

An implicit Vulkan layer that turns 30 rendered fps into 60, 90 or 120 displayed
fps, on any Vulkan game — native, or Direct3D through DXVK / VKD3D-Proton. No
change to the game.

- **Virtual swapchain**: the game renders into private images, the layer owns the
  real swapchain and decides what to present and when
- **The game is never blocked** — `vkQueuePresentKHR` costs it ≈ 0.1 ms; the
  synthesis runs on a dedicated thread and a separate compute queue
- Five compute shaders, no CPU round trip: luma pyramid, hierarchical block
  matching, median filter, 4×4 refinement, bidirectional warping
- **≈ 30 dB PSNR** against the real frame, against ≈ 25 dB for a blend and
  ≈ 22 dB for frame duplication — measured, not asserted
- Clean under `VK_LAYER_KHRONOS_validation`, synchronization validation included
- When the motion cannot be explained, it shows the real frame rather than a blend

### BAD — Bdex Anomaly Detector

`Python` · `Linux` · `SQLite`

Hardware telemetry at 1 Hz on Linux, to build a labelled dataset and train an
anomaly detector on it — clogged heatsink, blocked airflow, unstable overclock.

- **Zero mandatory dependency** — `/proc`, `/sys` and the standard library are enough
- 13 independent readers (k10temp, amdgpu, NVML, NVMe, RAPL, PSI, kmsg…);
  a missing source disables itself instead of filling the database with nulls
- **Three-stage** error detection: 38 kernel classification rules declared as
  data, a catch-all on priorities ≤ 3, and hardware counters that catch what the
  kernel counts without necessarily logging
- `--doctor` reports what the machine makes it possible to detect **and what it does not**

### cs2edge — Calibrated CS2 predictions

`Python` · `NumPy`

Probabilistic model of match outcomes, built around a verifiable constraint:
when it announces 70 %, the team wins roughly 70 times out of 100.

- **NumPy-only core** — ridge logistic regression solved by IRLS, temperature
  calibration, pipeline written by hand
- Antisymmetry guaranteed by construction: `p(A beats B) + p(B beats A) = 1` to
  machine precision
- **Walk-forward backtest** — a random cross-validation would give far better
  scores, and entirely false ones
- **Abstains on 17 % of matches**: a tipster who has an opinion on everything
  gives you no way to tell convictions from guesses
- Measurement shaped the product: a tier removed because it lied on 62
  observations, a marginal recalibrated which brought the gap from +10.5 % down
  to +2.0 %

### Up Network — ERP / CRM

`NestJS` · `Prisma` · `PostgreSQL` · `React` · `TypeScript`

Multi-company management suite for SMEs, developed over six months during an
internship: CRM, sales cycle, purchasing & stock, projects, HR and accounting
reports.

- **10 modules** · **84 permissions** enforced server-side · **34 Prisma
  models** · **128** unit tests
- The active company comes from the token, never from the client — no route
  accepts a `?companyId=`
- Quote → order → invoice → payment, with credit notes, multi-currency and
  frozen documents protected by an optimistic lock
- French regulatory reports: aged balance, VAT by rate, FEC export


## Technical stack

| Area | Technologies & concepts |
| :--- | :--- |
| **Python & data** | **Python** · NumPy · pandas · SQLite · Streamlit |
| **Artificial intelligence** | **AI · Neural networks** · Probabilistic modelling · Calibration · Walk-forward backtesting |
| **Systems & graphics** | C · C++ · Vulkan · GLSL compute · Linux · CMake |
| **Web & backend** | TypeScript · React · NestJS · Node.js · Prisma · PostgreSQL · REST APIs |
| **Development** | Git · Docker · systemd |
