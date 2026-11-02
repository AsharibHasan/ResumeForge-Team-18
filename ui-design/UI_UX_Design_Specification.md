# ResumeForge: UI/UX Design Specification & Wireframes

## 1. Design System & Brand Identity
- **Primary Color:** Deep Slate Navy (`#0F172A`)
- **Accent Color:** Vibrant Indigo / Electric Violet (`#4F46E5` / `#6366F1`)
- **Success / Match Accent:** Emerald Green (`#10B981`)
- **Warning / Skill Gap Accent:** Amber Orange (`#F59E0B`)
- **Neutral Background:** Slate Mist (`#F8FAFC`)
- **Typography:** Inter, SF Pro Display, JetBrains Mono for metrics and JSON data

---

## 2. Screen Hierarchy & Navigation Flows

```text
[Landing Page]
     │
     ▼
[Authentication: Login / Register]
     │
     ▼
[Main Workspace: 3-Column Split View]
 ┌──────────────────────┬────────────────────────┬─────────────────────────┐
 │ Col 1: Input Panel   │ Col 2: AI Analytics    │ Col 3: Live Preview     │
 │                      │                        │                         │
 │ • File Upload Drop   │ • Match Score (Gauge)  │ • Formatted ATS Resume  │
 │ • Parsed Sections    │ • Skill Gap Badges     │ • Side-by-Side Diff View│
 │ • Target JD Input    │ • AI Rewrite Prompts   │ • Accept / Reject Edits │
 │ • Role Selector      │ • Interview Q&A Copilot│ • One-Click Export PDF  │
 └──────────────────────┴────────────────────────┴─────────────────────────┘
```

---

## 3. UI Screen Specifications

### Screen 1: Ingestion & Upload View
- Drag-and-drop zone with instant file validation (`.pdf`, `.docx`).
- Textarea with auto-expanding line counts for pasting job descriptions.
- "Analyze & Align" primary call-to-action button with animated progress indicator.

### Screen 2: Evaluation & Skill Gap Dashboard
- **ATS Score Circular Gauge:** Visual 0–100 progress ring with status tag (*Needs Improvement*, *Good*, *Strong Match*).
- **Skill Discrepancy Matrix:**
  - *Green Pills:* Found skills (e.g., Python, SQL, REST APIs).
  - *Red/Amber Pills:* Missing target skills (e.g., Apache Airflow, Docker, AWS).
- **Quick-Insert Recommendation:** Clicking a missing skill triggers an AI bullet suggester prompt.

### Screen 3: Interactive Diff & Tailoring Studio
- High-fidelity split view showing **Original Work Experience Bullet** on the left and **AI-Enhanced STAR Bullet** on the right.
- Visual token highlight of added keywords and action verbs.
- Action buttons: `Accept`, `Regenerate`, `Edit Manually`, `Discard`.

### Screen 4: Interview & Career Copilot
- Accordion cards with generated technical and behavioral questions tailored to the resume-JD gaps.
- Expandable model answers highlighting the candidate's actual projects.
