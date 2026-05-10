# AI LEX 2026 — Questionnaire (deployment guide)

A self-contained static site (one HTML file) you can host for free on GitHub Pages. Submissions go to Formspree (free tier, 50/month, enough for the 30-40 expected responses).

## What you have here

- `index.html` — the questionnaire (open it directly in a browser to see it work end to end, except for submission).
- `README.md` — this file.

## What you need to do once

You will need two free accounts: GitHub (for hosting the page) and Formspree (for receiving submissions). Total time: about 30 to 45 minutes the first time.

### Step 1 — Create a GitHub account

1. Go to https://github.com/signup
2. Use your jmprunet@gmail.com (or your Cathay address). Pick a username — keep it simple, e.g. `jmprunet` or `jeanmarcprunet`. This will appear in the URL of your hosted page.
3. Verify your email. Free plan is fine.

### Step 2 — Create a repository for the questionnaire

1. Once logged in, click the green "New" button (or go to https://github.com/new).
2. Repository name: `ai-lex-2026`
3. Description: `AI LEX 2026 pre-event questionnaire`
4. Set it to **Public** (required to use free GitHub Pages).
5. Tick "Add a README file" (we will overwrite it).
6. Click "Create repository".

### Step 3 — Upload the questionnaire file

The simplest path is the web upload (no git command line needed):

1. In your new repo, click "Add file" → "Upload files".
2. Drag-drop both `index.html` and `README.md` from this folder.
3. Scroll down, leave "Commit directly to the main branch" selected, click "Commit changes".

### Step 4 — Turn on GitHub Pages

1. In the repo, click "Settings" (top tab).
2. In the left sidebar, click "Pages".
3. Under "Build and deployment" → "Source", select "Deploy from a branch".
4. Under "Branch", select `main` and folder `/ (root)`. Click "Save".
5. Wait one to two minutes. The page will be live at:

   `https://YOUR_USERNAME.github.io/ai-lex-2026/`

   Replace `YOUR_USERNAME` with the username you picked in Step 1. The URL appears at the top of the Pages settings page once ready.

At this point the page is live and looks correct, but the submit button does not yet send anything anywhere. We do that next.

### Step 5 — Create a Formspree account and get a form endpoint

1. Go to https://formspree.io and click "Get started".
2. Sign up with your email. Free plan is fine.
3. Once in, click "New Form".
4. Form name: `AI LEX 2026 Questionnaire`. Email: where you want to receive the submissions (your jean-marc.prunet@cathay.fr or jmprunet@gmail.com).
5. Click "Create Form". You will see an "Endpoint URL" that looks like `https://formspree.io/f/abcdwxyz`. Copy it.

Note: Formspree free tier is 50 submissions per month and limits some advanced features. 50 is enough for this event. If you want JSON of all submissions, the Formspree dashboard exports CSV/JSON anytime.

### Step 6 — Plug the endpoint into the page

1. In your repo, click `index.html`.
2. Click the pencil icon (top right of the file content) to edit.
3. Use Ctrl-F (or Cmd-F) to find `REPLACE_ME`.
4. Replace `https://formspree.io/f/REPLACE_ME` with the URL you copied at Step 5. Keep the quotes.
5. Scroll down, "Commit changes".
6. Wait one minute. Reload your live page.
7. Fill the questionnaire as a test (use a fake company "Cathay Capital" so we can spot it). Submit. You should receive the email at the address you set in Step 5.

### Step 7 — Send the link to participants

The link to share is your live URL: `https://YOUR_USERNAME.github.io/ai-lex-2026/`

Suggested sender: Cécile or Valentine, on behalf of the Cathay AI LEX team. Wording can be very short, e.g.:

> Following the AI LEX invitation: a 10 to 15 minute pre-event questionnaire to help us shape the breakouts and consolidate portfolio benchmarks. Please fill before [DATE]. Link: [URL]. Confidential financial section is Cathay-only and never attributed.

## How responses look in Formspree

Each submission arrives as an email and is stored in the Formspree dashboard. The body is a JSON dump of all answers. You can export everything as CSV or JSON anytime from the dashboard.

If you want a fancier downstream (Notion, Google Sheet, Airtable), Formspree paid plans support webhooks, but the CSV export plus a manual paste into a sheet is enough for this event.

## How to update the questionnaire later

If you want to change a question, an option, or the wording:

1. In your repo, click `index.html`, click the pencil icon, edit the text.
2. The questionnaire content is defined in the `SCHEMA` array near the top of the script section. Search for `SECTION 0`, `SECTION 1`, etc. The structure is readable.
3. Commit changes. The live page updates within a minute.

For a deeper change (new section, new question type), open a chat with me, paste the section you want to change, and I will give you the edited block.

## How to make a private "thank you for completing" landing

Already built in. After submission, the page shows a clean confirmation. No extra setup needed.

## Things that are intentionally simple

- No login. We rely on Formspree for backend and on participants self-identifying. Adding auth would require a paid Formspree plan or Cloudflare Workers.
- No data export inside the app. Formspree dashboard handles it.
- LocalStorage (in the browser) saves progress so a participant can pause and resume in the same browser. It does not survive a different device or a private window.

## Local test before pushing to GitHub

Just double-click `index.html` on your Mac. It opens in your default browser. Everything works except the actual submission (which needs the live page deployed since Formspree validates the origin).

## Troubleshooting

- "Submission failed" message after Submit → either you have not replaced `REPLACE_ME` with your real Formspree endpoint, or your Formspree account has not yet confirmed the form.
- Page does not update after a commit → wait two minutes, then hard-refresh (Shift-Cmd-R on Mac).
- Page shows a 404 → in repo Settings → Pages, check that branch is `main` and folder is `/ (root)`.

For anything else, ping me in Cowork.
