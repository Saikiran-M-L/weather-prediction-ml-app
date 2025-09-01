# 🌦️ Weather Prediction for Major German Cities  

This is a full-stack machine learning project that predicts weather conditions (temperature, humidity, windspeed, etc.) for a specified city and date. It uses a two-stage ML pipeline and provides a web interface for interaction.

- 🏙️ Hamburg  
- 🏙️ Berlin  
- 🏙️ Munich  
- 🏙️ Cologne  
- 🏙️ Frankfurt  

The unique part of this pipeline is that while **many features are used during training**, at prediction time (in production), the model only requires:  

- **City**  
- **Date**  

---

## 🧠 Project Workflow  

### **Stage 1 Model (Feature Generator)**  
- **Inputs**:  
  - City (OneHotEncoded)  
  - Date (converted into cyclical features `sin_dayofyear`, `cos_dayofyear`)  

- **Outputs**: Intermediate weather features used in Stage 2 (e.g., `tempmax`, `dew`, `windgust`, `uvindex` etc.)  

---

### **Stage 2 Model (Final Predictor)**  
- **Inputs**: Features generated from Stage 1  
- **Outputs**:  
  - 🌡 Temperature  
  - 💧 Humidity  
  - 🌧 Precipitation  
  - 🍃 Windspeed  
  - 🤒 Feelslike  
  - 🔽 Pressure  
  - 📝 Weather Description (classification)  
  - 🌤 Weather Icon (classification)  

---

## ⚙️ Installation  

1. Clone the repository:  
```bash
git clone https://github.com/Saikiran-M-L/weather-prediction-ml-app.git
cd weather-prediction-ml-app
```

2. (Optional) Install Git LFS if models/data are large:  
```bash
git lfs install
```

3. Install dependencies:  
```bash
pip install -r requirements.txt
```

---

## 📊 Training the Models  

### Stage 1 (Feature Generator)  
Run the notebook:  
```bash
cd notebooks
jupyter notebook stage1_training.ipynb
```

This will train the **Stage 1 model** and save:  
- `models/stage1_model.joblib`  
- `models/city_encoder_stage1.joblib`  

---

### Stage 2 (Final Predictor)  
Run the notebook:  
```bash
cd notebooks
jupyter notebook stage2_training.ipynb
```

This will train the **Stage 2 model** and save:  
- `models/stage2_model.joblib`  

---

## 🌍 Running the Flask API  

1. Go to the app directory:  
```bash
cd app
```

2. Run the Flask API:  
```bash
python api.py
```

3. API will be available at:  
```
http://127.0.0.1:4500/predict
```

---

## 📌 Example API Request  

**POST request** to `/predict`:  

```json
{
  "city": "Berlin",
  "date": "2025-09-01"
}
```

**Response (example):**  

```json
{
  "temperature": 21.3,
  "humidity": 67,
  "precipitation": 0.2,
  "windspeed": 12.5,
  "feelslike": 20.8,
  "pressure": 1013,
  "description": "Partly Cloudy",
  "icon": "partly-cloudy-day"
}
```

---

## 📈 Model Evaluation  

- Regression models are evaluated using:  
  - R² Score  
  - MAE (Mean Absolute Error)  
  - RMSE (Root Mean Squared Error)  

- Classification models are evaluated using:  
  - Accuracy  
  - F1-score  

Evaluation results are included inside the training notebooks.  

---

## 🔮 Future Improvements  

- Improve classification of rare weather events  
- Add real-time weather API comparison (for benchmarking)  
- Deploy API to cloud (AWS/GCP/Heroku)  

---

## 👨‍💻 Author  

Developed by **Saikiran**  
# Weather Temperature Predictor

## Overview
A Flask-based machine learning web app that predicts the daily temperature in major German cities using historical weather data.

## Stack
- Python (Flask, scikit-learn)
- HTML (form)
- Deployment: Render / Heroku

## How to Run
1. Install requirements:
   ```
   pip install -r requirements.txt
   ```

2. Train the model:
   ```
   weather_prediction_stage1_model.ipynb
   weather_prediction_stage2_model.ipynb

3. Run the app:
   ```
   python app.py
   ```

4. Access at `http://localhost:4500`

---

## ❗ Notes

- Use Git LFS to manage .pkl files over 100MB.
- CORS enabled globally via flask-cors for API access from frontend.
- Supports Vue.js frontend served from Flask or separately deployed.

---
