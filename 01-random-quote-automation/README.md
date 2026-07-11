# 01: Random Quote to Google Sheets Automation

This project is a simple workflow built using **n8n** that automates the process of collecting random inspirational quotes.

The workflow sends an HTTP request to the **DummyJSON Quotes API**, retrieves a random quote along with its author, and appends the information to a **Google Spreadsheet**. It demonstrates how n8n can integrate external REST APIs with cloud services to automate data collection without writing backend code.

---

## 🎯 Project Objective

The goal of this project is to understand the fundamentals of workflow automation by integrating multiple services into a single automated process.

This project helped me understand:

- Consuming data from a public REST API
- Processing JSON responses
- Mapping API fields inside n8n
- Connecting and writing data to Google Sheets
- Building an end-to-end automation workflow

---

## ⚙️ Workflow Overview

```text
Manual Trigger
      │
      ▼
HTTP Request
(GET Random Quote)
      │
      ▼
Google Sheets
(Append Quote & Author)
```

---

## 📖 Workflow Explanation

### 🔹 Manual Trigger

Starts the workflow manually whenever the **Execute Workflow** button is clicked.

### 🔹 HTTP Request

Makes a **GET** request to the DummyJSON Quotes API and retrieves a random inspirational quote.

### 🔹 Google Sheets

Extracts the **quote** and **author** from the API response and appends them as a new row in the connected Google Spreadsheet.

---

## ✨ Features

- Fetches a random quote from the DummyJSON API
- Stores both the quote and author
- Integrates REST APIs with Google Sheets
- Parses JSON responses from a REST API
- Beginner-friendly automation workflow

---

## 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| n8n | Workflow Automation |
| HTTP Request Node | REST API Integration |
| Google Sheets | Cloud Data Storage |
| DummyJSON API | Random Quote Source |
| JSON | Data Format |

---

## 🌐 API Used

**Endpoint**

```http
GET https://dummyjson.com/quotes/random
```

### Example Response

```json
{
  "id": 4,
  "quote": "The Will To Win, The Desire To Succeed...",
  "author": "Confucius"
}
```

---

## 📂 Project Structure

```text
01-random-quote-automation/
│
├── README.md
├── workflow1.json
├── workflow1.png
└── output1.png

```


## 🚀 Future Improvements

- Add a **Schedule Trigger** to run automatically
- Store execution timestamps
- Prevent duplicate quotes
- Log workflow execution history
- Send quotes via Email or Telegram
