<div align="center">

# Bdex

**Développeur — du compteur matériel à l'API métier.**

Étudiant en 3ᵉ année à Epitech. Je construis des systèmes qu'on peut mesurer
et des modèles qu'on peut vérifier.

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

## 🧭 Ce qui traverse mes projets

Une même règle, du bas niveau jusqu'à la donnée : **ne jamais inventer ce qu'on
n'a pas mesuré.** Un capteur absent ne vaut pas zéro, il vaut `NULL`. Un modèle
qui annonce 70 % doit gagner 70 fois sur 100, et le prouver. Un dépôt qui ne
liste pas ses limites en cache.

---

## 🔧 Projets

### 🩺 [BAD — Bdex Anomaly Detector](https://github.com/Bdexez/BAD_-Bdex_Anomaly_Detector-)

`Python` · `Linux` · `SQLite`

Télémétrie matérielle à 1 Hz sous Linux, pour construire un dataset labellisé et
y entraîner un détecteur d'anomalies — ventirad encrassé, flux d'air obstrué,
overclock instable.

- **Zéro dépendance obligatoire** — `/proc`, `/sys` et la stdlib suffisent
- 13 readers indépendants (k10temp, amdgpu, NVML, NVMe, RAPL, PSI, kmsg…) ;
  une source absente se désactive au lieu de polluer la base
- Détection d'erreurs à **trois étages** : 38 règles de classement kernel
  déclarées en données, un attrape-tout sur les priorités ≤ 3, et des compteurs
  matériels qui attrapent ce que le noyau compte sans le journaliser
- `--doctor` dit ce que la machine permet de détecter **et ce qu'elle ne permet pas**

### 🎯 [cs2edge — pronostiqueur calibré](https://github.com/Bdexez/CS_S)

`Python` · `NumPy`

Modèle probabiliste d'issue de matchs, construit autour d'une contrainte
vérifiable : quand il annonce 70 %, l'équipe gagne environ 70 fois sur 100.

- **Cœur en NumPy seul** — régression logistique ridge résolue par IRLS,
  calibration par température, pipeline écrit à la main
- Antisymétrie garantie par construction : `p(A bat B) + p(B bat A) = 1` à la
  précision machine
- **Backtest walk-forward** — une validation croisée aléatoire donnerait des
  scores bien meilleurs et entièrement faux
- **S'abstient sur 17 % des matchs** : un pronostiqueur qui se prononce sur tout
  ne permet pas de distinguer ses convictions de ses devinettes
- La mesure a façonné le produit : un palier supprimé parce qu'il mentait sur
  62 observations, une marginale recalibrée qui a ramené l'écart de +10,5 % à +2,0 %

### 🏢 [Up Network — ERP / CRM](https://github.com/Bdexez/up_network2.0)

`NestJS` · `Prisma` · `PostgreSQL` · `React` · `TypeScript`

Suite de gestion multi-société pour PME, développée pendant six mois en stage :
CRM, cycle de vente, achats & stock, projets, RH et états comptables.

- **10 modules** · **84 permissions** appliquées côté serveur · **34 modèles
  Prisma** · **128 tests** unitaires
- La société active vient du jeton, jamais du client — aucune route n'accepte
  de `?companyId=`
- Devis → commande → facture → règlement, avec avoirs, multi-devises et
  documents figés protégés par verrou optimiste
- États réglementaires français : balance âgée, TVA par taux, export FEC

---

## 🛠️ Stack

| | |
|---|---|
| **Langages** | C · C++ · x86-64 · Python · TypeScript · SQL · Dart |
| **Backend** | NestJS · Node.js · Prisma · PostgreSQL · SQLite · REST · OpenAPI |
| **Front** | React · Vite · Flutter |
| **Data** | NumPy · pandas · calibration · backtest walk-forward · Streamlit |
| **Systèmes** | Linux · sysfs/procfs · systemd · Docker · Git |

---

## 📍 En ce moment

Je travaille l'étage modèle de **BAD** et l'intégration de données réelles dans
**cs2edge**. Ouvert aux échanges sur le bas niveau Linux, la modélisation
probabiliste et tout ce qui touche à la mesure.

<div align="center">
<sub>📫 <a href="https://linkedin.com/in/elian-marzari">LinkedIn</a></sub>
</div>
