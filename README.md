![image](https://github.com/user-attachments/assets/96536451-8b1a-4475-94dc-cd1e65e8bc8f)

# Login & Register Form

This project is a basic user authentication system that allows users to register and log in to the application. It is built using Node.js, `pnpm` as the package manager, `express` for the server framework, `ejs` for templating, `jsonwebtoken` (JWT) for authentication, and a local database (`db-local`).


## Features

- User registration with password hashing.
- User login with JWT-based authentication.
- Session handling using JWT for protected routes.
- Views rendered with `ejs` templates.
- Local database `db-local` to store user data.

## Requirements

- Node.js (v14.x or higher)
- pnpm (v6.x or higher)

## Setup

1. Clone the repository:

   ```bash
   git clone <repository-url>
   cd <repository-folder>
    ```

2.  Install dependencies using pnpm:

```bash
pnpm install
 ```

3.  Create a .env file in the root directory and set up the following environment variables:

```env
PORT=3000
SECRET_JWT_KEY=your_jwt_secret
```

4.  Start the server:
```bash
pnpm run dev
 ```

5. The application will run on http://localhost:3000.

## Endpoints

1. Registration
- URL: `/register`
- Method: POST
- Description: Authenticates a user.
- Body:
    - `username` (string): The user's username.
    - `password` (string): The user's password.
- Response:
    - Success: `200 OK` with a message `User registered successfully`.
    - Error: `400 Bad Request` if the user already exists.

2. Login
- URL: `/login`
- Method: POST
- Description: Authenticates a user.
- Body:
    - `username` (string): The user's username.
    - `password` (string): The user's password.
- Response:
    - Success: `200 OK` with a JWT token in response.
    - Error: `401 Unauthorized` if credentials are invalid.

3. Protected Route
- URL: `/protected`
- Method: GET
- Description: Access to this route requires a valid JWT.
- Headers:
    - `Authorization`: Bearer `<JWT Token>`
- Response:
    - Success: `200 OK` with the dashboard data.
    - Error: `403 Forbidden` if the token is missing or invalid.
## Authentication

The system uses JWT for authentication. When a user logs in, they receive a JWT that must be sent in the `Authorization` header (in the format Bearer <token>) for accessing protected routes.


    
## How It Works

1.  Registration: A new user can register by providing a username and password. The password is hashed using `bcrypt` and stored in the local database (`db-local/users.json`).

2.  Login: A registered user can log in by providing valid credentials. On successful login, a JWT is generated and returned to the user.

3.  Protected : Users need to send their JWT token with requests to protected routes (like `/protected`). The JWT is verified by the middleware before granting access to the route.


## Views

The project uses `ejs` to render the frontend views.

- Login View & Register(views/index.ejs): A simple login form where users can enter their username and password and register too.
- protected View (views/protected.ejs): simple page that only the log user can see

## Author

- Name: William Espinoza

- Email: [@espinozaw657@gmail.com](espinozaw657@gmail.com)

