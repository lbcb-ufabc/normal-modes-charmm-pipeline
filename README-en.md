# Normal Mode Analysis Pipeline

## 📌 Description

This pipeline consists of a set of scripts adapted from the workflow developed by David Perahia for performing **Normal Mode Analysis (NMA)** and structural fluctuation analysis of proteins.

The workflow includes:

* Restrained energy minimization,
* Hessian matrix diagonalization,
* Normal Mode generation,
* RMSF (Root Mean Square Fluctuation) analysis.

The Normal Modes CHARMM Pipeline was developed to automate the steps of preparation, execution, and analysis of normal mode calculations in biomolecular systems.
It integrates auxiliary scripts and routines that allow:

* Preparation of input files for CHARMM.
* Execution of normal mode calculations.
* Processing and analysis of the results.
---

## 🎯 When to Use

Use this pipeline when you want to:

* Analyze collective protein motions
* Generate Normal Modes
* Explore conformational flexibility
* Calculate RMSF values
* Study structural dynamics using Normal Mode Analysis

---

## 📂 What This Pipeline Generates

* Minimized structures
* Normal Mode files
* Structural trajectories
* RMSF/fluctuation data

---

## ⚙️ Requirements

Requirements and software dependencies are described in:

[Requirements](https://github.com/Labbiofisbiocomp/modos-normais-charmm/blob/main/requirements.md)

---

## 🔄 Pipeline Overview

```text
Initial structure
        ↓
Restrained energy minimization
        ↓
Hessian matrix diagonalization
        ↓
Normal mode generation
        ↓
Atomic fluctuation analysis (RMSF)
```
---

## ▶️ How to Run (Step-by-Step)
Clone the repository and set up the environment:
```bash
git clone https://github.com/Labbiofisbiocomp/normal-modes-charmm-pipeline.git
cd normal-modes-charmm-pipeline
```

Execute the scripts in the following order:

```bash
charmm < mini-restraint.inp > mini-restraint.out
charmm < ligdiag.inp > ligdiag.out
charmm < traj_diag.inp > traj_diag.out
charmm < fluct-mod.inp > fluct-mod.out
```

---

## 📥 Inputs

* `step1_pdbreader.psf`
* `step1_pdbreader.crd`

---

## 📤 Outputs

* `min_restr.crd`
* `modes.mod`
* `flut-@i.pdb`

---

# 🧪 Step Details

---

## 🔒 Mini-restraint

Performs structural minimization using a series of restraints until reaching the unrestrained minimum energy state.

### Input

```text id="gdb2ks"
step1_pdbreader.psf
step1_pdbreader.crd
```

### Output

```text id="2xzw9e"
./min_restr.crd
```

---

## 🧬 Ligdiag

Diagonalizes the Hessian matrix.

### Input

```text id="0l2i5o"
step1_pdbreader.psf
min_restr.crd
```

---

## 🎞️ Traj_diag

Generates the normal modes.

### Input

```text id="1n7l38"
step1_pdbreader.psf
min_restr.crd
```

### Output

```text id="98kc5m"
./modes.mod
```

---

## 📊 Fluct_mod

Calculates RMSF (Root Mean Square Fluctuation) based on atomic fluctuations.

### Input

```text id="f4r87h"
step1_pdbreader.psf
min_restr.crd
```

### Output

```text id="8l5khm"
./flut-@i.pdb
```

---

## ⚠️ Observations

* Scripts must be executed **in the correct order**
* Verify generated outputs before proceeding to the next step
* Ensure that PSF and CRD files are correctly formatted
---

## 📌 Notes

This pipeline was adapted from the workflow developed by David Perahia.
