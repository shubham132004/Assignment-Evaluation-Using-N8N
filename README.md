# 📘 Assignment Evaluation – Agentic AI Workflow 


https://github.com/user-attachments/assets/ab700326-e063-454a-8eb9-7b984a8c4542


### Automating Student Assignment Evaluation Using n8n, Google Gemini & Telegram Bot 🚀  

This project is an **Agentic AI-powered Assignment Evaluation System** designed to automate the evaluation of student assignments submitted in PDF format.  
Using **n8n**, **Google Gemini Chat Model**, **Telegram Bot**, and **Python**, the system extracts questions and answers, evaluates them, generates scores, provides feedback, and sends the final structured report to the student through Telegram.

---

## 🧠 Overview

Students upload a **ZIP file containing multiple PDF assignments** via a Telegram bot.  
The system then:

- Extracts PDFs  
- Processes each PDF individually  
- Extracts text  
- Identifies question-answer pairs  
- Evaluates each answer  
- Generates scores and feedback  
- Sends a formatted evaluation report  

The end-to-end process is fully automated.

---

## 🖼 Workflow Diagram

<img width="1701" height="729" alt="Screenshot 2025-12-04 121419" src="https://github.com/user-attachments/assets/9e80b99d-0cb9-4374-8fdd-815f78748b89" />

## 🔄 Workflow Steps :

### 1. Telegram Trigger

- Workflow begins when a ZIP file is uploaded through Telegram.

### 2. Compression Node – Decompress ZIP

- The ZIP file is decompressed to extract all PDF files.

### 3. Split Out Node

- Splits the ZIP content into individual PDF items.

### 4. Loop Over Items

- Processes each PDF file sequentially.

### 5. Extract from File (PDF Mode)

- Extracts text from the PDF.

### 6. AI Agent – Google Gemini Chat Model

- Extracted text is analyzed and converted into structured Q&A JSON.

### 7. Python Node

- Cleans and processes the AI-generated JSON.

### 8. Edit Fields Node

- Creates a structured data object.

### 9. Basic LLM Chain – Google Gemini Chat Model

- Generates the full evaluation report including scores and feedback.

### 10. Python Node

- Formats the evaluation text for delivery.

### 11. Edit Fields Node

- Creates output fields for Telegram.

### 12. Telegram Send Message Node

- Sends summary of evaluation:
```
Report Title :  {{ $json.output.report_title }}
Student Name : {{ $json.output.student_name }}
Module Name : {{ $json.output.module_name }}
Total Score : {{ $json.output.total_score }} 
Overall Feedback : {{ $json.output.overall_feedback }}
```

### 13. Wait Node (8 Seconds)

Waits before evaluating the next PDF file from the loop.

## 🧾 JSON Format Returned by Google Gemini

```json
{
  "qa_pairs": [
    {
      "question": "string",
      "answer": "string"
    }
  ]
}
```
## 📝 Evaluation Report Format

```
Assignment Evaluation Report  
Student: <Student Name>  
Module: <Module Name>

Q1. <question>  
Answer: <student_answer>  
Score: <X>/<total_marks>  
Feedback: <feedback>

Q2. <question>  
Answer: <student_answer>  
Score: <X>/<total_marks>  
Feedback: <feedback>

...

Total Score: <Total>/100  
Overall Feedback: <overall_feedback>
```

## 🔗 Try the  JSON  
You can **click the link below to download the JSON output file and test it**:

👉 https://github.com/shubham132004/Assignment-Evaluation-Using-N8N/tree/main/JSON%20FILE

## ⭐ Features

- Automated evaluation of multiple PDF assignments

- Converts text into structured Q&A format

- AI-powered scoring and feedback

- Returns evaluation directly through Telegram

- Fully agentic and scalable

- Zero manual checking required

## 🚀 Tech Stack

| Technology                   | Purpose                      |
| ---------------------------- | ---------------------------- |
| **n8n**                      | Workflow automation          |
| **Google Gemini Chat Model** | Evaluation and feedback      |
| **Telegram Bot API**         | File input and output        |
| **Python Nodes**             | JSON processing & formatting |
| **Extract from PDF**         | Text extraction              |
| **Compression Node**         | ZIP handling                 |


## ⭐ Support

If this project helped you, please give the repository a star ⭐ on GitHub.
