# Vets2PM PMP Readiness Map

An AI-driven adaptive learning tool for future Vets2PM students preparing for the PMP exam.

**Vision:** an AI-driven adaptive learning system that speeds up learning for Vets2PM students and improves PMP pass rates.

**Definition of done:** an embedded LMS with AI analysis that turns student performance into heat maps, so students can focus their study.

## What's in this repo

| Path | What it is |
| --- | --- |
| `prototype/index.html` | The working prototype (a single HTML page). |
| `prototype/sample-questions.csv` | 38 original PMP-style practice questions in the upload format. |

The prototype also runs as a hosted Claude artifact: <https://claude.ai/artifact/QmagGE6pTW7sxmnL6ai3ZQ>

## Prototype features

- **Heat map:** accuracy by PMP domain and task area. It follows the exam content outline used from July 2026: People 33%, Process 41%, Business Environment 26%. The task names are paraphrased.
- **Readiness dashboard:** a weighted readiness gauge, domain bars against a target, pace, coverage, and a trend of scores across sessions.
- **Practice modes:** weak-area practice (adaptive), review mistakes, mixed practice, and a timed exam simulation at the real exam pace of 80 seconds per question, with flag-for-review.
- **Question bank:** upload questions as CSV or JSON. See the format below.
- **AI tutor:** a chat tutor, "explain this question", a debrief after each session, and AI-built study sessions. *Works only when the page is opened inside Claude.*
- **Admin mode:** a shared question bank (add, edit, delete), plus a class view with a class heat map, a student roster and the hardest questions. *Works only when the page is opened inside Claude.*

Opened directly in a browser, the page works offline. Progress is saved in that browser, and the AI and admin features are hidden.

### Run it locally

Open `prototype/index.html` in any modern browser. No build step is needed.

### Question format (CSV)

```csv
domain,task,question,a,b,c,d,answer,explanation
People,Conflict & collaboration,"Two team members disagree about priorities. What should the PM do first?",Decide for them,Facilitate a discussion to find a solution together,Escalate,Ignore it,B,Collaboration addresses the root cause.
```

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
