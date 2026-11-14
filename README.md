<!-- ═══════════════════════════════════════════════════════════════════════ -->
<!-- FLAME IN FREEFALL — FINAL PREMIUM README                                -->
<!-- ═══════════════════════════════════════════════════════════════════════ -->

<div align="center">

<!-- Tumhari Downloaded GIF -->
<img src="https://raw.githubusercontent.com/kis566/flame-in-freefall/main/giphy.gif"
     alt="Flame in Freefall Animation"
     width="200px"
     hight="200px"
     style="max-width:900px; border-radius:50px;">


<h1>FLAME IN FREEFALL</h1>
<h3><em>SI-Powered Fire Safety Insights from Microgravity Combustion Data</em></h3>

<p>
  <a href="https://www.spaceappschallenge.org/"><img src="https://img.shields.io/badge/Event-NASA%20Space%20Apps%202026-0b3d91?style=for-the-badge&logo=nasa&logoColor=white" alt="NASA Space Apps"></a>
  <img src="https://img.shields.io/badge/Status-Hackathon%20Prototype-ff6b35?style=for-the-badge" alt="Status">
  <img src="https://img.shields.io/badge/Category-Space%20Exploration-4ecdc4?style=for-the-badge" alt="Category">
  <img src="https://img.shields.io/badge/Difficulty-Advanced-red?style=for-the-badge" alt="Difficulty">
</p>

<p>
  <img src="https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white" alt="HTML5">
  <img src="https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white" alt="CSS3">
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black" alt="JS">
  <img src="https://img.shields.io/badge/Chart.js-FF6384?style=flat-square&logo=chartdotjs&logoColor=white" alt="Chart.js">
  <img src="https://img.shields.io/badge/No%20API-100%25%20Offline-success?style=flat-square" alt="Offline">
</p>

<br>

> **"In microgravity, there is no buoyancy. Flames are spherical and blue — invisible to traditional sensors. We built the tool to make them visible."**

[**Explore the Dashboard**](#-getting-started) · [**View Architecture**](#-system-architecture) · [**Read the Science**](#-the-science-behind-the-code)

</div>

---

## 📖 Table of Contents
- [The Crisis](#-the-crisis)
- [Our Solution](#-our-solution)
- [Core Innovations](#-core-innovations)
- [System Architecture](#-system-architecture)
- [Interactive Simulations & Features](#-interactive-simulations--core-features)
- [The Science Behind the Code](#-the-science-behind-the-code)
- [NASA PSI Database Attribution](#-nasa-psi-database-attribution)
- [Getting Started](#-getting-started)
- [Tech Stack & Constraints](#️-tech-stack--constraints)
- [Hackathon Judging Criteria Alignment](#-hackathon-judging-criteria-alignment)

---

## 🚨 The Crisis

NASA's Physical Sciences Informatics (PSI) database contains over **12 Terabytes of combustion data** spanning 40 years (24 core experiments). 

Yet, a critical bottleneck remains: **Mission engineers do not have time to read it.**

When designing the Artemis Lunar Habitat, engineers face an unprecedented threat:
- **Oxygen-Rich Environment:** Lunar habitats will run at **30%+ O₂ at ≤10.2 psi**.
- **The Flammability Spike:** This atmosphere makes materials **over 40% more flammable** than on Earth.
- **The Detection Blackout:** In microgravity, the absence of buoyancy means fires don't form teardrop shapes; they form slow-moving, blue, spherical flames that evade legacy smoke detectors (as seen in the Apollo 1 and Mir incidents).

**The Challenge:** Build an interactive SI-powered dashboard that summarizes, ranks, and interprets this data to deliver actionable fire safety insights.

---

## 💡 Our Solution

We did not build a static dashboard. We built a **Mission-Aware Decision Support Tool.**

**Flame in Freefall** dynamically parses NASA's normalized data and adapts its UI, ranking algorithms, and predictive models based on the specific mission profile selected by the user.

---

## ✨ Core Innovations

<table>
  <tr>
    <td width="50%">
      <h3>🎯 1. Mission-Aware Re-Ranking</h3>
      <p>Stop manually filtering. Select <em>"Lunar Base"</em> and the dataset instantly re-weights. High-O₂ experiments (like CFI-G) shoot to #1. Switch to <em>"Spacecraft / ISS"</em> and large-scale tests (like Saffire-I) take the lead. <strong>Same data, different priority.</strong></p>
    </td>
    <td width="50%">
      <h3>⚠️ 2. Automated Gap Analysis</h3>
      <p>We don't just show what NASA <em>has</em> tested. Our engine scans the dataset to find blind spots (e.g., <em>"No solid-fuel experiment exceeds 30% O₂"</em>). This provides a forward-looking research roadmap for Artemis planners.</p>
    </td>
  </tr>
  <tr>
    <td width="50%">
      <h3>🎚️ 3. Predictive Fire Model</h3>
      <p>An interactive sandbox with O₂, pressure, and fuel-type sliders. The engine predicts flame propagation and extinction risks calibrated directly against the actual findings of <strong>SAME (2019)</strong>, <strong>CFI-G (2021)</strong>, and <strong>FLEX (2012)</strong>.</p>
    </td>
    <td width="50%">
      <h3>🔧 4. Hardware Recommendations</h3>
      <p>We translate data into engineering. Based on the active mission, the tool recommends concrete hardware choices: <em>fine water mist vs. CO₂ suppression</em>, detector placement geometry, and safe material selection.</p>
    </td>
  </tr>
</table>

---

## 🏗️ System Architecture

Built with a focus on **speed, mission-critical reliability, and zero API dependencies** for deep-space latency environments.

```mermaid
graph TD
    %% Data Layer
    subgraph Data Layer [100% Client-Side Normalized Data]
        A[NASA PSI Database<br/>~12 TB Raw Telemetry] -->|Normalization| B(data/investigations-data.js<br/>20 Validated Investigations)
    end

    %% Logic Layer
    subgraph Engine [Dual Physics & Simulation Engine]
        B --> C{Mission State Router}
        C -->|Scenario Weighting| D[Dynamic Re-Ranking<br/>5 Mission Scenarios]
        C -->|NLP Engine| E[SI Intent Engine<br/>Regex & Keyword Semantics]
        C -->|Sandbox Parameters| F[Flame Physics Engine<br/>Navier-Stokes & Radiation]
        C -->|Ventilation Vector| G[Habitat Airflow Model<br/>Smoke Transport Vector]
    end

    %% Presentation Layer
    subgraph UI [Telemetry & Mission HUD]
        D --> H[Investigation Matrix Cards]
        E --> I[Interactive Mission Chat]
        F --> J[Canvas Flame Simulator<br/>0g / 0.16g / 1g + IR / Chem]
        G --> K[Habitat Duct Architecture<br/>Sensor Blackout Visualizer]
        D --> L[Chart.js Cross-Mission Analytics]
        C --> M[NASA Technical Memorandum<br/>NASA-TM-2026 Flight Brief]
    end

    style A fill:#0b3d91,stroke:#fff,color:#fff
    style B fill:#ff6b35,stroke:#fff,color:#fff
    style C fill:#4ecdc4,stroke:#fff,color:#000
    style F fill:#e74c3c,stroke:#fff,color:#fff
    style G fill:#3498db,stroke:#fff,color:#fff
    style J fill:#2ecc71,stroke:#fff,color:#000
    style M fill:#8e44ad,stroke:#fff,color:#fff
```

---

## 🔬 Interactive Simulations & Core Features

### 1. 🎛️ Real-Time Flame Physics Simulator (Microgravity vs Earth)
An interactive 60fps HTML5 Canvas simulation governed by combustion fluid dynamics:
- **0g Microgravity (Spherical Blue Flame):** With buoyancy eliminated ($Gr \approx 0$), transport is governed purely by molecular diffusion. Oxygen diffuses symmetrically inward, yielding a spherical flame emitting blue $CH^*$ radical chemiluminescence (~431 nm).
- **0.16g Lunar Gravity (Oblate Ellipsoid):** Low gravity produces an asymmetric, squashed ellipsoid flame with partial convection.
- **1.0g Earth Gravity (Teardrop Yellow Flame):** Strong thermal buoyancy draws cool air upward ($Gr \gg 1$), creating soot incandescence and a tall teardrop plume.
- **Cool Flame Regime:** Under high oxygen conditions (>60%), low-temperature combustion (~580 K) is simulated where the flame is invisible in thermal IR but remains an active oxidizer.
- **Extinguishment Stress-Testing:** Real-time triggers for **CO₂ gas blanketing** and **Fine Water Mist injection** to test suppression dynamics.

### 2. 🛰️ Artemis Lunar Habitat Cross-Section (Sensor Geometry Visualizer)
A direct visual proof of why legacy terrestrial smoke detectors fail in space:
- **Forced Convection Loop:** Lunar habitats require continuous mechanical ventilation (0.1–0.2 m/s). Without natural buoyancy, smoke particles follow streamlines horizontally rather than rising to the ceiling.
- **In-Duct Sensor Advantage:** Detects combustion particulate in **~4.2 seconds**, whereas ceiling-mounted sensors remain in a detection blackout zone for **>95 seconds**.
- **Interactive Smoke Trajectory:** Real-time particle system rendering smoke streamlines through the return air duct and filtration loop.

### 3. ⏱️ 60-Second Guided Judge Tour
- Built-in one-click automated walkthrough designed specifically for hackathon evaluators.
- Highlights the 5 core milestones: **Scenario Re-ranking**, **Flame Physics Simulator**, **Habitat Architecture**, **Gap Analysis**, and **NASA Flight Brief Generation**.
- Integrated with synthetic NASA audio telemetry sound effects via Web Audio API.

### 4. 📄 NASA Technical Memorandum Flight Brief Generator
- Formats telemetry and design recommendations into standard **NASA-TM-2026-ARTEMIS-FIRE-09** documentation.
- Instant **Copy to Markdown** and **Export to Flight JSON** for direct integration into mission planning flight packages.

---

## 📐 The Science Behind the Code

### 1. Buoyancy & The Grashof Number ($Gr$)
On Earth, natural convection is driven by thermal density gradients described by the dimensionless Grashof number:

$$Gr = \frac{g \cdot \beta \cdot (T_f - T_\infty) \cdot L^3}{\nu^2}$$

- **On Earth ($g = 9.81\text{ m/s}^2$):** $Gr \sim 10^6 \gg 1$, driving rapid upward buoyant acceleration.
- **In Microgravity ($g \approx 10^{-6}\text{ m/s}^2$):** $Gr \to 0$. Natural convection drops out entirely. Flame propagation becomes diffusion-controlled (Stefan-Maxwell diffusion).

### 2. The Stefan-Boltzmann Radiative Extinction
Because hot combustion products do not escape via convection, heat accumulates around the flame front until radiative losses exceed heat generation:

$$\dot{q}_{rad} = \varepsilon \sigma A (T_{flame}^4 - T_{\infty}^4)$$

In microgravity, this radiative heat loss leads to the unique phenomenon of **radiative extinction** or steady-state **cool flames** ($T \approx 500\text{–}800\text{ K}$) as observed in NASA's **FLEX** and **ACME** investigations.

---

## 📊 NASA PSI Database Attribution

This project synthesizes **20 core NASA microgravity combustion investigations** from the Physical Sciences Informatics database:

| Experiment | Full Name | Facility | Key Physical Insight |
| :--- | :--- | :--- | :--- |
| **FLEX** | Flame Extinguishment Experiment | CIR / MDCA | Discovered self-sustaining spherical cool flames in heptane droplets. |
| **SAME** | Smoke Aerosol Measurement Experiment | ISS Glovebox | Showed smoke particle size distribution shifts dramatically in 0g. |
| **CFI-G** | Confined Flame Investigation | CIR | Proved thin fuel flame spread accelerates in oxygen-enriched lunar air. |
| **Saffire I–VI** | Spacecraft Fire Safety | Cygnus Vehicle | First large-scale (1m+) fabric flammability tests in low-g depressurization. |
| **ACME** | Advanced Combustion via Microgravity | CIR | Methane and ethylene spherical burner dynamics & soot-free regimes. |
| **BASS** | Burning and Suppression of Solids | ISS Glovebox | Discovered slow air currents make solid flames burn hotter than in still air. |
| **SPICE** | Smoke Point In Co-flow Experiment | CIR | Gas-phase soot generation thresholds without buoyant acceleration. |
| **DAFT** | Dust Aerosol Flammability Test | Drop Tower | Particulate combustion hazards in low gravity and lunar dust simulant. |

---

## 🚀 Getting Started

### ⚡ Option 1: Direct Launch (Zero Setup)
No installations, no npm packages, no API keys required!
1. Clone or download this repository.
2. Double-click `index.html` to open it in Chrome, Edge, Firefox, or Safari.
3. Everything is bundled and functions 100% offline.

### 💻 Option 2: Local HTTP Server (Optional)
If you prefer running via a local web server:
```bash
# Using Python 3
python -m http.server 8000
```
Then visit `http://localhost:8000` in your web browser.

---

## 🛠️ Tech Stack & Constraints

- **Core Technologies:** HTML5, CSS3 (Custom Glassmorphism Design System), Vanilla ES6+ JavaScript.
- **Rendering & Audio:** HTML5 Canvas 2D API (60 FPS physics), Pure Web Audio API Synthesizer (No external audio files).
- **Libraries:** Chart.js (Data visualizations), Lucide Icons.
- **Architectural Constraint:** **100% Offline Capable.** Fully operable inside deep space habitats or isolated test environments without terrestrial internet connectivity.

---

## 🏆 Hackathon Judging Criteria Alignment

| Criteria | How "Flame in Freefall" Delivers |
| :--- | :--- |
| **Mission Impact** | Directly addresses NASA's highest-risk Artemis hazard: 30%+ O₂ habitability combined with microgravity sensor detection blackouts. |
| **Creativity** | Dual real-time simulations: 60fps Navier-Stokes flame physics + Artemis air-duct sensor geometry visualizer with instant suppression testing. |
| **Scientific Validity** | Grounded in exact NASA PSI investigations (FLEX, Saffire, SAME, CFI-G) with peer-reviewed equations ($Gr \to 0$, radiative extinction). |
| **Technical Execution** | Zero API keys, zero node build steps, 100% standalone and offline, Web Audio synthesis, interactive 60-second judge tour. |
| **Presentation** | Professional glassmorphism HUD interface, NASA Technical Memorandum flight brief export, real-time audio telemetry cues. |

---

<div align="center">
  <sub>Developed for the NASA Space Apps Challenge 2026. Built with scientific passion for space exploration safety.</sub>
</div>
