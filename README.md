# The Immunological Threshold of Malignancy: A Bistable ODE Framework for the Benign-to-Malignant Transition

**Author:** Agniz Dutta (Independent Researcher)  
**Model:** Immunological Bifurcation Model of Tumour Progression (IBM-TP)  

[![Open In Colab]([https://google.com)](https://google.com](https://colab.research.google.com/drive/1SJDcDstpIpTwTZUwzos8XW1NxVv-TWAo?usp=sharing)) 

---

## Overview

This repository contains the official computational implementation and figure-generation pipeline accompanying the manuscript **"The Immunological Threshold of Malignancy: A bistable ODE framework for the 'Benign-to-Malignant' transition."**

The **IBM-TP** is a three-variable, dimensionless coupled ordinary differential equation (ODE) system tracking:
* **$B(t) \in [0, \infty)$**: Tumour biomass (normalised to reference carrying capacity $K_0 = 1$)
* **$A(t) \in [0, \infty)$**: Net immune–apoptotic pressure
* **$H(t) \in [0, 1]$**: Oncogenic hallmark index (cumulative driver mutation burden)

The model demonstrates how two patients harbouring tumours of identical initial mass ($B_0 = 0.14$) and identical oncogenic burden ($H_0 = 0.26$) diverge into either **durable immune-controlled dormancy** or **invasive malignancy** based solely on initial host immune competence ($A_0$).

---

## Governing Equations

$$\frac{dB}{dt} = r B \left(\frac{B}{\theta(H)} - 1\right)\left(1 - \frac{B}{K(H)}\right) - \delta A B + \rho$$

$$\frac{dA}{dt} = \frac{\sigma B}{1 + \kappa B} - \mu_A A - \gamma H A$$

$$\frac{dH}{dt} = \varepsilon B (1 - H) - \nu A H$$

where carrying capacity expands exponentially with oncogenic progression, $K(H) = K_0 e^{\alpha H}$, and the Allee escape threshold erodes as $\theta(H) = \theta_0 e^{-\beta H}$.

---
## Quick Start & Reproducibility

### Option 1: Run in Google Colab (No Installation Required)
1. Click the **Open in Colab** badge at the top of this page (or upload `Dutta_IBM_TP_Supplementary_Code.ipynb` to [Google Colab](https://google.com)).
2. Select **Runtime > Run all**. All equilibrium verifications and 300 DPI PNG figures will generate automatically.

### Option 2: Run Locally on Windows / macOS / Linux
1. Clone this repository:
   ```bash
   git clone https://github.com
   cd IBM-TP-Tumor-Progression
   ```
2. Install the required scientific Python libraries:
   ```bash
   pip install numpy scipy matplotlib jupyter
   ```
3. Launch Jupyter Notebook and run all cells top-to-bottom:
   ```bash
   jupyter notebook Dutta_IBM_TP_Supplementary_Code.ipynb
   ```

---

## Verified Equilibrium Coordinates (Baseline Parameters)

| Equilibrium State | $B^*$ | $A^*$ | $H^*$ | Local Stability |
| :--- | :---: | :---: | :---: | :--- |
| **Dormant Attractor** | `0.00135` | `0.00197` | `0.265` | Locally asymptotically stable ($\text{Re}(\lambda_i) < 0$) |
| **Unstable Saddle** | `0.0668` | `0.0546` | `0.478` | Unstable saddle ($\exists\,\text{Re}(\lambda_i) > 0$) |
| **Malignant Attractor** | `8.307` | `0.238` | `0.963` | Locally asymptotically stable ($\text{Re}(\lambda_i) < 0$) |

---

## Citation

If you use this model or code in your research, please cite:

```bibtex

  title   = {The Immunological Threshold of Malignancy: A bistable ODE framework for the "Benign-to-Malignant" transition},
  author  = {Dutta, Agniz},
  year    = {2026},
}
```

---



