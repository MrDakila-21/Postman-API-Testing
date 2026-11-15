Restful-Booker API Test Suite
Postman collection for testing the Restful-Booker API — a chained flow covering authentication, CRUD operations, and negative scenarios.

What it covers
The collection runs five endpoints in sequence, passing data between requests using Postman collection variables:

POST /auth — generates an auth token, saved as auth_token
POST /booking — creates a booking, extracts bookingid as booking_id
PUT /booking/:id — updates the booking using {{booking_id}} and Cookie: token={{auth_token}}
GET /booking/:id — verifies the update by asserting specific field values
DELETE /booking/:id — cleans up the test data

A sixth request (negative test) sends a PUT with an invalid token and asserts a 403 Forbidden response.

Notes on API behaviour
POST /auth returns 200 on both success and failure. Tests check the response body rather than the status code.
DELETE /booking/:id returns 201 Created on success (not 204). Assertions match this contract
