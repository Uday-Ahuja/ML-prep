# Machine Learning Development Life Cycle (MLDLC)

---

## Stages Overview

The MLDLC is **not hard-bound** - stages may overlap or iterate based on project needs.

---

## 1. Frame the Problem

**Goal:** Understand the problem thoroughly and plan approach

**Key Activities:**
- Define business objective
- Identify success metrics
- Determine if ML is actually needed
- Scope the project timeline and resources

---

## 2. Gathering Data

### Data Sources & Formats

#### CSV Files
- Simple, tabular format
- Easy to work with
- Most common for structured data

#### API (Application Programming Interface)
**Definition:** Interface that allows applications to communicate and exchange data

**How it works:**
- Send request to API endpoint
- Receive data in structured format (usually JSON)
- Example: Weather API, Stock market API

#### Web Scraping
**Definition:** Extracting data from websites programmatically

**Process:**
- Use Python libraries (BeautifulSoup, Scrapy)
- Parse HTML to extract required information
- Example: Scraping hotel prices from Trivago

#### Database
**Data Warehouse:**
- Centralized repository storing historical data
- Optimized for analysis and reporting
- Example: Company's sales data over years

**ETL (Extract, Transform, Load):**
- **Extract:** Get data from source
- **Transform:** Clean and format data
- **Load:** Store in target database

**Spark Clusters:**
- Distributed computing for big data
- Processes massive datasets in parallel
- Handles data too large for single machine

---

## 3. Data Preprocessing

**Why needed:** Raw data cannot be directly used for ML

### Common Data Issues:

#### Data Incompatibility
- Multiple sources with different formats
- Inconsistent naming conventions
- Different units of measurement

#### Noise
- Random errors in data
- Incorrect values
- Sensor errors or human mistakes

#### Structural Issues
- Missing columns
- Inconsistent data types
- Duplicate entries

#### Outliers
**Definition:** Data points significantly different from others

**Example:** House prices dataset where one house costs ₹100 crore among ₹50 lakh houses

### Preprocessing Steps:

1. **Remove duplicates** - Eliminate repeated records
2. **Handle missing values** - Fill or remove incomplete data
3. **Remove outliers** - Filter extreme values
4. **Scaling/Standardization** - Bring features to similar ranges

**Example:** Converting age (0-100) and salary (₹0-₹50L) to same scale (0-1)

---

## 4. Exploratory Data Analysis (EDA)

**Goal:** Understand data before building models

### Key Activities:

#### Study Relationships
- Analyze connection between input features and output
- Identify patterns and trends

#### Visualization
- **Univariate Analysis:** Study single feature (e.g., age distribution)
- **Bivariate Analysis:** Relationship between two features (e.g., age vs salary)
- **Multivariate Analysis:** Multiple features together

#### Handle Imbalanced Data
**Problem:** Unequal distribution of classes

**Example:** Fraud detection - 99% legitimate, 1% fraud

**Solution:** Balance using techniques like oversampling/undersampling

**Why EDA matters:** Helps make informed decisions in later stages

---

## 5. Feature Engineering and Selection

### Feature Engineering

**Feature:** Input column/variable in dataset

**Definition:** Creating new features or modifying existing ones to improve model performance

**Example:**
- Original: "Number of rooms", "Number of washrooms"
- Engineered: "Square feet" (represents both)
- Result: Single feature instead of two, more relevant information

**Other examples:**
- Combine "birth year" → "age"
- "Date" → "Day of week", "Month", "Quarter"

### Feature Selection

**Definition:** Selecting most important columns, removing irrelevant ones

**Benefits:**
- **Reduced training time** - Fewer features = faster computation
- **Improved accuracy** - Remove noise from irrelevant features
- **Better interpretability** - Easier to understand model

**Example:** In house price prediction, "owner's name" is irrelevant, remove it

---

## 6. Model Training, Evaluation, Selection

### Training Multiple Models

**Process:**
- Try multiple algorithms (Linear Regression, Decision Trees, Neural Networks)
- Compare results on same data
- Select best performing algorithm

### Hyperparameter Tuning

**Hyperparameter:** Settings that control how algorithm learns

**Definition:** Fine-tuning model parameters to optimize performance

**Example:** 
- Learning rate in neural networks
- Depth of decision tree
- Number of neighbors in KNN

### Ensemble Learning

**Definition:** Combining multiple algorithms to create a stronger model

**Techniques:**
- **Bagging:** Average predictions from multiple models
- **Boosting:** Sequential models where each corrects previous errors
- **Stacking:** Use output of multiple models as input to final model

**Why it works:** Different algorithms capture different patterns

---

## 7. Model Deployment

**Goal:** Make model accessible to users

### Deployment Process:

#### Step 1: Model Serialization
**Tool:** Pickle (Python library)
- Converts trained model to binary file
- Saves model for later use
- File can be loaded without retraining

#### Step 2: Create API
**API (Application Programming Interface):** Interface for user to interact with model

#### Step 3: Integration Flow
1. User provides input through application
2. Python code sends data to API
3. API loads binary model file
4. Model makes prediction
5. API returns result in JSON format
6. Result displayed to user

**JSON (JavaScript Object Notation):** Lightweight data format for easy data exchange

### Deployment Platforms:

- **Heroku:** Cloud platform for deploying apps
- **AWS (Amazon Web Services):** Comprehensive cloud platform
- **GCP (Google Cloud Platform):** Google's cloud infrastructure

---

## 8. Testing

**Goal:** Validate model performance with real users

### Testing Process:

#### Beta Testing
- Release new feature to **trusted users** (small group)
- Collect feedback on accuracy and usability

#### A/B Testing
**Definition:** Comparing two versions to see which performs better

**Example:**
- **Version A:** Old recommendation algorithm
- **Version B:** New ML model
- Compare metrics (click rate, user satisfaction)

### Decision Making:

**Good Feedback:**
- Proceed to Stage 9 (Optimize)
- Deploy to all users

**Bad Feedback:**
- Identify issues
- Update model accordingly
- Re-test before full deployment

---

## 9. Optimize

**Goal:** Maintain and improve model in production

### Key Activities:

#### Backup Strategy
- **Backup trained model** - Save current version before updates
- **Backup training data** - Preserve data for retraining
- **Ensure rollback capability** - Can revert to previous version if issues arise

#### Load Balancing
**Definition:** Distribute incoming requests across multiple servers

**Why needed:** Handle high traffic without server overload

#### Model Retraining

**Model Rotting (Model Drift):** Model accuracy decreases over time as real-world data changes

**Example:** 
- Model trained on 2020 data
- 2025 patterns differ (new trends, behaviors)
- Model becomes less accurate

**Solution:**
- Retrain model periodically with fresh data
- **Frequency decision factors:**
  - How fast does data change?
  - Business requirements
  - Resource availability

**Common frequencies:**
- Daily (stock market predictions)
- Weekly (e-commerce recommendations)
- Monthly (customer churn prediction)
- Quarterly (credit risk assessment)

---

## Lifecycle Characteristics

### Iterative Process
- Not linear - may go back to previous stages
- Continuous improvement cycle
- Feedback from deployment influences earlier stages

### Stage Dependencies
- Each stage builds on previous ones
- Quality at each stage affects final model
- Poor data preprocessing → Poor model performance

---

## Key Terminology Summary

| Term | Definition |
|------|------------|
| **Feature** | Input column/variable in dataset |
| **ETL** | Extract, Transform, Load - data pipeline process |
| **API** | Interface for applications to communicate |
| **JSON** | Lightweight data exchange format |
| **Outlier** | Data point significantly different from others |
| **Hyperparameter** | Settings controlling algorithm learning |
| **Ensemble** | Combining multiple models |
| **Model Drift** | Decrease in accuracy over time |
| **A/B Testing** | Comparing two versions |
| **Load Balancing** | Distributing traffic across servers |

---

## Common Mistakes to Avoid

1. **Skipping EDA** - Jumping straight to modeling without understanding data
2. **No backup plan** - Deploying without rollback capability
3. **Ignoring model drift** - Never retraining deployed models
4. **Poor feature selection** - Using all features without evaluation
5. **Insufficient testing** - Deploying without user feedback

---

## Real-World Application

**Example: E-commerce Product Recommendation**

1. **Frame:** Increase sales through personalized recommendations
2. **Gather:** User browsing history, purchase data, product catalog
3. **Preprocess:** Remove duplicates, handle missing ratings
4. **EDA:** Analyze purchase patterns, popular categories
5. **Feature Engineering:** Create "user interest score", "product popularity"
6. **Model Training:** Try collaborative filtering, content-based, hybrid
7. **Deploy:** API serving recommendations on product pages
8. **Test:** A/B test with 10% users
9. **Optimize:** Retrain weekly with new purchase data

---

## Next Steps After MLDLC

- Monitor model performance continuously
- Collect user feedback systematically
- Stay updated with new algorithms
- Document entire process for future reference
- Scale infrastructure as needed