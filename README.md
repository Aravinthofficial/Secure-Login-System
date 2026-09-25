# Secure Login System

A secure web-based authentication system built using Node.js, Express.js, SQLite, and bcrypt.

## Features

- User registration
- User login and logout
- Secure password hashing using bcrypt
- Session management
- Server-side input validation
- SQL injection protection
- Helmet security headers
- Environment variable support
- Protected dashboard

## Technologies Used

- Node.js
- Express.js
- SQLite
- bcrypt
- express-session
- Helmet
- dotenv
- HTML
- CSS

## Project Structure

SecureLogin/
├── app.js
├── .env
├── .gitignore
├── package.json
├── package-lock.json
├── users.db
├── views/
│   ├── login.html
│   ├── register.html
│   └── dashboard.html
└── public/
    └── style.css

## Installation

Open the terminal and run:

cd SecureLogin
npm install
node app.js

Open the application in your browser:

http://localhost:3000

## Environment Variables

Create a .env file:

SESSION_SECRET=my-super-secret-login-key-2026

Do not upload the .env file to a public GitHub repository.

## Security

- Passwords are stored as bcrypt hashes.
- Plaintext passwords are not stored.
- Parameterized SQL queries help prevent SQL injection.
- Server-side validation protects user input.
- Password confirmation is required.
- Minimum password length is 8 characters.
- HTTP-only session cookies are used.
- SameSite cookies are enabled.
- Helmet provides security-related HTTP headers.
- Sensitive configuration is stored in .env.
- Duplicate usernames and emails are prevented.

## Database

The application uses SQLite.

Users table:

id
username
email
password_hash
created_at

Database structure:

CREATE TABLE IF NOT EXISTS users (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    username TEXT NOT NULL UNIQUE,
    email TEXT NOT NULL UNIQUE,
    password_hash TEXT NOT NULL,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP
);

## Authentication Flow

Registration:

User
|
v
Registration Form
|
v
Server Validation
|
v
Check Existing User
|
v
bcrypt Hashing
|
v
SQLite Database

Login:

Email + Password
|
v
Find User
|
v
bcrypt.compare()
|
+----------------+
|                |
Correct        Incorrect
|                |
v                v
Session          Error
|
v
Dashboard

Logout:

Dashboard
|
v
Logout
|
v
Session Destroyed
|
v
Login Page

## Testing

The application should be tested for:

- Valid registration
- Empty registration fields
- Password mismatch
- Password below 8 characters
- Duplicate email
- Valid login
- Invalid login
- Dashboard access
- Logout
- Unauthorized dashboard access
- Password stored as bcrypt hash
- SQL injection protection

## Future Improvements

- Two-Factor Authentication (2FA)
- Password reset
- Email verification
- Login rate limiting
- Account lockout
- HTTPS deployment
- Stronger password policies
- CSRF protection
- Production-grade session storage

## Conclusion

The Secure Login System demonstrates basic secure authentication practices using Node.js, Express.js, SQLite, bcrypt, express-session, Helmet, and dotenv.

The system protects passwords using hashing, helps prevent SQL injection through parameterized queries, validates user input on the server, and uses sessions to control authenticated access.
