# BioGIM
BioGIM (Biodesulfurization Growth Inhibition Model)

This model is part of the 
.
# BioGIM: Biodesulfurization Growth Inhibition Model

[![DOI](https://zenodo.org/badge/DOI/YOUR_DOI_HERE.svg)](https://doi.org/YOUR_DOI_HERE)

BioGIM (Biodesulfurization Growth Inhibition Model) is an open-source Python package for modeling the biotransformation of thiosulfate by sulfur-oxidizing bacteria (SOB) under conditions of sulfate inhibition. The model is designed for both research and teaching, and is based on a Haldane-type kinetics framework.

> **From the publication:**  
> *A Haldane-based kinetic model—BioGIM (Biodesulfurization Growth Inhibition Model)—was developed to account for sulfate-induced growth inhibition, predict the critical sulfate inhibition threshold (PSO₄,max), and capture the metabolic switch from thiosulfate to elemental sulfur as a secondary energy substrate.*

This model and its application are described in detail in our peer-reviewed article (**DOI: [pending]**).

---

## Table of Contents

- [Model Description](#model-description)
- [Features](#features)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Inputs and Outputs](#inputs-and-outputs)
- [Parameters](#parameters)
- [Example Usage](#example-usage)
- [How to Cite](#how-to-cite)
- [License](#license)
- [Contact](#contact)

---

## Model Description

BioGIM is a mechanistic model formulated in Python to describe:

- Microbial growth dynamics and substrate consumption under thiosulfate biodesulfurization.
- The effect of sulfate product (SO₄²⁻) inhibition on microbial growth and metabolism.
- The critical sulfate inhibition threshold (PSO₄,max) and its effect on metabolic pathways.
- The metabolic switch from thiosulfate to elemental sulfur (S⁰) as a secondary substrate under substrate-limited conditions.

BioGIM uses four state variables:
- Biomass (X)
- Thiosulfate (S, S₂O₃²⁻)
- Sulfate (P, SO₄²⁻)
- Elemental sulfur (PS, S⁰)

And twelve parameters, which are dynamically estimated or provided by the user. All model equations and parameter definitions are given in [Table 1 of the published paper](https://doi.org/YOUR_DOI_HERE).

---

## Features

- **Dynamic simulation** of microbial, substrate, and product concentrations.
- **Parameter estimation** and model calibration using experimental time-series data.
- **Scenario and sensitivity analyses** for process optimization.
- **Publication-quality plotting** for model validation and reporting.
- **Open-source and extensible** for custom bioprocess applications.

---

## Installation

**1. Clone the repository**
```bash
git clone https://github.com/YOUR_USERNAME/BioGIM.git
cd BioGIM
2. Install required dependencies
pip install -r requirements.txt
Dependencies include: numpy, scipy, matplotlib.
________________________________________
Quick Start
Run the example script to see a typical model calibration and simulation:
python run_biogim_example.py
Or, open and explore the Jupyter notebook in the /examples directory for step-by-step analysis.
________________________________________
Inputs and Outputs
Inputs
•	Time-series experimental data:
o	Biomass (gDCW/L)
o	Thiosulfate (mol/L)
o	Sulfate (mol/L)
o	Elemental sulfur (mol/L)
•	Model parameter values (provided or to be fitted).
Outputs
•	Simulated time profiles of all state variables.
•	Estimated kinetic and inhibition parameters.
•	Model goodness-of-fit metrics (R², RMSE).
•	Sensitivity and scenario analysis results.
•	High-quality plots for publication or reports.
________________________________________
Parameters
BioGIM uses twelve parameters, including:
•	μmax-H: Maximum specific growth rate (h⁻¹)
•	Ks: Half-saturation constant for thiosulfate (mol/L)
•	Ki: Inhibition constant for thiosulfate (mol/L)
•	PSO₄,max: Critical sulfate inhibition threshold (mol/L)
•	ms: Maintenance coefficient (mol S₂O₃/gDCW·h)
•	k_so: Elemental sulfur utilization rate (L/gDCW·h)
•	n: Sulfate inhibition factor
•	Stoichiometric and yield coefficients (Yxs, Yps, Yp2s, etc.)
For full details, see Table 1 in the publication.
________________________________________
Example Usage
Here is a minimal example to run a simulation using BioGIM:
import numpy as np
from scipy.integrate import odeint
from biogim import model, default_params  # assuming model.py

# Example: Simulate time course
y0 = [0.01, 0.1, 0.0, 0.0]  # Initial [X, S, P, PS]
t = np.linspace(0, 100, 100)

solution = odeint(model, y0, t, args=default_params)
# solution[:, 0] = Biomass, solution[:, 1] = Thiosulfate, etc.
For more examples, see the /examples directory.
________________________________________
How to Cite
If you use BioGIM for research or teaching, please cite:
Outshine Tunmise, et al. (202X).
"A Haldane-based kinetic model for sulfate inhibition and metabolic switching in thiosulfate biodesulfurization." Journal Name, https://doi.org/YOUR_DOI_HERE
You may also cite this repository (see Zenodo badge above).
________________________________________
License
BioGIM is licensed under the MIT License. See LICENSE for details.
________________________________________
Contact
Questions, bug reports, or suggestions?
•	Open an issue
•	Contact:
Outshine Tunmise
Department of Biological Systems Engineering
Washington State University
Email: your_email@wsu.edu
________________________________________
BioGIM: advancing open, reproducible science in biodesulfurization kinetics.

---

**Customize as follows:**
- Replace `YOUR_DOI_HERE`, `YOUR_USERNAME`, and `your_email@wsu.edu` as needed.
- After publication, update citation details and Table 1 link.
- If you want a quickstart Jupyter notebook or requirements.txt, just ask!

