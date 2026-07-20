# 05: AI Blog Generator

This project is an AI-powered content generation workflow built using **n8n**, **Google Sheets**, and the **Groq API**. It automatically generates complete blog content whenever a new row is added to a Google Sheet.

The workflow reads blog requirements such as the topic, target audience, tone, word count, and keyword from Google Sheets, uses an AI Agent powered by **Groq's Llama 3.3 70B Versatile** model to generate structured content, and updates the generated results back into the spreadsheet.

---

## 🎯 Project Objective

The objective of this project is to automate blog generation by integrating workflow automation with Large Language Models (LLMs).

Through this project, I gained hands-on experience with:

- Building event-driven workflows in n8n
- Using Google Sheets as both the input source and output destination
- Integrating the Groq API with n8n
- Generating long-form AI content
- Using Structured Output Parser for consistent AI responses
- Automatically updating spreadsheets with generated content

---

## ⚙️ Workflow Overview

```text
Google Sheets Trigger
(Row Added)
        │
        ▼
AI Agent
(Groq Chat Model)
        │
        ▼
Structured Output Parser
        │
        ▼
Google Sheets
(Append or Update Row)
```

---

## 📝 Workflow Explanation

### 🔹 Google Sheets Trigger

The workflow starts automatically whenever a new row is added to the connected Google Sheet.

Each row contains the information required to generate a blog, including:

- Topic
- Target Audience
- Tone
- Word Count
- Keyword

---

### 🔹 AI Agent (Groq Chat Model)

The AI Agent uses **Groq's Llama 3.3 70B Versatile** language model to generate a complete blog based on the provided inputs.

The generated output includes:

- Blog Title
- Blog Content
- Hashtags
- Meta Description

The content is generated according to the specified topic, audience, tone, keyword, and desired word count.

---

### 🔹 Structured Output Parser

The Structured Output Parser converts the AI-generated response into a structured format. This ensures that each generated field is mapped correctly to its corresponding column in Google Sheets.

---

### 🔹 Google Sheets (Append or Update Row)

After the AI generates the blog, the workflow automatically updates the corresponding row in Google Sheets.

The generated information is written into columns such as:

- Title
- Blog
- Hashtags
- Meta Description

This creates an automated blog generation pipeline with minimal manual effort.

---

## ✨ Features

- Automatically triggers when a new row is added to Google Sheets
- Generates complete AI-powered blog content
- Creates blog titles automatically
- Generates relevant hashtags
- Generates meta descriptions
- Produces structured AI output
- Automatically updates Google Sheets
- Eliminates manual content creation

---

## 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| n8n | Workflow Automation |
| Google Sheets | Trigger, Input & Output Storage |
| Groq API | AI Inference |
| Llama 3.3 70B Versatile | Large Language Model |
| Structured Output Parser | Structures AI Response |
| JSON | Structured Data Exchange |

---

## 📊 Input Example

Each new row in Google Sheets contains information such as:

| Field | Example |
|--------|---------|
| Topic | Benefits of AI in Education |
| Target Audience | College Students |
| Tone | Friendly |
| Word Count | 1000 |
| Keyword | AI in Education |

---

## 📄 Generated Output

For every new row, the workflow automatically generates:

- Blog Title
- Complete Blog Content
- Relevant Hashtags
- Meta Description

The generated content is automatically written back into the corresponding columns of the Google Sheet.

---

## 📁 Project Structure

```text
05-ai-blog-generator/
│
├── README.md
├── workflow.json
├── workflow.png
└── output.png
```

---

## 🚀 How to Use

1. Import `workflow.json` into n8n.
2. Configure your Groq API credentials.
3. Connect your Google Sheets account.
4. Update the spreadsheet reference in the Google Sheets nodes.
5. Activate the workflow.
6. Add a new row containing the blog requirements.
7. Wait for the workflow to execute automatically.
8. View the generated title, blog content, hashtags, and meta description in the spreadsheet.

---
