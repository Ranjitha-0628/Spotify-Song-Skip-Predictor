# 🎵 Spotify Skip Predictor

A machine learning project that predicts whether a user will skip a song based on audio features, listening context, and behavioral patterns.

![Python](https://img.shields.io/badge/python-3.8+-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Status](https://img.shields.io/badge/status-complete-success.svg)

## 📋 Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Dataset](#dataset)
- [Model Architecture](#model-architecture)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Key Insights](#key-insights)
- [Future Improvements](#future-improvements)

## 🎯 Overview

This project analyzes music listening behavior to predict song skips using machine learning. By examining factors like song tempo, energy, genre transitions, and listening context (time of day, position in session), the model achieves **~61% accuracy** in predicting whether a user will skip a track.

### Why This Matters
Understanding skip behavior helps:
- 🎧 Playlist curators create better listening experiences
- 📊 Streaming platforms improve recommendation algorithms
- 🎵 Artists understand what keeps listeners engaged

## ✨ Features

- **Synthetic Data Generation**: Creates realistic listening session data with 5,000+ song plays
- **Behavioral Modeling**: Encodes real-world skip patterns
- **Machine Learning**: Random Forest classifier with 100 decision trees
- **Feature Importance Analysis**: Identifies which factors most influence skip behavior
- **Interactive Visualizations**: Charts showing skip patterns
- **Real-time Predictions**: Test the model on custom songs

## 📊 Dataset

### Generated Features

**Song Audio Features:**
- `tempo`: Beats per minute (BPM)
- `energy`: Song intensity (0-1 scale)
- `danceability`: How suitable for dancing (0-1)
- `valence`: Musical positivity/happiness (0-1)
- `loudness`: Volume in decibels
- `duration_sec`: Song length in seconds
- `genre`: Musical genre (pop, rock, hip-hop, electronic, indie, jazz, classical)

**Listening Context:**
- `time_of_day`: When played (morning, midday, evening, night)
- `position_in_session`: Song order (1-15)
- `genre_switch`: Genre change from previous song

**Target Variable:**
- `skipped`: 1 if skipped, 0 if listened through
- `skip_time_sec`: When skip occurred

### Data Statistics
- **Total Songs**: ~5,700 plays
- **Sessions**: 500
- **Average Session**: 11-12 songs
- **Skip Rate**: ~56%

## 🤖 Model Architecture

**Algorithm**: Random Forest Classifier

**Why Random Forest?**
- Handles numerical and categorical features
- Resistant to overfitting
- Provides feature importance rankings

**Parameters:**
```python
RandomForestClassifier(
    n_estimators=100,
    max_depth=10,
    min_samples_split=20,
    random_state=42
)
```

## 🚀 Installation
```bash
# Clone repository
git clone https://github.com/yourusername/spotify-skip-predictor.git
cd spotify-skip-predictor

# Install packages
pip install pandas numpy scikit-learn matplotlib seaborn

# Launch Jupyter
jupyter notebook
```

## 💻 Usage
```python
# Generate data
df = generate_spotify_data(n_sessions=500)

# Train model
model = RandomForestClassifier(n_estimators=100)
model.fit(X_train, y_train)

# Predict
predictions = model.predict(X_test)
```

## 📈 Results

- **Accuracy**: 61.14%
- **ROC-AUC Score**: ~0.65
- **Baseline**: 50% (random)

## 💡 Key Insights

### Top Skip Predictors
1. **Position in Session**: Fatigue after song 10
2. **Genre Switching**: +20% skip probability
3. **Energy-Time Mismatch**: Wrong energy for time of day
4. **Duration**: Songs over 5 minutes skipped more
5. **Extreme Tempos**: <80 or >160 BPM

### Recommendations
- 🎼 Maintain genre consistency
- ⏰ Match energy to time of day
- 📏 Keep songs under 5 minutes
- 🎯 Front-load best tracks (songs 1-8)
- 🎚️ Stay in 90-140 BPM range

## 🔮 Future Improvements

- [ ] Integrate real Spotify API data
- [ ] Add user demographics
- [ ] Try XGBoost, Neural Networks
- [ ] Build web app deployment
- [ ] Add lyrics sentiment analysis

## 📧 Contact

**Your Name**
- GitHub: [Ranjitha-0628](https://github.com/Ranjitha-0628)
- Email: ranjithakrishnapa@gmail.com

---

⭐ Star this project if you found it helpful!

