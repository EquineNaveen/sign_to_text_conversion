# Sign Language Recognition System

This project implements a real-time sign language recognition system using Decision Tree. It captures hand gestures via webcam, processes them with MediaPipe, and classifies them using a RandomForest model.

## Project Structure

- **artifacts/** - Directory containing pickle files and models
  - **data/** - Raw training image of each class organized by gesture class
  - **dataspace.pickle** - Processed hand landmark data
  - **modelspace.pkl** - Trained RandomForest model

## Setup Instructions

### Environment Setup

1. Create a Python environment (Python 3.10+ recommended)
2. Install dependencies:
   ```bash
   pip install opencv-python mediapipe scikit-learn numpy pandas
   ```


### 1. Data Collection

Run `image_creation.ipynb` to collect training data:
- The script will access your webcam
- Follow the prompts to capture images for each gesture class
- Press 'q' to start capturing images for a class
- It will capture 200 images per class

### 2. Data Processing

Run `pickle_conversion.ipynb` to process the images:
- Detects hand landmarks using MediaPipe
- Normalizes and extracts landmark coordinates
- Saves processed data to `artifacts/dataspace.pickle`

### 3. Model Training

Run `trainer.ipynb` to train the model:
- Loads processed data from `dataspace.pickle`
- Splits data into training and test sets
- Trains a RandomForest classifier
- Evaluates model accuracy
- Saves the model to `artifacts/modelspace.pkl`

### 4. Real-time Classification

Run `classifier.ipynb` to start real-time sign language recognition:
- Accesses webcam feed
- Processes each frame to detect hand landmarks
- Uses the trained model to classify gestures
- Displays recognized letters and builds words
- Special gestures for 'space', 'delete', and 'wait'

### 5. Letter to Sign Visualization

Run `lettertosign.ipynb` to visualize sign language:
- Enter a word when prompted
- The system will display images of corresponding sign language gestures

## Supported Gestures

The system recognizes the following 29 gestures:
- Letters A-Z (26 gestures)
- Space (1 gesture)
- Delete (1 gesture)
- Wait (1 gesture)

