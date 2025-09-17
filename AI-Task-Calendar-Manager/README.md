# 🧑‍💻 AI Task & Calendar Manager (n8n Workflow)

## 📌 Overview
This workflow integrates **OpenAI GPT-4, Google Calendar, and Google Sheets** inside **n8n**.  
It acts as an **AI-powered assistant** that can:
- Understand natural language queries.
- Create, search, and update events in Google Calendar.
- Append, fetch, and update rows in Google Sheets.
- Maintain conversational memory to handle context across interactions.

## 🛠 Workflow Features
- **Chat Trigger** → Listens to chat messages as input.  
- **AI Agent** → Powered by OpenAI GPT-4 with memory for natural conversation.  
- **Google Calendar** →  
  - Create events with title, time, and description.  
  - Search existing events by date range.  
  - Update events after searching for the correct record.  
- **Google Sheets** →  
  - Append new task rows (Task Name, Description, Due Date, Priority).  
  - Search for tasks by due date.  
  - Update existing task rows.  
- **Memory Buffer** → Keeps track of conversation context to support multi-turn interactions.

## 📂 Workflow Structure
1. **Trigger**: Chat message received.  
2. **AI Agent**: Interprets the message using GPT-4.  
3. **Actions** (depending on intent):  
   - Create an event in Google Calendar.  
   - Search existing events.  
   - Append, update, or fetch rows in Google Sheets.  
4. **Response**: Returns the processed result back through the AI Agent.  

## 🔗 Workflow Image

![Workflow](<img width="990" height="596" alt="image" src="https://github.com/user-attachments/assets/8a71d38d-efda-4e41-80d7-3e8ebb35e141" />
)

## 🚀 Usage Instructions
1. Import `AI Agent.json` into your **n8n instance**.  
2. Set up credentials for:  
   - **Google Calendar**  
   - **Google Sheets**  
   - **OpenAI API**  
3. Start the workflow.  
4. Send a chat message (e.g., *“Create a task to finish report by 20/09/2025, priority high”*).  
5. The AI agent will parse and update both **Google Calendar** and **Sheets** accordingly.

## ✅ Example Use Cases
- Add tasks with due dates and priorities via chat.  
- Automatically schedule meetings in Google Calendar.  
- Search and update existing tasks or events through natural language queries.  
