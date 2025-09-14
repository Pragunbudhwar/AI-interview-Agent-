# 🤖 AI Interview Coach  
*A self-hosted, intelligent mock interview partner.*  

This project is an **interactive AI interview coach** designed to simulate realistic technical interviews. It generates **role-specific questions**, evaluates user responses, and provides **structured feedback** — helping candidates prepare for interviews with a hands-on, conversational approach.  

The system combines a **locally-hosted LLM** with **workflow automation** for a scalable and flexible architecture.  

---

## ✨ Key Features  

- 🎯 **Role-Specific Questions**  
  Generate realistic interview questions tailored to roles like *Cloud Security, DevOps, or Software Engineering*.  

- 📝 **Structured Feedback**  
  Get detailed analysis of your answers, covering *clarity, correctness, and conciseness*, along with scoring.  

- 🔄 **Interactive Mock Interview**  
  Works like a real interview loop — new questions and follow-ups are asked dynamically.  

- 🧩 **Decoupled Architecture**  
  The AI logic (Flask + LLM) and workflow orchestration (n8n) are independent, making it **modular and scalable**.  

---

## 🛠️ Technologies Used  

- **[Python 3.9+](https://www.python.org/)** – Core programming language  
- **[Flask](https://flask.palletsprojects.com/)** – Lightweight web server exposing REST API endpoints  
- **[Hugging Face Transformers](https://huggingface.co/transformers/)** – To load and run locally-hosted LLMs  
  - *Models tested*: `bigscience/bloom-560m` and `mistralai/Mistral-7B-Instruct-v0.1`  
- **[PyTorch](https://pytorch.org/)** – Deep learning backend for model inference  
- **[n8n](https://n8n.io/)** – Workflow automation and orchestration engine  
- **[ngrok](https://ngrok.com/)** – Secure tunneling to expose local Flask server to n8n Cloud  
- **Shell & cURL** – For local testing and debugging of webhooks  

---

## ⚙️ Architecture Overview 
User (candidate)
│
├──> Webhook → n8n Workflow
│ │
│ ├──> HTTP Request → Local Flask API (/generate)
│ │ │
│ │ └──> Locally-hosted LLM (Bloom / Mistral)
│ │ - Generates interview question OR
│ │ - Evaluates user answer
│ │
│ └──> Respond to Webhook → Returns AI output to user
│
└──> User sends next answer → cycle continues 

--


![Project Architechture](AI-interview-Agent-
/The AI Agent Interview .png)




