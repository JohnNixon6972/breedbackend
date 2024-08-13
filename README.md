Here's a `README.md` file for your Flask API that uses a TensorFlow Lite model to predict dog breeds based on an image URL.

---

# Dog Breed Prediction API

This Flask API predicts the breed of a dog from an image URL using a TensorFlow Lite model. The model takes in an image, processes it, and returns the predicted breed and confidence score.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Example Request](#example-request)
- [Model and Labels](#model-and-labels)
- [Acknowledgments](#acknowledgments)

## Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/JohnNixon6972/breedbackend
   cd dog-breed-prediction-api
   ```

2. **Create and activate a virtual environment (optional but recommended):**

   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install the required packages:**

   ```bash
   pip install -r requirements.txt
   ```

4. **Ensure you have the TensorFlow Lite model and labels file:**

   - `b0_tflite.tflite`: The TensorFlow Lite model file.
   - `labels.txt`: A text file containing the breed labels, one per line.

   These files should be placed in the same directory as the Flask application.

## Usage

To start the Flask server, run:

```bash
python app.py
```

The API will be available at `http://127.0.0.1:5000/`.

## API Endpoints

### `GET /`

- **Description:** A simple test endpoint to check if the API is running.
- **Response:**
  ```json
  {
    "val": "Hello Gourav"
  }
  ```

### `GET /predict`

- **Description:** Predict the dog breed from an image URL.
- **Request Body:**
  - JSON object containing the `img_url` key:
    ```json
    {
      "img_url": "https://example.com/dog.jpg"
    }
    ```
- **Response:**
  - JSON object containing the predicted breed and confidence score:
    ```json
    {
      "breed": "Golden Retriever",
      "score": 98.76
    }
    ```

## Example Request

You can use `curl` or any HTTP client to make a request to the `/predict` endpoint.

### Example using `curl`:

```bash
curl -X GET http://127.0.0.1:5000/predict -H "Content-Type: application/json" -d '{"img_url": "https://example.com/dog.jpg"}'
```

### Example using Python:

```python
import requests

url = "http://127.0.0.1:5000/predict"
data = {"img_url": "https://example.com/dog.jpg"}

response = requests.get(url, json=data)
print(response.json())
```

## Model and Labels

- **Model:** The TensorFlow Lite model (`b0_tflite.tflite`) should be trained and optimized for predicting dog breeds.
- **Labels:** The `labels.txt` file should list all possible dog breeds corresponding to the model's output indices.

## Acknowledgments

This project uses TensorFlow Lite for model inference and the Flask framework for serving the API. Special thanks to any open-source contributors and resources used during the development.

---

This `README.md` provides clear instructions for setting up and using your Flask API, along with examples of how to interact with it.
