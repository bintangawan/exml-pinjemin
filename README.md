# Express FastAPI Client

## Overview
This service acts as a reverse proxy between the frontend application and the machine learning backend. It handles API requests from the frontend, forwards them to the FastAPI machine learning service, and returns the responses back to the frontend.

## Architecture
- **Frontend**: Hosted on Netlify (https://pinjemin.netlify.app)
- **Proxy Server**: This Express.js application
- **ML Backend**: FastAPI service (https://ml.pinjemin.site)

## Features
- Routes API requests to the appropriate ML service endpoints
- Handles CORS for secure cross-origin requests
- Validates request payloads before forwarding
- Provides detailed error handling and logging
- Health check endpoint for monitoring

## API Endpoints

### User Recommendations
```
POST /api/recommend/user
```
Forwards user recommendation requests to the ML backend.

### Item Recommendations
```
POST /api/recommend/item
```
Requires `user_id` and `product_id` in the request body.

### Search Recommendations
```
POST /api/recommend/search
```
Requires `user_id` and `keyword` in the request body.

### Data Refresh
```
POST /api/refresh_data
```
Triggers a data refresh in the ML backend.

### Health Check
```
GET /api/health
```
Returns the current status of the proxy server.

## Setup and Installation

### Prerequisites
- Node.js (v14 or higher)
- npm

### Installation
1. Clone the repository
2. Install dependencies:
```
npm install
```

### Running the Server
```
npm start
```
The server will run on port 5001 by default, or the port specified in the PORT environment variable.

### Development
For development with auto-restart:
```
npx nodemon app.js
```

## Environment Variables
- `PORT`: Server port (default: 5001)
- `FASTAPI_URL`: URL of the FastAPI backend (default: https://ml.pinjemin.site)

## Security
- CORS is configured to only allow requests from the frontend domain
- Request validation prevents malformed requests from reaching the ML backend