# Café Directory API

This repository contains an API for a café directory. The API is developed using Flask and SQLAlchemy.

## API Endpoints

The café directory API offers the following endpoints:

### GET /random

This endpoint returns a randomly selected café from the database.

### GET /all

This endpoint returns all cafés in the database.

### GET /search

This endpoint allows searching for a café by location. It accepts a query parameter `loc` to specify the location and returns the café details if found.

### POST /add

This endpoint adds a new café to the database. It accepts form data with the following fields:

- `name` (required): The name of the café.
- `map_url` (required): The URL to the café's location on a map.
- `img_url` (required): The URL to an image of the café.
- `loc` (required): The location of the café.
- `sockets` (optional): Boolean indicating if the café has power sockets.
- `toilet` (optional): Boolean indicating if the café has a toilet.
- `wifi` (optional): Boolean indicating if the café has Wi-Fi.
- `calls` (optional): Boolean indicating if the café allows taking calls.
- `seats` (required): The seating capacity of the café.
- `coffee_price` (optional): The price of coffee at the café.

### PATCH /update-price/{cafe_id}

This endpoint updates the price of a café. It accepts the café ID as a path parameter and the new price as a query parameter `new_price`.

### DELETE /report-closed/{cafe_id}

This endpoint deletes a café from the database. It requires an API key as a query parameter `api-key` for authentication. The café ID should be provided as a path parameter.

## Data Model

The café data model used in the API is as follows:

```python
class Cafe(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(250), unique=True, nullable=False)
    map_url = db.Column(db.String(500), nullable=False)
    img_url = db.Column(db.String(500), nullable=False)
    location = db.Column(db.String(250), nullable=False)
    seats = db.Column(db.String(250), nullable=False)
    has_toilet = db.Column(db.Boolean, nullable=False)
    has_wifi = db.Column(db.Boolean, nullable=False)
    has_sockets = db.Column(db.Boolean, nullable=False)
    can_take_calls = db.Column(db.Boolean, nullable=False)
    coffee_price = db.Column(db.String(250), nullable=True)
```

## Usage

To use the café directory API, you can make HTTP requests to the appropriate endpoints described above. You can test the API using tools like cURL or Postman.
