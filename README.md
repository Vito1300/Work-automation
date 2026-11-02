# Job search with Claude — a simple career-ops fork

A personal job-search assistant that runs in **Claude Code** and your own **Chrome**.
Give it your CV and it will:

1. **Format your CV** into a clean PDF (English and/or Ukrainian).
2. **Fill in your profiles** on LinkedIn, Djinni, Work.ua, Robota.ua, DOU and Upwork.
3. **Find jobs** on all those sites, score each one 1–5 against your CV, and **show everything in a dashboard**.

Nothing is sent without you: you press "Apply" / "Save" yourself, or say "yes" first.

> A simplified fork of [career-ops](https://github.com/santifer/career-ops) by santifer (MIT). The full original docs are in [docs/README.career-ops.md](docs/README.career-ops.md).

---

## Setup (once)

You need three things:

- [**Claude Code**](https://claude.com/claude-code) — the Claude desktop app (Code tab) or the CLI.
- [**Node.js**](https://nodejs.org) — the LTS version, default install.
- **Google Chrome** with the **Claude** extension (Chrome Web Store), signed in to the same account. Log in to Djinni, LinkedIn, etc. in that Chrome.

Then:

1. Get the project: click **Code → Download ZIP** on this page and unzip it (or `git clone` it).
2. Open the folder in Claude Code.
3. Type `/cv`.

That's it. On the first run Claude installs everything else it needs by itself.

---

## How to use it — 3 commands

Type these in the Claude Code chat.

### 1. `/cv` — your CV

Claude asks how you'd like to start: paste your CV, drop an old PDF into `documents/`, share your LinkedIn, or just tell it about your experience. After a few questions (name, contacts, target role, salary) you get:

- `output/General/CV.pdf` — English CV
- `output/General/CV-UA.pdf` — Ukrainian CV

Want a different look? Say "show me other templates" or "make it one page, no colors".

### 2. `/fill-profile` — your job-site profiles

```
/fill-profile djinni
```

Also: `linkedin`, `workua`, `robotaua`, `dou`, `upwork`.
Claude drafts every field in the chat first, you edit it, then it fills the form in your Chrome and asks before each "Save".

### 3. `/scan-all` — find jobs + dashboard

The first run asks what to look for (keywords, experience, minimum salary, remote/office, which sites). Then Claude:

1. reads job-alert emails in Gmail (if connected, read-only);
2. goes through Djinni, DOU, Work.ua, Robota.ua, Jooble, LinkedIn and Upwork in your Chrome;
3. skips what doesn't fit (and tells you why);
4. scores the rest, writes a report and a tailored CV for every job scoring 4.0+;
5. **opens the dashboard** (`output/dashboard.html`) — a table with scores, statuses, filters and search.

Like a job? Say "**apply to #3**". Claude fills in the application and stops right before the send button. You press it.

Open the dashboard any time by asking Claude "open the dashboard".

---

## Where things live

| File / folder | What's in it |
|---------------|--------------|
| `cv.md` | your CV — the single source of truth; Claude never invents anything beyond it |
| `config/profile.yml` | contacts, target role, salary, language |
| `config/scan-all.yml` | what and where to search (created on the first `/scan-all`) |
| `output/` | CV PDFs and `dashboard.html` |
| `reports/` | a breakdown of every job |
| `data/applications.md` | the tracker of all jobs |

None of these files go to git — your data stays on your computer.

## FAQ

**"Chrome is not connected."** Open Chrome, turn on the Claude extension, open its side panel, then run the command again.

**A site asks me to log in / shows a captcha.** Claude never types passwords or solves captchas. Log in yourself, then say "continue".

**I want to change what it searches for.** Say "also search for Vue", or edit `config/scan-all.yml`.

**I want it to always do something my way** (e.g. "cover letters under 60 words"). Just say so — the rule is saved to `modes/_custom.md` and applies from then on.

**Everything else** (interview prep, cover letters, rejection analysis and more): `/career-ops`.

## License

MIT — see [LICENSE](LICENSE). Original project: [santifer/career-ops](https://github.com/santifer/career-ops).
