🤖 AI Interview Coach
An automated, self-hosted mock interview partner.
This project provides a complete, interactive, and intelligent interview coach that helps users prepare for specific job roles. The system is designed as an agentic workflow, leveraging a locally hosted Large Language Model (LLM) to generate tailored questions and provide structured, multi-faceted feedback on a user's answers.
✨ Features
Role-Specific Questions
Get realistic technical interview questions based on a chosen job role (e.g., Cloud Security, DevOps).
Structured Feedback
Receive an in-depth evaluation of your answer, including a score and analysis of clarity, correctness, and conciseness.
Interactive Conversation
Continuous mock interview experience: follow-up questions and new challenges adapt to your responses.
Decoupled Architecture
AI logic (Flask app) is separated from automation & orchestration (n8n workflow), ensuring flexibility and scalability.
📦 Tech Stack
n8n: Core automation & orchestration engine, connecting user input, AI model, and response loop.
Python & Flask: Local web server providing API endpoints for the AI model.
Hugging Face: Source for locally hosted LLMs (Bloom-560m or GPT-2).
Locally Hosted LLM: The AI "brain" for generating questions and feedback.
ngrok: Creates a secure tunnel for n8n to communicate with your local AI model via webhook.
🔹 Architecture Overview
The system works as a real-time interaction loop:
User Initiation
A mock interview starts when the user sends a webhook request to n8n with their job role:
{
  "action": "generate",
  "jobRole": "cloud security"
}
n8n Orchestration
Webhook triggers the n8n workflow.
An HTTP Request Node forwards prompts to /generate on the local Flask server.
Logic Nodes decide whether to generate a new question or evaluate an answer.
Local LLM Processing
Flask app receives requests at /generate.
LLM (e.g., Bloom-560m) generates either:
A new interview question, or
Structured feedback on the user’s last response.
Response & Continuation
Flask app sends results back to n8n.
Respond to Webhook Node returns the question/feedback to the user.
User answers → triggers new webhook → loop continues.
🚀 Getting Started
Clone the Repository
git clone https://github.com/yourusername/ai-interview-coach.git
cd ai-interview-coach
Set Up Python Environment
pip install -r requirements.txt
Host the LLM
Download Bloom-560m or GPT-2 from Hugging Face.
Configure it in your Flask app.
Run Flask Server
python app.py
Expose with ngrok
ngrok http 5000
Configure n8n
Import the provided workflow.
Update the HTTP Request node to point to your ngrok URL.
