# BioGIM: Biodesulfurization Growth Inhibition Model

[![DOI](https://zenodo.org/badge/DOI/10.1016/j.gce.2025.08.004.svg)](https://doi.org/10.1016/j.gce.2025.08.004)

BioGIM (Biodesulfurization Growth Inhibition Model) is an open-source Haldane-based kinetics model for modeling the biotransformation of thiosulfate (S₂O₃²⁻) to sulfate (SO₄²⁻) and elemental sulfur (S⁰) by sulfur-oxidizing bacteria (SOB) under conditions of sulfate inhibition. It is implemented in Python v3.12.7.

> **From the publication:**  
> *A Haldane-based kinetic model—BioGIM (Biodesulfurization Growth Inhibition Model)—was developed to describe growth dynamics...by accounting...for sulfate-induced growth inhibition, predict the critical sulfate inhibition threshold (P<sub>SO₄,max</sub>), and capture...the metabolic switch from the primary substrate (thiosulfate) to a secondary substrate (elemental sulfur) under thiosulfate-limited conditions*

This model and its application are described in detail in our peer-reviewed article (**https://doi.org/10.1016/j.gce.2025.08.004**).

---

## Table of Contents

- [Model Description](#model-description)
- [Features](#features)
- [Functionalities](#functionalities)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Inputs and Outputs](#inputs-and-outputs)
- [Parameters and Variables](#parameters-and-variables)
- [How to Cite](#how-to-cite)
- [License](#license)
- [Contact](#contact)

---

## Model Description

BioGIM is a mechanistic model formulated in Python to describe:

- Microbial growth dynamics and thiosulfate biodesulfurization to sulfate and elemental sulfur.
- The effect of sulfate product (SO₄²⁻) inhibition on microbial growth and metabolism.
- The critical sulfate inhibition threshold (P<sub>SO₄,max</sub>) and its effect on metabolic pathways.
- The metabolic switch from thiosulfate to elemental sulfur (S⁰) as a secondary substrate under substrate-limited conditions.

BioGIM uses four time-series state variables:
- Biomass (X)
- Thiosulfate (S, S₂O₃²⁻)
- Sulfate (P, SO₄²⁻)
- Elemental sulfur (PS, S⁰)

And twelve parameters, which are dynamically estimated based on the state variables. All model equations and parameter definitions are given in [Table 1 of the published paper](https://www.sciencedirect.com/science/article/pii/S2666952825000780?via%3Dihub#tbl1:~:text=Table%201.%20BioGIM%20parameter%20and%20variable%20annotations%20with%20definitions).

---

## Features

- **Dynamic simulation** of microbial growth, substrate consumption, and product (sulfate and elemental sulfur) production.
- **Parameter estimation** and model calibration using experimental time-series data.
- **Validation, scenario analysis, and sensitivity analysis** for process optimization.
- **Publication-quality plotting** for model validation and reporting.
- **Open-source and extensible** for custom bioprocess applications.

---

## Functionalities

All major functionalities of BioGIM are available as interactive Jupyter notebooks in the [notebooks/](notebooks/) directory:

- `01_joint_calibration.ipynb` – Joint parameter calibration with experimental data
- `02_validation.ipynb` – Model validation on independent datasets
- `03_sensitivity_analysis.ipynb` – Sensitivity analysis for key model parameters
- `04_scenario_analysis.ipynb` – Scenario and parameter sweep analyses
- `05_thiosulfate_biotransformation.ipynb` – Biotransformation of thiosulfate to sulfate and elemental sulfur

Open these notebooks with [Jupyter Notebook](https://jupyter.org/) or [JupyterLab](https://jupyterlab.readthedocs.io/).

---

## Installation

**1. Clone the repository**
````bash
git clone https://github.com/Dotosh/BioGIM.git
cd BioGIM
````
**2. Install required dependencies**
````bash
pip install -r requirements.txt
Dependencies include: numpy, scipy, matplotlib.
````
---

## Quick Start
Open or run the notebook files to see a typical model calibration, validation, and other simulations for step-by-step analysis.

---

## Inputs and Outputs
Inputs
- Time-series experimental data for state variables.
- Experimental yields.
- Boundary conditions.

Outputs
- Simulated time profiles of all state variables.
- Estimated kinetic and inhibition parameters.
- Model goodness-of-fit metrics (R², RMSE).
- Sensitivity and scenario analysis results.
- High-quality plots for publication or reports.

---

## Parameters and Variables

BioGIM uses twelve parameters and four state variables, including:

**Parameters**

- *μ<sub>max-H</sub>*: Maximum specific growth rate for Haldane fitting (h⁻¹)
- *K<sub>s</sub>*: Half-saturation constant for thiosulfate (mol S₂O₃²⁻/L)
- *K<sub>i</sub>*: Inhibition constant for thiosulfate (mol S₂O₃²⁻/L)
- *P<sub>SO₄,max</sub>*: Critical sulfate inhibition threshold (mol SO₄²⁻/L)
- *m<sub>s</sub>*: Maintenance coefficient (mol S₂O₃²⁻/gDCW·h)
- *k<sub>so</sub>*: Specific sulfur oxidation rate constant (L/gDCW·h)
- *ks<sub>switch</sub>*: Thiosulfate-to-sulfur switch concentration (mol S₂O₃²⁻/L)
- *k*: Sulfate inhibition factor
- Stoichiometric and yield coefficients:
    - *Y<sub>xs</sub>*: Biomass yield coefficient g DCW/mol S₂O₃²⁻
    - *Y<sub>ps</sub>*: Thiosulfate-to-sulfate yield coefficient mol SO₄²⁻/mol S₂O₃²⁻
    - *Y<sub>p2s</sub>*: Thiosulfate-to-sulfur yield coefficient mol S⁰/mol S₂O₃²⁻
    - *Y<sub>so4_s0</sub>*: Sulfur-to-sulfate yield coefficient mol SO₄²⁻/mol S⁰

**State Variables**
- X - Biomass concentration (g DCW/L)
- S - Thiosulfate concentration (mol S₂O₃²⁻/L)
- P - Sulfate concentration (mol SO₄²⁻/L)
- Ps - Elemental sulfur concentration (mol S⁰/L)

For full details, see [Table 1](https://www.sciencedirect.com/science/article/pii/S2666952825000780?via%3Dihub#tbl1:~:text=Table%201.%20BioGIM%20parameter%20and%20variable%20annotations%20with%20definitions) in the publication.

---

## How to Cite
If you use BioGIM for research or teaching, please cite:

Dada, O. I., Abeysinghe, S., Rahat, S. S., Liyanage, T. U. H., Xiong, X., Zhu, K., Yu, L., Neibergs, S., & Chen, S. (2025). Kinetic modeling of sulfate inhibition effects on growth dynamics of novel _Thioalkalivibrio_ sp. Isolates from Soap Lake, Washington. _Green Chemical Engineering_. https://doi.org/10.1016/j.gce.2025.08.004

---

## License
BioGIM is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

## Contact
Questions, bug reports, or suggestions?

Contact:\
Oluwatunmise Dada\
Department of Biological Systems Engineering\
Washington State University\
Email: oluwatunmise.dada@wsu.edu


________________________________________
BioGIM: Biodesulfurization Growth Inhibition Model



