# ResumeForge: Comprehensive Problem Statement & Domain Analysis

## 1. Domain Background & Industry Context
In today's modern talent acquisition ecosystem, applicant volumes have surged exponentially. As a result:
- Over **75% of candidate resumes are filtered out** before reaching human eyes by Applicant Tracking Systems (ATS) relying on rigid parsing heuristics.
- Job descriptions (JDs) require hyper-specific, modern tech stacks and domain competencies that vary substantially even for identical role titles (e.g., Data Engineer vs. AI/Data Platform Engineer).
- Job seekers struggle to customize their application records for every opening due to the steep cognitive overhead and manual time commitment required.

## 2. Core Problem Formulation
Job seekers face four critical bottlenecks:
1. **The 'One-Size-Fits-All' Generic Resume Dilemma:** Static resumes fail to highlight relevant technical accomplishments matching specific job postings, yielding low ATS ranking scores.
2. **Opaque Competency & Skill Deficits:** Applicants receive binary rejections without knowing which critical skills, frameworks, or certifications caused the disqualification.
3. **Manual Overhead & Cognitive Burnout:** Customizing resumes line-by-line across dozens of job applications leads to formatting errors, inconsistent bullet phrasing, and high application fatigue.
4. **Lack of Actionable, Explainable Feedback:** Existing commercial resume scanners provide superficial scores (e.g., "72/100") based solely on keyword frequency without semantic understanding, context extraction, or actionable rewrite guidance.

## 3. Existing System Deficiencies
| Existing Approach | Operational Mechanism | Fundamental Limitation |
| :--- | :--- | :--- |
| **Manual Word Processors** | Handcrafted edits in Word/Docs | Consumes 1-2 hours per application; prone to typographic errors. |
| **Legacy ATS Checkers** | Exact lexical keyword matching | Blind to semantic synonyms (e.g., "Postgres" vs "Relational DB"); zero rewrite suggestions. |
| **Generic LLM Prompts** | Unconstrained ChatGPT copy-paste | Generates hallucinations, unverified accomplishments, and breaks ATS document formatting. |

## 4. Proposed Solution: The ResumeForge Platform
ResumeForge establishes a Generative AI-powered career development platform that bridges candidates and recruiters:
- **Deep Resume Parsing:** Translates unstructured PDF/Word documents into normalized schema models (Skills, Experiences, Projects, Education).
- **Semantic JD Match Engine:** Maps extracted competencies against recruiter requirements using vector embeddings rather than simplistic keyword counts.
- **RAG-Grounded Rewriting:** Generates impact-oriented resume revisions using the Google/STAR framework (Situation, Task, Action, Result) with strict grounding to eliminate hallucinations.
- **Explainable Guidance:** Each suggested alteration displays reasoning (e.g., *"Added Airflow to bullet 2 because the target job requires pipeline orchestration"*).
- **Human-in-the-Loop Control:** Users retain full authority to accept, modify, or reject AI suggestions before exporting clean, ATS-compliant documents.
