# Testing the MemeStream API with Postman

## Prerequisites
1. Ensure MongoDB is running locally
2. Start the API server with `node server.js`
3. Open Postman

## Test Cases

### 1. Create a New Meme (POST)

**Request:**
- Method: POST
- URL: `http://localhost:5000/memes`
- Headers: `Content-Type: application/json`
- Body:
```json
{
  "userId": "new_user_2",
  "imageUrl": "https://media.giphy.com/media/l0Exk8EUzSLsrErEQ/giphy.gif",
  "caption": "Testing MemeStream 🚀",
  "lat": -29.85,
  "lng": 31.02
}
```

**Expected Response:**
- Status: 201 Created
- Body: JSON object containing:
  - All submitted fields
  - Generated `_id`
  - `timestamp` field

### 2. Get All Memes (GET)

**Request:**
- Method: GET
- URL: `http://localhost:5000/memes`

**Expected Response:**
- Status: 200 OK
- Body: Array of meme objects

### 3. Filter Memes by User (GET)

**Request:**
- Method: GET
- URL: `http://localhost:5000/memes?userId=new_user_2`

**Expected Response:**
- Status: 200 OK
- Body: Array of meme objects for the specified user

## Sample Response Format
```json
{
  "_id": "64ffd4...",
  "userId": "new_user_2",
  "imageUrl": "https://media.giphy.com/media/l0Exk8EUzSLsrErEQ/giphy.gif",
  "caption": "Testing MemeStream 🚀",
  "lat": -29.85,
  "lng": 31.02,
  "timestamp": "2025-07-31T..."
}
```

## Troubleshooting
1. If the server doesn't respond, ensure it's running on port 5000
2. Check MongoDB connection if you get database-related errors
3. Verify that all required fields (userId, imageUrl) are included in POST requests
