# 02: Webhook to Google Sheets Automation

This project is a simple workflow built using **n8n** that demonstrates how to receive data through an HTTP Webhook and automatically store it in Google Sheets.

The workflow exposes a **Webhook endpoint** that accepts incoming JSON data via a POST request. Once the request is received, n8n extracts the required fields and appends them as a new row in a connected Google Spreadsheet, eliminating the need for manual data entry.

---

## 🎯 Project Objective

The objective of this project is to understand the fundamentals of workflow automation by integrating a REST API with Google Sheets using n8n.

Through this project, I gained hands-on experience with:

- Creating Webhook endpoints in n8n
- Receiving JSON data through HTTP POST requests
- Parsing request payloads
- Mapping JSON fields to Google Sheets columns
- Connecting Google Sheets with n8n
- Building a simple data collection workflow

---

## ⚙️ Workflow Overview

```text
Client / Postman
        │
        ▼
Webhook (POST Request)
        │
        ▼
Google Sheets
(Append New Row)
```

---

## 📝 Workflow Explanation

### 🔹 Webhook

The Webhook node creates an HTTP endpoint that listens for incoming **POST** requests. When a request containing JSON data is received, it triggers the workflow and passes the request payload to the next node.

**Example Request**

```json
{
  "name": "Harleen Arora",
  "email": "harleenarora7555@gmail.com",
  "city": "Ludhiana"
}
```

### 🔹 Google Sheets

The Google Sheets node extracts the required fields from the webhook payload:

- `name`
- `email`
- `city`

These values are mapped to their respective Google Sheets columns and automatically appended as a new row every time a valid request is received.

---

## ✨ Features

- Accepts HTTP POST requests
- Parses JSON payloads
- Automatically stores data in Google Sheets
- Eliminates manual data entry
- Beginner-friendly automation workflow
- Easy to extend with additional nodes
- Can be tested using Postman or any HTTP client

---

## 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| n8n | Workflow Automation |
| Webhook | Receive HTTP Requests |
| Google Sheets | Data Storage |
| JSON | Data Format |
| REST API | Communication |

---

## 📡 API Example

### Endpoint

```http
POST https://your-n8n-instance/webhook/your-webhook-url
Content-Type: application/json
```

### Request Body

```json
{
  "name": "Harleen Arora",
  "email": "harleenarora7555@gmail.com",
  "city": "Ludhiana"
}
```

### Response

```json
{
  "message": "Workflow was started"
}
```

---

## 📁 Project Structure

```text
02-webhook-google-sheets-automation/
│
├── README.md
├── workflow.json
├── workflow.png
├── postman.png
└── output.png
```

---

## 🚀 How to Use

1. Import the workflow into n8n.
2. Connect your Google account.
3. Configure the Google Sheets node.
4. Activate the workflow.
5. Copy the Webhook URL.
6. Send a POST request using Postman or any HTTP client.
7. Verify that the submitted data has been added to the connected Google Spreadsheet.

---
