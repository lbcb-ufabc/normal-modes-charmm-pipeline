# Normal Mode Analysis Pipeline

## 📌 Description

This pipeline was developed to perform **Normal Mode Analysis (NMA)** and structural fluctuation analysis of proteins using **CHARMM**.

Adapted from the workflow developed by **David Perahia**, the pipeline automates the steps of system preparation, energy minimization, normal mode calculation, and structural fluctuation analysis, enabling the investigation of collective motions and conformational flexibility in biomolecular systems.

---

## ⚙️ Requirements

The software requirements and dependencies are available at:

[Requirements](https://github.com/Labbiofisbiocomp/normal-modes-charmm-pipeline/blob/main/requirements.md)

---

# 📖 About the Project

This pipeline was developed to:

- perform restrained energy minimization;
- calculate normal modes using CHARMM;
- analyze collective protein motions;
- calculate structural fluctuations (RMSF);
- generate files for downstream structural analyses.

---

# 📂 Repository Structure

```text
.
├── requirements.md
├── mini-restraint.inp
├── ligdiag.inp
├── traj-diag.inp
├── fluct-mod.inp
├── README-en.md
└── README.md
```

---

## 🔄 Pipeline Overview

```text
Initial structure
        ↓
Restrained energy minimization
        ↓
Hessian matrix diagonalization
        ↓
Generation of normal modes
        ↓
Atomic fluctuation (RMSF) analysis
```

---

## ▶️ How to Run

Execute the scripts in the following order:

```bash
charmm < mini-restraint.inp > mini-restraint.out
charmm < ligdiag.inp > ligdiag.out
charmm < traj-diag.inp > traj-diag.out
charmm < fluct-mod.inp > fluct-mod.out
```

---

## 📥 Inputs

* `step1_pdbreader.psf` → Topology file.
* `step1_pdbreader.crd` → Initial structure coordinates.

---

## 📤 Outputs

At the end of the execution, the following files are generated:

- `min_restr.crd` containing the minimized structure;
- `modes.mod` containing the calculated normal modes;
- `flut-@i.pdb` containing the structural fluctuation (RMSF) values.

---

## 🧪 File Structure

- `mini-restraint.inp` → Performs restrained energy minimization.
- `ligdiag.inp` → Calculates and diagonalizes the Hessian matrix.
- `traj-diag.inp` → Generates the normal modes of the minimized structure.
- `fluct-mod.inp` → Calculates structural fluctuations (RMSF) from the normal modes.

---

## ⚠️ Important Notes

* The scripts must be executed in the order presented above.
* Ensure that the `.psf` and `.crd` files are properly prepared before execution.
* Verify the output files before proceeding to downstream analyses.
* Processing time may vary depending on the size of the biomolecular system.

---

## 📌 Notes

This pipeline was adapted from the workflow developed by **David Perahia** to automate **Normal Mode Analysis** using **CHARMM**.
