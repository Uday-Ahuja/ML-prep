# Challenges in Machine Learning

---

## 1. Data Collection

Issues when collecting data for corporate projects.

**Approaches to solve:**
1. **Fetch data from APIs** (e.g., Flickr API)
2. **Web Scraping** (e.g., scraping Google)

---

## 2. Insufficient or Unlabeled Data

**The Unreasonable Effectiveness of Data:**
The algorithm doesn't matter as much when dataset size is huge.

**Example:**
- Algorithm A is better than Algorithm B
- Dataset sizes: 100 vs 10,000,000
- Despite being inferior, Algorithm B will perform better due to massive data

**Key Insight:** More data often beats better algorithms

---

## 3. Non-Representative Data

When major data that defines the dataset's identity is missing, the model tends to predict less accurate outputs.

**Example:**
World Cup winning team prediction survey done only in India would be biased towards India's win.

### Types of Poor Representation:

#### Sampling Noise
- Sample data doesn't represent population well
- Example: Survey from limited geographic region

#### Sampling Bias
- Lack of representative sampling
- Example: Taking data from 200 countries but only from Indian nationals

---

## 4. Poor Quality Data

**Common issues:**
- Abrupt/anomalous values
- Outliers
- Missing values
- Different formats of values (inconsistent data entry)

**Impact:** Reduces model accuracy and reliability

---

## 5. Irrelevant Features

> **"Garbage In, Garbage Out"**

Data should be relevant to the output you require.

**Input decides output** - feature selection is critical.

### Feature Engineering Example:
Instead of separate columns for:
- Weight
- Height

Combine into:
- BMI (Body Mass Index)

This reduces dimensionality while maintaining relevant information.

---

## 6. Overfitting

**Definition:** When the model memorizes the data instead of learning patterns from it.

**Symptoms:**
- Very high training accuracy (close to 100%)
- Poor performance on new/test data
- Model learns noise instead of signal

**Analogy:** Like memorizing exam answers without understanding concepts

---

## 7. Underfitting

**Definition:** When the model is too simple to capture underlying patterns in data.

**Symptoms:**
- Low training accuracy
- Low test accuracy
- Model fails to learn even basic patterns

**Cause:** Model complexity is insufficient for the problem

---

## 8. Software Integration

Integrating ML models into existing software systems presents challenges:
- Compatibility issues
- Performance requirements
- Scalability concerns
- Version control of models

---

## 9. Offline Learning and Deployment

**Challenges:**
- Deployment not stable
- Expensive process
- Model retraining required
- Version management
- Monitoring in production

**Batch Learning Limitations:**
- Can't adapt to real-time changes
- Requires periodic retraining
- Downtime during updates

---

## 10. Cost Involved

ML projects require significant investment in:
- Data collection and cleaning
- Computing resources (GPUs, cloud)
- Model development time
- Deployment infrastructure
- Ongoing maintenance

---

## Teacher's Recommendations

### Build End-to-End ML Projects:
1. **Create complete ML models** (not just notebooks)
2. **Deploy in real applications:**
   - Web apps
   - Mobile apps
   - Desktop software
3. **Learn MLOps:**
   - Model versioning
   - CI/CD for ML
   - Monitoring and logging
   - Automated retraining

### Why This Matters:
Companies want engineers who can build AND deploy, not just experiment in Jupyter notebooks.

---

## Key Takeaways

1. **Data quality > Algorithm quality** (often)
2. **Representative data is critical**
3. **Feature engineering matters**
4. **Balance between overfitting and underfitting**
5. **Deployment is as important as model building**
6. **Learn the full pipeline, not just modeling**

---

## Related Concepts to Explore
- Data augmentation techniques
- Cross-validation strategies
- Regularization methods
- MLOps best practices
- Model monitoring in production