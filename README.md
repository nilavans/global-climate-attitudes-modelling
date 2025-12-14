## 📋 Overview

This project investigates global climate attitudes using supervised and unsupervised machine learning approaches. We address two key research questions:
1. **Can machine learning models predict strong support for climate commitments?**
2. **Do demographic factors or attitudes play a greater role in determining support?**


### Key Findings

|Finding|Result |
|---------|--------|
|Best Model| Logistic Regression (82.8% accuracy)|
|Demographics vs Attitudes| Attitudes matter more — Age ranked 44th/68 features |
| Country Typologies| 3 distinct clusters with a clear North-South divide |

---

## 📊 Dataset
**Source:** [UNDP Peoples' Climate Vote 2024]( https://www.undp.org/publications/peoples-climate-vote-2024)
|Attribute | Value |
| ----------- | ------- |
|Total Records | 45,145 |
|Countries | 73 |
| Survey Questions |15 |
| Final Sample (after preprocessing) | 141 country-age groups |
| Features | 68 (67 attitudes + 1 demographic) |

---

## 🔬 Methodology

### Data Preprocessing Pipeline

```
Raw Data (45,145 rows)
    ↓
Filter: Adult ages (18-35, 36-59, 60+) + "All Education"
    ↓
Complete Groups Only (all 15 questions answered)
    ↓
Reshape: Long → Wide format
    ↓
Feature Engineering (67 attitude features + Age_Numeric)
    ↓
Binary Target: Strong Support (>85%) vs Moderate (≤85%)
    ↓
Final Dataset: 141 observations × 68 features

```
### Why Country × Age?
The survey data provides age breakdowns OR education breakdowns — never both simultaneously. After comparing completeness rates:

| Option | Complete Groups | Rate |
| -------- | ----------------- | ------ |
| Country × Age | 141 | 49.1% |
| Country × Education | 135 | 48.7% |
| Country only | 72 | 100% |

Country × Age was selected because:
- "Under 18" had ** 0 complete observations ** → excluded
- Age is more relevant for generational climate attitude research
- Provides more granular data than country-only aggregation
---

## 🤖 Models
### Supervised Learning (Predictive Modelling)
| Model | Accuracy | F1 Score | Balanced Accuracy |
| ------- | ---------- | ---------- | -------------------|
| **Logistic Regression** | **82.8%** | **82.8%**| **82.9%**|
| Random Forest | 72.4% | 71.4% | 72.4% |

**Why Logistic Regression wins:** The relationship between attitudes and climate support is approximately linear. The simpler model generalises better with 141 observations.

### Unsupervised Learning (Clustering)
**K-Means (K=3)** applied to 72 country-level aggregates:
| Cluster | Name | Countries | Key Characteristics |
| --------- | ------ | ----------- | ---------------------|
| 0 | Engaged & Action-Oriented | 20 | High collaboration support (92%), Latin America, SE Asia |
| 1 | Moderate & Cautious | 13 | Lowest urgency (72%), USA, UK, Germany, Japan |
| 2 | Highly Concerned & Urgent | 39 | Highest transition urgency (49%), Africa, South Asia |

**Key Insight:**
 Clear **North-South divide** — Developing nations show higher urgency for climate action than developed economies.

 ---
 ### Team Name (Nine Tales):
| Name                           | Student ID  | Email                  |
|--------------------------------|-------------|-------------------------|
| Nilavan Sritharan              | 201997034   | shvj0061@leeds.ac.uk   |
| Asjad Moiz Khan                | 202023700   | gfqs0308@leeds.ac.uk   |
| Krithik Sharan Suresh Alagianayagi | 202000567 | mxnp0398@leeds.ac.uk   |
| Zhenny Marifatul Husna         | 201859055   | dpvq0990@leeds.ac.uk   |

---


## 📚 References

1. Hornsey, M. J., et al. (2016). Meta-analyses of the determinants and outcomes of belief in climate change. *Nature Climate Change*, 6(6), 622–626.
2. Poortinga, W., et al. (2023). Generational differences in climate-related beliefs, risk perceptions and emotions in the UK. *Commun Earth Environ*, 4(229).
3. Lee, T. M., et al. (2015). Predictors of public climate change awareness and risk perception around the world. *Nature Climate Change*, 5(11), 1014–1020.
4. UNDP & University of Oxford. (2024). Peoples' Climate Vote 2024: Data centre.

---
## 🙏 Acknowledgements

- **UNDP** and **University of Oxford** for the Peoples' Climate Vote 2024 dataset.
- **University of Leeds, School of Computer Science** — COMP5122M Data Science Module

















