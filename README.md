# Copilot Training Site

Static training site for Microsoft 365 Copilot in a HIPAA-covered workplace.
Six modules, each ending in a Microsoft Forms quiz. No build step, no JavaScript,
no data collected on the site itself.

## Structure

```
index.html                      hub page
modules/m01-fundamentals.html   Copilot fundamentals
modules/m02-word-outlook.html   Word & Outlook
modules/m03-excel-teams.html    Excel & Teams
modules/m04-copilot-chat.html   Copilot Chat
modules/m05-phi-and-ai.html     PHI & AI rules (required)
modules/m06-hipaa-refresher.html HIPAA refresher (required)
assets/styles.css               shared stylesheet
```

## Setup

1. Create a **public** GitHub repository and push these files to the `main` branch root.
2. Repo → Settings → Pages → Source: **Deploy from a branch**, branch `main`, folder `/ (root)`.
3. The site publishes at `https://<username>.github.io/<repo>/` within a few minutes.

## Wire up the quizzes

Each module page has one placeholder link:

```
REPLACE_WITH_FORMS_URL_M01 ... REPLACE_WITH_FORMS_URL_M06
```

1. In Microsoft Forms (work account), create one quiz per module. Use **quiz** type so
   scores are automatic. In Form settings, restrict to **people in my organization** and
   enable **record name** — that's what makes completions attributable.
2. Copy each form's share link and replace the matching placeholder. Search the repo for
   `REPLACE_WITH_FORMS_URL` to confirm none remain.
3. Responses live in Forms / an Excel workbook inside your tenant. Completion data never
   touches this public repo.

## Content rules for this repo (it is public)

Before every commit, confirm the change contains:

- No PHI or any of the 18 HIPAA identifiers, including in screenshots and image metadata
- No real patient scenarios — synthetic examples only
- No internal system names, URLs, tenant names, or org charts
- No staff names or contact details (route everything to role titles: "Privacy Officer")

If a commit ever slips, rewriting git history is required, not just a follow-up commit —
public repo history is permanently scrapeable.

## Maintenance

- Microsoft Learn links are verified as of July 2026; re-check them quarterly.
- Retrain triggers under HIPAA: material policy change, new tools, new roles. Update the
  relevant module and re-issue its quiz.
