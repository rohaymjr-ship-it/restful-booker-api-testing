# Restful-Booker API Testing Project

API testing project built with **Postman**, covering full CRUD operations and authentication flow against the [Restful-Booker API](https://restful-booker.herokuapp.com/apidoc/index.html).

## 📌 Overview

This project demonstrates manual + scripted API testing skills using Postman, including:
- Authentication (token-based)
- Full CRUD operations (Create, Read, Update, Delete)
- Partial updates (PATCH)
- Automated test assertions (`pm.test`) for every request
- Status code, response body, and field-level validation

## 🛠️ Tools Used

- **Postman** — for building requests, writing test scripts, and running the collection
- **Restful-Booker API** — free public API designed for testing practice

## 📂 Project Structure

```
restful-booker-api-testing/
│
├── collection/
│   └── Restful-Booker.postman_collection.json
├── screenshots/
│   ├── auth-create-token.png
│   ├── booking-create.png
│   ├── booking-getone.png
│   ├── booking-getall.png
│   ├── booking-update-put.png
│   ├── booking-patch.png
│   ├── booking-delete.png
│   └── test-results.png
└── README.md
```

## 🔑 Endpoints Covered

| Method | Endpoint | Description | Auth Required |
|--------|----------|--------------|----------------|
| POST | `/auth` | Generate authentication token | No |
| POST | `/booking` | Create a new booking | No |
| GET | `/booking/{id}` | Get a single booking by ID | No |
| GET | `/booking` | Get all booking IDs | No |
| PUT | `/booking/{id}` | Update a booking (full replace) | Yes |
| PATCH | `/booking/{id}` | Update a booking (partial) | Yes |
| DELETE | `/booking/{id}` | Delete a booking | Yes |

## ✅ Test Scripts

Every request in this collection includes automated test assertions written in JavaScript using Postman's `pm.test()`, covering:
- Correct status codes (200, 201, etc.)
- Required response fields exist
- Correct data types and values
- Response time checks

Example test script (used on the `GetOne` request):

```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Response has required fields", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property('firstname');
    pm.expect(jsonData).to.have.property('lastname');
    pm.expect(jsonData).to.have.property('bookingdates');
});
```

## 📸 Test Results

Screenshots of passing test results for each request are available in the `/screenshots` folder.

## 🚀 How to Run This Collection

1. Clone or download this repository
2. Open Postman
3. Click **Import** → select `collection/Restful-Booker.postman_collection.json`
4. Run requests individually, or use the **Collection Runner** to run them all in sequence
5. View test results in the **Test Results** tab after each request

## 👤 Author

**Abdulrahman Rohaym**
Software Testing (QA).

