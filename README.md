# PolyGoat i18n Auditor

An AI agent that audits a GitHub repository containing a React application for internationalization (i18n) readiness. It maps the application, checks it against audit criteria based on an expanded version of LILT's software internationalization readiness checklist, and produces a report with findings (location, severity, evidence) and a prioritized action plan for making the codebase ready for localization with i18next.

> **Status:** in active development. The code is in a private repository; a walkthrough is available on request.

## Why

Internationalization problems are cheap to fix early and expensive to fix late. Hardcoded strings, concatenated sentences, locale-unaware dates and numbers, and layouts that break with longer text usually surface only when the first translation lands. This auditor finds them before that, with evidence a developer can act on.

## How it works

1. **Audit:** map the application and collect evidence.
2. **Recommendations:** prioritized, actionable fixes.
3. **Remediation (later):** agents apply approved fixes and open pull requests for review.

Before auditing, the auditor checks whether a repository is in scope by reading only its package.json files, then builds a repository profile (stack, structure, existing i18n setup). Nothing from the audited repository is ever run.

## Scope

The scope is defined by what the auditor can **fix reliably**, not only by what it can read.

| Level | What it covers |
|---|---|
| **Fully supported:** audit, recommendations, automated fixes | React web apps in JavaScript or TypeScript; client-side SPAs (Vite, Create React App); target library react-i18next |
| **Audit only:** findings and general recommendations | Next.js and other server-rendered React; repositories using another i18n library (react-intl, LinguiJS); backend repositories (read-only checks) |
| **Out of scope** | Vue, Angular, Svelte, React Native, plain HTML sites, native mobile apps |

Out-of-scope repositories get a short report stating what was found, instead of a partial audit.

**Why this scope:** one pattern set (JSX, hooks, react-i18next) keeps scanners, agent prompts and fixes consistent; one target library means every automated change can be validated the same way (keys exist, placeholders match, build passes); new frameworks can be added later as their own modules.

**Status:** in active development. Working today: scope detection from a GitHub URL, safe cloning, and repository profiling. The agent-driven audit is in progress. The code is in a private repository; a walkthrough is available on request.

## Built with

Python, uv, pytest, LLM agents. Background: 10+ years in localization and translation technology.

## Contact

Leandro Ardiles · [LinkedIn](https://www.linkedin.com/in/<your-handle>) · leand.ardiles@gmail.com
