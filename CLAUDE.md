# This checkout is a simplified fork of career-ops

Three commands cover the whole flow; offer them first, before the full career-ops menu:

| Command | Skill | What it does |
|---------|-------|--------------|
| `/cv` | `.claude/skills/cv/` | Builds `cv.md` + `config/profile.yml` from the user's CV/LinkedIn/answers, renders `output/General/CV.pdf` |
| `/fill-profile <site>` | `.claude/skills/fill-profile/` | Fills LinkedIn / Djinni / Work.ua / Robota.ua / DOU / Upwork profiles in the user's Chrome, every save confirmed |
| `/scan-all` | `.claude/skills/scan-all/` | Searches every enabled site through Claude in Chrome, evaluates, updates the tracker, opens `output/dashboard.html` |

- **First-run setup is yours, not the user's.** Before any of the three commands, if `node_modules/` is missing run `npm install`, then `npx playwright install chromium` (needed for PDFs). If `node` itself is missing, tell the user to install the LTS from https://nodejs.org and restart Claude Code. Say in one line what you're installing; don't ask them to run commands.
- New user (no `cv.md`) → start with `/cv`, whatever they asked.
- Dashboard: `node dashboard-html.mjs --open` (also `npm run dashboard`).
- **Updates:** this fork changes system-layer files (`README.md`, `CLAUDE.md`, `.claude/skills/`, `templates/`), which `update-system.mjs` would overwrite with upstream copies. So in this fork, skip AGENTS.md → "Update Check" at session start and never run `update-system.mjs apply`. Updates come with `git pull` from the fork.
- Reply in the user's language (Ukrainian when they write Ukrainian).

@AGENTS.md
