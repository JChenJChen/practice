# CODESIGNAL COURSE PATH "APIs Made Easy with Python and Flask" NOTES

- https://learn.codesignal.com/course-paths/74
- https://learn.codesignal.com/preview/course-paths/74#courses

4 lessons, 20 lessons:
1. Introduction to Flask Basics - 6 lessons
2. Mastering Flask HTTP Methods - 5 lessons
3. Flask Data Modeling with Marshmallow - 5 lessons
4. Securing Flask Apps with JWT Authentication - 4 lessons

course path skills:
- developing:
  - Server-Side Programming
  - Data Management and Database Querying
  - API Integration, Design, & Development
- intermediate:
  - Authentication, Authorization, & Security


## Mastering Flask HTTP Methods

### GET

```py
# TODO: Import the Flask class from the flask package
from flask import Flask
# TODO: Initialize a Flask app instance and call it my_app, remember to pass __name__ as an argument
my_app = Flask(__name__)
    
if __name__== "__main__":
# TODO: Check if the script is run directly (not imported)
    my_app.run(port=6000, host= "127.0.0.1")    
    # TODO: Start the  server  on port 6000

# To run the application, use the following command in the terminal:
python solution.py


pip install gunicorn

# run Flask app with gunicorn. In terminal:
gunicorn filename:app
# listening for requests on 127.0.0.1:8000 by default

# Change the command to bind (-b) the server to all IP addresses (0.0.0.0) on port 7000.
gunicorn filename:app -b 0.0.0.0:7000

# Specifying IP and PortSpecifying IP and Port
'''
gunicorn -b 0.0.0.0:8080 filename:app

gunicorn options:
- Worker Processes
- Timeouts
- Logging
- Daemon Mode
'''
```

#### Routes & Decorators

```py
# Define a route with a decorator
@app.route('/hello')
def hello():
    # Return a simple string response
    return "Hello, World!"

# http://localhost:5000/hello -> "Hello World"

# Defining GET method:
@app.route('/greet', methods=['GET'])


# Returning JSON for Structured Responses
from flask import jsonify

# Flask automatically sets response headers to application/json -- tells client to interpret the data as JSON:
# Content-Type: application/json

return jsonify(message="Hey there! This is a JSON response!")
```

- JSON's preferable over dicts:
- Converts dict to valid JSON string
- Explicitly sets the appropriate response headers
  - While returning a dict directly may set "Content-Type: application/json", 
  - using jsonify's 'more explicit & reliable to ensure proper formatting and headers.


#### Path Parameters:
```py
@app.route('/greet/<str:first_name>/<int:age>', methods=['GET'])
def greet_full_name(first_name, age):
    return jsonify(message=f"Greetings, {first_name} {age}!")
```

```py
from flask import request
@app.route('/route', methods=['GET'])
def function():
    # Extract the 'parameter_name' query parameter or use 'default_value' if not provided
    variable = request.args.get('parameter_name', 'default_value')


# Query parameters don't need to be in the route path, they're extracted from the URL using request.args
@app.route('/welcome',methods=['GET'])
def welcome():
    name = request.args.get('name', 'Visitor')
    return jsonify(message= f"Welcome, {name}! Enjoy your stay on this route.")

# The loop in /profiles/<int:profile_id> should compare profile['id'] with profile_id.



# Mock database as a list of dictionaries
database = [
    {"id": 1, "profile_name": "ron"},
    {"id": 2, "profile_name": "hermione"},
    {"id": 3, "profile_name": "harry"}
]

# TODO: Define a route to get all profiles at '/all_profiles'
@app.route('/all_profiles', methods=['GET'])
def all_profiles():
    # TODO: Return the entire profiles database as JSON
    return jsonify(database)
# TODO: Define a route at '/profiles' to get a single profile by ID with an int path parameter
@app.route('/profiles/<int:profile_id>')
def profiles(profile_id):
    # TODO: Loop through the database to find the profile with the given ID
    for profile in database:
        if profile['id'] == profile_id:
            # Return the found profile as JSON
            return jsonify(profile)
        else:
    # TODO: Return an error message with a 404 status code if the profile is not found
            return jsonify("error=Profile not found"), 404

```

### POST

```py
# Define a route to create a new user
@app.route('/users', methods=['POST'])
def create_user():
    # Get the new user data from the request body
    new_user = request.get_json()

    # Validate the new user data
    if "username" not in new_user:
        # Return a 400 Bad Request error if data is invalid
        return jsonify(error="Invalid data"), 400

    # Generate a new ID by finding the maximum existing ID and adding 1
    new_id = max(user['id'] for user in database) + 1
    new_user["id"] = new_id

    # Add the new user to the mock database
    database.append(new_user)
    
    # Return the newly added user as JSON with a status code 201 (Created)
    return jsonify(new_user), 201
```

### PUT - API call to update
```py
# Define a route to update an existing user
@app.route('/users/<int:user_id>', methods=['PUT'])
def update_user(user_id):
    # Get the updated user data from the request body
    updated_user = request.get_json()
    
    # Validate the updated user data
    if "username" not in updated_user:
        # Return an error message about invalid data in JSON format and a 400 status code
        return jsonify(message="User not found: invalid data"), 400
    
    # Find and update the user in the mock database
    for user in database:
        if user['id'] == user_id:
            # Update the user's username
            user['username'] = updated_user['username']
            # Return the updated user data in JSON format
            return jsonify(user), 200
            
    
    # Return an error message about user not being found in JSON format and a 404 status code
    return jsonify(message="User not found in json format"), 404
```

### DELETE - API call to delete user
```py
# Define a route to delete a user
@app.route('/users/<int:user_id>', methods=['DELETE'])
def delete_user(user_id):
    # Find the user to delete by looping through the database
    for user in database:
        if user['id'] == user_id:
            # Remove the user from the database
            database.remove(user)
            # TODO: Modify to return a 204 No Content status code
            return '', 204
    
    # Return an error message if the user is not found
    return jsonify(error="User not found"), 404

```

### Endpoint that accepts & combines multiple HTTP request types 

Instead of having separate GET, PUT, and DELETE endpoints for individual users, all these operations now reside at /users/<int:user_id>.
- Endpoint Without ID: This combines GET to retrieve all users and POST to create a new user.
- Endpoint With ID: This combines GET, PUT, and DELETE for operations on individual users specified by their ID.

```py
# Combined methods without user id
@app.route('/users', methods=['GET', 'POST'])
def handle_users():
    # Check if the request method is GET to retrieve all users
    if request.method == 'GET':
        return jsonify(database)
    
    # Check if the request method is POST to create a new user
    elif request.method == 'POST':
        new_user = request.get_json()
        if "username" not in new_user:
            return jsonify(error="Invalid data"), 400
        new_id = max(user['id'] for user in database) + 1
        new_user["id"] = new_id
        database.append(new_user)
        return jsonify(new_user), 201

# Combined methods with user id
@app.route('/users/<int:user_id>', methods=['GET', 'PUT', 'DELETE'])
def handle_user(user_id):
    # Check if the request method is GET to retrieve a user by ID
    if request.method == 'GET':
        for user in database:
            if user['id'] == user_id:
                return jsonify(user)
        return jsonify(error="User not found"), 404
    
    # Check if the request method is PUT to update a user by ID
    elif request.method == 'PUT':
        updated_user = request.get_json()
        if "username" not in updated_user:
            return jsonify(error="Invalid data"), 400
        for user in database:
            if user['id'] == user_id:
                user['username'] = updated_user['username']
                return jsonify(user)
        return jsonify(error="User not found"), 404

    # Check if the request method is DELETE to delete a user by ID
    elif request.method == 'DELETE':
        for user in database:
            if user['id'] == user_id:
                database.remove(user)
                return jsonify(message="User deleted")
        return jsonify(error="User not found"), 404
```

## Flask Data Modeling with Marshmallow

> https://codesignal.com/learn/lesson/3010
> 
- `fields.Int()`: Represents an integer.
- `fields.Float()`: Represents a floating-point number.
- `fields.Str()`: Represents a string.
- `fields.Email()`: Represents an email, ensuring valid email format.

### Defining Schemas and Serializing Data with Marshmallow

- integration library: `integration library`
- standalone version (used in course): `pip install marshmallow`
- why use Marshmellow: 
  - consistency: adherence to data schema
  - validation:  checks data type & format
  - (de)serialization: to/from JSON

```py
from marshmallow import Schema, fields

# Define a Marshmallow schema for user data
class UserSchema(Schema):
    # Non-matching key & schema field: Maps 'user_id' in data to 'id' in schema.
    # id's not marked as required bc it's generated automatically
    id = fields.Int(data_key='user_id')  
    username = fields.Str(required=True)   # String field for the username
    email = fields.Email()    # Email field for the user's email

# Create an instance of the User schema
user_schema = UserSchema()

# Define a route to fetch user data by id
@app.route('/users/<int:user_id>', methods=['GET'])
def get_user(user_id):
    # Find user in the database
    user = next((user for user in database if user['id'] == user_id), None)
    
    # If user is not found, return 404 error
    if user is None:
        return jsonify(error='User not found'), 404

    # Serialize the user data using Marshmallow's dump method
    result = user_schema.dump(user)
    
    # Return serialized data as JSON response
    return jsonify(result)

```

### Validating Incoming Data

> https://codesignal.com/learn/lesson/3011

```py
from flask import request, jsonify
from marshmallow import ValidationError

# Define a route to handle user creation
@app.route('/users', methods=['POST'])
def create_user():
    try:
        # Validate the incoming JSON data using the User schema
        user_data = user_schema.load(request.get_json())
    except ValidationError as err:
        # Return validation errors as a JSON response
        return jsonify(error = err.messages), 400
```


```py
# Full example code
from flask import Flask, request, jsonify
from marshmallow import Schema, fields, ValidationError

# Initialize a Flask app instance
app = Flask(__name__)

# Mock database as a list of dictionaries
database = [
    {"id": 1, "username": "cosmo", "email": "cosmo@example.com"},
    {"id": 2, "username": "jake", "email": "jake@example.com"},
    {"id": 3, "username": "emma", "email": "emma@example.com"}
]

# Define a Marshmallow schema for user data
class UserSchema(Schema):
    id = fields.Int()
    username = fields.Str(required=True)
    email = fields.Email(required=True)

# Create an instance of the User schema
user_schema = UserSchema()

# Define a route to handle user creation
@app.route('/users', methods=['POST'])
def create_user():
    try:
        # Validate the incoming JSON data
        user_data = user_schema.load(request.get_json())
    except ValidationError as err:
        # Return validation errors as JSON response
        return jsonify(error=err.messages), 400

    # Generate a new ID by finding the maximum existing ID and adding 1
    new_id = max(user['id'] for user in database) + 1
    user_data["id"] = new_id

    # Add the new user to the mock database
    database.append(user_data)

    # Return the newly created user data as JSON response
    return jsonify(user_data), 201

```
### Nested Schemas

> https://codesignal.com/learn/lesson/3012

```py
# Define a nested schema for address
class AddressSchema(Schema):
    street = fields.Str(required=True)
    city = fields.Str(required=True)

# Define a main schema for user with nested address
class UserSchema(Schema):
    id = fields.Int()
    username = fields.Str(required=True)
    email = fields.Email(required=True)
    address = fields.Nested(AddressSchema, required=True)
```
### Data Validation

> https://codesignal.com/learn/lesson/3013

```py
from marshmallow import Schema, fields, validate

class UserSchema(Schema):
    id = fields.Int()  # Optional
    username = fields.Str(  # Required
        required=True,
        validate=validate.Length(min=3, max=20)
    )
    email = fields.Email(required=True)  # Required
    age = fields.Int(validate=validate.Range(min=18, max=99))  # Optional
    website = fields.Url()  # Optional
```

### Building Your Own Custom Validator



---

# chatGPT: REST API in Python - copying code practice
```py
from flask import Flask, request, jsonify
from flask_alchemy import SQLAlchemy
from datetime import datetime
from wekzeug.security import generate_password_hash, check_password_hash
import jwt
import datetime
from functools import wraps

# initial Flask app and DB
app = Flask(__name__)
app.config['SQLALCHEMY_DB_URI'] = 'sqlite:///datingapp.db'
app.config['SECRET_KEY'] = 'secret_key'
db = SQLAlchemy(app)

# models
class User(db.Model):
    id = db.Column(db.integer, primary_key=True)
    username = db.Column(db.string(80), unique=True, nullable=False)
    email = db.Column(db.string(120), unique=True, nullable=False)
    password = db.Column(db.string(200), nullable=False)
    gender = db.Column(db.string(10), nullable=False)
    bio = db.Column(db.Text, nullable=False)
    created_at = db.Column(db.DateTime, default=datetime.datetime.now(datetime.UTC))

# routes
@app.route('/register', methods=['POST'])
def register():
    data = register.get_json()
    hashed_password = generate_password_hash(user.password, data['password']):
        return jsonify.(user_data)
    
@app.route('/profile', methods='[PUT]')
@token_required
def update_profile (current_user):
    data = request.get_json()
    current_user.bio = data.get('bio', current_user.bio)
    db.session.committ()
    return jsonify({'message': 'profile created'})
```