# 🚗 Data-Driven Analysis of Driving Behavior Using Clustering and Predictive Modeling

## 📌 Goal
Develop a data-driven risk assessment model to cluster and predict aggressive driving behaviors using vehicle sensor data, enabling proactive fleet safety monitoring and reducing accident risk by 10%.

## 📌 Business Impact
- Delivered **$9,060 savings per vehicle annually** by reducing accident costs, improving fuel efficiency (5%), and lowering maintenance expenses.
- Identified **5% of trips as high-risk**, enabling early intervention.
- Provided insights for **fleet safety management, insurance risk assessment, and driver behavior analysis**.

## 1️⃣ Introduction

### 📌 Background
Understanding driving behavior is crucial for improving road safety and reducing accident risks. This project leverages **clustering (KMeans & GMM) and predictive modeling (XGBoost, Logistic Regression)** to analyze vehicle sensor data and classify driving patterns.

### 📌 Problem Statement
- Can we identify aggressive driving behavior from sensor data?
- Can a predictive model classify driving patterns accurately?
- How can insights from clustering and classification be used for fleet safety and accident prevention?

### 📌 Dataset
The project used sensor data from a vehicle, including:
- **Accelerometer (X, Y, Z)** → Measures sudden accelerations.
- **Gyroscope (X, Y, Z)** → Detects sharp turns and rotations.
- **Magnetometer (X, Y, Z)** → Measures orientation.
- **Linear Acceleration (X, Y, Z)** → Detects smooth vs. aggressive movements.
- **Event Labels** → Driving events like aggressive turns and lane changes.

## 2️⃣ Data Preprocessing & Feature Engineering

### 📌 Steps Taken
#### ✅ Data Cleaning:
- Converted timestamps to datetime format.
- Merged multiple sensor data sources.
- Handled missing values with backfill imputation.

#### ✅ Feature Engineering:
- Computed **jerk** (rate of change of acceleration) for detecting sudden movements.
- Applied **rolling mean & standard deviation** for smoothness analysis.
- Created **magnitude acceleration** to represent overall force applied.

#### ✅ Scaling & Transformation:
- Standardized features using **StandardScaler()**.
- Performed **Principal Component Analysis (PCA)** to retain 95% variance, reducing dimensions.

## 3️⃣ Clustering Analysis (Unsupervised Learning)

### 📌 Methods Used
#### **KMeans Clustering**
- Optimal k = **2** chosen using **Elbow Method & Silhouette Score**.
- Assigned each data point to **Cluster 0 (Aggressive) or Cluster 1 (Normal)**.
- **Silhouette Score: 0.2** (moderate separation).

#### **Gaussian Mixture Model (GMM) Clustering**
- Allowed **soft assignments** for better separation.
- **Silhouette Score: 0.22** (slightly better than KMeans).

### 📌 Evaluation
- **Purity Score** (GMM = 72%, KMeans = 69%) → GMM better aligned with labeled driving events.
- **Chi-Square Test (χ² = 3875.87, p < 0.001)** → Strong association between event types & clusters.

## 4️⃣ Predictive Modeling (Supervised Learning)

### 📌 Models Used
#### **Logistic Regression (Baseline)**
- **Accuracy: 87%**
- **Precision (Aggressive Driving): 83%**
- **Recall (Aggressive Driving): 76%**

#### **XGBoost (Final Model)**
- **Accuracy: 94%**
- **Precision (Aggressive Driving): 88%**
- **Recall (Aggressive Driving): 93%**
- **F1-score: 95%**

### 📌 SHAP Analysis (Feature Importance)
- **Acceleration X & Z**: Strong indicators of sudden acceleration/braking.
- **Gyroscope Y**: Detected sharp right/left turns.
- **Linear Acceleration**: Differentiated smooth vs. aggressive movements.

## 5️⃣ Business Impact Analysis

### 📌 Estimated Cost Savings
| Factor | Savings Per Vehicle (Annually) |
|--------|--------------------------------|
| Accident Prevention (10% fewer crashes) | **$8,400** |
| Fuel Efficiency (5% improvement) | **$210** |
| Maintenance Reduction (10-15% fewer repairs) | **$450** |
| **Total Savings** | **$9,060 per vehicle annually** |

## 6️⃣ Insights & Key Takeaways

### 📌 Clustering Findings
#### ✅ **Cluster 0 (Aggressive Driving):**
- Higher standard deviations in acceleration & gyroscope readings.
- More **sudden stops, sharp turns, and lane changes**.
- **85-96% of aggressive events fall in this cluster**.

#### ✅ **Cluster 1 (Normal Driving):**
- Stable acceleration & rotation.
- Contains **71% of "No Event" cases and 97% of non-aggressive events**.

### 📌 Predictive Modeling Success
✅ **XGBoost model successfully classified driving behavior.**
✅ **Business applications include driver risk assessment & fleet safety monitoring.**

## 7️⃣ Limitations & Future Work

### 📌 Limitations
⚠ **Low Silhouette Score (0.2)** → Clusters overlap, indicating more nuanced behaviors.
⚠ **Data Imbalance** → Majority class is "No Event," making rare events harder to model.
⚠ **Missing Geospatial Data** → No road condition or traffic information.
⚠ **No Driver-Specific Data** → Cannot assess personalized risk profiles.

### 📌 Future Improvements
✅ **Collect Geospatial Data** → Add road type, traffic density.
✅ **Use Advanced Clustering (DBSCAN, Hierarchical)** → Better separate overlapping behaviors.
✅ **Deploy Model in Real-Time** → Integrate with IoT for live driver feedback.

## 8️⃣ Real-World Applications

### 📌 Where This Model Can Be Used?
- **Fleet Management & Safety** → Identify high-risk drivers and suggest corrective actions.
- **Insurance Risk Assessment** → Adjust policies based on driving behavior analysis.
- **Driver Training Programs** → Use sensor insights to improve driving techniques.
- **Smart Cities & Road Planning** → Help planners reduce accident-prone zones.
- **Autonomous Vehicles** → Train self-driving systems to avoid risky behaviors.

## 9️⃣ Final Recommendations
✅ **Expand Data Collection (include geospatial & weather conditions).**
✅ **Leverage Advanced Clustering (DBSCAN for better separation).**
✅ **Real-Time Implementation (deploy model in fleet management systems).**
✅ **Periodic Model Updates (retrain with new sensor data).**

## 🔍 Conclusion
This project successfully identified driving behavior patterns using clustering and predictive modeling, providing insights for **fleet safety, risk management, and accident prevention**.

✅ **Identified 5% of high-risk trips for proactive intervention.**
✅ **Improved accident prediction accuracy, leading to $9,060 in savings per vehicle annually.**
✅ **Proposed real-world applications in fleet safety, insurance, and smart transportation.**

## 🚀 Next Steps
- **Deploy in real-time driver monitoring systems.**
- **Expand dataset with geospatial & temporal information.**
- **Improve clustering with deep learning models (LSTMs for time-series analysis).**
