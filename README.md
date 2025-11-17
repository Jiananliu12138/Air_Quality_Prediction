# Air Quality Prediction Project

## Overview
This project provides a complete end-to-end pipeline for air quality prediction using historical and forecasted weather and air quality data. The system leverages Hopsworks for feature storage, model registry, and monitoring, and supports batch inference and dashboarding for multiple sensors in a city.

## Features

1. **Backfill Feature Pipeline**
    - Downloads >1 year of historical weather data.
    - Loads historical air quality data from CSV.
    - Registers both datasets as Feature Groups in Hopsworks.

2. **Daily Feature Pipeline**
    - Scheduled via GitHub Actions to run daily.
    - Downloads yesterday’s weather and air quality data, plus 7 day weather forecasts.
    - Updates Feature Groups in Hopsworks with new data.

3. **Training Pipeline**
    - Selects features for a Feature View.
    - Reads training data from the Feature View.
    - Trains a regression model to predict air quality (pm25).
    - Registers the trained model with Hopsworks.

4. **Batch Inference Pipeline & Dashboard**
    - Downloads the trained model from Hopsworks.
    - Predicts air quality for the next 7 days for all active sensors in Vienna.
    - Plots and saves a dashboard visualizing predictions.

5. **Prediction Monitoring (Hindcast)**
    - Plots a hindcast graph comparing predictions vs. actual measured air quality.
    - Monitors and visualizes model accuracy over time.

6. **Lagged Features**
    - Adds lagged air quality features (previous 1, 2, 3 days) to the model.

7. **Multi-Sensor Predictions**
    - Provides predictions for all air quality sensors in Vienna.

## Project Structure
- `mlfs/airquality/`: Core modules for data retrieval, feature engineering, and model logic.
- `notebooks/airquality/`: Jupyter notebooks for backfill, feature pipeline, training, inference, and monitoring.
- `data/`: Example CSVs for air quality and weather data.
- `docs/`: Documentation and dashboard assets.

## Usage
1. **Backfill Historical Data**: Run the backfill notebook to populate Feature Groups with historical data.
2. **Daily Pipeline**: Schedule the daily pipeline notebook to keep Feature Groups up to date.
3. **Model Training**: Use the training pipeline notebook to train and register models.
4. **Batch Inference**: Run the inference notebook to generate and visualize predictions.
5. **Monitoring**: Use the hindcast analysis in the inference notebook to monitor prediction accuracy.

## Requirements
- Python 3.10+
- Hopsworks account and API key
- See `requirements.txt` and `pyproject.toml` for dependencies

## Scheduling
- Use GitHub Actions to automate daily data ingestion and feature pipeline execution.

## References
- [aqicn.org](https://aqicn.org) for air quality data
- [Hopsworks](https://www.hopsworks.ai/) for feature store and model registry
   
# Create a conda or virtual environment for your project before you install the requirements
    pip install -r requirements.txt


##  Run pipelines with make commands

    make aq-backfill
    make aq-features
    make aq-train
    make aq-inference
    make aq-clean

or 
    make aq-all

## Dashboard URL
https://jiananliu12138.github.io/Air_Quality_Prediction/air-quality/vienna.html
