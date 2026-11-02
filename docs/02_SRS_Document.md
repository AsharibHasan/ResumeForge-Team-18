# Software Requirements Specification (SRS)
## Project Name: ResumeForge
### Standard: Conforming to IEEE 830-1998 Guidelines

---

## 1. Introduction

### 1.1 Purpose
This document specifies the software, hardware, functional, and non-functional requirements for the **ResumeForge** platform. It serves as the baseline agreement between the project team (Syed Mustafa Uddin, Afraz Ullah Khan, Syed Asharibuddin Hasan), supervisor Mohammed Zama Uddin Atif, Manac Infotech Pvt. Ltd., and stakeholders.

### 1.2 Scope
ResumeForge is a web-based, Generative AI platform designed to automate resume optimization, calculate ATS compatibility scores, highlight skill discrepancies, generate context-specific cover letters, and provide tailored interview preparation.

### 1.3 Definitions, Acronyms, and Abbreviations
- **ATS:** Applicant Tracking System
- **LLM:** Large Language Model
- **RAG:** Retrieval-Augmented Generation
- **JD:** Job Description
- **API:** Application Programming Interface
- **STAR:** Situation, Task, Action, Result framework

---

## 2. Overall Description

### 2.1 Product Perspective
ResumeForge functions as an independent, cloud-ready client-server web application. The frontend communicates with a Python backend through secure RESTful endpoints, with an AI orchestration layer interfacing with LLMs and local vector stores.

### 2.2 User Characteristics
- **Standard Candidate / Student:** Seeks quick optimization, resume score benchmarking, and interview assistance.
- **Placement Officer / Admin:** Monitors aggregate batch analytics and candidate readiness metrics.

### 2.3 Operating Environment
- Client: Any modern web browser (Google Chrome 110+, Mozilla Firefox 110+, Safari 16+, Edge).
- Server: Python 3.10+ runtime, Linux/Debian or containerized Docker host.
- Database: Relational database (PostgreSQL) and Vector Database (FAISS/ChromaDB).

---

## 3. Specific System Requirements

### 3.1 Functional Requirements (FR)

#### Module 1: Authentication & User Management
- **FR-1.1:** System shall permit secure user registration and login via Email/Password and OAuth2 (Google/GitHub).
- **FR-1.2:** System shall enforce role-based access control (Student/Jobseeker vs. Administrator).

#### Module 2: Ingestion & Resume Parsing
- **FR-2.1:** System shall accept user resume files in `.pdf`, `.docx`, and `.txt` formats up to 10 MB.
- **FR-2.2:** System shall parse resumes into structured JSON entities: Contact Info, Work History, Education, Core Skills, and Projects.
- **FR-2.3:** System shall accept target Job Descriptions pasted as raw text or uploaded via URL.

#### Module 3: Semantic Analysis & ATS Scoring Engine
- **FR-3.1:** System shall calculate a multidimensional match score (0–100%) between the resume and the target JD.
- **FR-3.2:** System shall identify:
  - Exact Matched Skills
  - Missing Essential Skills (Hard skills)
  - Recommended Skills (Soft skills & tools)
- **FR-3.3:** System shall display explainable rationale for each score penalty.

#### Module 4: Generative AI Tailoring & Grounded Rewriting
- **FR-4.1:** System shall rewrite candidate bullet points using strong action verbs, quantifiable metrics, and STAR phrasing without hallucinating experiences.
- **FR-4.2:** System shall provide side-by-side comparison (Original vs. Suggested Bullet).
- **FR-4.3:** System shall generate tailored cover letters aligned with company mission statements.

#### Module 5: Export & Compilation
- **FR-5.1:** System shall export finalized resumes into clean, single-column or ATS-friendly two-column PDF and DOCX formats.

---

### 3.2 Non-Functional Requirements (NFR)

- **NFR-1 (Performance & Latency):** Resume parsing must execute within 4.0 seconds. AI score and initial critique must render in under 8.0 seconds.
- **NFR-2 (Reliability & Availability):** The platform shall ensure a 99.5% uptime during placement cycles.
- **NFR-3 (Security & Data Privacy):** User resumes and personal data must be encrypted at rest (AES-256) and in transit (TLS 1.3). No user data shall be used for public LLM training without explicit opt-in.
- **NFR-4 (Usability & Responsiveness):** The UI shall maintain a mobile-first, responsive viewport layout following WCAG 2.1 AA accessibility guidelines.
- **NFR-5 (Scalability):** The backend architecture shall support horizontal autoscaling via containerized microservices.
