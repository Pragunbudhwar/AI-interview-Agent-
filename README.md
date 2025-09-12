# 🎓 AI Interview Coach🤖 
## An automated, self-hosted mock interview partner.This project provides a complete, interactive, and intelligent interview coach that helps users prepare for specific job roles. The system is designed as an agentic workflow, leveraging a locally-hosted Large Language Model (LLM) to generate tailored questions and provide structured, multi-faceted feedback on a user's answers.

---


## 🚀 What It Does  
# 🔍 Asks interview questions tailored to a chosen job role (e.g., cloud security, DevOps, etc.)🧠 Accepts the user’s answer (in text form)
# 🧬 Evaluates the answer with structured, AI-generated feedback (clarity, correctness, conciseness, and a score)
# 📄 Provides continuous practice through an interactive loop — like a personal mock interview partner.It doesn’t just say "good job."It tells you what to improve, what you did well, and then guides you to the next question to continue the practice.

---

# 🧠 Key Components

## 💡 The LLM Brain
+ Generates tailored interview questions.
+ Creates structured, detailed feedback on a user's answer.
+ Operates locally on your machine for full control.
  
## 🧩 The n8n Orchestrator
+ Captures user input via a webhook (API call).
+ Decides whether to generate a question or evaluate an answer.
+ Forwards prompts and answers to the local LLM.
+ Returns results back to the user to maintain the flow.

  
## ⚙️ Tech Stackn8n (Automation & Orchestration)Python / Flask (Local API server)Hugging Face (For downloading the LLM)Locally Hosted LLM (e.g., Bloom-560m, GPT-2)ngrok (Creates a secure public tunnel)📦 How It WorksA user starts a mock interview by sending a webhook to n8n with their desired jobRole.An n8n workflow is triggered and forwards the prompt to your local Flask server's /generate endpoint.Your Python/Flask application receives the request and uses the locally-hosted LLM to either create a new question or evaluate an answer.The LLM generates a response based on the logic you've designed.The Flask app sends the LLM's response back to n8n, which returns it to the user via a webhook response.The user provides their answer, which starts a new webhook call to evaluate their response, continuing the interactive loop.💡 Why This Matters✅ Built for continuous, personalized practice✅ No VMs, no monthly subscription fees for the LLM✅ Fast, scalable, cost-efficient for personal use✅ Ideal for personal development, CI/CD pipelines, or as a secure backend API📁 Output Example{
 "question_id": "q123",
 "job_role": "DevOps",
 "interview_question": "Explain the concept of Immutable Infrastructure and its benefits in a DevOps environment.",
 "feedback": {
  "score": 85,
  "clarity": "The answer was clear and well-structured, but could be improved with a more concise opening statement.",
  "correctness": "Correctly identified key benefits like consistency and rollback, but missed mentioning the 'golden image' concept.",
  "conciseness": "The answer was a bit long. Try to provide a summary of the key points before diving into the details."
 }
}
