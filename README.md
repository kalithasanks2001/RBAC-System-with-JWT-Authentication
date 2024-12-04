# RBAC System with JWT Authentication

This project implements a **Role-Based Access Control (RBAC)** system using **Flask** and **JWT** (JSON Web Tokens) for authentication. It includes API endpoints for **user registration**, **login**, and **access control** based on user roles.

## Features
- **User Registration**: Allows new users to register with a specified role (`Admin`, `User`, or `Moderator`).
- **Login**: Authenticates users and issues a JWT token for secure access to resources.
- **Role-Based Access**: Users can access resources based on their role and permissions (defined for each role).
- **JWT Authentication**: Secures API endpoints using JWT tokens.

## Technology Stack
- **Python** (3.x)
- **Flask**: A lightweight web framework for building the API.
- **PyJWT**: For generating and validating JWT tokens.
- **Requests**: For sending HTTP requests (used in the test script).
- **Nest-Asyncio**: For running Flask in Jupyter Notebooks (if applicable).

## Setup and Installation

### 1. Clone the Repository
Clone the repository to your local machine:

```bash
git clone https://github.com/<your-username>/rbac-system.git
cd rbac-system
```

### 2. Install Dependencies
Make sure you have Python 3.x installed. Then, install the required libraries:

```bash
pip install flask pyjwt requests nest_asyncio
```

### 3. Run the Flask Application
To run the Flask application, execute the following command in your terminal:

```bash
python rbac_flask_test.py
```

This will start the Flask server locally on `http://127.0.0.1:5000`.

The Flask app will be available, and you can begin testing the API using the test script below.

## Testing the API

### **Test Flow**

Once the Flask application is running, the test script will automatically perform the following steps:

1. **Register a new user**: Sends a `POST` request to the `/register` endpoint with a `username`, `password`, and `role`.
2. **Login**: Sends a `POST` request to the `/login` endpoint using the registered credentials to receive a **JWT token**.
3. **Access a resource**: Sends a `GET` request to the `/resource/<action>` endpoint, passing the JWT token in the `Authorization` header. It checks if the logged-in user has permission to access the specified resource (`read`, `write`, or `delete`).

### **Modify the Test Script**

In the `rbac_flask_test.py` script, you can modify the following variables to test different users and actions:

```python
username = "testuser"   # Change the username
password = "testpass"    # Change the password
role = "User"            # Change to "Admin", "User", or "Moderator"
```

The script will automatically test the role-based permissions for the `read` action, but you can modify the action to test other permissions (`write`, `delete`, etc.) as well.

### **Test Output**

After running the script, you should see output similar to this:

```
Register User Response: {'message': 'User registered successfully!'}
Login Response: {'token': 'your_jwt_token_here'}
Access Resource (read) Response: {'message': 'Access granted for read action.'}
```

If the user is not authorized to access a resource, you will see an "Access denied!" message.

## API Endpoints

### **1. POST /register**

Registers a new user.

**Request Body**:
```json
{
  "username": "testuser",
  "password": "testpass",
  "role": "User"  // Role can be "Admin", "User", or "Moderator"
}
```

**Response**:
- Success: `{"message": "User registered successfully!"}`
- Failure (User already exists): `{"message": "User already exists!"}`
- Failure (Invalid role): `{"message": "Invalid role!"}`

### **2. POST /login**

Logs in a user and returns a JWT token.

**Request Body**:
```json
{
  "username": "testuser",
  "password": "testpass"
}
```

**Response**:
- Success: `{"token": "your_jwt_token_here"}`
- Failure (Invalid credentials): `{"message": "Invalid credentials!"}`

### **3. GET /resource/<action>**

Accesses a resource based on the action (`read`, `write`, `delete`), and checks if the user has the required role.

**Request Header**:
```plaintext
Authorization: your_jwt_token_here
```

**Response**:
- Success: `{"message": "Access granted for <action> action."}`
- Failure (Access denied): `{"message": "Access denied!"}`

This README file provides a detailed guide to set up, run, and test your **RBAC system** with **JWT authentication** using Flask. 

### Key Points:
- **Cloning and Installing**: Instructions to clone the repo and install dependencies.
- **Running Flask**: How to run the Flask app.
- **Testing**: How the test script works, including modifying it for different test cases.
- **API Endpoints**: A description of the API endpoints used for registration, login, and resource access.

Let me know if you need to add or modify anything in this README! 😊
