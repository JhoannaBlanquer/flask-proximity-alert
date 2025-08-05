# Flask Warehouse Proximity Alert

This is an AI-Powered Proximity Alerts for Warehouse Deliveries, a Flask microservice that calculates the geospatial distance between a **warehouse** and a **delivery location**. It can be used to trigger proximity-based alerts (e.g., if a delivery is within 100–500 meters of a warehouse).

---

## Tech Stack 

- Python 3
- Flask
- geopy (for accurate geospatial distance)
- flask-cors

---

## Installation

```bash
# Clone the project
git clone https://github.com/JhoannaBlanquer/flask-proximity-alert.git
cd flask-proximity-alert

# Setup virtual environment
python3 -m venv venv
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

---

## Run the App Locally

```bash
python app.py
```

The app will be available at:  
**http://127.0.0.1:5000**

---

## API Endpoint

### `POST /check_proximity`

**Request:**

```json
{
  "warehouse": [14.5995, 120.9842],
  "delivery": [14.6000, 120.9850],
  "radius": 250
}
```

- `warehouse`: array of [latitude, longitude]
- `delivery`: array of [latitude, longitude]
- `radius`: proximity range in meters

**Response:**

```json
{
  "distance": 105.83,
  "within_range": true
}
```

---

## Test with cURL

```bash
curl -X POST http://127.0.0.1:5000/check_proximity \
-H "Content-Type: application/json" \
-d '{"warehouse": [14.5995, 120.9842], "delivery": [14.6000, 120.9850], "radius": 250}'
```

---

## Deployment 
The latest version of this service is deployed and available at:
https://flask-proximity-alert-n0v7.onrender.com

---

## Integration with Frontend

This Flask microservice is integrated with a Laravel-based frontend available at:  
[logistics-dashboard](https://github.com/JhoannaBlanquer/logistics-dashboard.git)

- The Laravel app allows users to input delivery coordinates and choose a proximity radius.
- These inputs are sent to the Flask backend via HTTP POST requests using Laravel's built-in HTTP client.
- The Flask API responds with the calculated distance and whether the delivery is within the specified range.
- Data exchange between the Laravel frontend and Flask backend is handled via **RESTful JSON APIs**, enabling fast, real-time proximity calculations.