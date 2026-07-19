# 04: AI Study Tutor

This project is a context-aware AI study assistant built using **n8n**, **Google Sheets**, **Python**, and the **Groq API**. It receives a student's question through an HTTP Webhook, retrieves any previous conversation history from Google Sheets, and uses that context to generate a personalized, student-friendly response using AI.

Each new interaction is automatically stored in Google Sheets, allowing the tutor to maintain conversation history for future questions.

---

## 🎯 Project Objective

The objective of this project is to understand how to build context-aware AI workflows by combining workflow automation, Python scripting, AI, and cloud-based data storage.

Through this project, I gained hands-on experience with:

- Building AI-powered workflows in n8n
- Receiving user input through HTTP Webhooks
- Integrating Google Sheets for conversation storage
- Implementing conditional workflow logic using the If node
- Processing workflow data using Python
- Maintaining conversation history for contextual AI responses
- Integrating the Groq API with n8n

---

## ⚙️ Workflow Overview

```text
Webhook (POST Request)
        │
        ▼
Google Sheets (Get Rows)
        │
        ▼
If (Previous Conversation Exists?)
   ┌──────────────┴──────────────┐
   │                             │
 Yes                            No
   │                             │
   ▼                             ▼
Code (Python)              Edit Fields
(Build Conversation        (Set Default
 History)                   History)
   │                             │
   └──────────────┬──────────────┘
                  ▼
      AI Agent (Groq Chat Model)
                  │
                  ▼
   Google Sheets (Append Row)
                  │
                  ▼
        Respond to Webhook
```

---

## 📝 Workflow Explanation

### 🔹 Webhook

The Webhook node creates an HTTP endpoint that accepts incoming **POST** requests containing the student's name and question. Once a request is received, it triggers the workflow and forwards the data to the next node.

**Example Request**

```json
{
  "student": "Harleen Arora",
  "question": "What is the difference between a for loop and a while loop in Python?"
}
```

---

### 🔹 Google Sheets (Get Rows)

The Google Sheets node searches the connected spreadsheet for previous conversations associated with the student. If previous interactions are found, they are passed to the next step for processing.

---

### 🔹 If

The If node checks whether previous conversation records exist for the student.

- **Yes:** Previous conversations are processed using the Python node.
- **No:** A default history value is created before sending the request to the AI Agent.

---

### 🔹 Code (Python)

The Code (Python) node processes the student's previous conversations retrieved from Google Sheets. It extracts earlier questions and answers, formats them into a structured conversation history, and prepares the context for the AI Agent.

This enables the AI to generate responses that maintain continuity across multiple interactions.

---

### 🔹 Edit Fields

If no previous conversation exists, the Edit Fields node creates a default `history` value (`"No previous conversation"`). This ensures that the AI Agent always receives a consistent input structure.

---

### 🔹 AI Agent (Groq)

The AI Agent uses **Groq's Llama 3.3 70B Versatile** language model to generate clear, student-friendly explanations.

The AI:

- Uses previous conversation history when available
- Explains concepts in simple language
- Breaks complex topics into smaller steps
- Includes examples when appropriate
- Encourages learning with follow-up questions

---

### 🔹 Google Sheets (Append Row)

After generating a response, the workflow automatically stores the interaction in Google Sheets, including:

- Student Name
- Question
- AI-generated Answer
- Timestamp

This builds a conversation history that can be used to provide context in future interactions.

---

### 🔹 Respond to Webhook

The Respond to Webhook node sends the AI-generated response back to the client, completing the request.

---

## ✨ Features

- Accepts student questions through an HTTP Webhook
- Retrieves previous conversation history from Google Sheets
- Uses Python to process and format conversation history
- Generates context-aware AI responses
- Supports both new and returning students
- Automatically stores every interaction in Google Sheets
- Returns responses instantly through the Webhook
- Can be tested using Postman or any HTTP client

---

## 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| n8n | Workflow Automation |
| Webhook | Receive HTTP Requests |
| Google Sheets | Conversation Storage |
| Python | Data Processing |
| If Node | Conditional Logic |
| Groq API | AI Inference |
| Llama 3.3 70B Versatile | Large Language Model |
| JSON | Request Format |

---

## 📡 Sample API Example

### Endpoint

```http
POST https://your-n8n-instance/webhook/Ai-Study-tutor
Content-Type: application/json
```

### Request Body

```json
{
  "student": "Harleen Arora",
  "question": "What is the difference between a for loop and a while loop in Python?"
}
```


---

## 📁 Project Structure

```text
04-ai-study-tutor/
│
├── README.md
├── workflow.json
├── workflow.png
├── demo.mp4
├── postman.png
└── output.png
```

---

## 🚀 How to Use

1. Import `workflow.json` into n8n.
2. Configure your Groq API credentials.
3. Connect your Google Sheets account.
4. Update the spreadsheet reference in the Google Sheets nodes.
5. Activate the workflow.
6. Copy the Webhook URL.
7. Send a POST request using Postman or any HTTP client.
8. Receive the AI-generated response.
9. Verify that the conversation has been stored in Google Sheets for future context.

---
