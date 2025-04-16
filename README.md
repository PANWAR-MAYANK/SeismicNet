# 🌍 Earthquake Magnitude & Depth Prediction using Deep Learning

Predicting the magnitude and depth of earthquakes using only their geographic coordinates (latitude and longitude) with state-of-the-art deep learning models.

![Earthquake Prediction Map](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c0/2010_Earthquake_Epicenters.png/640px-2010_Earthquake_Epicenters.png)

---

> *“Earthquakes don't kill people. Buildings do. But early warnings and insights can change that.”*

---

## 🚀 Project Overview

This project leverages deep learning techniques to predict two crucial seismic parameters — **magnitude** and **depth** — from an earthquake’s **latitude** and **longitude**. Using the [USGS Earthquake Database](https://www.kaggle.com/datasets/usgs/earthquake-database/data), I explored multiple neural network architectures, including a powerful LSTM model, to capture underlying geographic patterns in seismic activity.

Earthquake prediction is inherently complex due to non-linear and spatio-temporal dependencies. Deep learning, particularly LSTMs and dense neural nets, enables modeling such intricate relationships — potentially contributing to disaster risk mitigation and early warning systems.

---

## 📌 Problem Statement

Given:
- **Latitude** and **Longitude** (input features)

Predict:
- **Magnitude** (on the Richter scale)
- **Depth** (in kilometers)

Both target variables are continuous.

---


## 📁 Dataset Description

The dataset used in this project is sourced from the [USGS Earthquake Database on Kaggle](https://www.kaggle.com/datasets/usgs/earthquake-database/data). It provides a comprehensive record of global seismic activity, detailing essential information about each earthquake event.

- **Total Records**: 23,595 earthquake events
- **Total Columns**: 22 features per record
- **Data Range**: Covers events from the early 20th century up to recent years
- **Format**: CSV (Comma-Separated Values)
- 

### 🎯 Target Variables
- **Magnitude**: A continuous variable typically ranging from 0 to 10 on the Richter scale. It quantifies the energy released during an earthquake.
- **Depth**: A continuous variable representing the distance (in kilometers) from the Earth's surface to the earthquake's hypocenter. It spans from shallow depths (< 70 km) to deep-focus earthquakes (> 300 km).

### 🧠 Input Features
- **Latitude**: Continuous values from -90° to 90°, indicating the earthquake's north-south location.
- **Longitude**: Continuous values from -180° to 180°, denoting the earthquake's east-west location.

 ### 🧾 Sample Columns in the Dataset
| Column Name      | Description                                           |
|------------------|-------------------------------------------------------|
| `Date`           | Date of the earthquake event                          |
| `Time`           | Time of the event                                     |
| `Latitude`       | Epicenter latitude (used as input)                   |
| `Longitude`      | Epicenter longitude (used as input)                  |
| `Depth`          | Earthquake depth in kilometers (used as target)      |
| `Magnitude`      | Richter scale magnitude (used as target)             |
| `Location Name`  | Descriptive location name                            |
| `Type`           | Earthquake type (e.g., Earthquake, Explosion, etc.)  |

These geographic coordinates are the sole input to the deep learning models, aiming to predict the corresponding magnitude and depth values. The minimalistic input design helps evaluate how spatial positioning alone can inform seismic intensity and depth estimations.

This dataset's structure makes it ideal for exploring spatial relationships in geophysical data and applying advanced neural architectures like LSTMs and dense networks for real-world regression tasks.



---

## 🧠 Models Implemented

### 🔹 Neural Network Model 1
- Feedforward architecture with 3 dense layers.
- ReLU activations for hidden layers.
- Softmax (classification) output layer.
- Optimizer: Adam.
- Grid search for batch size and epochs.
- **MSE on validation set: -97.94**

---

### 🔹 Neural Network Model 2
- Integrated `KerasRegressor` with `GridSearchCV`.
- ReLU activations; RMSprop optimizer.
- Hidden Layers: Two layers with 16 neurons each.
- Hyperparameter optimization for activation, neurons, and optimizer.
- **MSE on validation set: 0.014**

---

### 🔹 Neural Network Model 3
- Regularization with 20% dropout after each layer.
- Linear output activation for regression.
- Hidden Layers: Two layers with 64 neurons each.
- Early stopping enabled with patience of 100 epochs.
- **MSE on validation set: 5768.42**

---

### 🔹 LSTM Model (Best Performing)
- Architecture: 2 LSTM layers (64 units each) + dropout.
- Compiled with Adam optimizer and MSE loss.
- Trained for 100 epochs with early stopping.
- Evaluation on test data:
  - **Loss**: 4910.75
  - **MAE**: 27.23
  - **MSE**: 4910.75
- Prediction Metrics:
  - **Magnitude** — MAE: 0.31 | MSE: 0.19
  - **Depth** — MAE: 54.15 | MSE: 9821.32

---

## 📊 Visualizations

### 📈 Histogram Comparisons
- Actual vs Predicted Magnitudes
- Actual vs Predicted Depths

### 🌐 Geospatial Mapping
- Earthquake locations color-coded by predicted magnitude/depth.
- Implemented using `Cartopy` and `Plotly`.

<div align="center">
<img src="https://raw.githubusercontent.com/your-username/your-repo/main/assets/magnitude_map.png" width="600" />
</div>

---

## 🧪 Evaluation Metrics

- **Mean Squared Error (MSE)**
- **Mean Absolute Error (MAE)**
- Validation and Test Set Metrics reported.
- Grid Search for Hyperparameter Tuning (where applicable).
- EarlyStopping used to prevent overfitting.

---

## 📚 Lessons Learned

- **Architecture complexity ≠ better performance** — Simpler models often outperformed deeper ones.
- **Regularization** — Dropout layers and early stopping improved generalization.
- **Preprocessing impact** — Standard scaling of input data was crucial for model convergence.
- **LSTM advantages** — Despite using only spatial input (lat/long), LSTM captured underlying patterns effectively.

---

## 💡 Recommendations & Future Work

- Incorporate **additional features** like tectonic plate movement, historical tremor frequency, or geological fault lines.
- Use **temporal data** (e.g., sequence of past quakes) to improve LSTM/GRU effectiveness.
- Deploy as a **real-time web dashboard** for visual analytics.
- Build ensemble models for more robust predictions.
- Integrate with **satellite or weather data** for holistic forecasting.


---


## 🌟 Why This Project Matters

Understanding and predicting seismic activity is a high-impact application of deep learning in geosciences. Though earthquakes are inherently unpredictable in many ways, models like these can help detect **patterns**, improve **preparedness**, and ultimately **save lives**.

---

