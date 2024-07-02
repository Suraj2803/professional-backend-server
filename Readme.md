# Backend API Documentation

## Overview

This backend API is built using the MERN stack (MongoDB, Express.js, React, and Node.js) and includes JWT (JSON Web Token) authentication for secure access. This documentation provides details on how to set up, configure, and use the API endpoints.

## Table of Contents

1. [Installation](#installation)
2. [Configuration](#configuration)
3. [API Endpoints](#api-endpoints)
4. [Authentication](#authentication)
5. [Error Handling](#error-handling)
6. [Testing](#testing)
7. [License](#license)

## Installation

To get started, clone the repository and install the necessary dependencies:

```bash
git clone https://github.com/yourusername/yourproject.git
cd yourproject
npm install
```

## Configuration

Create a `.env` file in the root directory of your project and add the following environment variables:

```env
PORT=5000
MONGODB_URI=your_mongodb_uri
JWT_SECRET=your_jwt_secret
```

## API Endpoints

### User Registration

**Endpoint:** `/api/users/register`

**Method:** `POST`

**Description:** Registers a new user.

**Request Body:**
```json
{
    "name": "John Doe",
    "email": "john@example.com",
    "password": "password123"
}
```

**Response:**
```json
{
    "message": "User registered successfully",
    "user": {
        "id": "user_id",
        "name": "John Doe",
        "email": "john@example.com"
    }
}
```

### User Login

**Endpoint:** `/api/users/login`

**Method:** `POST`

**Description:** Authenticates a user and returns a JWT token.

**Request Body:**
```json
{
    "email": "john@example.com",
    "password": "password123"
}
```

**Response:**
```json
{
    "token": "jwt_token"
}
```

### Get User Profile

**Endpoint:** `/api/users/profile`

**Method:** `GET`

**Description:** Returns the profile of the authenticated user.

**Headers:**
```json
{
    "Authorization": "Bearer jwt_token"
}
```

**Response:**
```json
{
    "id": "user_id",
    "name": "John Doe",
    "email": "john@example.com"
}
```

## Authentication

This API uses JWT for authentication. Users must include the JWT token in the `Authorization` header as follows:

```json
{
    "Authorization": "Bearer your_jwt_token"
}
```

### Generating JWT Token

JWT tokens are generated during the user login process and must be included in the `Authorization` header for all protected routes.

## Error Handling

All endpoints return standard HTTP status codes along with a JSON response. For example:

**Error Response:**
```json
{
    "error": "Invalid credentials"
}
```

**Status Codes:**
- `200 OK`: The request was successful.
- `400 Bad Request`: The request was invalid or cannot be served.
- `401 Unauthorized`: Authentication failed or user does not have permissions for the requested operation.
- `404 Not Found`: The requested resource could not be found.
- `500 Internal Server Error`: An error occurred on the server.

## Testing

To run tests, use the following command:

```bash
npm test
```

### Dotenv experimental command
    // "dev": "nodemon -r dotenv/config --experimental-json-modules src/index.js"


Ensure you have set up your testing environment correctly in the `.env.test` file.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

For any questions or issues, please contact [your email address].