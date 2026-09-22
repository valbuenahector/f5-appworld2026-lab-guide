# AppWorld 2026 Lab Guide — "Code. Secure. Repeat."

Student-facing lab guide and supporting assets for the AppWorld 2026 hands-on lab. Sibling repo to [`ai-generated-app`](../ai-generated-app) — that repo is the vulnerable target application; this repo is the guide participants follow while attacking and then securing it.

Tracked in the F5 workspace at `projects/f5/appworld-lab-guide/`.

## What this lab covers

A two-hour lab walking through an AI-assisted DevSecOps workflow:

1. **Module 0** – Intro & environment orientation (verify VSCode Server, GitLab, F5XC tenant access)
2. **Module 1** – AI-generated vulnerable app (vibe coding, demo only)
3. **Module 2** – Deploy and secure the F5 AI-generated app via GitLab CI/CD + initial security controls
4. **Module 3** – Advanced runtime security with F5XC WAAP
5. **Module 4** – F5XC Web App Scanning (WAS) as a DAST tool

The loop the lab reinforces: **Code (AI-assisted) → Commit → Scan (SAST/WAS/API) → Protect (DAST/WAAP/API Sec/Bot/Anomaly) → Improve → Repeat.**

## Files

| File | Purpose |
|------|---------|
| [`lab-guide.md`](lab-guide.md) | The student-facing guide — step-by-step tasks per module, with image references into `Appworld2026/` |
| [`lab.txt`](lab.txt) | Lab overview, objectives, and table of contents — source outline for `lab-guide.md` |
| [`prompts.txt`](prompts.txt) | Working scratchpad of prompts used to draft/update `lab-guide.md` sections — not student-facing content |
| [`Appworld2026/`](Appworld2026) | Screenshot/image assets referenced by `lab-guide.md`, one subfolder per module (`Module0`–`Module4`) |

## Step notation

In `lab-guide.md`, steps are tagged:

- **USER:** — the student performs this step
- **AUTO:** — an automated flow runs (e.g. a CI/CD pipeline) and the step is a visualization/checkpoint, not a manual action

## Related repos

- [`ai-generated-app`](../ai-generated-app) — the intentionally-vulnerable Flask app deployed and secured during the lab
