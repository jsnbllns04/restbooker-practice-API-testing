# Restful-Booker API Testing

Practice API test suite built in **Postman** against the public [Restful-Booker](https://restful-booker.herokuapp.com) API.

## Coverage
Full booking lifecycle, with response assertions on each step:

| Request | Method | What's checked |
|---|---|---|
| Token generation | POST /auth | Token returned and stored |
| List all bookings | GET /booking | Status and response structure |
| Create booking | POST /booking | Status, body fields, booking ID stored |
| Get / update / partial update / delete | GET, PUT, PATCH, DELETE /booking/{id} | Status codes and updated values |
| Get deleted booking | GET /booking/{id} | 404 after deletion |

## Negative Tests
- Invalid credentials return no token
- Update and delete are rejected without a token or with an invalid token (403)
- Requesting a non-existent booking returns 404
- Creating a booking with a missing required field is rejected

## Approach
- Collection and environment variables (`base_url`, `bookingId`, `token`)
- Requests chained by storing values from earlier responses
- Test scripts using `pm.test` and `pm.expect`

## How to run
1. Import `postman/Restbooker.postman_collection.json` and `postman/Restbooker.postman_environment.json` into Postman
2. Select the **Restbooker** environment
3. Run the collection with the Collection Runner

## Author
Jason Aubrey P. Billones, jsnbllns04@gmail.com
