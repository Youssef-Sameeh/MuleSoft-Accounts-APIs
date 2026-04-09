<<<<<<< HEAD
# Salesforce Accounts API — MuleSoft Internship Project

A simple REST API built with MuleSoft Anypoint Studio that connects to Salesforce and retrieves Account records.

---

## Prerequisites

- Anypoint Studio 7.x (with embedded JDK 17)
- Salesforce Developer org account
- Postman or curl for testing

---

## Setup Steps

### 1. Clone / Open the Project
Open Anypoint Studio and import the project folder via:
**File → Import → Anypoint Studio → Anypoint Studio Project from File System**

### 2. Configure Salesforce Credentials
Open `src/main/mule/salesforce-accounts-api.xml` and update the Salesforce config with your credentials:

- **Consumer Key**: from your Salesforce Connected App
- **Consumer Secret**: from your Salesforce Connected App
- **Username**: your Salesforce username (e.g. `user@agentforce.com`)
- **Password**: your Salesforce password
- **Security Token**: from Salesforce → Settings → Reset My Security Token

### 3. Salesforce Connected App Setup
In your Salesforce Developer org:
1. Go to Setup → App Manager → New Connected App (classic URL)
2. Enable OAuth Settings
3. Set Callback URL to `http://localhost`
4. Add **Full access (full)** as an OAuth scope
5. Save and wait ~5 minutes for propagation
6. Copy the Consumer Key and Secret into the project config

### 4. Enable OAuth Username-Password Flow
In Salesforce Setup → OAuth and OpenID Connect Settings:
- Enable **Allow OAuth Username-Password Flows**

---

## How to Run

1. Open the project in Anypoint Studio
2. Right-click the project → **Run As → Mule Application**
3. Wait for the console to show:
```
Started app 'salesforce-accounts-api'
```
4. The API is now running on `http://localhost:8081`

---

## API Endpoint

| Method | Endpoint    | Description                        |
|--------|-------------|------------------------------------|
| GET    | /accounts   | Returns a list of Salesforce Accounts |

---

## Example Request

```
GET http://localhost:8081/accounts
```

## Example Response

```json
[
    {
        "accountName": "Edge Communications",
        "industry": "Electronics",
        "annualRevenue": "1.39E8"
    },
    {
        "accountName": "Burlington Textiles Corp of America",
        "industry": "Apparel",
        "annualRevenue": "3.5E8"
    },
    {
        "accountName": "Pyramid Construction Inc.",
        "industry": "Construction",
        "annualRevenue": "9.5E8"
    },
    {
        "accountName": "Dickenson plc",
        "industry": "Consulting",
        "annualRevenue": "5.0E7"
    },
    {
        "accountName": "Grand Hotels & Resorts Ltd",
        "industry": "Hospitality",
        "annualRevenue": "5.0E8"
    }
]
```

## Error Response

If the connection to Salesforce fails, the API returns:

```json
{
    "error": true,
    "message": "Failed to connect to Salesforce. Please try again later."
}
```

---

## Project Structure

```
salesforce-accounts-api/
├── src/
│   └── main/
│       └── mule/
│           └── salesforce-accounts-api.xml   # Main flow
├── pom.xml                                    # Maven dependencies
└── README.md                                  # This file
```

---

## Flow Overview

```
HTTP Listener (/accounts) → Salesforce Query → DataWeave Transform → HTTP Response
```

1. **HTTP Listener** — Listens on port 8081 for GET /accounts requests
2. **Salesforce Query** — Executes SOQL: `SELECT Name, Industry, AnnualRevenue FROM Account LIMIT 10`
3. **DataWeave Transform** — Maps Salesforce fields to clean JSON output
4. **Error Handler** — Returns a JSON error message if Salesforce connection fails
=======
# MuleSoft-Accounts-APIs
A REST API that connects to Salesforce and retrieves account data.
>>>>>>> 497ff2dcd4d79f2a6f0bcd75a4e4cb8c8e85d2eb
