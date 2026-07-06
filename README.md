# Pipeline de Análise de Modos Normais

## 📌 Descrição

Este pipeline consiste em um conjunto de scripts adaptados do workflow desenvolvido por David Perahia para realizar **Análise de Modos Normais (Normal Mode Analysis - NMA)** e análise de flutuações estruturais de proteínas.

O workflow inclui:

* Minimização de energia com restrições,
* Diagonalização da matriz Hessiana,
* Geração de Modos Normais,
* Análise de RMSF (Root Mean Square Fluctuation).

O Normal Modes CHARMM Pipeline foi desenvolvido para automatizar etapas de preparação, execução e análise de cálculos de modos normais em sistemas biomoleculares.
Ele integra scripts auxiliares e rotinas que permitem:

* Preparação de arquivos de entrada para o CHARMM.
* Execução de cálculos de modos normais.
* Processamento e análise dos resultados.
  
---

## 🎯 Quando usar

Utilize este pipeline quando desejar:

* Analisar movimentos coletivos de proteínas
* Gerar Modos Normais
* Explorar flexibilidade conformacional
* Calcular valores de RMSF
* Estudar dinâmica estrutural utilizando Análise de Modos Normais

---

## 📂 O que este pipeline gera

* Estruturas minimizadas
* Arquivos de modos normais
* Trajetórias estruturais
* Dados de RMSF/flutuação

---

## ⚙️ Requisitos

Os requisitos e dependências de software estão descritos em:

[Requirements](https://github.com/Labbiofisbiocomp/normal-mode-charmm-pipeline/blob/main/requirements.md)

---

## 🔄 Visão geral do pipeline

```text
Estrutura inicial
        ↓
Minimização de energia com restrições
        ↓
Diagonalização da matriz Hessiana
        ↓
Geração dos modos normais
        ↓
Análise de flutuação atômica (RMSF)
```
---

## ▶️ Como executar (passo a passo)

Clone o repositório e configure o ambiente:
```bash
git clone https://github.com/Labbiofisbiocomp/normal-modes-charmm-pipeline.git
cd normal-modes-charmm-pipeline
```

Execute os scripts na seguinte ordem:

```bash
charmm < mini-restraint.inp > mini-restraint.out
charmm < ligdiag.inp > ligdiag.out
charmm < traj-diag.inp > traj-diag.out
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

# 🧪 Detalhamento das etapas

---

## 🔒 Mini-restraint

Realiza a minimização estrutural utilizando uma série de restrições até atingir o estado mínimo sem restrições.

### Input

```text
step1_pdbreader.psf
step1_pdbreader.crd
```

### Output

```text
./min_restr.crd
```

---

## 🧬 Ligdiag

Diagonaliza a matriz Hessiana.

### Input

```text
step1_pdbreader.psf
min_restr.crd
```

---

## 🎞️ Traj-diag

Gera os modos normais.

### Input

```text
step1_pdbreader.psf
min_restr.crd
```

### Output

```text
./modes.mod
```

---

## 📊 Fluct_mod

Calcula o RMSF (Root Mean Square Fluctuation) com base nas flutuações atômicas.

### Input

```text
step1_pdbreader.psf
min_restr.crd
```

### Output

```text
./flut-@i.pdb
```

---
## ⚠️ Observações importantes

* Os scripts devem ser executados **na ordem correta**
* Verifique os outputs gerados antes de prosseguir para a próxima etapa
* Certifique-se de que os arquivos PSF e CRD estejam corretamente formatados

---

## 📌 Notas

Este pipeline foi adaptado do workflow desenvolvido por David Perahia.
