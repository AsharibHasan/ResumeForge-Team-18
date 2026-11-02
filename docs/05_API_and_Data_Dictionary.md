# ResumeForge: API Endpoints & Data Dictionary

## 1. RESTful API Specifications

### Authentication & Users
- `POST /api/v1/auth/register` : Create new user account.
- `POST /api/v1/auth/login` : Authenticate user & return JWT bearer token.

### Analysis & Processing
- `POST /api/v1/resume/upload` : Upload raw resume file; returns parsed JSON schema.
- `POST /api/v1/resume/parse-jd` : Ingest raw job description text; extracts required skills and role levels.
- `POST /api/v1/analyze/match` : Runs semantic similarity; returns score and skill gap matrix.
  - **Payload:** `{ "resume_id": "uuid", "job_description_text": "..." }`
  - **Response:**
    ```json
    {
      "overall_score": 84,
      "breakdown": {
        "keyword_score": 78,
        "semantic_score": 89,
        "format_score": 95
      },
      "matched_skills": ["Python", "FastAPI", "SQL", "Git"],
      "missing_skills": ["Apache Kafka", "Docker", "AWS ECS"],
      "recommended_keywords": ["CI/CD pipelines", "Microservices"]
    }
    ```

### Tailoring & Generative AI
- `POST /api/v1/generate/tailor-bullets` : Request STAR-aligned bullet point rewrites.
- `POST /api/v1/generate/cover-letter` : Synthesizes grounded cover letter.
- `POST /api/v1/generate/interview-prep` : Returns predicted interview questions and answers.

### Export
- `POST /api/v1/export/pdf` : Generates and compiles ATS-compliant formatted PDF.

---

## 2. Core Data Dictionary
| Field Name | Data Type | Constraints | Description |
| :--- | :--- | :--- | :--- |
| `user_id` | UUID | Primary Key | Unique identifier for registered candidate |
| `resume_id` | UUID | Primary Key | Unique document instance ID |
| `parsed_skills` | Array[String] | Indexed | Extracted skills normalized against skill ontology |
| `ats_score` | Integer | 0 <= score <= 100 | Composite match rating |
| `bullet_text` | Text | Non-null | Single work experience or project description line |
| `star_metric` | Boolean | Default: False | Flag indicating presence of quantifiable metric |
