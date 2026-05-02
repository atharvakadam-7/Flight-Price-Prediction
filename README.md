# Flight Price Prediction

A Flask web app that estimates flight ticket prices based on travel details like airline, route, departure time, and number of stops. Enter your trip parameters, and the app runs them through a trained XGBoost model to give you a fare estimate.

The project covers the full pipeline — raw data to deployed web app — with the EDA, feature engineering, and training work documented in a Jupyter notebook if you want to follow along or tweak the model.

---

## Demo

> Add a screenshot of the web interface here once available.

---

## How the Model Was Built

The training data covers domestic Indian flights with records across airlines like IndiGo, Jet Airways, Air India, and others. The raw dataset needed a fair amount of cleaning before it was usable — departure and arrival times were stored as strings, duration was in a mixed format, and the route column needed parsing to extract stop counts reliably.

After preprocessing, the key features fed into the model are:

- Airline
- Source and destination city
- Departure time and arrival time (hour extracted)
- Total stops (non-stop, 1 stop, 2+ stops)
- Flight duration (in minutes)
- Date, month of journey

XGBoost was chosen over simpler regressors because flight prices are non-linear — the relationship between stops, duration, and price doesn't behave uniformly across airlines. The full reasoning, feature importance plots, and evaluation metrics are in `flight_price.ipynb`.

---

## Tech Stack

- **Flask** — web framework and API layer
- **XGBoost** — regression model for fare prediction
- **Scikit-learn** — preprocessing and pipeline utilities
- **Pandas / NumPy** — data cleaning and feature engineering
- **HTML / CSS** — frontend templates (Jinja2)

---

## Repository Structure

```
Flight-Price-Prediction/
│
├── app.py                  # Flask application and prediction route
├── flight_price.ipynb      # EDA, feature engineering, and model training
├── flight_xgb.pkl          # Serialized trained XGBoost model
│
├── templates/              # HTML templates for the web interface
│
├── dataset/                # Training and test CSV files
│
└── requirements.txt
```

---

## Running Locally

**1. Clone the repo**

```bash
git clone https://github.com/atharvakadam-7/Flight-Price-Prediction.git
cd Flight-Price-Prediction
```

**2. Install dependencies**

```bash
pip install -r requirements.txt
```

**3. Start the app**

```bash
python app.py
```

Open `http://127.0.0.1:5000` in your browser. Fill in the travel details and hit Predict.

---

## Dataset

The training data contains domestic Indian flight records with the following fields:

| Field | Description |
|---|---|
| Airline | Carrier name (IndiGo, Air India, Jet Airways, etc.) |
| Source / Destination | Departure and arrival cities |
| Dep_Time / Arrival_Time | Scheduled times for departure and arrival |
| Duration | Total flight time |
| Total_Stops | Number of layovers (non-stop through 4 stops) |
| Price | Ticket fare in INR — the target variable |

The dataset is split into train and test files, both included in `dataset/`. The notebook walks through the cleaning steps if you want to understand what was done before the data reached the model.

---

## Notes

The model generalizes reasonably well within the range of the training data — Indian domestic routes, standard airline carriers, and journey dates within the original dataset period. Predictions outside that scope (international routes, carriers not in the training set) will be less reliable.

If you want to retrain with newer data or experiment with hyperparameters, `flight_price.ipynb` has the full pipeline. Swapping in updated flight data and rerunning the notebook will produce a new `.pkl` file you can drop straight into the app.
