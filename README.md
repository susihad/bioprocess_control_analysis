# 🧫 Comparative Analysis of Bioprocess Control Strategies
> A data-driven study of industrial-scale penicillin fermentation using the IndPenSim simulation dataset

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python) ![Dask](https://img.shields.io/badge/Dask-distributed-orange) ![SciPy](https://img.shields.io/badge/SciPy-statistical%20analysis-green) ![Tableau](https://img.shields.io/badge/Tableau-visualization-lightblue)

---

## 📌 Project Overview

This project compares three industrial bioprocess control strategies applied to a 100,000-litre penicillin fermentation simulation. Using statistical analysis and data visualization, the study evaluates productivity, PAA (Phenylacetic Acid) control quality, and economic impact across control approaches.

**Key Question:** Does Advanced Process Control (APC) with real-time Raman spectroscopy outperform traditional control methods in penicillin manufacturing?

**Short Answer:** Yes — by 18–23%, with statistical significance of p < 0.005.

---

## 🗂️ Dataset

- **Source:** [IndPenSim — Industrial Penicillin Simulation](http://www.industrialpenicillinsimulation.com)
- **Size:** ~2.5 GB | 100 batches | 113,935 rows | 2,239 columns
- **Format:** CSV (process parameters + Raman spectroscopy measurements)

The dataset is **not included** in this repository due to its size. Please download it directly from the source above or from the [Mendeley Data repository](https://data.mendeley.com).

### Batch Structure

| Batch Range | Control Strategy |
|-------------|-----------------|
| 1 – 30 | Recipe-Driven |
| 31 – 60 | Operator-Controlled |
| 61 – 90 | APC with Raman Spectroscopy |
| 91 – 100 | Fault batches (process deviations) |

---

## ⚗️ Background

The fermentation reaction converts glucose, ammonia, and phenylacetic acid (PAA) into Penicillin G using the fungus *Penicillium chrysogenum*:

```
C₆H₁₂O₆ + NH₃ + O₂ + PAA → Penicillin G + CO₂ + H₂O + Biomass
```

Key control parameters include: aeration rate, agitation, pH, temperature, feed rate, and dissolved oxygen.

---

## 📊 Key Findings

### Productivity (kg/h)

| Strategy | Mean Productivity | vs. APC |
|----------|------------------|---------|
| Recipe-Driven | 12,917 kg/h | –18.1% |
| Operator-Controlled | 12,431 kg/h | –22.7% |
| **APC-Raman** | **15,248 kg/h** | **Best** |

- ANOVA: F = 7.16, **p = 0.001** → statistically significant difference
- Recipe vs. Operator: p = 0.60 → **no significant difference** (human intervention alone doesn't help)

### Effect Size (Cohen's d)

| Comparison | Cohen's d | Interpretation |
|------------|-----------|---------------|
| Recipe vs. Operator | 0.14 | Small (negligible) |
| Recipe vs. APC | 0.80 | Large |
| Operator vs. APC | 1.14 | Very Large |

### PAA Control Stability (CV%)

| Strategy | Mean CV% | Stability vs. APC |
|----------|----------|------------------|
| Recipe-Driven | 41.81% | 83.5% worse |
| Operator-Controlled | 54.91% | 87.4% worse |
| **APC-Raman** | **6.90%** | **Most stable** |

APC-Raman continuously modulates PAA flow using real-time spectroscopic feedback, compared to the rigid stepwise feeding (bang-bang control) used in the other strategies.

### 💰 Estimated Economic Impact

Assuming penicillin price of $100/kg and 33.7 batches/year:

| Comparison | Extra Production/Year | Additional Revenue/Year |
|------------|----------------------|------------------------|
| APC vs. Recipe | +18,066,205 kg | **+$1.81 billion** |
| APC vs. Operator | +21,829,238 kg | **+$2.18 billion** |

---

## 🛠️ Tools & Libraries

| Tool | Purpose |
|------|---------|
| `pandas` | Data manipulation |
| `dask` | Loading large (>2GB) CSV files |
| `scipy` | ANOVA, t-tests, statistical analysis |
| `numpy` | Numerical computation |
| `matplotlib` | Time series visualization |
| `Tableau` | Exploratory data analysis & outlier detection |

---

## 🚀 How to Run

1. **Download the dataset** from [IndPenSim](http://www.industrialpenicillinsimulation.com) and save to your Google Drive

2. **Open the notebook** in Google Colab:  
   [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1iIIam78Uc7jGepcU0aga5QOKX10HntoT?usp=sharing)

3. **Update the file path** in the notebook to match your Google Drive location:
   ```python
   zip_path = '/content/drive/MyDrive/Bio Data/100_Batches_IndPenSim.zip'
   ```

4. **Run all cells** sequentially

---

## 📁 Repository Structure

```
bioprocess-control-analysis/
├── README.md
├── penicillin_simulation_dataset_analysis.ipynb    # Main analysis notebook
└── requirements.txt                                # Python dependencies
```

---

## 📦 Requirements

```
pandas
dask[dataframe]
scipy
numpy
matplotlib
```

Install with:
```bash
pip install pandas "dask[dataframe]" scipy numpy matplotlib
```

---

## 📚 References

- Goldrick S., Stefan A., Lovett D., Montague G., Lennox B. (2015). *The development of an industrial-scale fed-batch fermentation simulation.* Journal of Biotechnology, 193:70–82.

- Goldrick S., Duran-Villalobos C., Jankauskas K., Lovett D., Farid S.S., Lennox B. (2019). *Modern day control challenges for industrial-scale fermentation processes.* Computers and Chemical Engineering.

## 👤 Author
   **Susila Hadiyati**  
   [LinkedIn](https://linkedin.com/in/susilahadiyati) | [GitHub](https://github.com/susihad)
   
Enjoy!
