
# 🎯 AI-Powered Resume Screener & Talent Intelligence Platform

A modern, full-stack, enterprise-grade AI resume screening web application built to streamline candidate evaluations, quantify role alignment, and generate tailored technical interview questions.

Designed for seamless development and execution in **Visual Studio Code**.

---

## 🌟 Key Features

- **Dual AI Engine**:
  - **Google Gemini 1.5 Flash**: Deep contextual reasoning, semantic assessment of accomplishments, executive hiring summaries, and dynamic interview question generation.
  - **Local Semantic NLP Engine (Offline Fallback)**: Built-in `scikit-learn` TF-IDF vectorizer, cosine similarity, and 350+ technical skills taxonomy. Works **100% out of the box** without requiring any API keys!
- **Multi-Format Document Parsing**:
  - Extract text cleanly from **PDF (`pypdf`)**, **Word (`python-docx`)**, and **Plain Text/Markdown**.
  - Automatic extraction of candidate name, email, phone, LinkedIn, and GitHub links.
- **Multi-Dimensional Competency Scoring**:
  - **Overall Match Gauge (0–100%)** with color coding & celebration confetti.
  - **Radar Chart Breakdown**: Skills Alignment, Experience Tenure, Semantic Relevance, Academic Background, and ATS Compliance.
- **Skills Taxonomy & Gap Analysis**:
  - Highlights **Matched Required Skills** (green badges).
  - Flags **Missing Critical Skills** (red badges).
  - Discovers **Complementary Bonus Skills** (blue badges).
- **Targeted Interview Question Generator**:
  - Generates technical questions to probe identified candidate weaknesses.
  - Generates deep architectural questions on claimed strengths.
  - Includes an **"Evaluation Guide"** for recruiters to know what signals to look for in candidate answers.
- **Batch Candidate Leaderboard**:
  - Upload multiple resumes simultaneously against a single job description.
  - Ranks candidates automatically in a ranked leaderboard table.
- **Executive Dossier & PDF Export**:
  - Generates clean, printer-friendly executive reports formatted for hiring committee presentations.
- **Historical Screening Archives**:
  - Built-in SQLite database stores past evaluations for fast recall and comparison.
- **Dark / Light Theme & Responsive Recruiter UI**:
  - Clean Tailwind CSS interface with Lucide icons and smooth animations.

---

## 🚀 Quickstart in VS Code

### 1. Open the Project in VS Code
Open VS Code, press `Ctrl+K Ctrl+O` (or `File -> Open Folder...`), and select:
```
C:\Users\Chalana P\.gemini\antigravity\scratch\ai-resume-screener
```

### 2. Run the Application
You have three easy ways to run the screener:

- **Method A (VS Code Debugger / 1-Click)**:
  - Press `F5` (or click `Run -> Start Debugging`).
- **Method B (VS Code Terminal)**:
  - Open terminal (`Ctrl+\``) and execute:
    ```bash
    python app.py
    ```
- **Method C (Windows Script)**:
  - Double-click `run.bat` or run `.\run.ps1` in PowerShell.

### 3. Open in Browser
Navigate to:
```
http://127.0.0.1:5000
```

---

## 🔑 Optional: Configuring Google Gemini AI

The application comes pre-configured with a **Local Intelligent NLP Engine** so it works immediately out of the box without any setup.

To unlock Gemini AI's deep reasoning:
1. Click the **Settings (gear icon)** in the top right of the dashboard.
2. Enter your Gemini API key (Get a free API key at [Google AI Studio](https://aistudio.google.com/)).
3. Click **Save Settings**. (You can also set `GEMINI_API_KEY=your_key` in the `.env` file).

---

## 📂 Project Architecture

```
ai-resume-screener/
├── .vscode/                   # VS Code configuration
│   ├── launch.json            # 1-click F5 run configuration
│   ├── tasks.json             # Build and startup tasks
│   └── settings.json          # Workspace recommendations
├── app.py                     # Flask application & REST API
├── config.py                  # Environment and application configuration
├── requirements.txt           # Pinned dependencies
├── .env.example               # Environment template
├── .env                       # Environment variables
├── run.bat                    # Windows batch launcher
├── run.ps1                    # PowerShell launcher
├── models/
│   └── database.py            # SQLite history and screening persistence
├── services/
│   ├── parser.py              # PDF, Word (.docx), and text parser
│   ├── skills_database.py     # 350+ skills taxonomy and canonical aliases
│   ├── nlp_screener.py        # Local TF-IDF & heuristic screening engine
│   ├── gemini_screener.py     # Google Gemini 1.5 Flash LLM screener
│   └── screener_engine.py     # Unified engine orchestrator
├── static/
│   ├── css/style.css          # Custom styling and print styles
│   └── js/
│       ├── app.js             # UI state, Chart.js, batch & single screening
│       └── presets.js         # Pre-loaded sample resumes & job descriptions
├── templates/
│   ├── index.html             # Recruiter dashboard UI
│   └── report.html            # Printable executive candidate dossier
├── uploads/                   # Upload directory for candidate files
└── sample_data/               # Instant test files
    ├── resumes/               # 4 pre-built candidate resumes
    └── job_descriptions/      # 4 pre-built job descriptions
```

---

## 🧪 Testing with Pre-loaded Sample Data

You don't need to hunt for sample resumes to test the system:

1. **Job Presets Dropdown**: Select from pre-loaded roles:
   - *Senior Full Stack Engineer (Python & React)*
   - *Machine Learning & Generative AI Engineer*
   - *Lead Cloud & DevOps Infrastructure Engineer*
   - *Frontend React Engineer*
2. **Candidate Presets Dropdown**: Select from pre-loaded candidates:
   - *Alex Chen* (Senior Full-Stack Developer - 7 yrs exp)
   - *Sarah Miller* (Lead ML & Data Scientist - 5 yrs exp)
   - *David Kumar* (Junior Frontend Developer - 1.5 yrs exp)
   - *Elena Rostova* (Senior DevOps & Cloud Engineer - 6 yrs exp)
3. Click **Screen Resume with AI** to view real-time score gauges, radar charts, strengths/weaknesses, and tailored interview questions!

---

## 🛠️ REST API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/` | Main Recruiter Dashboard |
| `GET` | `/api/status` | Engine status and model configuration |
| `GET` | `/api/presets` | Pre-loaded sample resumes and job descriptions |
| `POST` | `/api/screen` | Screen single resume (file upload or raw text) |
| `POST` | `/api/screen-batch` | Screen and rank multiple resumes against a job description |
| `GET` | `/api/history` | List previous candidate screenings |
| `GET` | `/api/history/<id>` | Retrieve specific candidate evaluation |
| `DELETE` | `/api/history/<id>` | Delete a screening record |
| `POST` | `/api/save-api-key` | Dynamically update Google Gemini API key |
| `GET` | `/report/<id>` | Printable / PDF-ready executive dossier |
