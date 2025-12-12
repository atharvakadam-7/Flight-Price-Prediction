
# Flight Price Prediction App ✈️

A machine learning web application that predicts flight ticket prices based on airline, source, destination, departure time, and stops. Built with **Flask**, **XGBoost**, and **Pandas**.

## 🚀 Features
- **Predict Flight Fares**: Enter travel details to get an estimated ticket price.
- **Machine Learning**: Uses an XGBoost regressor trained on historical flight data.
- **Data Analysis**: Includes a Jupyter notebook (`flight_price.ipynb`) showing EDA, feature engineering, and model training.

## 🛠️ Tech Stack
- **Python** (Pandas, NumPy, Scikit-learn)
- **Machine Learning**: XGBoost
- **Web Framework**: Flask
- **Frontend**: HTML/CSS

## 📂 Project Structure
- `app.py`: Main Flask application.
- `flight_price.ipynb`: Notebook for data cleaning and model training.
- `flight_xgb.pkl`: Trained model file.
- `templates/`: HTML templates for the web interface.
- `dataset/`: Training and testing data.

## 💻 How to Run Locally
1. Clone the repository:
git clone https://github.com/atharvakadam-7/Flight-Price-Prediction.git
2. Install dependencies:
pip install -r requirements.txt
3. Run the app:
python app.py
4. Open your browser and go to `http://127.0.0.1:5000/`.

## 📊 Dataset
The model was trained on a flight dataset containing information like:
- **Airlines**: Indigo, Jet Airways, Air India, etc.
- **Route**: Departure/Arrival times, Source, Destination.
- **Stops**: Number of layovers.
