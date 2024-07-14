
# FastAPI Item Management API

This is a FastAPI application for managing items in an inventory. It allows you to add, update, query, and delete items with specific attributes such as name, price, count, and category.

## Requirements

- Python 3.10+
- FastAPI
- Uvicorn
- Pydantic

## Installation

1. Clone the repository:
   ```sh
   git clone <repository-url>
   cd <repository-directory>
   ```

2. Create and activate a virtual environment:
   ```sh
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. Install the dependencies:
   ```sh
   pip install fastapi uvicorn
   ```

## Running the Application

To run the FastAPI application, use the following command:
```sh
uvicorn main:app --reload
```
This will start the development server and enable hot-reloading.

## Endpoints

### Get All Items

- **URL**: `/`
- **Method**: `GET`
- **Description**: Returns all items in the inventory.
- **Response**:
  ```json
  {
    "items": {
      "0": {
        "name": "Hammer",
        "price": 9.99,
        "count": 20,
        "id": 0,
        "category": "tools"
      },
      "1": {
        "name": "Pliers",
        "price": 5.99,
        "count": 20,
        "id": 1,
        "category": "tools"
      },
      "2": {
        "name": "Nails",
        "price": 1.99,
        "count": 100,
        "id": 2,
        "category": "consumables"
      }
    }
  }
  ```

### Query Item by ID

- **URL**: `/items/{item_id}`
- **Method**: `GET`
- **Description**: Returns an item by its ID.
- **Parameters**:
  - `item_id` (int): ID of the item to query.
- **Response**:
  ```json
  {
    "name": "Hammer",
    "price": 9.99,
    "count": 20,
    "id": 0,
    "category": "tools"
  }
  ```

### Query Items by Parameters

- **URL**: `/items/`
- **Method**: `GET`
- **Description**: Returns items matching the given query parameters.
- **Query Parameters**:
  - `name` (str, optional): Name of the item.
  - `price` (float, optional): Price of the item.
  - `count` (int, optional): Count of the item.
  - `category` (Category, optional): Category of the item (`tools` or `consumables`).
- **Response**:
  ```json
  {
    "query": {
      "name": "Hammer",
      "price": 9.99,
      "count": 20,
      "category": "tools"
    },
    "selection": [
      {
        "name": "Hammer",
        "price": 9.99,
        "count": 20,
        "id": 0,
        "category": "tools"
      }
    ]
  }
  ```

### Add an Item

- **URL**: `/`
- **Method**: `POST`
- **Description**: Adds a new item to the inventory.
- **Request Body**:
  ```json
  {
    "name": "Screwdriver",
    "price": 3.99,
    "count": 50,
    "id": 3,
    "category": "tools"
  }
  ```
- **Response**:
  ```json
  {
    "added": {
      "name": "Screwdriver",
      "price": 3.99,
      "count": 50,
      "id": 3,
      "category": "tools"
    }
  }
  ```

### Update an Item

- **URL**: `/update/{item_id}`
- **Method**: `PUT`
- **Description**: Updates an existing item in the inventory.
- **Parameters**:
  - `item_id` (int): ID of the item to update.
- **Query Parameters**:
  - `name` (str, optional): New name of the item.
  - `price` (float, optional): New price of the item.
  - `count` (int, optional): New count of the item.
- **Response**:
  ```json
  {
    "updated": {
      "name": "Hammer",
      "price": 10.99,
      "count": 30,
      "id": 0,
      "category": "tools"
    }
  }
  ```

### Delete an Item

- **URL**: `/delete/{item_id}`
- **Method**: `DELETE`
- **Description**: Deletes an item from the inventory.
- **Parameters**:
  - `item_id` (int): ID of the item to delete.
- **Response**:
  ```json
  {
    "deleted": {
      "name": "Hammer",
      "price": 9.99,
      "count": 20,
      "id": 0,
      "category": "tools"
    }
  }
  ```

## Running Tests

To be added...

## License

This project is licensed under the MIT License.
