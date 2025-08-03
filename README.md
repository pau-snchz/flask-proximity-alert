# Flask Proximity Alert (Backend API)

This repository contains the backend API for AI-powered proximity alerts for warehouse deliveries.  
It provides endpoints for calculating delivery proximity to a warehouse and serves as the data source for the [logistics-dashboard](https://github.com/pau-snchz/logistics-dashboard) (frontend Laravel application).

---

## Features

- **Warehouse & Delivery Location Input:** Accepts delivery coordinates, uses stored warehouse location.
- **Radius Selection:** Configurable alert radius (100m, 250m, 500m).
- **Proximity Calculation:** Computes distance between warehouse and delivery.
- **API Responses:** Returns JSON indicating proximity status and distance.
- **Intended Frontend:** Built to integrate with the [logistics-dashboard](https://github.com/pau-snchz/logistics-dashboard) Laravel frontend.

---

## Getting Started

### Prerequisites

- Python 3.8+
- [pip](https://pip.pypa.io/en/stable/)

### Installation

```bash
git clone https://github.com/pau-snchz/flask-proximity-alert.git
cd flask-proximity-alert
python -m venv venv
source venv/bin/activate    # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### Running the API

```bash
python app.py
```
---

## API Usage

The API exposes endpoints to:

- **Check delivery proximity:**  
  Send a POST request with delivery coordinates and radius to get status and distance.

Example request using **curl**:
```bash
curl -X POST http://localhost:5000/api/check_proximity \
  -H "Content-Type: application/json" \
  -d '{"warehouse": [14.5995, 120.9842], "delivery": [14.6000, 120.9850], "radius": 250}'
```

Example response:
```json
{
  "within_range": true,
  "distance": 102.42
}
```

---

## Integration

The frontend for this API is: [logistics-dashboard](https://github.com/pau-snchz/logistics-dashboard) (Laravel)

- The frontend provides a user interface for inputting delivery coordinates, selecting radius, and visualizing the results on a map.
- This backend is currently deployed on [Render](https://render.com) and its endpoint configured in the frontend’s `.env` or config files.

---

## Technologies Used

- Python
- Flask (Web Framework)
- Geopy or similar for geolocation calculations
