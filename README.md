# AWS Cloud Practitioner Quiz System

An adaptive quiz engine built for **AWS Cloud Practitioner (CLF-C02)** study using ChatGPT-5.  
This system pulls from your local project folder — including **flashcard CSVs, course transcripts, and history logs** — to deliver **smart, randomized, feedback-driven quiz sessions** with **persistent tracking**.

---

##  Quick Start

### 1️ Prerequisites
- ChatGPT-5 or later.  
- A project folder containing:
  - `flashcards.csv` — your question/answer bank.  
  - One or more `.html`, `.txt`, `.pdf`, or `.docx` transcripts from courses.  
  - (Optional) `quiz_history.csv` if you’ve saved results from previous sessions.

### 2️ Launching the Quiz System
1. Open a **new GPT-5 chat**.  
2. Paste in the **AI Prompt** from this project.  
3. Type:
   ```
   Use all files in my project folder.
   ```
4. When ready to play:
   ```
   Begin Session
   ```

---

##  File Structure

| File | Purpose |
|------|----------|
| `flashcards.csv` | Core Q&A bank. Columns: `Question,Answer,Topic,Difficulty,Alternatives` |
| Transcripts (`.html`, `.txt`, `.pdf`) | Source material for generating extra questions |
| `quiz_history.csv` | Saved performance history across sessions |
| `README.md` | You’re reading it |

---

##  Session Commands

| Command | Description |
|----------|--------------|
| **Begin Session** | Start or restart a randomized quiz session |
| **End Session** | End session, show score and analytics |
| **Hint** | Get a small clue for current question |
| **Skip** | Skip question without penalty |
| **Review Missed Questions** | Replay questions you got wrong |
| **Show Topics** | List all detected topics |
| **Set Mode Hard** | Enable timers and fewer hints |
| **Set Mode Study** | Disable timers, show hints and explanations freely |
| **Spaced Review** | Review a prioritized set of missed or weak questions |
| **Export History** | Output all recorded quiz history in CSV |
| **Export Misses** | Output only missed questions |
| **Import History** | Paste or upload previous quiz_history.csv to merge progress |
| **Reset History** | Wipe persistent history (requires confirmation) |

---

##  Scoring & Analytics

Each session tracks and reports:
- **Overall Score** — correct / total + percentage  
- **Longest Correct Streak**  
- **Per-Topic Accuracy** (if `Topic` column exists)  
- **Per-Difficulty Accuracy** (if `Difficulty` column exists)  
- **Fast Review Queue** — missed items for spaced review  
- **Summary Stats** — strengths, weaknesses, recommendations  
- **Copyable “Missed Questions” Set** — for flashcard apps or manual review  

---

##  Persistent History

After every `End Session`, the system outputs a **History Block** in CSV format, e.g.:

```
date_time,question_id,topic,difficulty,outcome,source,session_id
2025-10-20T14:25:32Z,aws-001,Security,Medium,Correct,csv,Session-7
```

### To save your history:
1. Copy the entire CSV block into a text file.  
2. Save as `quiz_history.csv` in your project folder.  
3. Next session, it’ll be automatically loaded and merged.

---

##  Extended Questions

During sessions, the system may fetch **(Extended)** questions from the web to include fresh AWS topics, new service updates, or realistic scenario questions.  
These are marked clearly and included in scoring.

---

##  Example Workflow

1. Upload:
   - `flashcards.csv`
   - All course transcripts
   - Optional `quiz_history.csv`
2. Start a GPT-5 chat with the prompt.
3. Run:
   ```
   Begin Session
   ```
4. Answer questions. Use `hint`, `skip`, or `end session` anytime.
5. When finished, copy the **History Block (CSV)** and save it as `quiz_history.csv`.
6. Re-upload next time to keep long-term stats.

---

##  Tips
- Keep your **flashcards.csv** clean and organized — consistent topic and difficulty tags make analytics more useful.  
- Regularly **Review Missed Questions** or run **Spaced Review** sessions to lock in weak areas.  
- Back up your `quiz_history.csv` to maintain lifetime performance data.  
- Add new transcripts or course materials anytime — the system automatically integrates them.  

---

##  Example CSV Format

### `flashcards.csv`
```csv
Question,Answer,Topic,Difficulty,Alternatives
"What AWS service is used for object storage?","Amazon S3","Storage","Easy","S3|Simple Storage Service"
"What pillar of the Well-Architected Framework focuses on protecting data and systems?","Security","Well-Architected","Medium","Protecting Information|Data Protection"
```

### `quiz_history.csv`
```csv
date_time,question_id,topic,difficulty,outcome,source,session_id
2025-10-20T14:25:32Z,aws-001,Security,Medium,Correct,csv,Session-7
```

---

##  Ending a Session

When you type:
```
End Session
```
You’ll receive:
- Session summary (score, streak, breakdowns)
- Copyable list of missed questions
- Exportable `History Block` in CSV format  

Save that block as `quiz_history.csv` for next time.

---

##  Philosophy

This system isn’t just about memorizing — it’s built to **simulate exam conditions**, test **critical thinking**, and identify your **true readiness**.  
Each round gets smarter as your dataset and history grow.
