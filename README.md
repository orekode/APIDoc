---

# API Integration Documentation

This document outlines the details for integrating the backend API endpoints with the frontend application. The following endpoints and their respective data structures are explained to facilitate a smooth integration process.

## Table of Contents
- [API Integration Documentation](#api-integration-documentation)
  - [Table of Contents](#table-of-contents)
  - [API Endpoints](#api-endpoints)
    - [Send OTP](#send-otp)
    - [Confirm OTP](#confirm-otp)
    - [Save Personal Info](#save-personal-info)
    - [Get Personal Info](#get-personal-info)
    - [Save Financial Info](#save-financial-info)
    - [Get Financial Info](#get-financial-info)
    - [Save Appliance Info](#save-appliance-info)
    - [Get Appliance Info](#get-appliance-info)
    - [Get Appliances](#get-appliances)
    - [Add Appliance](#add-appliance)
    - [Delete Appliance](#delete-appliance)
    - [Get Plans](#get-plans)
  - [Data Structures](#data-structures)
    - [Appliances Data Structure](#appliances-data-structure)
    - [Plans Data Structure](#plans-data-structure)
  - [Sample Request and Response](#sample-request-and-response)
    - [Sample Fetch POST Request (JavaScript)](#sample-fetch-post-request-javascript)
    - [Sample Fetch GET Request (JavaScript)](#sample-fetch-get-request-javascript)

## API Endpoints

### Send OTP

**Endpoint:** `POST /sendOtp`

**Description:** Sends an OTP to the user's email for verification.

**Request Body:**
```json
{
    "email": "user@example.com"
}
```

**Response:**
- Success:
  ```json
  {
      "success": true,
      "message": "Otp sent successfully",
      "data": []
  }
  ```
- Error:
  ```json
  {
      "success": false,
      "message": "Failed to send email OTP",
      "errors": []
  }
  ```

### Confirm OTP

**Endpoint:** `POST /confirmOtp`

**Description:** Confirms the OTP sent to the user's email.

**Request Body:**
```json
{
    "email": "user@example.com",
    "otp": "1234"
}
```

**Response:**
- Success:
  ```json
  {
      "success": true,
      "message": "Email confirmed",
      "data": []
  }
  ```
- Error:
  ```json
  {
      "success": false,
      "message": "Invalid or expired OTP",
      "errors": []
  }
  ```

### Save Personal Info

**Endpoint:** `POST /personalInfo`

**Description:** Saves the personal information of the user.

**Request Body:**
```json
{
    "firstName": "John",
    "lastName": "Doe",
    "location": "New York",
    "phoneNumber": "1234567890",
    "gender": "Male",
    "password": "password",
    "email": "user@example.com"
}
```

**Response:**
- Success:
  ```json
  {
      "success": true,
      "message": "Personal Information Stored",
      "data": []
  }
  ```
- Error:
  ```json
  {
      "success": false,
      "message": "An unexpected error occurred",
      "errors": []
  }
  ```

### Get Personal Info

**Endpoint:** `GET /personalInfo`

**Description:** Retrieves the personal information of the user.

**Query Parameters:**
```json
{
    "email": "user@example.com"
}
```

**Response:**
- Success:
  ```json
  {
      "success": true,
      "message": "Request processed successfully",
      "data": {
          "firstName": "John",
          "lastName": "Doe",
          "location": "New York",
          "phoneNumber": "1234567890",
          "gender": "Male",
          "email": "user@example.com",
          "password": ""
      }
  }
  ```
- Error:
  ```json
  {
      "success": false,
      "message": "Personal Information Not Found",
      "errors": []
  }
  ```

### Save Financial Info

**Endpoint:** `POST /financialInfo`

**Description:** Saves the financial information of the user.

**Request Body:**
```json
{
    "homeOwner": true,
    "salaryWorker": true,
    "minSpend": 1000,
    "maxSpend": 5000,
    "interestDesc": "Looking for budget appliances"
}
```

**Response:**
- Success:
  ```json
  {
      "success": true,
      "message": "Financial Information Stored",
      "data": []
  }
  ```
- Error:
  ```json
  {
      "success": false,
      "message": "An unexpected error occurred",
      "errors": []
  }
  ```

### Get Financial Info

**Endpoint:** `GET /financialInfo`

**Description:** Retrieves the financial information of the user.

**Query Parameters:**
```json
{
    "email": "user@example.com"
}
```

**Response:**
- Success:
  ```json
  {
      "success": true,
      "message": "Request processed successfully",
      "data": {
          "homeOwner": true,
          "salaryWorker": true,
          "minSpend": 1000,
          "maxSpend": 5000,
          "interestDesc": "Looking for budget appliances"
      }
  }
  ```
- Error:
  ```json
  {
      "success": false,
      "message": "Financial Information Not Found",
      "errors": []
  }
  ```

### Save Appliance Info

**Endpoint:** `POST /applianceInfo`

**Description:** Saves the appliance information of the user.

**Request Body:**
```json
{
    "email": "user@example.com",
    "appliances": [
        { "id": 1, "quantity": 2 },
        { "id": 2, "quantity": 1 }
    ]
}
```

**Response:**
- Success:
  ```json
  {
      "success": true,
      "message": "Appliance Information Stored",
      "data": {
          "plan": {
              "planId": 1,
              "name": "Basic Plan",
              "systemType": "Solar",
              "description": "Basic solar plan",
              "amount": 50.00,
              "paymentId": 1,
              "paymentFreq": "monthly",
              "paymentPlans": [
                  {
                      "paymentId": 1,
                      "amount": 50.00,
                      "paymentFreq": "monthly"
                  }
              ],
              "appliances": [
                  {
                      "applianceId": 2,
                      "name": "Refrigerator",
                      "quantity": 1
                  },
                  {
                      "applianceId": 1,
                      "name": "Television",
                      "quantity": 1
                  },
                  {
                      "applianceId": 4,
                      "name": "Air Conditioner",
                      "quantity": 1
                  },
                  {
                      "applianceId": 5,
                      "name": "Lights",
                      "quantity": 2
                  }
              ]
          }
      }
  }
  ```
- Error:
  ```json
  {
      "success": false,
      "message": "An unexpected error occurred",
      "errors": []
  }
  ```

### Get Appliance Info

**Endpoint:** `GET /applianceInfo`

**Description:** Retrieves the appliance information of the user.

**Query Parameters:**
```json
{
    "email": "user@example.com"
}
```

**Response:**
- Success:
  ```json
  {
      "success": true,
      "message": "Request processed successfully",
      "data": {
          "appliances": [
              { "id": 1, "quantity": 2 },
              { "id": 2, "quantity": 1 }
          ]
      }
  }
  ```
- Error:
  ```json
  {
      "success": false,
      "message": "Appliance Information Not Found",
      "errors": []
  }
  ```

### Get Appliances

**Endpoint:** `GET /appliances`

**Description:** Retrieves a list of all available appliances.

**Response:**
- Success:
  ```json
  {
      "success": true,
      "message": "Request processed successfully",
      "data": [
          {
              "id": 1,
              "name": "Air Conditioner"
          },
          {
              "id": 2,
              "name": "Refrigerator"
          }
      ]
  }
  ```
- Error:
  ```json
  {
      "success": false,
      "message": "An unexpected error occurred",
      "errors": []
  }
  ```

### Add Appliance

**Endpoint:** `POST /appliances`

**Description:** Adds a new appliance to the system.

**Request Body:**
```json
{
    "name": "Washing Machine"
}
```

**Response:**
- Success:
  ```json
  {
      "success": true,
      "message": "Appliance added successfully",
      "data": []
  }
  ```
- Error:
  ```json
  {
      "success": false,
      "message": "An unexpected error occurred",


      "errors": []
  }
  ```

### Delete Appliance

**Endpoint:** `DELETE /appliances`

**Description:** Deletes an appliance from the system.

**Request Body:**
```json
{
    "id": 1
}
```

**Response:**
- Success:
  ```json
  {
      "success": true,
      "message": "Appliance deleted successfully",
      "data": []
  }
  ```
- Error:
  ```json
  {
      "success": false,
      "message": "An unexpected error occurred",
      "errors": []
  }
  ```

### Get Plans

**Endpoint:** `GET /plans`

**Description:** Retrieves a list of all available plans.

**Response:**
- Success:
  ```json
  {
      "success": true,
      "message": "Request processed successfully",
      "data": [
          {
              "planId": 1,
              "name": "Basic Plan",
              "systemType": "Solar",
              "description": "Basic solar plan",
              "amount": 50.00,
              "paymentId": 1,
              "paymentFreq": "monthly",
              "paymentPlans": [
                  {
                      "paymentId": 1,
                      "amount": 50.00,
                      "paymentFreq": "monthly"
                  }
              ],
              "appliances": [
                  {
                      "applianceId": 2,
                      "name": "Refrigerator",
                      "quantity": 1
                  },
                  {
                      "applianceId": 1,
                      "name": "Television",
                      "quantity": 1
                  },
                  {
                      "applianceId": 4,
                      "name": "Air Conditioner",
                      "quantity": 1
                  },
                  {
                      "applianceId": 5,
                      "name": "Lights",
                      "quantity": 2
                  }
              ]
          }
      ]
  }
  ```
- Error:
  ```json
  {
      "success": false,
      "message": "An unexpected error occurred",
      "errors": []
  }
  ```

## Data Structures

### Appliances Data Structure
```json
{
    "id": 1,
    "name": "Air Conditioner"
}
```

### Plans Data Structure
```json
{
    "planId": 1,
    "name": "Basic Plan",
    "systemType": "Solar",
    "description": "Basic solar plan",
    "amount": 50.00,
    "paymentId": 1,
    "paymentFreq": "monthly",
    "paymentPlans": [
        {
            "paymentId": 1,
            "amount": 50.00,
            "paymentFreq": "monthly"
        }
    ],
    "appliances": [
        {
          "applianceId": 2,
          "name": "Refrigerator",
          "quantity": 1
        },
        {
          "applianceId": 1,
          "name": "Television",
          "quantity": 1
        },
        {
          "applianceId": 4,
          "name": "Air Conditioner",
          "quantity": 1
        },
        {
          "applianceId": 5,
          "name": "Lights",
          "quantity": 2
        }
    ]
}
```

## Sample Request and Response

### Sample Fetch POST Request (JavaScript)
```javascript
const data = {
    email: 'user@example.com',
    appliances: [
        { id: 1, quantity: 2 },
        { id: 2, quantity: 1 }
    ]
};

fetch('https://your-backend-url/applianceInfo', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json'
    },
    body: JSON.stringify(data)
})
.then(response => response.json())
.then(data => console.log('Success:', data))
.catch(error => console.error('Error:', error));
```

### Sample Fetch GET Request (JavaScript)
```javascript
const email = 'user@example.com';

fetch(`https://your-backend-url/personalInfo?email=${email}`, {
    method: 'GET',
    headers: {
        'Content-Type': 'application/json'
    }
})
.then(response => response.json())
.then(data => console.log('Success:', data))
.catch(error => console.error('Error:', error));
```

This documentation should help you seamlessly integrate the frontend with the backend APIs. If you have any questions or encounter any issues, please reach out for further assistance.

---
