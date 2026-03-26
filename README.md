# NOx Combustion Modeling
### Lean Premixed Methane-Air Combustor — 5-Stage PSR Network
**Colorado State University — M.Eng Aerospace Engineering — May 2025**

---

## Project Overview

This project numerically investigates NOx formation (NO and NO₂) in a 
lean premixed methane-air combustor using a network of five perfectly 
stirred reactors (PSRs) in series. The simulation captures the effects 
of equivalence ratio and residence time on emissions throughout the 
combustion and post-flame stages — directly relevant to gas turbine 
combustor design and emissions compliance.

| Parameter | Value |
|---|---|
| Fuel | Methane (CH₄) |
| Oxidizer | Air (O₂:N₂ = 1:3.76) |
| Reaction mechanism | GRI-Mech 3.0 |
| Initial temperature | 800 K |
| Pressure | 20 bar |
| Equivalence ratios (ϕ) | 0.6, 0.7, 0.8, 0.9, 1.0 |
| Residence times (τ) | 2, 5, 10, 20 ms |
| Reactor stages | 5 PSRs in series |
| Simulation platform | Python, Cantera, Jupyter/Anaconda |

---

## Physical Setup
```
Inlet (CH₄ + Air)
     │
     ▼
  PSR Stage 1  →  PSR Stage 2  →  PSR Stage 3  →  PSR Stage 4  →  PSR Stage 5
  (τ advance)     (τ advance)     (τ advance)     (τ advance)     (τ advance)
                                                                        │
                                                                        ▼
                                                              NO, NO₂ extracted
```

Each PSR is modeled as an Ideal Gas Reactor in Cantera. The outlet 
composition of each stage feeds directly into the next, capturing the 
gradual evolution of combustion chemistry through post-flame zones.

---

## Tools & Methods

| Tool | Application |
|---|---|
| **Python** | Simulation workflow automation, data collection |
| **Cantera (GRI-Mech 3.0)** | Chemical kinetics, PSR network modeling |
| **Jupyter Notebook / Anaconda** | Development and execution environment |
| **Matplotlib** | Results visualization and parametric plots |

---

## Key Results

- **NO** mole fractions increase progressively across the reactor 
  network, peaking near ϕ ≈ 0.7–0.8 before declining toward 
  stoichiometric conditions
- **NO₂** shows monotonic increase with equivalence ratio, driven by 
  post-flame oxidation of NO with peroxy radicals in later reactor stages
- **Residence time** has a significant effect on NO₂ formation — longer 
  residence times allow more complete post-flame oxidation
- Results confirm that **model-form uncertainty dominates** in the lean 
  regime, with thermal NO (Zel'dovich mechanism) being the primary 
  production pathway
- Findings provide practical insights for **gas turbine combustor 
  design** — particularly for minimizing NOx while maintaining lean 
  premixed operation

---

## Simulation Methodology

### Equivalence Ratio Setup (Cantera API)
```python
gas.set_equivalence_ratio(phi, "CH4", {"O2": 1, "N2": 3.76})
```

### Residence Time Advancement
```python
sim.advance(sim.time + tau)
```

Each PSR stage advances by the residence time τ before passing its 
outlet composition to the next stage — replicating the gradual passage 
of gases through discrete combustion zones.

### Parametric Sweep
All combinations of ϕ ∈ {0.6, 0.7, 0.8, 0.9, 1.0} and 
τ ∈ {2, 5, 10, 20 ms} were simulated, generating a full parametric 
dataset of NO and NO₂ mole fractions across all 5 reactor stages.

---

## Skills Demonstrated

`Python` `Cantera` `GRI-Mech 3.0` `Chemical Kinetics` `PSR Networks`
`NOx Emissions Modeling` `Combustion Simulation` `Parametric Analysis`
`Matplotlib` `Jupyter Notebook` `Gas Turbine Combustion` `Lean Premixed Combustion`

---

## Files

| File | Description |
|---|---|
| `NOx_PSR_simulation.ipynb` | Jupyter notebook with full simulation code |
| `FinalProject_Combustion_Report.pdf` | Full technical report |

---

## Project Report

Full technical report included in this repository.

---

## Author

**Faisal Zohad Sayyed**
M.Eng Aerospace Engineering — Colorado State University
[LinkedIn](https://www.linkedin.com/in/faisalzsayyed/) |
[GitHub](https://github.com/faisalzsayyed)
