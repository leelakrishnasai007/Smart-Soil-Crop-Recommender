# Smart Soil Crop Recommender 🌱 (Machine Learning + EDA)

A data-driven crop recommendation project that predicts the most suitable crop based on soil properties
(N, P, K, pH, EC, Sulphur, and trace elements like Fe, Zn, Mn, Cu, B).

This repository is organized to be recruiter-friendly:
- clear problem statement
- reproducible notebook
- dataset included
- results and comparison of multiple ML models
- project artifacts (slides + poster) included in /docs

------------------------------------------------------------

Why this project?

Choosing the right crop is not just about experience — it depends heavily on soil chemistry.
If farmers pick a crop that doesn’t match soil conditions, it can lead to:
- lower yield
- wasted fertilizer and water
- higher cost and poor sustainability

This project demonstrates how classic machine learning can turn soil test values into practical crop suggestions.

------------------------------------------------------------

What the project does (high-level)

Think of it like a small ML pipeline:

1) Load soil dataset (nutrients + soil health indicators)
2) Clean and validate the data
3) Explore relationships (EDA + visualizations)
4) Convert crop labels to model-ready format (encoding)
5) Train multiple classifiers
6) Compare models using accuracy + confusion matrix + ROC curve
7) Recommend the crop class for a given soil profile

------------------------------------------------------------

System overview (mini architecture)

Soil Dataset (CSV)
        |
        v
Preprocessing (cleaning, label encoding, scaling)
        |
        v
Model Training (LogReg / Decision Tree / Random Forest / SVM)
        |
        v
Evaluation (accuracy, precision, recall, F1, ROC, confusion matrix)
        |
        v
Prediction (recommended crop label)

Key idea:
- the dataset is the foundation
- EDA explains patterns
- model evaluation proves reliability

------------------------------------------------------------

Dataset (what’s inside)

Rows: 620
Columns: 12

Features:
- N (Nitrogen)
- P (Phosphorus)
- K (Potassium)
- pH
- EC (Electrical Conductivity)
- S (Sulphur)
- Cu, Fe, Mn, Zn, B (trace elements)
- label (crop name)

Crops include examples like pomegranate, mango, grapes, mulberry, ragi, potato.

File location in this repo:
data/agri.csv

------------------------------------------------------------

Exploratory Data Analysis (EDA)

The notebook includes:
- missing value checks
- label distribution
- nutrient summary statistics
- correlation heatmap
- feature-wise visualizations (histograms, violin plots, scatter plots)
- crop-specific trends for pH and EC

Goal of EDA here:
not only to plot graphs, but to understand what features separate crops.

------------------------------------------------------------

Models implemented

This project compares multiple classifiers:

- Logistic Regression (baseline)
- Logistic Regression with L1 regularization
- Decision Tree
- Random Forest
- SVM

Why multiple models?
Because different algorithms behave differently:
- linear models are fast and simple
- tree-based models handle non-linearity well
- SVM can generalize strongly with the right kernel

------------------------------------------------------------

Results (summary)

Top performance:
- Random Forest: ~96% accuracy
- SVM: ~96% accuracy

Baseline:
- Logistic Regression: ~93.5% accuracy

Takeaway:
non-linear models performed best because soil data patterns are not purely linear.

------------------------------------------------------------

How to run (local)

1) Clone the repository
git clone <your-repo-url>
cd Smart-Soil-Crop-Recommender

2) Create a virtual environment (recommended)
python -m venv venv

macOS / Linux:
source venv/bin/activate

Windows:
venv\Scripts\activate

3) Install dependencies
pip install -r requirements.txt

4) Run the notebook
jupyter notebook

Open:
notebooks/Smart_Soil_Crop_Recommender.ipynb

------------------------------------------------------------

How to use

Inside the notebook:
- run all cells from top to bottom
- training + evaluation will run
- you can test a custom soil input by replacing a sample row and calling model.predict()

------------------------------------------------------------

Limitations

- This is a supervised classifier trained on a fixed dataset
- It works best when new soil samples match the dataset’s value ranges
- It does not include weather, region/climate, irrigation, or market factors
- It’s a model for soil-based suitability, not a full farming decision engine

------------------------------------------------------------

Future improvements

1) Add real “recommendation output”
- instead of only predicting a label, show top-3 crops with confidence scores

2) Add external context
- weather, season, rainfall, climate zone, satellite/NDVI

3) Build a simple UI
- Streamlit web app where a user enters soil values and gets crop output

4) Region-specific models
- train separate models for different regions for more realistic recommendations

------------------------------------------------------------

Tech stack

- Python
- Jupyter Notebook
- pandas, numpy
- matplotlib, seaborn
- scikit-learn