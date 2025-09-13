🤖 AI Interview Coach
A self-hosted, intelligent mock interview partner.
This project is an interactive AI interview coach designed to simulate realistic technical interviews. It generates role-specific questions, evaluates user responses, and provides structured feedback — helping candidates prepare for interviews with a hands-on, conversational approach.
The system combines a locally-hosted LLM with workflow automation for a scalable and flexible architecture.
✨ Key Features
🎯 Role-Specific Questions
Generate realistic interview questions tailored to roles like Cloud Security, DevOps, or Software Engineering.
📝 Structured Feedback
Get detailed analysis of your answers, covering clarity, correctness, and conciseness, along with scoring.
🔄 Interactive Mock Interview
Works like a real interview loop — new questions and follow-ups are asked dynamically.
🧩 Decoupled Architecture
The AI logic (Flask + LLM) and workflow orchestration (n8n) are independent, making it modular and scalable.
🛠️ Technologies Used
Python 3.9+ – Core programming language
Flask – Lightweight web server exposing REST API endpoints
Hugging Face Transformers – To load and run locally-hosted LLMs
Models tested: bigscience/bloom-560m and mistralai/Mistral-7B-Instruct-v0.1
PyTorch – Deep learning backend for model inference
n8n – Workflow automation and orchestration engine
ngrok – Secure tunneling to expose local Flask server to n8n Cloud
Shell & cURL – For local testing and debugging of webhooks
⚙️ Architecture Overview
User (candidate)  
   │  
   ├──> Webhook → n8n Workflow  
   │        │  
   │        ├──> HTTP Request → Local Flask API (/generate)  
   │        │        │  
   │        │        └──> Locally-hosted LLM (Bloom / Mistral)  
   │        │               - Generates interview question OR  
   │        │               - Evaluates user answer  
   │        │  
   │        └──> Respond to Webhook → Returns AI output to user  
   │  
   └──> User sends next answer → cycle continues  
🚀 Getting Started
Clone the Repository
git clone https://github.com/your-username/ai-interview-coach.git
cd ai-interview-coach
Set Up Python Environment
pip install flask torch transformers
Run Local Flask API
python local_llm_api.py
Flask will run at: http://127.0.0.1:6000
Expose API with ngrok
ngrok http 6000
Example URL: https://xxxxxx.ngrok-free.app/generate
Configure n8n Workflow
Add a Webhook Node (listens to /interview)
Add an HTTP Request Node (POST → your ngrok /generate URL)
Add a Respond to Webhook Node (returns LLM output)
Save & activate the workflow
Test via cURL
curl -X POST https://your-n8n-instance/webhook/interview \
-H "Content-Type: application/json" \
-d '{"action":"generate","jobRole":"cloud security"}'
🤝 Contributing
Contributions are welcome!
Fork the project
Create your feature branch (git checkout -b feature/NewFeature)
Commit your changes (git commit -m 'Add some NewFeature')
Push to the branch (git push origin feature/NewFeature)
Open a Pull Request
📌 Why This Project Stands Out
Demonstrates end-to-end AI integration (LLM + automation + orchestration).
Highlights practical use of NLP in real-world interview preparation.
Built with scalability in mind — easily switch LLMs or plug into different workflows.
Great example of combining MLOps, workflow automation, and applied AI into a single portfolio project.
