# 🚀 Node.js Express RESTful API Boilerplate

<div align="center">

![Node.js](https://img.shields.io/badge/Node.js-18.x-green?style=for-the-badge&logo=node.js)
![Express](https://img.shields.io/badge/Express-4.17-black?style=for-the-badge&logo=express)
![MongoDB](https://img.shields.io/badge/MongoDB-5.0-green?style=for-the-badge&logo=mongodb)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

**A production-ready boilerplate for building RESTful APIs using Node.js, Express, and Mongoose**

[Features](#-features) • [Quick Start](#-quick-start) • [Documentation](#-api-documentation) • [Contributing](#-contributing)

</div>

---

## 📋 Table of Contents

- [Features](#-features)
- [Quick Start](#-quick-start)
- [Installation](#-installation)
- [Environment Variables](#-environment-variables)
- [Project Structure](#-project-structure)
- [API Documentation](#-api-documentation)
- [Available Scripts](#-available-scripts)
- [Authentication](#-authentication)
- [Error Handling](#-error-handling)
- [Validation](#-validation)
- [Logging](#-logging)
- [Testing](#-testing)
- [Docker Support](#-docker-support)
- [Contributing](#-contributing)
- [License](#-license)

---

## ✨ Features

### 🔐 Security & Authentication
- **JWT Authentication** - Secure token-based authentication with refresh tokens
- **Password Encryption** - Bcrypt password hashing
- **Role-based Authorization** - Flexible permission system
- **Rate Limiting** - Protection against brute force attacks
- **Security Headers** - Helmet.js for HTTP security headers
- **XSS Protection** - Request data sanitization
- **MongoDB Injection Protection** - Query sanitization

### 🛠️ Development Tools
- **API Documentation** - Auto-generated Swagger/OpenAPI docs
- **Hot Reload** - Nodemon for development
- **Linting** - ESLint + Prettier for code quality
- **Git Hooks** - Husky + lint-staged for pre-commit checks
- **Error Handling** - Centralized error handling middleware
- **Request Validation** - Joi schema validation

### 📊 Monitoring & Logging
- **Winston Logger** - Comprehensive logging system
- **Morgan** - HTTP request logger
- **PM2** - Production process management

### 🧪 Testing
- **Jest** - Unit and integration testing
- **Supertest** - API endpoint testing
- **Test Coverage** - Code coverage reports

### 🐳 DevOps
- **Docker Support** - Containerized development and production
- **Environment Config** - dotenv for environment management
- **CI/CD Ready** - Travis CI configuration included

---

## 🚀 Quick Start

### Prerequisites

- **Node.js** >= 12.0.0
- **MongoDB** >= 4.0
- **npm** or **yarn**

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Abhishek371222/Bolier-Plate.git
   cd Bolier-Plate
   ```

2. **Install dependencies**
   ```bash
   npm install
   # or
   yarn install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env
   ```
   
   Edit `.env` and update the following:
   ```env
   PORT=3000
   MONGODB_URL=mongodb://127.0.0.1:27017/node-boilerplate
   JWT_SECRET=your-super-secret-jwt-key-change-this-in-production
   ```

4. **Start MongoDB**
   ```bash
   # Make sure MongoDB is running on your system
   # Windows: Start MongoDB service
   # macOS: brew services start mongodb-community
   # Linux: sudo systemctl start mongod
   ```

5. **Run the application**
   ```bash
   # Development mode
   npm run dev
   
   # Production mode
   npm start
   ```

6. **Access the API**
   - API Base URL: `http://localhost:3000`
   - API Documentation: `http://localhost:3000/v1/docs`
   - Root Endpoint: `http://localhost:3000/`

---

## 📁 Project Structure

```
Bolier-Plate/
├── src/
│   ├── config/          # Configuration files
│   │   ├── config.js    # Environment configuration
│   │   ├── logger.js    # Winston logger setup
│   │   ├── morgan.js    # HTTP request logger
│   │   ├── passport.js  # Passport strategies
│   │   └── roles.js     # Role permissions
│   ├── controllers/     # Route controllers
│   ├── middlewares/     # Custom middlewares
│   ├── models/          # Mongoose models
│   │   └── plugins/     # Custom mongoose plugins
│   ├── routes/          # API routes
│   │   └── v1/          # API version 1
│   ├── services/        # Business logic layer
│   ├── utils/           # Utility functions
│   ├── validations/     # Request validation schemas
│   ├── docs/            # Swagger documentation
│   ├── app.js           # Express app configuration
│   └── index.js         # Application entry point
├── tests/               # Test files
│   ├── unit/            # Unit tests
│   └── integration/     # Integration tests
├── .env.example         # Environment variables template
├── .eslintrc.json       # ESLint configuration
├── .prettierrc.json     # Prettier configuration
├── docker-compose.yml   # Docker compose configuration
├── Dockerfile           # Docker image configuration
└── package.json         # Project dependencies
```

---

## 🔧 Environment Variables

Create a `.env` file in the root directory:

```env
# Server Configuration
PORT=3000
NODE_ENV=development

# Database
MONGODB_URL=mongodb://127.0.0.1:27017/node-boilerplate

# JWT Configuration
JWT_SECRET=your-super-secret-jwt-key-change-this-in-production
JWT_ACCESS_EXPIRATION_MINUTES=30
JWT_REFRESH_EXPIRATION_DAYS=30
JWT_RESET_PASSWORD_EXPIRATION_MINUTES=10
JWT_VERIFY_EMAIL_EXPIRATION_MINUTES=10

# Email Configuration (Optional)
SMTP_HOST=email-server
SMTP_PORT=587
SMTP_USERNAME=email-server-username
SMTP_PASSWORD=email-server-password
EMAIL_FROM=support@yourapp.com
```

---

## 📚 API Documentation

### Interactive API Docs

Once the server is running, visit:
- **Swagger UI**: `http://localhost:3000/v1/docs`

### Available Endpoints

#### 🔐 Authentication Routes

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/v1/auth/register` | Register a new user | No |
| POST | `/v1/auth/login` | Login user | No |
| POST | `/v1/auth/refresh-tokens` | Refresh access token | No |
| POST | `/v1/auth/forgot-password` | Send password reset email | No |
| POST | `/v1/auth/reset-password` | Reset password | No |
| POST | `/v1/auth/send-verification-email` | Send verification email | Yes |
| POST | `/v1/auth/verify-email` | Verify email | No |

#### 👥 User Routes

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/v1/users` | Create a user | Yes |
| GET | `/v1/users` | Get all users | Yes |
| GET | `/v1/users/:userId` | Get user by ID | Yes |
| PATCH | `/v1/users/:userId` | Update user | Yes |
| DELETE | `/v1/users/:userId` | Delete user | Yes |

### Example API Requests

#### Register a User
```bash
curl -X POST http://localhost:3000/v1/auth/register \
  -H "Content-Type: application/json" \
  -d '{
    "name": "John Doe",
    "email": "john@example.com",
    "password": "password123"
  }'
```

#### Login
```bash
curl -X POST http://localhost:3000/v1/auth/login \
  -H "Content-Type: application/json" \
  -d '{
    "email": "john@example.com",
    "password": "password123"
  }'
```

#### Get Users (Authenticated)
```bash
curl -X GET http://localhost:3000/v1/users \
  -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
```

---

## 🎯 Available Scripts

### Development
```bash
npm run dev          # Start development server with hot reload
```

### Production
```bash
npm start            # Start production server with PM2
```

### Testing
```bash
npm test             # Run all tests
npm run test:watch   # Run tests in watch mode
npm run coverage     # Generate test coverage report
```

### Code Quality
```bash
npm run lint         # Run ESLint
npm run lint:fix     # Fix ESLint errors
npm run prettier     # Check code formatting
npm run prettier:fix # Fix code formatting
```

### Docker
```bash
npm run docker:dev   # Run in Docker (development)
npm run docker:prod  # Run in Docker (production)
npm run docker:test  # Run tests in Docker
```

---

## 🔐 Authentication

### How It Works

1. **Register/Login** - User registers or logs in and receives:
   - Access Token (valid for 30 minutes)
   - Refresh Token (valid for 30 days)

2. **Making Authenticated Requests** - Include the access token in the Authorization header:
   ```
   Authorization: Bearer <access_token>
   ```

3. **Refreshing Tokens** - When the access token expires, use the refresh token:
   ```bash
   POST /v1/auth/refresh-tokens
   Body: { "refreshToken": "your_refresh_token" }
   ```

### Protecting Routes

```javascript
const express = require('express');
const auth = require('../../middlewares/auth');
const userController = require('../../controllers/user.controller');

const router = express.Router();

// Require authentication
router.get('/profile', auth(), userController.getProfile);

// Require specific permission
router.post('/users', auth('manageUsers'), userController.createUser);
```

---

## ⚠️ Error Handling

The application uses centralized error handling. Errors are automatically formatted and returned:

```json
{
  "code": 404,
  "message": "Not found"
}
```

In development mode, the error response also includes the stack trace.

### Custom Error Example

```javascript
const httpStatus = require('http-status');
const ApiError = require('../utils/ApiError');

if (!user) {
  throw new ApiError(httpStatus.NOT_FOUND, 'User not found');
}
```

---

## ✅ Validation

Request validation is handled using Joi schemas:

```javascript
const validate = require('../../middlewares/validate');
const userValidation = require('../../validations/user.validation');

router.post(
  '/users',
  validate(userValidation.createUser),
  userController.createUser
);
```

---

## 📝 Logging

Logging is configured using Winston:

```javascript
const logger = require('./config/logger');

logger.error('Error message');   // level 0
logger.warn('Warning message');   // level 1
logger.info('Info message');      // level 2
logger.http('HTTP message');       // level 3
logger.verbose('Verbose message'); // level 4
logger.debug('Debug message');    // level 5
```

---

## 🧪 Testing

### Running Tests

```bash
# Run all tests
npm test

# Run tests in watch mode
npm run test:watch

# Generate coverage report
npm run coverage
```

### Test Structure

- **Unit Tests**: `tests/unit/` - Test individual functions and modules
- **Integration Tests**: `tests/integration/` - Test API endpoints

---

## 🐳 Docker Support

### Development

```bash
docker-compose -f docker-compose.yml -f docker-compose.dev.yml up
```

### Production

```bash
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up
```

### Dockerfile

The project includes a Dockerfile for containerized deployments.

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct.

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- Inspired by [hagopj13/node-express-boilerplate](https://github.com/hagopj13/node-express-boilerplate)
- Built with ❤️ using Node.js, Express, and MongoDB

---

## 📞 Support

If you have any questions or need help, please:
- Open an issue on [GitHub](https://github.com/Abhishek371222/Bolier-Plate/issues)
- Check the [API Documentation](http://localhost:3000/v1/docs) when the server is running

---

<div align="center">

**Made with ❤️ by [Abhishek371222](https://github.com/Abhishek371222)**

⭐ Star this repo if you find it helpful!

</div>\n\n<!-- Updated 2025 -->\n