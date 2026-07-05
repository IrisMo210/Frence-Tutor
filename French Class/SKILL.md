---
name: french-class
description: >
  Group French class for Iris and her classmates, working toward DELF A2 in
  ~5 months (by ~2026-12-05) with the three Vocabulaire Progressif books. Use
  whenever Iris mentions the French class / la classe, wants to prepare a class
  lesson or exam ("prepare lesson 12", "prépare la leçon 12", "prepare exam 3"),
  wants a classmate's writing corrected ("correct this production écrite"),
  wants to sync class progress, or wants the class app updated/deployed. This is
  the GROUP counterpart of the personal french-tutor skill (parent folder) —
  personal lessons stay in french-tutor; anything about the shared class app or
  the 40-lesson class plan belongs here.
---

# French Class — La Classe de Français

Group class: Iris + classmates (each adds their name in the app). Goal: **pass
DELF A2 in ~5 months** (started July 2026). Curriculum = the REAL chapters of
the three Vocabulaire Progressif books, mapped to **40 lessons** in
`class-plan.md` (L1–L16 = Débutant Complet A1.1's 29 ch · L17–L32 = Débutant A1
3e éd.'s 28 ch · L33–L40 = Intermédiaire A2/B1 selection). **DELF-style exam
after every 5 lessons** (8 exams). Pace ≈ 2 lessons/week.

## Files (this folder: `...\Frence Tutor\French Class\`)
- `class-app.html` — THE app (source of truth). Self-contained HTML.
- `class-plan.md` — the 40-lesson ↔ real-chapter mapping with page numbers.
- `book-extracts/` — REAL text extracted from the books (oxico.sk sample PDFs):
  A1.1 sommaire + ch. 1–4 · A1 sommaire + ch. 1–5 · A2B1 sommaire + ch. 1–4.
  Use these word-for-word when preparing the matching lessons. (Private folder —
  never publish these texts to the public app/repo.)
- `../DELF/` — "Le DELF 100% réussite" books A1/A2/B1/B2: épreuves blanches PDFs
  + real MP3 audios + transcriptions + corrigés. The A2 ones are the class's
  official mock exams (run on paper in class, tutor marks with the corrigés).
- `class-app-layout-mockup*.html` — approved layout history (V1 chosen).
- **Deploy repo**: `C:\Users\IrisMo\la-classe-de-francais\` (local clone) →
  github.com/irismokkkk/**French-Class** (public) → LIVE at
  **https://irismokkkk.github.io/French-Class/** (Pages serves the `gh-pages`
  branch). Repo contains only `index.html` (copy of class-app.html) + `README.md`
  — NEVER the book extracts or scans.

## Design rules (approved by Iris — do not drift)
- Layout & palette = `../french-gender-chart.html` (V1 mockup): paper `#F6F4EF`,
  masculine blue `#2C5C86`, feminine rose `#A8425A`, gold `#B68A35`, fonts
  Cormorant Garamond / Karla / JetBrains Mono.
- Every noun WITH gender; masculine shown blue, feminine rose.
- Lesson tabs: Apprendre · Quiz · Écoute · Genre · Phrases · Conjugaison · Dialogue.
- Audio = browser TTS (speechSynthesis, fr-FR, rate .85): 🔊 on every word,
  sentence and dialogue bubble; Écoute drill (hear → choose meaning → shadow);
  exam listening part. Shadowing prompts, NO recording (her choice).
- Dialogues: one scene per lesson, 3 levels — ① listen&read ② choose your reply
  ③ type your reply from the English hint. Progress saved per lesson (P.dlg).
- Mixed review: 10 questions across studied lessons; missed items tracked in
  P.weak ("key = lessonN:wordIndex") and resurface ~50% of the time.
- Exams = full DELF A2 format: 4 parts × 25 (oral TTS / écrits / écrite with
  model+copy-to-tutor / orale checklist), pass ≥ 50/100 AND ≥ 5/25 per part.
- Per-person per-device progress (localStorage `fcl_*`); name pills; Sauvegarder/
  Restaurer = backup code "FCL1.<base64 JSON>".
- **Mode Classe** (two-layer model, Iris's design): the class meets daily, taught
  by two French-speaking classmates, on ONE dedicated shared device. The 🎓 button
  opens a slide-style teacher view: title → words in huge type (8/slide, 🔊 +
  "écouter tout") → grammar → dialogue (play + act in pairs) → "À vous de parler !"
  (speaking activities from the `PARLER` map, keyed by lesson n — add 3 prompts
  when preparing a lesson) → devoirs (book exercises + solo app homework).
  NO quiz/genre/conjugaison drills in class — those stay individual. Teachers
  advance lessons freely (‹ leçon ›); class position = localStorage `fclc_pos`
  on the class device only, separate from personal profiles. Keyboard ← → moves
  slides. Not-loaded lessons show the "prépare la leçon N" note.

## Preparing a lesson ("prépare la leçon N")
L1–L10 + L17 are loaded. To fill another, edit `class-app.html` between
`/* === LESSONS_START === */` and `/* === LESSONS_END === */`, find `{n:N,...}`:
- FIRST check `book-extracts/` — if the chapter text is there, use its exact
  words/expressions. Otherwise build from the chapter title (class-plan.md) and
  standard content; Iris photographs the book pages to verify and complete.
- `g` grammar note (HTML) · `w` 20–40 rows `["english","article français","/ipa/",
  g,"exFR","exEN"]` (nouns with article+gender; adjectives "masc / fém"; straight
  apostrophes) · `x` 5–6 sentences `["English.",["accepted","alt"]]` (accepted
  answers lowercase, no accents — norm() compares that way) · `v` verb infinitives
  (add new verbs to VERBS with 6 present forms) · `d` one dialogue scene
  `{t:"title",lines:[["A"|"M","français","English"],...]}` — "M" lines are the
  student's; 6–8 lines; use the lesson's vocab.
Then TEST (open in Chrome, run every tab) and deploy (below).

## Preparing an exam ("prépare l'examen N")
Replace `{n:N,after:X,ready:false}` between EXAMS_START/END with a full entry
like EX1–EX2: `listen` 2 docs {say, qs MCQ} (5 qs total, vocabulary of L1..X
only), `read` 2 texts (5 qs), `write` 2 DELF-style prompts + models, `speak`
5 class tasks. Set `ready:true`. ORIGINAL texts only (public app!) — model the
FORMAT on the DELF book's épreuves, never copy them. EX8 = the real DELF blanc
from `../DELF/Le DELF A2 100% réussite/` done in class.

## Correcting writing
Students tap "Copier → correction par le tuteur" and paste here. Correct against
the DELF A2 écrite grid (task fulfilment, vocabulary, grammar, coherence), show
corrections with one-line whys, give /25 to type into the app.

## Deploy after ANY edit to class-app.html
1. Copy `class-app.html` → `C:\Users\IrisMo\la-classe-de-francais\index.html`
2. `git -C C:\Users\IrisMo\la-classe-de-francais add -A; git -C C:\Users\IrisMo\la-classe-de-francais commit -m "update"; git -C C:\Users\IrisMo\la-classe-de-francais push origin main; git -C C:\Users\IrisMo\la-classe-de-francais branch -f gh-pages main; git -C C:\Users\IrisMo\la-classe-de-francais push -f origin gh-pages`
   (**gh-pages is the branch Pages serves** — always sync it with main)
3. Also commit/push the private `Frence Tutor` repo. Pages rebuilds in ~1 min;
   classmates just reopen https://irismokkkk.github.io/French-Class/

## Getting book content for ANY chapter (the vocabulary pipeline)
Priority order when preparing a lesson:
1. `book-extracts/*.txt` — real text already extracted (A1.1 somm+ch1–4, A1
   somm+ch1–5, A2B1 somm+ch1–4).
2. **Render the scanned book pages to images and READ them visually** (this
   works for every chapter, incl. A1.1): `tools\render-pdf.ps1 -Pdf <book.pdf>
   -Pages @(15,16,17) -OutDir <scratchpad>` then Read the PNGs — Claude reads
   scans perfectly. Uses the built-in Windows.Data.Pdf engine (WinRT), no
   installs, ~1 s/page. The A1.1 PDF ("...Complet (2015)-Livre _ A1.1.pdf") has
   114 pages ≈ the whole book; **PDF page = book page + 1**. Same technique for
   the A1 (77 MB) and A2B1 (41 MB) scans — verify each file's page offset once.
3. Iris photographs book pages and pastes them in chat.
Scribd links are login-walled — don't bother. Never publish book text/scans to
the public repo; only original app content.

## Known gotchas
- Article regexes: alternation order MUST be `une|un|les|le|la|l'` ("un" eats "une").
- Word COM CANNOT convert PDFs on this PC (hangs on a suppressed dialog even
  unblocked). For TEXT-layer PDFs: serve on localhost (PowerShell HttpListener),
  open in Chrome (MCP), Ctrl+A Ctrl+C in the viewer, `Get-Clipboard -Raw`
  (that's how book-extracts/ was made). For SCANNED PDFs: tools\render-pdf.ps1
  (above) — Chrome's viewer freezes on the big scans, don't use it for those.
- Users: "+ ajouter un nom" / "– retirer" pills manage classmates; removing
  deletes that person's fcl_p_<name> storage on that device (min 1 name kept).
- No Node/Python on this PC. TTS quality varies by device; iPhones need one tap
  before audio plays (browser rule) — first ▶ tap may be silent, tap again.
