# korean-writing-tutor

A Mistral Agents SDK agent that tutors French university students (CEFR B1.2–B2) writing
short Korean compositions, following the <국제 통용 한국어 표준 교육과정> levels 3–4.

## What it does (3-stage workflow)

1. **Topic selection** — greets the student in French, offers 5 topics (or accepts a free
   topic), and announces the target lengths: B1.2 350–450자 / B2 500–650자 (공백 포함).
2. **Manuscript paper (원고지)** — renders the submitted text on a 200자-style 원고지 as a
   self-contained HTML `<table>` (20 cells per line, `#d9534f` red grid, 첫 칸 들여쓰기).
3. **Correction report in French** — color-coded feedback with a legend:
   - 🔴 `#D32F2F` Lexique et nuance (어휘)
   - 🔵 `#1976D2` Grammaire : forme et sens (문법)
   - 🟢 `#2E7D32` Cohérence et cohésion (연결/응집성)
   - 🟣 `#7B1FA2` Structure du paragraphe (문단 구성)

   followed by: length evaluation, paragraph-structure analysis, language analysis
   (lexicon / grammar / coherence), a detailed correction table with the corresponding
   국제통용 level of each replacement (`3급 (B1)`, `4급 (B2)`, `5급 (C1)`), and the full
   revised text with revisions highlighted.

## Tool

- `count_characters(text)` — exact 글자 수 count (공백 포함 / 제외) and paragraph count for
  the length evaluation.

## Run locally

Put a `MISTRAL_API_KEY` in `.env`, then:

```bash
uv run --env-file .env agents chat
```

## Deploy

```bash
git remote add origin <your-repo>
git push -u origin main
uv run --env-file .env agents deploy
```
