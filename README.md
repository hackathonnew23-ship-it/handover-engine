# Handover Engine

Turns a leaving team member's scattered project activity into a usable handover: a scored, source-linked packet, a day-by-day plan, a meeting agenda and a last-day checklist with sign-offs.

Team HACKATHONNEW23: Jeevan M. Gowda, Pranav S. J, Nithya C.

## Run it

It is a single static page. Open `index.html` in a browser, or visit the live site (link in the repository description). No install or build step. An internet connection is needed for Three.js (cdnjs) and Google Fonts.

## How to use it

1. Press **Load sample**, or paste one activity entry per line, or upload a .txt, .log, .csv or .json file. Or open **Import live from GitHub**, enter a repository (owner/name) and the leaver's GitHub username, and press **Import and generate**.
2. Enter the leaving member, the successor and the last working day.
3. Press **Generate handover**.
4. Read the packet, the 3D graph, the plan, the meeting agenda and the checklist. Tick items as they are resolved.
5. Copy the summary or the full Markdown packet.

Entry format: `[2026-10-02] PR #482 Dev Menon: 2 review comments open, waiting on Priya`

## What it does

- Imports a person's pull requests, issues and commits live from the GitHub API (public repositories need no token)
- Parses entries and links those that share a PR or ticket reference
- Classifies items as access, knowledge, decision or open work
- Scores readiness with a penalty model and lists the reasons
- Shows who holds what in an interactive 3D graph
- Generates a plan, a timed meeting agenda, contacts and a checklist with three sign-offs
- Searches the packet by person, ticket, PR or word, on top of the category and risk filters
- Records each of the three sign-offs with a timestamp and shows a clear Approved status, which is included in the Markdown export
- Exports a summary and a Markdown packet
- Ember, a voice-guided helper with Next, Skip and Auto-play, plus a 3D guided tour

## Technology

HTML, CSS and JavaScript in one file. Three.js r128 for the 3D scenes. A rule-based analysis engine in plain JavaScript (the code between `ENGINE-START` and `ENGINE-END`). The browser Web Speech API for voice. Analysis runs in the browser. The only network calls are to the GitHub API when you use the import, and to load Three.js and fonts.

## Known limits

- Only GitHub is connected live. Jira, chat and calendar activity must be pasted or uploaded.
- The GitHub import reads the latest 100 pull requests and issues and 50 commits, and is limited to 60 requests an hour without a token.
- Classification is rule-based and can miss context that is not in the record.
- Nothing is saved on a server: no accounts, shared handovers or approval history.
- The 3D views need WebGL. Voice needs a browser with speech support.

## Planned for Round 3

1. Saved handovers with accounts, shareable links and recorded sign-offs.
2. Assisted extraction of decisions and context with source citations and accept or reject review.
3. Jira and Slack connectors merged with GitHub into one cross-linked timeline.
