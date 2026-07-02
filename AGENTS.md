# AGENTS.md

## PLAN AND ASK BEFORE DO

**CRITICAL: NEVER EVER DO ANY ACTION READING, MODIFYING OR RUNNING without explaining the plan.**

Each set of intended actions needs to be explained in the format:

> I understood that `<YOUR ANALYSIS>` so that I plan to `<GOALS YOU PURSUE>` by `<ACTIONS TO BE CONFIRMED>` estimating `<# of ITEMS>` `<ITEMS>` to be worked on. Confirm with go!

**YOU WILL NEVER PROCEED WITHOUT POSITIVE CONFIRMATION by go!**

## Efficiency

- Do NOT do unneeded file lookups based on guessing or assuming typos.
- Do NOT read files you already have contents for.
- Keep summaries to 2-3 lines max unless asked for detail.
- Minimize tool calls. Batch parallel calls. Avoid redundant calls.

## Security

**CRITICAL: NEVER leak credentials, passwords, hashes, internal hostnames, IPs, or any infrastructure details to public platforms (GitHub, Discourse, etc.). Firing offense.**

## Scientific Paper (CEUR-WS)

This project is a scientific paper targeting CEUR Workshop Proceedings
(CEUR-WS). AI support is strictly limited to:

- **Corrections**: spelling and grammar errors
- **Tool support**: creating tables, graphics, and similar formatting/build tasks

AI must NOT generate, rewrite, or contribute original scientific content,
arguments, or prose. All scientific claims, interpretations and conclusions
are the sole responsibility of the authors.

The CEUR-WS "Declaration on Generative AI" (see
<https://ceur-ws.org/GenAI/Policy.html>) must be finalized in `main.tex`
before submission, consistent with this policy.

## GitHub Automation

This project uses GitHub Actions to automatically build the PDF from LaTeX
sources on every push to `main`.

### Structure

- `.github/workflows/build.yml` — CI workflow: checks out repo, builds PDF via `scripts/tex2pdf --github`, and commits the updated PDF if changed
- `scripts/tex2pdf` — LaTeX build script (pdfLaTeX + BibTeX, 3-pass). Supports `--build`, `--check`, `--install`, `--clean`, `--fonts`, `--github`, and `--help`
- `scripts/bash_messages` — colored terminal messaging helper (sourced by `tex2pdf`)
- `.gitignore` — excludes LaTeX build artifacts
- `README.md` — links to the PDF in the repo

### Template

- `ceurart.cls` — official CEUR-WS 1-column document class
- `elsarticle-num-names.bst` — CEUR-WS bibliography style
- `main.tex` — paper skeleton (title, author, empty Abstract + Introduction)
- `wikifairness.bib` — bibliography (currently empty)
