<div align="center">

# Bdex

**Developer — from the hardware counter to the business API.**

Third-year student at Epitech. I build systems you can measure and models you
can verify.

<br>

![C](https://img.shields.io/badge/C-00599C?logo=c&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?logo=cplusplus&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)
![NestJS](https://img.shields.io/badge/NestJS-E0234E?logo=nestjs&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?logo=react&logoColor=black)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white)
![Linux](https://img.shields.io/badge/Arch%20Linux-1793D1?logo=archlinux&logoColor=white)

[![LinkedIn](https://img.shields.io/badge/LinkedIn-elian--marzari-0A66C2?logo=linkedin&logoColor=white)](https://linkedin.com/in/elian-marzari)

</div>

---

## 🧭 What runs through my projects

One rule, from the lowest level up to the data: **never invent what you haven't
measured.** A missing sensor is not zero, it is `NULL`. A model that announces
70 % has to win 70 times out of 100, and prove it. A repository that doesn't
list its limitations is hiding some.

---

## 🔧 Projects

### 🩺 [BAD — Bdex Anomaly Detector](https://github.com/Bdexez/BAD_-Bdex_Anomaly_Detector-)

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

### 🎯 [cs2edge — calibrated tipster](https://github.com/Bdexez/CS_S)

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

### 🏢 [Up Network — ERP / CRM](https://github.com/Bdexez/up_network2.0)

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

---

## 🛠️ Stack

| | |
|---|---|
| **Languages** | C · C++ · x86-64 · Python · TypeScript · SQL · Dart |
| **Backend** | NestJS · Node.js · Prisma · PostgreSQL · SQLite · REST · OpenAPI |
| **Front** | React · Vite · Flutter |
| **Data** | NumPy · pandas · calibration · walk-forward backtest · Streamlit |
| **Systems** | Linux · sysfs/procfs · systemd · Docker · Git |

---

## 📍 Right now

I'm working on the model stage of **BAD** and on feeding real data into
**cs2edge**. Happy to talk about low-level Linux, probabilistic modelling and
anything to do with measurement.

<div align="center">
<sub>📫 <a href="https://linkedin.com/in/elian-marzari">LinkedIn</a></sub>
</div>
