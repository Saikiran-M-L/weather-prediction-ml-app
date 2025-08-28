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
   python train_model.py
   ```

3. Run the app:
   ```
   python app.py
   ```

4. Access at `http://localhost:5000`

## Deployment (Heroku)
Add Procfile and push to Heroku with:
```
git init
heroku create
git add .
git commit -m "Initial commit"
git push heroku master
```