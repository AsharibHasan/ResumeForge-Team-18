# ResumeForge: System Architecture & Design Diagrams

## 1. High-Level 5-Tier Architecture
The ResumeForge platform is structured into five distinct operational tiers:

```
[ Tier 1: User / Presentation Layer ]
  ├── Web Browser (HTML5 / Tailwind CSS / Vanilla JS)
  ├── Resume PDF/Docx Uploader & Dynamic Markdown Viewer
  └── Real-Time Career Chat & Diff Reviewer
             │ (HTTPS / REST API)
             ▼
[ Tier 2: Application / API Gateway Layer ]
  ├── Python 3.10+ FastAPI / Flask Web Framework
  ├── Auth Middleware (JWT & OAuth2)
  └── Rate Limiting & Validation Pipelines
             │
             ▼
[ Tier 3: Core AI & Processing Services ]
  ├── Parser Engine (pdfplumber, regex tokenizers)
  ├── Semantic Matching & Scoring (Sentence-Transformers)
  ├── RAG Pipeline & Prompt Orchestrator (LangChain)
  └── LLM Generation Engine (Resume Tailoring, Cover Letters, Q&A)
             │
             ▼
[ Tier 4: Data & Knowledge Persistence Layer ]
  ├── Relational DB (PostgreSQL / SQLite for User Data & History)
  ├── Vector Store (FAISS / ChromaDB for Skill Ontologies & Embeddings)
  └── Object Storage (AWS S3 / Firebase for Stored Resumes)
             │
             ▼
[ Tier 5: Administration & Monitoring ]
  ├── Admin Dashboard & Model Usage Analytics
  └── Continuous Feedback & Evaluation Loop
```

---

## 2. Comprehensive Mermaid UML Diagrams

### A. Data Flow Diagram (DFD Level 1)
```mermaid
graph TD
    User([User / Job Seeker]) -->|Uploads Resume PDF & Target JD| Gateway[API Gateway / Parsing Route]
    Gateway --> Parser[Document Ingestion Engine]
    Parser -->|Structured JSON Profile| Analyzer[Semantic Match & Scoring Engine]
    Gateway -->|Target JD Text| Analyzer
    Analyzer --> VectorDB[(Skill Knowledge Base)]
    Analyzer -->|Match Scores & Gap Matrix| RAG[RAG & Prompt Orchestrator]
    RAG --> LLM[Generative AI Engine]
    LLM -->|Tailored Bullets & Recommendations| DiffEngine[Interactive Diff & Review Engine]
    DiffEngine -->|Final Approved Resume| Exporter[PDF/DOCX Generator]
    Exporter --> User
```

### B. Use Case Diagram
```mermaid
flowchart LR
    Candidate((Candidate / Job Seeker))
    Admin((Platform Admin))

    subgraph ResumeForge Core System
        UC1[Upload & Parse Resume]
        UC2[Paste Target Job Description]
        UC3[View ATS Compatibility Score]
        UC4[Inspect Missing Skill Gaps]
        UC5[Accept / Reject AI Tailored Bullets]
        UC6[Generate Custom Cover Letter]
        UC7[Practice Role-Specific Interview Questions]
        UC8[Download ATS-Friendly PDF]
        UC9[Monitor System Usage & API Quotas]
        UC10[Update Skill Taxonomy]
    end

    Candidate --> UC1
    Candidate --> UC2
    Candidate --> UC3
    Candidate --> UC4
    Candidate --> UC5
    Candidate --> UC6
    Candidate --> UC7
    Candidate --> UC8

    Admin --> UC9
    Admin --> UC10
```

### C. Sequence Diagram: Resume Tailoring & Score Workflow
```mermaid
sequenceDiagram
    autonumber
    actor User as Job Seeker
    participant UI as Frontend Client
    participant API as Backend API
    participant Parser as Parsing Engine
    participant AI as GenAI & RAG Engine
    participant DB as Vector DB & Store

    User->>UI: Uploads Resume.pdf & pasts Job Description
    UI->>API: POST /api/v1/analyze (multipart payload)
    API->>Parser: Extract text & structure entities
    Parser-->>API: Profile JSON (Skills, History, Projects)
    API->>DB: Query standard skill embeddings
    DB-->>API: Return taxonomy vectors
    API->>AI: Compute match % + prompt for tailoring
    AI-->>API: Returns ATS Score, Skill Gaps & Rewritten Bullets
    API-->>UI: 200 OK (JSON Analytics & Suggestions)
    UI-->>User: Displays Score Dashboard & Side-by-Side Diff
    User->>UI: Accepts suggestions & clicks "Download Resume"
    UI->>API: POST /api/v1/export (Formatted Template)
    API-->>UI: Return ATS-Compliant PDF
    UI-->>User: Downloads optimized file
```

---

## 3. Entity-Relationship (ER) Schema

```
+--------------------+       +----------------------+       +-----------------------+
|       USERS        |       |       RESUMES        |       |       JOB_POSTS       |
+--------------------+       +----------------------+       +-----------------------+
| id (PK, UUID)      |1     *| id (PK, UUID)        |       | id (PK, UUID)         |
| email (VARCHAR)    |-------| user_id (FK)         |       | user_id (FK)          |
| password_hash      |       | file_path (VARCHAR)  |       | title (VARCHAR)       |
| full_name (VARCHAR)|       | parsed_data (JSONB)  |       | company (VARCHAR)     |
| created_at (TS)    |       | ats_score (INT)      |       | jd_text (TEXT)        |
+--------------------+       | created_at (TS)      |       | required_skills(JSONB)|
                             +----------------------+       +-----------------------+
                                        |                               |
                                        +---------------+---------------+
                                                        |
                                                        ▼
                                            +-----------------------+
                                            |     EVALUATIONS       |
                                            +-----------------------+
                                            | id (PK, UUID)         |
                                            | resume_id (FK)        |
                                            | job_id (FK)           |
                                            | score (FLOAT)         |
                                            | skill_gaps (JSONB)    |
                                            | suggestions (JSONB)   |
                                            | created_at (TS)       |
                                            +-----------------------+
```
