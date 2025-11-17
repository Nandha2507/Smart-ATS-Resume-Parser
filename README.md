# CrewAI ATS Resume Analyzer

An AI-powered Resume ATS Analyzer built using **CrewAI**, designed to parse resumes, rewrite them for ATS systems, refine bullet points, and evaluate the resume against a given job title and job description.

This repository demonstrates a multi-agent pipeline that transforms raw resume text into a structured, ATS‑optimized, and job‑matched document.

---

## 🚀 Features

- **Resume Parsing** – Extracts clean, structured information from raw resume text.
- **ATS Optimization** – Rewrites resume content to align with ATS keyword expectations.
- **Bullet Point Refinement** – Enhances clarity, impact, and action-orientation in bullet points.
- **JD‑Matching Evaluation** – Scores the resume against a job title and description.
- **Modular Multi‑Agent Workflow** using CrewAI.

---

## 🧠 System Architecture Diagram

```
Raw Resume Text
        │
        ▼
┌───────────────────────┐
│   Parser Agent         │
│ (Resume Cleaning)      │
└───────────────────────┘
        │
        ▼
┌───────────────────────┐
│  ATS Writer Agent      │
│ (Rewrite for ATS)      │
└───────────────────────┘
        │
        ▼
┌───────────────────────┐
│ Bullet Refiner Agent   │
│ (Improve Resume Bullets)│
└───────────────────────┘
        │
        ▼
┌───────────────────────┐
│  Evaluator Agent       │
│ (Score vs Job Description)
└───────────────────────┘
        │
        ▼
Final Resume + ATS Score
```

---

## 📂 Project Structure

```
.
├── agents.py
├── tasks.py
├── crew.py
├── README.md
└── requirements.txt
```

---

## 🛠️ Setup Instructions

### **1. Clone the Repository**
```bash
git clone https://github.com/your-username/crewai-ats-resume-analyzer.git
cd crewai-ats-resume-analyzer
```

### **2. Create Virtual Environment**
```bash
python -m venv venv
source venv/bin/activate   # macOS / Linux
venv\Scripts\activate    # Windows
```

### **3. Install Requirements**
```bash
pip install -r requirements.txt
```

### **4. Set Your API Keys**
CrewAI requires an LLM provider such as OpenAI or Anthropic.

Example:
```bash
export OPENAI_API_KEY="your_key_here"
```

---

## 🧩 Explanation of Agents

### **1. Parser Agent**
- Cleans and extracts structured resume information.
- Removes noise, formatting and ensures consistency.
- Output feeds directly into the ATS rewrite step.

### **2. ATS Writer Agent**
- Rewrites the parsed resume in an ATS‑optimized format.
- Uses keywords from job title and job description.
- Enhances alignment with recruiter expectations.

### **3. Bullet Refiner Agent**
- Polishes bullet points for clarity, action verbs, impact.
- Ensures structure: *Action → Context → Outcome*.
- Produces highly readable and strong resume statements.

### **4. Evaluator Agent**
- Compares final resume against job title + job description.
- Produces:
  - ATS match score
  - Skill gap insights
  - Recommendations to improve alignment

---

## 🧩 Explanation of Tasks

### **parse_resume_task**
- Input: Raw resume text  
- Output: Cleaned, structured resume data  
- Assigned to: Parser agent  

### **rewrite_for_ats_task**
- Input: Cleaned resume  
- Output: ATS‑optimized rewritten resume  
- Assigned to: ATS writer agent  

### **refine_bullets_task**
- Input: Rewritten resume  
- Output: Enhanced bullet points  
- Assigned to: Refiner agent  

### **evaluate_ats_task**
- Input: Final polished resume  
- Output: Matching score + evaluation report  
- Assigned to: Evaluator agent  

---

## ▶️ Running the Pipeline

Example usage inside your script:

```python
from crew import run_pipeline

cleaned, rewritten, final_resume, evaluation = run_pipeline(
    raw_resume_text="Your resume text here...",
    job_title="Data Scientist",
    job_description="Job description text..."
)

print(final_resume)
print(evaluation)
```

---

## 📌 Notes

- The pipeline runs each agent **sequentially**.
- Multi‑agent execution ensures high‑quality transformation.
- Easy to extend with new tasks or agents.

---

## 🤝 Contribution

Pull requests are welcome! For major changes, open an issue first to discuss what you’d like to modify.

---

## 📜 License

MIT License

---

If you need help with deployment, UI, API server, or converting this into a Streamlit / FastAPI app, feel free to ask!
