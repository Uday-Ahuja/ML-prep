# Types of Machine Learning

**Study Source:** CampusX 100 Days of ML

---

## Classification by Application/Theory or supervision

### 1. Supervised Learning
- **Regression:** Predict continuous numerical values
- **Classification:** Predict categorical labels

### 2. Unsupervised Learning
- **Clustering:** Group similar data points
- **Dimensionality Reduction:** Reduce number of features
- **Anomaly Detection:** Identify outliers
- **Association:** Find relationships between variables

### 3. Semi-Supervised Learning
- Mix of labeled and unlabeled data

### 4. Reinforcement Learning
- Learning through rewards and penalties

---

## Types of Data

### Numerical Data
- Age
- Weight
- CGPA
- IQ

### Categorical Data
- Gender
- Nationality
- Yes/No labels

## Types of Learning
### Memorizing
- Learning by storing exact instances of data and recalling them when needed.
### Generalizing
- Learning by extracting patterns or rules from data, enabling predictions on unseen examples.

---

## Supervised Learning (Detailed)

**Definition:** Model learns from labeled data (both input and output columns) to predict outputs for new inputs.

**Example Dataset:** Student Placement Prediction (50,000 students)

| IQ  | CGPA | Placement |
|-----|------|-----------|
| 87  | 7.1  | Yes       |
| 111 | 8.9  | Yes       |
| 75  | 6.3  | No        |

- **Input columns:** IQ, CGPA
- **Output column:** Placement

**Two Types:**
- **Regression:** Output is numerical (e.g., predict salary)
- **Classification:** Output is categorical (e.g., Yes/No, spam/not spam)

---

## Unsupervised Learning (Detailed)

**Definition:** Learning patterns from data without labeled outputs. Model discovers structure, relationships, or irregularities purely from input features.

### Use Cases:

#### 1. Clustering
**Purpose:** Grouping data points into similar clusters

**How it works:** Points within a cluster are more similar to each other than to those in other clusters

**Example:** Customer segmentation in marketing

#### 2. Dimensionality Reduction
**Purpose:** Reducing number of input features while preserving important information

**Benefits:**
- Simplify data
- Reduce noise
- Speed up training
- Enable visualization

**Example:** PCA (Principal Component Analysis)

#### 3. Anomaly Detection
**Purpose:** Identifying data points that deviate significantly from normal patterns

**Use cases:**
- Fraud detection
- System failure detection
- Outlier identification

#### 4. Association Rule Learning
**Purpose:** Discovering frequent patterns and relationships between variables

**Example:** Market basket analysis - "If customer buys bread, they often buy butter"

---

## Semi-Supervised Learning

**Definition:** Learning from a dataset with small amount of labeled data and large amount of unlabeled data

**Key Idea:** Use structure in unlabeled data to improve learning when labeled data is scarce or expensive

**When to use:**
- Labeling data is expensive (medical imaging, expert annotations)
- Large unlabeled dataset available
- Small labeled dataset available

---

## Reinforcement Learning

**Definition:** Agent interacts with environment, takes actions, and learns policy by maximizing cumulative reward through trial and error

**Key Components:**
- **Agent:** The learner/decision maker
- **Environment:** The world agent interacts with
- **Actions:** Choices agent can make
- **Rewards/Penalties:** Feedback from environment
- **Policy:** Strategy agent learns

**Key Idea:** Learning driven by feedback (rewards/penalties), not labeled datasets

**Examples:**
- Game playing AI (AlphaGo)
- Self-driving cars
- Robot navigation

---

## Learning Modes (Batch vs Online)

### Batch Learning (Conventional)

**Definition:** Model trained once on entire dataset and doesn't update unless retrained from scratch

**Characteristics:**
- Requires all training data at once
- Model remains static after training
- Retraining is expensive and done periodically
- Training happens offline

**When to use:**
- Data is stable
- Training can be done offline
- Real-time adaptation not required
- Computational resources available for periodic retraining

**Example:** Monthly model retraining with accumulated data

---

### Online Learning

**Definition:** Model updates itself incrementally as new data arrives, one instance or small batch at a time

**Characteristics:**
- Learns continuously
- Adapts to changing data distributions
- Lower memory and computation per update
- Can handle concept drift

**When to use:**
- Data arrives as a stream
- System must adapt in real-time
- Data distribution may change over time
- Limited memory/storage

**Example:** Stock price prediction, spam filters that adapt to new spam patterns
**libraries:** skleran(SGD regressor),River, Vowpal Wabbit etc
**Learning Rate:**
- Means how frequently you want to train the data
- Important for efficiency of the model since too frequent learning can decrease efficiency of the model.
- Forgets past data and learns the new one so learning rate should pace with changing trends ie shall not be too fast nor too slow.

**Out of Core Learning:**
- Done offline but techniques of online ML are used
- Wen you have large dataset which cannot directly be used to train the model
- Data is broken/divided into smaller datasets and then those small datasets one-by-one are used to train the model
  
**Disadvantages:**
- Tricky : Because of multiple variables (learning speed, data processing on server)
- Risky : if someone controls the incoming data the model should be taken down from server to protect model being biased etc (anomaly detection could be used to protect model from such risks)

---
## Ways of learning
### Instance Based Learning:
- Follows the memorizing approach.
- The model stores training data and makes predictions based on similarity to stored instances.
- Example: K-Nearest Neighbors (KNN) – predicts output based on the distance between points.
- Characteristics:
      - Requires storing training data → higher memory usage.
      - No explicit model is formed; all reasoning happens at query time.
### Model Based Learning:
- Follows the generalizing approach.
- The model tries to learn underlying patterns and represent them as a function or rule.
- Mechanism: Creates a mathematical function (decision function/boundary) to predict outputs logically rather than by just comparing points.
- Advantages:
    - Can discard training data after learning → lower memory usage.
    - Decisions are based on the learned function, not raw data.
- Examples: Linear Regression, Logistic Regression, Decision Tree.
--- 
## Summary

**Supervised vs Unsupervised:**
- Supervised = Has labels → Predict
- Unsupervised = No labels → Discover patterns

**Batch vs Online:**
- Batch = Train once, use forever (until retrain)
- Online = Continuously learn from new data

---

## Questions to Explore
- When to choose which type of learning?
- Can we combine supervised and unsupervised?
- Real-world hybrid approaches?