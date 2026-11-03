# PMP/ACP Guide

*(formerly the Vets2PM PMP Readiness Map)*

An AI-driven adaptive learning tool for future Vets2PM students preparing for the PMP exam.

**Vision:** an AI-driven adaptive learning system that speeds up learning for Vets2PM students and improves PMP pass rates.

**Definition of done:** an embedded LMS with AI analysis that turns student performance into heat maps, so students can focus their study.

## What's in this repo

| Path | What it is |
| --- | --- |
| `prototype/index.html` | The working prototype (a single HTML page). |
| `prototype/sample-questions.csv` | 38 original PMP-style practice questions in the upload format. The hard questions and case studies are built into the page. |

The prototype also runs as a hosted Claude artifact: <https://claude.ai/artifact/QmagGE6pTW7sxmnL6ai3ZQ>

## Three separate tracks

| Track | Body | Outline used | Domains |
| --- | --- | --- | --- |
| PMP | PMI | Exam content outline, July 2026 | People 33%, Process 41%, Business Environment 26% |
| PMI-ACP | PMI | Exam content outline, 2024 | Mindset 28%, Leadership 25%, Product 19%, Delivery 28% |
| PSM I | Scrum.org | 2020 Scrum Guide + focus areas | Scrum framework, People & teams, Product agility (no official weights) |

Each track has its own questions, heat map, progress and Study topics. Uploads take an optional `track` column (PMP, ACP, PSM), or infer it from the task code (P1–B6, AM1–AD4, SF1–SP4).

**Study tab:** 10 topics per track with key points, a YouTube search link, a practice set, and a Library of official links and instructor-uploaded PDFs.

## Prototype features

- **Heat map:** accuracy by PMP domain and task area. It follows the exam content outline used from July 2026: People 33%, Process 41%, Business Environment 26%. The task names are paraphrased.
- **Readiness dashboard:** a weighted readiness gauge, domain bars against a target, pace, coverage, and a trend of scores across sessions.
- **Practice modes:** weak-area practice (adaptive), review mistakes, mixed practice, and a timed exam simulation at the real exam pace of 80 seconds per question, with flag-for-review.
- **Question bank:** upload questions as CSV or JSON. See the format below.
- **AI tutor:** a chat tutor, "explain this question", a debrief after each session, and AI-built study sessions. *Works only when the page is opened inside Claude.*
- **Admin mode:** a shared question bank (add, edit, delete), plus a class view with a class heat map, a student roster and the hardest questions. *Works only when the page is opened inside Claude.*
- **Aron, the AI coach:** always available from the Ask Aron button or the `/` key, plus "Ask Aron" buttons on every question. Inside Claude he answers anything (concepts, study plans, careers, certifications). Outside Claude he answers from the app's own notes.
- **Careers:** how military work already maps to project management (14 translations and real examples), how each industry uses predictive, agile or hybrid methods, 12 career paths with what you need and optional certifications, and a certification requirements table. Details open in Apple-style sheets, with scroll animations.
- **Account:** create a profile (name, branch, status, job code, exam and date, career interest). Inside Claude it uses the Claude sign-in and syncs across devices; elsewhere it is saved in the browser. Email and password accounts come with the production app.
- **Video lessons:** explainer videos for the hardest topics (EVM, critical path, risk responses, the Agile Manifesto, Scrum, cumulative flow) in Study and Help. They open on YouTube.
- **Search:** a built-in search (⌘K or Ctrl K, or the Search button) across study topics, formulas, diagrams, videos, PDFs and official resources, careers, certifications, case studies, practice questions and help.
- **Wide-screen side panels:** on screens 1400px and wider, the left panel shows today's readiness, the next best step, quick links and the library. The right panel shows Ask Aron, the question of the day, a military-to-PM tip, videos to watch next and exam facts.
- **Exam check-in and score report:** before an exam simulation or quiz, students type their name, choose a scoreboard name and avatar, and can add an email. Afterwards they get a practice score report rated AT/T/BT/NI by domain. It is clearly labelled as a practice report, not an official PMI or Scrum.org result. The report can be downloaded, printed or emailed (email opens the student's mail app; automatic sending needs the production app).
- **Community:** the question of the day with a streak, a class scoreboard showing each student's best score on each exam and quiz, and a chat room where students tag @Aron for help or ask him to fact-check any message. Needs Claude for the shared scoreboard and chat.
- **Sourced questions:** every ACP and PSM I question names its source (Scrum Guide 2020, PMI-ACP exam content outline, Agile Practice Guide). Four levels: Easy, Medium, Hard, Very hard.
- **Hard questions and case studies:** 17 hard and very hard questions (network float, EVM/TCPI, PERT, EMV, decision trees, contracts) and 4 multi-question case studies with exhibits.
- **Charts and diagrams:** cumulative flow diagram, burndown, EVM S-curve, network diagram, control chart, probability/impact matrix and power/interest grid, drawn as SVG.
- **Study hub:** an EVM calculator, a formula sheet, the PMI mindset, and guides to reading each diagram.
- **Help center:** FAQ search, "report a problem with this question", and help requests. Admins get an inbox to reply and resolve.

Opened directly in a browser, the page works offline. Progress is saved in that browser, and the AI and admin features are hidden.

### Sprint quizzes (MBI)

The **Quizzes** tab supports the current sprint:

- **Quiz 1–3** are the baseline quizzes. **Quiz 4** is the advanced validation quiz that shows improvement.
- Every question is tagged with a **difficulty** (Easy, Medium, Hard, Very hard) and an **exam outline task** (P1–P6, R1–R7, B1–B6).
- **Difficulty check:** compares each question's tagged level with how students actually scored (Easy ≥ 80% correct, Medium 60–79%, Hard 40–59%, Very hard < 40%). Admins can apply the suggested level once a question has 5 or more answers.
- **Exam outline coverage:** questions per task area per quiz, with gaps highlighted.
- **Test data:** download every answer as CSV (student, quiz, question number, domain, task code, difficulty, answer, correct, seconds, time). Admins can download the whole class. The tagged question bank also downloads as CSV.

Use `prototype/quiz-template.csv` as the upload format.

### Run it locally

Open `prototype/index.html` in any modern browser. No build step is needed.

### Question format (CSV)

```csv
quiz,number,difficulty,domain,task,question,a,b,c,d,answer,explanation
Quiz 1,1,Easy,People,P2,"Two team members disagree about priorities. What should the PM do first?",Decide for them,Facilitate a discussion to find a solution together,Escalate,Ignore it,B,Collaboration addresses the root cause.
```

- `quiz` is Quiz 1 to Quiz 4 (or just 1–4). `number` is the question's position in the quiz. `difficulty` is Easy, Medium, Hard or Very hard (Moderate and Advanced still work). An optional `source` column is shown under the explanation. All are optional.
- `task` takes the exam outline code (P1–P6, R1–R7, B1–B6) or the task name.

- `domain` starts with People, Process, or Business.
- `answer` is A–D or 1–4.
- A task name the app doesn't know gets its own tile on the heat map.

## Roadmap

1. **Quizzes online (first increment):** write the quizzes and tag every question by domain and task.
2. **Score reports** by domain.
3. **Heat map** per student, by task.
4. **AI advice:** explains weak spots and suggests what to study, reviewed by an instructor.
5. **Adaptive quizzes**, and tracking pass rates before and after.

## Next: the production app

The recommended stack, from the alternatives analysis:

- A custom web app on managed hosting: Next.js on Vercel, plus Supabase for Postgres and auth.
- Roles: student, instructor and admin.
- The AI runs on Vets2PM's own Claude API key.
- Optional LTI embedding into an existing LMS.
