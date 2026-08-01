# Student Mental Health Score Prediction

A simple FastAPI application for predicting student mental health scores from social media usage and lifestyle features.

## Project Structure

- `main.py` - FastAPI app that loads a pre-trained model and exposes a prediction endpoint.
- `Mental_Health_Model.pkl` - Serialized machine learning model used for inference.
- `requirements.txt` - Python dependencies required to run the app.
- `Student Social Media And Mental Health Impact.csv` - Dataset used for analysis and model training.
- `Predicting_Student_Mental_Health_Score_from_Social_Media_Usage.ipynb` - Jupyter notebook containing exploratory analysis and model development.

## Requirements

- Python 3.8+ recommended
- `venv` or another virtual environment tool

## Setup

1. Create and activate a virtual environment:

```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
```

2. Install dependencies:

```powershell
pip install -r requirements.txt
```

## Run the API

Start the FastAPI server with Uvicorn:

```powershell
uvicorn main:app --reload
```

The API will be available at `http://127.0.0.1:8000`.

## Endpoints

- `GET /` - health check endpoint.
- `POST /predict` - returns a predicted mental health score.

## Request Example

Send JSON with student data to `/predict`:

```json
{
  "age": 21,
  "gender": "Female",
  "country": "India",
  "academic_level": "Undergraduate",
  "most_used_platform": "Instagram",
  "purpose_of_use": "Entertainment",
  "avg_daily_usage_hours": 3.5,
  "daily_unlocks": 20,
  "study_hours": 4.0,
  "physical_activity_hours": 1.0,
  "sleep_hours_per_night": 7.0,
  "stress_level": "Medium"
}
```

## Response Example

```json
{
  "predicted_mental_health_score": 6.78
}
```

## Notes

- The app uses a pre-trained model loaded from `Mental_Health_Model.pkl`.
- Country values outside the top listed countries are grouped into `Other`.
- Input validation is handled by Pydantic in `main.py`.
