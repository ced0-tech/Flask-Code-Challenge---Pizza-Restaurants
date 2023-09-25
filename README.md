Flask Code Challenge - Pizza Restaurants
This Flask application is designed to meet the requirements of the Pizza Restaurant domain. It provides an API with various functionalities related to restaurants and pizzas. The application supports CRUD operations for restaurants, pizzas, and the association between them via the RestaurantPizza model.

Getting Started
To get started with this project, follow the steps below:

Clone the repository to your local machine:

bash
Copy code
git clone https://github.com/ced0-tech/Flask-Code-Challenge---Pizza-Restaurants.git
Install the required dependencies using pip:

bash
Copy code
pip install -r requirements.txt
Set up the database by running the following commands:

bash
Copy code
flask db init
flask db migrate
flask db upgrade
Run the Flask server:

bash
Copy code
flask run
Models
This application uses three models to represent the data:

Restaurant: Represents a pizza restaurant with a name, address, and a many-to-many relationship with pizzas via the RestaurantPizza model.

Pizza: Represents a pizza with a name, ingredients, and a many-to-many relationship with restaurants via the RestaurantPizza model.

RestaurantPizza: Represents the association between restaurants and pizzas. It includes a price field and belongs to both a restaurant and a pizza.

Validations
RestaurantPizza Model: The RestaurantPizza model includes a validation that ensures the price falls between 1 and 30.

Restaurant Model: The Restaurant model includes validations for the restaurant name: it must be less than 50 characters in length and must be unique.

Routes
The API provides the following routes, adhering to RESTful conventions:

GET /restaurants
Retrieve a list of all restaurants.

Example Response:

json
Copy code
[
  {
    "id": 1,
    "name": "Dominion Pizza",
    "address": "Good Italian, Ngong Road, 5th Avenue"
  },
  {
    "id": 2,
    "name": "Pizza Hut",
    "address": "Westgate Mall, Mwanzi Road, Nrb 100"
  }
]
GET /restaurants/:id
Retrieve a specific restaurant by ID, including its associated pizzas.

Example Response (if the restaurant exists):

json
Copy code
{
  "id": 1,
  "name": "Dominion Pizza",
  "address": "Good Italian, Ngong Road, 5th Avenue",
  "pizzas": [
    {
      "id": 1,
      "name": "Cheese",
      "ingredients": "Dough, Tomato Sauce, Cheese"
    },
    {
      "id": 2,
      "name": "Pepperoni",
      "ingredients": "Dough, Tomato Sauce, Cheese, Pepperoni"
    }
  ]
}
Example Response (if the restaurant does not exist):

json
Copy code
{
  "error": "Restaurant not found"
}
DELETE /restaurants/:id
Delete a restaurant by ID, along with its associated RestaurantPizza entries.

Example Response (if the restaurant exists and is deleted successfully):

json
Copy code
{}  # Empty response body
Example Response (if the restaurant does not exist):

json
Copy code
{
  "error": "Restaurant not found"
}
GET /pizzas
Retrieve a list of all pizzas.

Example Response:

json
Copy code
[
  {
    "id": 1,
    "name": "Cheese",
    "ingredients": "Dough, Tomato Sauce, Cheese"
  },
  {
    "id": 2,
    "name": "Pepperoni",
    "ingredients": "Dough, Tomato Sauce, Cheese, Pepperoni"
  }
]
POST /restaurant_pizzas
Create a new RestaurantPizza entry associated with an existing pizza and restaurant.

Request Body Example:

json
Copy code
{
  "price": 5,
  "pizza_id": 1,
  "restaurant_id": 3
}
Example Response (if the RestaurantPizza is created successfully):

json
Copy code
{
  "id": 1,
  "name": "Cheese",
  "ingredients": "Dough, Tomato Sauce, Cheese"
}
Example Response (if the RestaurantPizza is not created successfully due to validation errors):

json
Copy code
{
  "errors": ["validation errors"]
}
Testing Endpoints
To test the endpoints, you can use tools like Postman or any API testing tool of your choice. Start the Flask server, make requests to the specified routes, and verify the responses.

Feel free to customize and expand upon this project to meet your specific needs and requirements. 




