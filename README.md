# Movie Review System

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Node.js Version](https://img.shields.io/badge/node-%3E%3D16.0.0-brightgreen)](https://nodejs.org/)
[![npm version](https://img.shields.io/badge/npm-%3E%3D8.0.0-blue)](https://www.npmjs.com/)
![Build Status](https://img.shields.io/badge/build-passing-brightgreen)

A comprehensive, production-ready movie review platform built with modern web technologies. This system provides a robust backend API for managing movies, user reviews, ratings, and social interactions with industry-standard practices for scalability, security, and maintainability.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Technology Stack](#technology-stack)
- [Architecture](#architecture)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [API Documentation](#api-documentation)
- [Database Schema](#database-schema)
- [Project Structure](#project-structure)
- [Development](#development)
- [Testing](#testing)
- [Deployment](#deployment)
- [Performance Optimization](#performance-optimization)
- [Security](#security)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)
- [Contact & Support](#contact--support)

## Overview

The Movie Review System is a sophisticated platform designed to enable users to discover, review, and rate movies. It provides a scalable backend infrastructure with comprehensive review management, user authentication, and advanced filtering capabilities. The system is built following SOLID principles, microservices architecture patterns, and industry best practices.

**Key Highlights:**
- RESTful API with comprehensive error handling
- JWT-based authentication and authorization
- Rate limiting and DDoS protection
- Caching strategies for performance optimization
- Comprehensive logging and monitoring
- Database transactions and data consistency
- Pagination and filtering capabilities
- Real-time updates support

## Features

### Core Features

#### 1. **Movie Management**
- Add, update, and delete movies with detailed metadata
- Support for multiple genres, directors, cast, and production details
- Movie search with advanced filters (genre, rating, release year)
- Trending movies and recommendations engine
- Support for multiple languages and regional variants

#### 2. **Review System**
- Create, read, update, and delete reviews
- Detailed review metadata (review date, last updated, helpful votes)
- Spoiler tag support for sensitive content
- Review verification (verified purchase/watched)
- Review moderation system

#### 3. **Rating System**
- 5-star rating scale with half-star granularity
- Aggregate rating calculations with weighted average
- Rating distribution analytics
- User-specific rating tracking

#### 4. **User Management**
- Secure user registration and authentication
- JWT token-based session management
- User profile management with avatar support
- User preferences and watchlist
- Follower/following system for social features

#### 5. **Social Features**
- Helpful votes on reviews
- Comment threads on reviews
- User notifications
- Activity feeds
- Social sharing capabilities

#### 6. **Admin & Moderation**
- Content moderation tools
- User management dashboard
- Review flagging system
- Analytics and reporting

### Advanced Features

- **Caching Layer**: Redis integration for performance optimization
- **Search Engine**: Elasticsearch integration for advanced search capabilities
- **Message Queue**: Async task processing (email notifications, analytics)
- **CDN Integration**: Optimized image delivery
- **Analytics**: User behavior tracking and insights

## Technology Stack

### Backend
- **Runtime**: Node.js (v16.0.0 or higher)
- **Framework**: Express.js v4.x
- **Language**: JavaScript (ES6+) / TypeScript support
- **Package Manager**: npm v8.0.0 or higher

### Database
- **Primary**: PostgreSQL 13+ (relational data)
- **Cache**: Redis 6+ (session management, caching)
- **Search**: Elasticsearch 7+ (optional, for advanced search)

### Authentication & Security
- **JWT**: jsonwebtoken for token-based authentication
- **Hashing**: bcryptjs for password encryption
- **Validation**: joi/express-validator for input validation
- **Security Headers**: helmet for HTTP security headers
- **Rate Limiting**: express-rate-limit for API protection

### Development Tools
- **Linting**: ESLint with Airbnb config
- **Formatting**: Prettier
- **Testing**: Jest + Supertest
- **API Documentation**: Swagger/OpenAPI 3.0
- **Database Migrations**: db-migrate or Sequelize
- **Monitoring**: Winston (logging), Morgan (HTTP logging)

### DevOps & Deployment
- **Containerization**: Docker & Docker Compose
- **CI/CD**: GitHub Actions / GitLab CI
- **Cloud Platform**: AWS / Azure / GCP (recommendations included)
- **Process Manager**: PM2 for production
- **Reverse Proxy**: Nginx

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     Client Applications                      │
│              (Web, Mobile, Third-party Apps)                 │
└────────────────────────┬────────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────────┐
│                    API Gateway                               │
│         (Authentication, Rate Limiting, Validation)          │
└────────────────────────┬────────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────────┐
│                  Express Application                         │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │  Controllers │  │   Services   │  │   Middleware │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │    Routes    │  │   Models     │  │ Validators   │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└────────────────────────┬────────────────────────────────────┘
         │               │               │
    ┌────▼───┐    ┌─────▼──┐     ┌─────▼──┐
    │PostgreSQL   │  Redis  │     │Message  │
    │Database     │  Cache  │     │ Queue   │
    └──────────┘  └─────────┘     └─────────┘
```

### Design Patterns Used

- **MVC Pattern**: Controllers, Services, and Models separation
- **Repository Pattern**: Data access abstraction layer
- **Middleware Pattern**: Request/response processing pipeline
- **Singleton Pattern**: Database and cache connections
- **Factory Pattern**: Object creation utilities
- **Strategy Pattern**: Different filtering and sorting strategies

## Prerequisites

Before getting started, ensure you have the following installed:

### System Requirements
- **OS**: Linux, macOS, or Windows with WSL2
- **Node.js**: v16.0.0 or higher
- **npm**: v8.0.0 or higher (or yarn v3.0.0+)
- **Git**: Latest version

### External Services
- **PostgreSQL**: v13 or higher
- **Redis**: v6 or higher
- **Docker** (optional): For containerized development

### Development Setup
- Code editor (VS Code recommended with ESLint, Prettier extensions)
- Postman or Insomnia (API testing)
- Git configured with SSH keys

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/gayathrisrikakara/movie-review-system-.git
cd movie-review-system-
```

### 2. Install Dependencies

```bash
npm install
```

Or using yarn:

```bash
yarn install
```

### 3. Setup Environment Variables

Create a `.env` file in the root directory:

```bash
cp .env.example .env
```

Configure the following variables in `.env`:

```env
# Server Configuration
NODE_ENV=development
PORT=3000
HOST=localhost

# Database Configuration
DB_HOST=localhost
DB_PORT=5432
DB_NAME=movie_review_db
DB_USER=postgres
DB_PASSWORD=your_secure_password
DB_POOL_MIN=2
DB_POOL_MAX=10

# Redis Configuration
REDIS_HOST=localhost
REDIS_PORT=6379
REDIS_PASSWORD=
REDIS_DB=0

# JWT Configuration
JWT_SECRET=your_secret_key_here_min_32_chars_long
JWT_EXPIRATION=7d
JWT_REFRESH_SECRET=your_refresh_secret_key
JWT_REFRESH_EXPIRATION=30d

# API Configuration
API_BASE_URL=http://localhost:3000/api
API_VERSION=v1
API_RATE_LIMIT_WINDOW_MS=900000
API_RATE_LIMIT_MAX_REQUESTS=100

# Email Configuration
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your_email@gmail.com
SMTP_PASSWORD=your_app_password
SMTP_FROM=noreply@moviereview.com

# Logging
LOG_LEVEL=debug
LOG_FORMAT=combined

# Security
CORS_ORIGIN=http://localhost:3000
CORS_CREDENTIALS=true
HELMET_ENABLED=true

# Third-party Services (Optional)
AWS_REGION=us-east-1
AWS_ACCESS_KEY_ID=your_key
AWS_SECRET_ACCESS_KEY=your_secret
```

### 4. Initialize Database

```bash
# Run migrations
npm run migrate:up

# Seed initial data (optional)
npm run seed:db
```

### 5. Start Redis (if not using Docker)

```bash
redis-server
```

### 6. Start Development Server

```bash
npm run dev
```

The server will start on `http://localhost:3000`

### Alternative: Docker Setup

```bash
# Build and start all services with Docker Compose
docker-compose up -d

# View logs
docker-compose logs -f app

# Stop services
docker-compose down
```

## Configuration

### Environment-Specific Configuration

The application supports multiple environments:

- **Development** (`NODE_ENV=development`): Debug logging, relaxed CORS
- **Staging** (`NODE_ENV=staging`): Production-like with additional debugging
- **Production** (`NODE_ENV=production`): Optimized, minimal logging, strict security

### Database Configuration

Connection pool settings for production:

```javascript
// config/database.js
DB_POOL_MIN: 5,      // Minimum connections
DB_POOL_MAX: 20,     // Maximum connections
DB_IDLE_TIMEOUT: 30000,
DB_ACQUISITION_TIMEOUT: 30000
```

### Cache Configuration

Redis caching strategy:

```javascript
// config/cache.js
CACHE_TTL_DEFAULT: 3600,     // 1 hour
CACHE_TTL_MOVIE: 86400,      // 24 hours
CACHE_TTL_RATING: 1800,      // 30 minutes
CACHE_TTL_USER: 7200         // 2 hours
```

## Usage

### Running the Application

#### Development Mode
```bash
npm run dev
```
Features: Hot reload, verbose logging, source maps

#### Production Mode
```bash
npm start
```
Or with PM2:
```bash
pm2 start ecosystem.config.js --env production
```

#### Testing Mode
```bash
npm test
```

### Quick Start Example

#### 1. Register a New User
```bash
curl -X POST http://localhost:3000/api/v1/auth/register \
  -H "Content-Type: application/json" \
  -d '{
    "email": "user@example.com",
    "password": "SecurePassword123!",
    "firstName": "John",
    "lastName": "Doe"
  }'
```

#### 2. Login
```bash
curl -X POST http://localhost:3000/api/v1/auth/login \
  -H "Content-Type: application/json" \
  -d '{
    "email": "user@example.com",
    "password": "SecurePassword123!"
  }'
```

Response:
```json
{
  "success": true,
  "data": {
    "accessToken": "eyJhbGciOiJIUzI1NiIs...",
    "refreshToken": "eyJhbGciOiJIUzI1NiIs...",
    "user": {
      "id": "uuid",
      "email": "user@example.com",
      "firstName": "John",
      "lastName": "Doe"
    }
  }
}
```

#### 3. Get All Movies
```bash
curl -X GET "http://localhost:3000/api/v1/movies?page=1&limit=10&sortBy=rating" \
  -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
```

#### 4. Create a Review
```bash
curl -X POST http://localhost:3000/api/v1/reviews \
  -H "Authorization: Bearer YOUR_ACCESS_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "movieId": "movie-uuid",
    "rating": 4.5,
    "title": "Great Movie!",
    "content": "This movie was amazing...",
    "containsSpoilers": false
  }'
```

## API Documentation

### Authentication Endpoints

#### Register User
```
POST /api/v1/auth/register
Content-Type: application/json

Request:
{
  "email": "user@example.com",
  "password": "SecurePass123!",
  "firstName": "John",
  "lastName": "Doe"
}

Response (201):
{
  "success": true,
  "data": {
    "userId": "uuid",
    "email": "user@example.com",
    "message": "Registration successful. Please verify your email."
  }
}
```

#### Login
```
POST /api/v1/auth/login
Content-Type: application/json

Request:
{
  "email": "user@example.com",
  "password": "SecurePass123!"
}

Response (200):
{
  "success": true,
  "data": {
    "accessToken": "jwt_token",
    "refreshToken": "jwt_refresh_token",
    "user": { ... }
  }
}
```

#### Refresh Token
```
POST /api/v1/auth/refresh
Content-Type: application/json

Request:
{
  "refreshToken": "jwt_refresh_token"
}

Response (200):
{
  "success": true,
  "data": {
    "accessToken": "new_jwt_token"
  }
}
```

### Movie Endpoints

#### Get All Movies
```
GET /api/v1/movies?page=1&limit=10&genre=action&sortBy=rating&order=desc
Authorization: Bearer token

Response (200):
{
  "success": true,
  "data": {
    "movies": [ ... ],
    "pagination": {
      "page": 1,
      "limit": 10,
      "total": 150,
      "totalPages": 15
    }
  }
}
```

#### Get Movie by ID
```
GET /api/v1/movies/:movieId
Authorization: Bearer token

Response (200):
{
  "success": true,
  "data": {
    "id": "uuid",
    "title": "Inception",
    "description": "...",
    "genre": ["Sci-Fi", "Thriller"],
    "director": "Christopher Nolan",
    "releaseDate": "2010-07-16",
    "rating": 4.7,
    "totalReviews": 1250,
    "runtime": 148,
    "cast": [ ... ]
  }
}
```

#### Create Movie (Admin Only)
```
POST /api/v1/movies
Authorization: Bearer admin_token
Content-Type: application/json

Request:
{
  "title": "Inception",
  "description": "A skilled thief...",
  "genre": ["Sci-Fi", "Thriller"],
  "director": "Christopher Nolan",
  "releaseDate": "2010-07-16",
  "runtime": 148,
  "cast": ["Leonardo DiCaprio", "Ellen Page"],
  "posterUrl": "https://...",
  "country": "USA",
  "budget": 160000000,
  "boxOffice": 839000000
}

Response (201):
{
  "success": true,
  "data": {
    "id": "uuid",
    "title": "Inception",
    ...
  }
}
```

#### Update Movie (Admin Only)
```
PUT /api/v1/movies/:movieId
Authorization: Bearer admin_token
Content-Type: application/json

Request:
{
  "title": "Inception (Updated)",
  "rating": 4.8
}

Response (200):
{
  "success": true,
  "data": { ... }
}
```

#### Delete Movie (Admin Only)
```
DELETE /api/v1/movies/:movieId
Authorization: Bearer admin_token

Response (200):
{
  "success": true,
  "message": "Movie deleted successfully"
}
```

### Review Endpoints

#### Create Review
```
POST /api/v1/reviews
Authorization: Bearer token
Content-Type: application/json

Request:
{
  "movieId": "uuid",
  "rating": 4.5,
  "title": "Amazing Masterpiece",
  "content": "This movie exceeded my expectations...",
  "containsSpoilers": false
}

Response (201):
{
  "success": true,
  "data": {
    "id": "uuid",
    "movieId": "uuid",
    "userId": "uuid",
    "rating": 4.5,
    "title": "Amazing Masterpiece",
    "content": "This movie exceeded my expectations...",
    "createdAt": "2024-01-15T10:30:00Z",
    "updatedAt": "2024-01-15T10:30:00Z"
  }
}
```

#### Get Movie Reviews
```
GET /api/v1/movies/:movieId/reviews?page=1&limit=10&sortBy=helpful
Authorization: Bearer token

Response (200):
{
  "success": true,
  "data": {
    "reviews": [ ... ],
    "pagination": { ... }
  }
}
```

#### Get User Reviews
```
GET /api/v1/users/:userId/reviews
Authorization: Bearer token

Response (200):
{
  "success": true,
  "data": {
    "reviews": [ ... ]
  }
}
```

#### Update Review
```
PUT /api/v1/reviews/:reviewId
Authorization: Bearer token
Content-Type: application/json

Request:
{
  "rating": 5,
  "title": "Updated Title",
  "content": "Updated content..."
}

Response (200):
{
  "success": true,
  "data": { ... }
}
```

#### Delete Review
```
DELETE /api/v1/reviews/:reviewId
Authorization: Bearer token

Response (200):
{
  "success": true,
  "message": "Review deleted successfully"
}
```

#### Mark Review as Helpful
```
POST /api/v1/reviews/:reviewId/helpful
Authorization: Bearer token

Response (200):
{
  "success": true,
  "data": {
    "helpfulCount": 42
  }
}
```

### Rating Endpoints

#### Get Movie Ratings Summary
```
GET /api/v1/movies/:movieId/ratings/summary
Authorization: Bearer token

Response (200):
{
  "success": true,
  "data": {
    "averageRating": 4.7,
    "totalRatings": 1250,
    "distribution": {
      "5": 500,
      "4": 400,
      "3": 200,
      "2": 100,
      "1": 50
    }
  }
}
```

#### Get User Rating for Movie
```
GET /api/v1/users/:userId/ratings/:movieId
Authorization: Bearer token

Response (200):
{
  "success": true,
  "data": {
    "movieId": "uuid",
    "userId": "uuid",
    "rating": 4.5,
    "createdAt": "2024-01-15T10:30:00Z"
  }
}
```

### Error Responses

All error responses follow this format:

```json
{
  "success": false,
  "error": {
    "code": "INVALID_INPUT",
    "message": "Validation failed",
    "details": [
      {
        "field": "email",
        "message": "Invalid email format"
      }
    ]
  }
}
```

Common error codes:
- `UNAUTHORIZED` (401): Missing or invalid authentication
- `FORBIDDEN` (403): Insufficient permissions
- `NOT_FOUND` (404): Resource not found
- `INVALID_INPUT` (400): Validation error
- `CONFLICT` (409): Resource already exists
- `INTERNAL_ERROR` (500): Server error

For complete API documentation, visit: `/api/v1/docs` (Swagger UI)

## Database Schema

### Users Table
```sql
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  email VARCHAR(255) UNIQUE NOT NULL,
  password_hash VARCHAR(255) NOT NULL,
  first_name VARCHAR(100) NOT NULL,
  last_name VARCHAR(100) NOT NULL,
  avatar_url VARCHAR(500),
  bio TEXT,
  is_admin BOOLEAN DEFAULT false,
  is_email_verified BOOLEAN DEFAULT false,
  email_verified_at TIMESTAMP,
  last_login_at TIMESTAMP,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  deleted_at TIMESTAMP
);

CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_users_created_at ON users(created_at);
```

### Movies Table
```sql
CREATE TABLE movies (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  title VARCHAR(255) NOT NULL,
  description TEXT,
  genre VARCHAR(100)[],
  director VARCHAR(255),
  release_date DATE,
  runtime INTEGER,
  cast VARCHAR(255)[],
  poster_url VARCHAR(500),
  backdrop_url VARCHAR(500),
  country VARCHAR(100),
  language VARCHAR(50),
  budget BIGINT,
  box_office BIGINT,
  imdb_rating DECIMAL(3,1),
  total_reviews INTEGER DEFAULT 0,
  average_rating DECIMAL(3,2) DEFAULT 0,
  is_published BOOLEAN DEFAULT true,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  deleted_at TIMESTAMP
);

CREATE INDEX idx_movies_title ON movies USING GIN(to_tsvector('english', title));
CREATE INDEX idx_movies_genre ON movies USING GIN(genre);
CREATE INDEX idx_movies_release_date ON movies(release_date);
```

### Reviews Table
```sql
CREATE TABLE reviews (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  movie_id UUID NOT NULL REFERENCES movies(id) ON DELETE CASCADE,
  user_id UUID NOT NULL REFERENCES users(id) ON DELETE CASCADE,
  rating DECIMAL(2,1) NOT NULL CHECK (rating >= 0 AND rating <= 5),
  title VARCHAR(255),
  content TEXT NOT NULL,
  contains_spoilers BOOLEAN DEFAULT false,
  is_verified BOOLEAN DEFAULT false,
  helpful_count INTEGER DEFAULT 0,
  unhelpful_count INTEGER DEFAULT 0,
  status ENUM('pending', 'approved', 'rejected') DEFAULT 'pending',
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  deleted_at TIMESTAMP
);

CREATE INDEX idx_reviews_movie_id ON reviews(movie_id);
CREATE INDEX idx_reviews_user_id ON reviews(user_id);
CREATE INDEX idx_reviews_created_at ON reviews(created_at);
CREATE INDEX idx_reviews_helpful_count ON reviews(helpful_count DESC);
```

### Ratings Table
```sql
CREATE TABLE ratings (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  movie_id UUID NOT NULL REFERENCES movies(id) ON DELETE CASCADE,
  user_id UUID NOT NULL REFERENCES users(id) ON DELETE CASCADE,
  rating DECIMAL(2,1) NOT NULL CHECK (rating >= 0 AND rating <= 5),
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  UNIQUE(movie_id, user_id)
);

CREATE INDEX idx_ratings_movie_id ON ratings(movie_id);
CREATE INDEX idx_ratings_user_id ON ratings(user_id);
```

### Helpful Votes Table
```sql
CREATE TABLE helpful_votes (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  review_id UUID NOT NULL REFERENCES reviews(id) ON DELETE CASCADE,
  user_id UUID NOT NULL REFERENCES users(id) ON DELETE CASCADE,
  is_helpful BOOLEAN NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  UNIQUE(review_id, user_id)
);

CREATE INDEX idx_helpful_votes_review_id ON helpful_votes(review_id);
```

## Project Structure

```
movie-review-system/
├── src/
│   ├── config/              # Configuration files
│   │   ├── database.js
│   │   ├── redis.js
│   │   ├── passport.js
│   │   └── constants.js
│   │
│   ├── controllers/         # Request handlers
│   │   ├── authController.js
│   │   ├── movieController.js
│   │   ├── reviewController.js
│   │   └── ratingController.js
│   │
│   ├── services/            # Business logic
│   │   ├── authService.js
│   │   ├── movieService.js
│   │   ├── reviewService.js
│   │   └── ratingService.js
│   │
│   ├── models/              # Data models
│   │   ├── User.js
│   │   ├── Movie.js
│   │   ├── Review.js
│   │   └── Rating.js
│   │
│   ├── routes/              # Route definitions
│   │   ├── authRoutes.js
│   │   ├── movieRoutes.js
│   │   ├── reviewRoutes.js
│   │   └── index.js
│   │
│   ├── middleware/          # Custom middleware
│   │   ├── authMiddleware.js
│   │   ├── errorHandler.js
│   │   ├── validationMiddleware.js
│   │   ├── rateLimiter.js
│   │   └── logger.js
│   │
│   ├── validators/          # Input validation schemas
│   │   ├── authValidator.js
│   │   ├── movieValidator.js
│   │   └── reviewValidator.js
│   │
│   ├── utils/               # Utility functions
│   │   ├── logger.js
│   │   ├── jwt.js
│   │   ├── errors.js
│   │   ├── cache.js
│   │   └── helpers.js
│   │
│   ├── db/                  # Database setup
│   │   ├── migrations/
│   │   ├── seeds/
│   │   └── connection.js
│   │
│   └── app.js               # Express app setup
│
├── tests/
│   ├── unit/
│   ├── integration/
│   └── e2e/
│
├── migrations/              # Database migrations
├── docker/
│   ├── Dockerfile
│   └── docker-compose.yml
│
├── docs/
│   ├── API.md
│   ├── DEPLOYMENT.md
│   └── ARCHITECTURE.md
│
├── .env.example
├── .eslintrc.js
├── .prettierrc
├── .gitignore
├── package.json
├── package-lock.json
├── jest.config.js
├── ecosystem.config.js
└── README.md
```

## Development

### Setting Up Development Environment

```bash
# Install dependencies
npm install

# Install dev dependencies
npm install --save-dev

# Setup Git hooks
npx husky install
```

### Code Standards

#### ESLint Configuration
```bash
npm run lint
npm run lint:fix
```

#### Code Formatting with Prettier
```bash
npm run format
```

#### Pre-commit Hooks
The project uses Husky for Git hooks:
- Lint code before commit
- Run tests before push

### Development Workflow

1. Create a feature branch
```bash
git checkout -b feature/new-feature
```

2. Make changes and commit
```bash
git add .
git commit -m "feat: add new feature"
```

3. Push and create a pull request
```bash
git push origin feature/new-feature
```

## Testing

### Test Structure

```bash
tests/
├── unit/              # Unit tests for services, utilities
├── integration/       # API endpoint tests
└── e2e/              # End-to-end user flow tests
```

### Running Tests

```bash
# Run all tests
npm test

# Run tests in watch mode
npm run test:watch

# Run tests with coverage
npm run test:coverage

# Run specific test file
npm test -- reviewService.test.js

# Run unit tests only
npm run test:unit

# Run integration tests only
npm run test:integration
```

### Writing Tests

Example test file:
```javascript
// tests/unit/reviewService.test.js
describe('ReviewService', () => {
  describe('createReview', () => {
    it('should create a review with valid data', async () => {
      const reviewData = {
        movieId: 'uuid',
        userId: 'uuid',
        rating: 4.5,
        title: 'Great Movie'
      };

      const result = await reviewService.createReview(reviewData);

      expect(result).toHaveProperty('id');
      expect(result.rating).toBe(4.5);
    });

    it('should throw error with invalid rating', async () => {
      const invalidData = {
        movieId: 'uuid',
        userId: 'uuid',
        rating: 6  // Invalid: > 5
      };

      await expect(reviewService.createReview(invalidData))
        .rejects.toThrow('Invalid rating');
    });
  });
});
```

### Test Coverage Goals

- **Overall**: > 80%
- **Critical paths**: > 95%
- **Utilities**: > 90%

## Deployment

### Pre-deployment Checklist

- [ ] All tests passing
- [ ] Code reviewed and approved
- [ ] Environment variables configured
- [ ] Database migrations ready
- [ ] Security audit completed
- [ ] Performance benchmarks acceptable
- [ ] Documentation updated

### Deployment to Production

#### Using Docker

```bash
# Build image
docker build -t movie-review-system:1.0.0 .

# Push to registry
docker push your-registry/movie-review-system:1.0.0

# Deploy using docker-compose
docker-compose -f docker-compose.prod.yml up -d
```

#### Using PM2

```bash
# Install PM2 globally
npm install -g pm2

# Deploy with ecosystem file
pm2 start ecosystem.config.js --env production

# Setup autorestart
pm2 startup
pm2 save

# Monitor
pm2 monit
```

#### Using Kubernetes

```bash
# Apply configuration
kubectl apply -f k8s/deployment.yaml

# Check status
kubectl get pods
kubectl logs deployment/movie-review-system

# Scale deployment
kubectl scale deployment movie-review-system --replicas=3
```

### Database Migrations in Production

```bash
# Backup database before migration
pg_dump movie_review_db > backup_$(date +%Y%m%d).sql

# Run migrations
npm run migrate:up

# Verify migration
npm run migrate:verify
```

### Rollback Procedures

```bash
# Rollback previous migration
npm run migrate:down

# Revert to previous deployment
docker-compose -f docker-compose.prod.yml down
docker pull your-registry/movie-review-system:previous-version
docker-compose -f docker-compose.prod.yml up -d
```

### Monitoring & Maintenance

```bash
# View application logs
pm2 logs movie-review-system

# Check system health
pm2 health

# Monitor resource usage
pm2 monit

# Setup log rotation
npm install pm2-logrotate
pm2 install pm2-logrotate
```

## Performance Optimization

### Caching Strategy

#### Redis Caching
```javascript
// Cache frequently accessed data
const cacheMovie = async (movieId) => {
  const cacheKey = `movie:${movieId}`;
  const cached = await redis.get(cacheKey);
  
  if (cached) return JSON.parse(cached);
  
  const movie = await Movie.findById(movieId);
  await redis.setex(cacheKey, 86400, JSON.stringify(movie)); // 24 hours
  
  return movie;
};
```

#### Query Optimization
- Use database indexes on frequently queried fields
- Implement query pagination to limit results
- Use SELECT to fetch only needed columns
- Implement lazy loading for relationships

### Database Optimization

```sql
-- Add useful indexes
CREATE INDEX idx_reviews_movie_user ON reviews(movie_id, user_id);
CREATE INDEX idx_reviews_rating ON reviews(rating);

-- Analyze query performance
EXPLAIN ANALYZE SELECT * FROM reviews WHERE movie_id = 'uuid' ORDER BY helpful_count DESC;

-- Vacuuming for maintenance
VACUUM ANALYZE;
```

### API Response Optimization

- **Compression**: Enable gzip compression
- **Pagination**: Implement cursor-based pagination for large datasets
- **Partial responses**: Allow clients to request specific fields
- **Batch operations**: Support bulk operations where applicable

### Load Testing

```bash
# Using Apache Bench
ab -n 10000 -c 100 http://localhost:3000/api/v1/movies

# Using wrk
wrk -t4 -c100 -d30s http://localhost:3000/api/v1/movies
```

## Security

### Authentication & Authorization

- **JWT Tokens**: Implement expiration and refresh token rotation
- **Password Security**: Use bcrypt with salt rounds >= 10
- **Rate Limiting**: Implement per-user and per-IP rate limiting
- **CORS**: Configure properly for frontend origins

### Input Validation

```javascript
// Always validate and sanitize inputs
const { body, validationResult } = require('express-validator');

router.post('/reviews', [
  body('rating').isFloat({ min: 0, max: 5 }),
  body('title').isLength({ min: 5, max: 200 }).trim().escape(),
  body('content').isLength({ min: 10 }).trim(),
  body('movieId').isUUID()
], (req, res) => {
  const errors = validationResult(req);
  if (!errors.isEmpty()) {
    return res.status(400).json({ errors: errors.array() });
  }
  // Process request
});
```

### SQL Injection Prevention

- Use parameterized queries/prepared statements
- Use ORM libraries like Sequelize, TypeORM
- Never concatenate user input into SQL strings

### XSS Prevention

- Use helmet for security headers
- Sanitize output in templates
- Implement Content Security Policy (CSP)

### CSRF Protection

- Implement CSRF tokens for state-changing operations
- Use SameSite cookie attribute

### Environment Security

```bash
# Never commit sensitive data
echo ".env" >> .gitignore
echo ".env.local" >> .gitignore

# Use environment variables for secrets
# Use AWS Secrets Manager / Azure Key Vault in production
```

### Security Headers

```javascript
// Helmet middleware automatically adds security headers
const helmet = require('helmet');
app.use(helmet());

// Headers added:
// - Content-Security-Policy
// - X-Frame-Options
// - X-Content-Type-Options
// - Strict-Transport-Security
// - X-XSS-Protection
```

## Troubleshooting

### Common Issues

#### 1. Database Connection Error
```
Error: connect ECONNREFUSED 127.0.0.1:5432
```
**Solution:**
```bash
# Check if PostgreSQL is running
sudo service postgresql status

# Start PostgreSQL
sudo service postgresql start

# Verify connection
psql -U postgres -d movie_review_db
```

#### 2. Redis Connection Error
```
Error: connect ECONNREFUSED 127.0.0.1:6379
```
**Solution:**
```bash
# Check Redis status
redis-cli ping

# Start Redis
redis-server

# Verify connection
redis-cli -h localhost -p 6379
```

#### 3. JWT Token Invalid Error
```
Error: JsonWebTokenError: invalid token
```
**Solution:**
- Verify JWT_SECRET matches between token generation and verification
- Check token expiration time
- Ensure token format: `Bearer <token>`

#### 4. CORS Error
```
Access to XMLHttpRequest blocked by CORS policy
```
**Solution:**
```javascript
// Update CORS configuration in .env
CORS_ORIGIN=http://frontend-url

// Or update app.js
app.use(cors({
  origin: process.env.CORS_ORIGIN,
  credentials: true
}));
```

#### 5. Memory Leak Issues
```bash
# Monitor memory usage
node --inspect app.js

# Use Chrome DevTools to profile
chrome://inspect
```

### Debugging

#### Enable Debug Logging
```bash
DEBUG=* npm run dev
```

#### Use Node Debugger
```bash
node inspect app.js
# In debugger: cont, next, step, quit
```

#### Browser DevTools Debugging
```javascript
// Add debugger statement in code
debugger;

// Run with inspect
node --inspect app.js

// Open chrome://inspect
```

### Performance Profiling

```bash
# Install clinic.js
npm install -g clinic

# Profile application
clinic doctor -- node app.js

# View report
# Reports are generated in HTML format
```

## Contributing

We welcome contributions! Please follow these guidelines:

### Code of Conduct
- Be respectful and inclusive
- No harassment or discrimination
- Report issues to maintainers

### Getting Started

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Make your changes
4. Write/update tests
5. Run linter and tests: `npm run lint && npm test`
6. Commit with conventional commits: `git commit -m "feat: describe feature"`
7. Push to your fork
8. Create a Pull Request

### Conventional Commits

```
feat: add new feature
fix: fix a bug
docs: documentation changes
style: formatting, semicolons, etc
refactor: code restructuring without behavior change
perf: performance improvements
test: adding or updating tests
chore: maintenance tasks
```

### Pull Request Process

1. Update documentation if needed
2. Add tests for new features
3. Ensure all tests pass
4. Update CHANGELOG.md
5. Request review from maintainers
6. Address feedback and re-request review

### Reporting Bugs

Create an issue with:
- Clear title and description
- Steps to reproduce
- Expected vs actual behavior
- Environment details (OS, Node version, etc.)
- Screenshots/error logs if applicable

### Suggesting Features

Create an issue with:
- Clear description of feature
- Use cases and benefits
- Possible implementation approach
- Any relevant references

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

### MIT License Summary

You are free to:
- ✅ Use commercially
- ✅ Modify the code
- ✅ Distribute
- ✅ Use privately

You must:
- 📋 Include copyright and license notice

## Contact & Support

### Getting Help

- **Documentation**: See [docs/](docs/) folder
- **Issues**: [GitHub Issues](https://github.com/gayathrisrikakara/movie-review-system-/issues)
- **Discussions**: [GitHub Discussions](https://github.com/gayathrisrikakara/movie-review-system-/discussions)

### Maintainers

- **Gayathri Srikakara** - [@gayathrisrikakara](https://github.com/gayathrisrikakara)

### Community Resources

- API Documentation: `http://localhost:3000/api/v1/docs`
- Architecture Guide: [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md)
- Deployment Guide: [docs/DEPLOYMENT.md](docs/DEPLOYMENT.md)

### Support Channels

- 📧 Email: support@moviereview.com
- 💬 Slack: [Join our community](link-to-slack)
- 🐦 Twitter: [@MovieReviewApp](https://twitter.com/MovieReviewApp)

---

### Additional Resources

- [Express.js Documentation](https://expressjs.com/)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)
- [Redis Documentation](https://redis.io/documentation)
- [JWT Best Practices](https://tools.ietf.org/html/rfc8725)
- [REST API Best Practices](https://restfulapi.net/)

### Version History

- **v1.0.0** (2024-01-15) - Initial release
  - Core movie management
  - Review and rating system
  - User authentication
  - Basic moderation

### Acknowledgments

- Thanks to all contributors
- Built with Express.js and PostgreSQL
- Inspired by industry best practices

---

**Last Updated**: January 15, 2024  
**Status**: Active Development  
**Maintained By**: Gayathri Srikakara
