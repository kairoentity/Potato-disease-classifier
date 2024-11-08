
# Potato Disease Classification

This project uses a Convolutional Neural Network (CNN) to classify potato leaves as either early blight, late blight, or healthy. Using a dataset of labeled leaf images, the model is trained to recognize distinct visual patterns associated with each condition, aiding in the early detection of these common diseases in potato crops. The model is deployed with FastAPI to enable easy access through a web interface for predictions.


## Model Architecture

The model is implemented using TensorFlow/Keras and follows a Convolutional Neural Network (CNN) architecture. The trained model is saved in the saved_models directory as 1.keras.

Key components:

* Input shape: Accepts RGB images
* Output: 3 classes (Early Blight, Late Blight, Healthy)
* The model performs binary classification using softmax activation in the output layer
## Deployment

### Prerequisites

* Python 3.7+
* FastAPI
* TensorFlow 2.x
* PIL (Python Imaging Library)
* uvicorn
## Usage

1. Install the required dependencies:
pip install fastapi uvicorn tensorflow pillow numpy

2. Run the FastAPI server:
python main.py

The server will start on http://localhost:8000

## API Endpoints

GET /ping: Health check endpoint

POST /predict: Upload an image for disease classification

## Example API Usage

#### Using Curl:

curl -X POST "http://localhost:8000/predict" \
     -H "accept: application/json" \
     -H "Content-Type: multipart/form-data" \
     -F "file=@potato_leaf.jpg"


#### Using Python Requests:

import requests

url = "http://localhost:8000/predict"
files = {"file": open("potato_leaf.jpg", "rb")}
response = requests.post(url, files=files)
print(response.json())
## Dataset 
The model is trained on the Plant Village dataset, which contains images of potato plant leaves in various conditions:

* Early Blight 
* Late Blight
* Healthy



## Data Preprocessing


* Images are loaded and resized to match the model's input requirements

* Data is normalized to the range [0,1]

* Dataset is split into training and validation sets
## Running the Server
1. Clone the repository:

    git clone <https://github.com/kairoentity/Potato-disease-classifier>

2. Ensure the model file is in the correct location:
saved_models/1.keras

3. Start the FastAPI server:
python main.py

4. Access the API documentation at http://localhost:8000/docs


## API Response Format

json

    {
        "class": "Potato___healthy",
        "confidence": 0.9823
    }


## Error Handling

The API includes basic error handling for:

* Invalid file formats
* Missing files
* Server errors
## Contributing

Feel free to open issues and pull requests for any improvements.