# User Authentication API

This project is a Node.js backend application that provides user authentication APIs using Express.js and MongoDB.

## Features

- User registration
- User login
- Forgot password functionality
- JWT-based authentication

## Prerequisites

- Node.js
- MongoDB
- Express.js

## Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/user-authentication-api.git
    cd user-authentication-api
    ```

2. Install dependencies:
    ```bash
    npm install
    ```

3. Create a `.env` file in the root directory with the following content:
    ```env
    PORT=4000
    MONGODB_URI=mongodb://localhost:27017/your_database_name
    JWT_SECRET=your_jwt_secret_key
    ```
    Replace `your_database_name` and `your_jwt_secret_key`.

4. Start the server:
    ```bash
    nodemon server.js
    ```

## API Endpoints

### 1. User Registration

- **URL:** `/register`
- **Method:** POST
- **Body:**
    ```json
    {
        "username": "testuser",
        "email": "testuser@example.com",
        "password": "password123"
    }
    ```
- **Success Response:**
    ```json
    {
        "code": 201,
        "content": { "message": "User registered successfully" }
    }
    ```

### 2. User Login

- **URL:** `/login`
- **Method:** POST
- **Body:**
    ```json
    {
        "username": "testuser",
        "password": "password123"
    }
    ```
- **Success Response:**
    ```json
    {
        "code": 200,
        "content": {
            "message": "Login Successful",
            "token": "your_jwt_token_here"
        }
    }
    ```

### 3. Forgot Password

- **URL:** `/forgot-password`
- **Method:** POST
- **Headers:**
    ```http
    Authorization: Bearer your_jwt_token_here
    ```
- **Body:**
    ```json
    {
        "email": "testuser@example.com"
    }
    ```
- **Success Response:**
    ```json
    {
        "code": 200,
        "content": { "message": "Password reset email sent (simulated)" }
    }
    ```

### 4. Home Route

- **URL:** `/`
- **Method:** GET
- **Success Response:**
    ```json
    {
        "code": 200,
        "content": "Welcome to user home page"
    }
    ```

## Testing

You can use tools like Postman or Thunder Client to test the APIs. Here's how to test each route:

1. Register a new user
2. Login with the registered user to get a JWT token
3. Use the JWT token in the Authorization header for the forgot password route

Note: The forgot password functionality simulates sending an email. Check the server console for the reset token log.

## Technologies Used

- Node.js
- Express.js
- MongoDB
- Mongoose
- JSON Web Tokens (JWT)
- bcrypt.js

## Security Notes

- Passwords are hashed before storing in the database.
- JWT is used for authentication.
- The forgot password route is protected and requires authentication.

## License

This project is licensed under the MIT License.
