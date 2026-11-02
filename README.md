# ResumeForge: Generative AI-Powered Career Development Platform

> **Department:** Computer Science & Engineering (Data Science)  
> **Industry Partner / Internship:** Manac Infotech Pvt. Ltd., Hyderabad  
> **Under the Supervision of:** Mohammed Zama Uddin Atif  
> **Team Members:**
> - Syed Asharibuddin Hasan (Roll No: 160923750045)  
> - Syed Mustafa Uddin (Roll No: 160923750038)  
> - Afraz Ullah Khan (Roll No: 160923750055)  

---

## 📌 Project Overview
**ResumeForge** is an end-to-end, Generative AI-driven career acceleration and resume intelligence ecosystem. Unlike static resume builders or brittle keyword-matching ATS checkers, ResumeForge integrates semantic NLP embeddings, Retrieval-Augmented Generation (RAG), and Large Language Models (LLMs) to perform automated resume tailoring, actionable competency gap analysis, interview question synthesis, and grounded career roadmapping.

---

## 📂 Repository Directory Structure

```text
├── docs/
│   ├── 01_Problem_Statement.md       # Comprehensive Problem Formulation & Industry Gaps
│   ├── 02_SRS_Document.md             # IEEE 830-compliant Software Requirements Specification
│   ├── 03_System_Architecture.md      # Tiered Architecture, Data Flow & Component Design
│   └── 05_API_and_Data_Dictionary.md  # Endpoints, Schemas, and Vector Store Specifications
├── diagrams/
│   ├── architecture_diagram.svg       # Full Layered System Architecture Vector
│   ├── workflow_pipeline.svg          # Ingestion to RAG & Generation Pipeline Vector
│   └── diagrams_guide.md              # Mermaid & ASCII Architectural Diagrams
├── ui-design/
│   ├── UI_UX_Design_Specification.md  # Design System, Wireframes & Screen Workflows
│   └── dashboard_wireframe.svg        # Visual UI Dashboard Wireframe
└── README.md                          # Repository Documentation & Overview
```

---

## 🚀 Key Functional Modules
1. **Dynamic Resume Ingestion & Parsing:** Extraction of semantically structured entities from PDF/DOCX using `pdfplumber` and rule-assisted tokenizers.
2. **Context-Aware ATS & Gap Analysis:** Vectorized cosine similarity scoring between candidate experience and recruiter Job Descriptions (JDs).
3. **Generative Tailoring Engine:** Retrieval-Augmented Generation (RAG) prompts that draft high-impact, STAR-metric bullet points while preserving factual integrity.
4. **Interactive Career Copilot:** Automated interview prep Q&A generation, tailored cover letters, and targeted learning path discovery.

---

## 🛠️ Technology Stack
- **Frontend:** HTML5, CSS3, JavaScript (ES6+), Tailwind CSS, Dynamic PDF Preview Canvas
- **Backend Core:** Python 3.10+, FastAPI / Flask RESTful APIs, PyPDF2, pdfplumber
- **AI & NLP:** LangChain, Sentence-Transformers, OpenAI / Qwen / Mistral LLM APIs, Vector Stores (ChromaDB / FAISS)
- **Database & Storage:** PostgreSQL / MongoDB, Firebase Auth & Storage, AWS S3
- **Version Control & DevOps:** Git, GitHub, Docker, Vercel

---

## 📝 GitHub Commit Guidelines for Phase Submission
When committing these design documents into your GitHub repository:
- **Commit Title:** `Added design phase documents`
- **Extended Description:** `Included Problem Statement, IEEE-standard SRS, System Architecture diagrams, and UI/UX design wireframes for ResumeForge.`
