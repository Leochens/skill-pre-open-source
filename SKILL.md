---
name: pre-open-source
description: Systematically prepare a repository or project before making it public/open source. Use when Codex is asked to do pre-open-source readiness work, open-source preparation, repo sanitization, README/LICENSE/CONTRIBUTING/CODE_OF_CONDUCT creation, issue/PR templates, .gitignore hardening, sensitive-content checks, license selection guidance, CI/release readiness, or risk review before publishing to GitHub/GitLab/Gitee.
---

# Pre-Open Source

## Goal

Prepare a project for public release by scanning the repository, identifying risks, recommending fixes, generating the minimum necessary open-source documents/configuration, and optionally applying safe changes after confirmation.

## Operating Rules

- Treat open-sourcing as a security and product-readiness task, not only documentation cleanup.
- Start read-only when the user asks for an assessment, audit, review, or "看看能不能开源".
- Do not delete files, rewrite Git history, publish, push, create releases, or expose suspected secrets without explicit user confirmation.
- Do not print secrets in chat. Redact tokens, keys, private URLs, emails, and credentials in findings.
- Prefer a clean migration to a new public repository when history may contain secrets, proprietary files, or messy private work.
- State that license guidance is practical engineering guidance, not legal advice.

## Workflow

1. **Scan the project**
   - Inspect repository structure, key entrypoints, package/build files, docs, config files, `.gitignore`, templates, CI files, license files, and Git state.
   - Check whether the project appears to contain private assets, environment files, generated outputs, build artifacts, logs, datasets, credentials, or internal documentation.
   - If Git history is relevant, inspect recent commits and known risky paths without dumping sensitive content.

2. **Clarify intent**
   - Ask only for missing high-impact context: project name, one-sentence description, target audience, intended license family, public/private boundaries, and whether edits should be applied automatically.
   - If the user already supplied enough context, proceed and mark unknowns as assumptions.

3. **Assess risks**
   - Report risks by severity: blockers, should-fix-before-release, nice-to-have.
   - Cover sensitive content, license ambiguity, missing docs, build/test uncertainty, dependency/security concerns, and repository hygiene.
   - Use `references/checklist.md` when a full readiness pass is requested.

4. **Confirm the plan**
   - Before changing files, summarize the proposed generated/modified files and any destructive or irreversible action.
   - For safe documentation/config additions, proceed when the user asked you to prepare or implement.
   - For history rewriting, deleting files, publishing, pushing, or public release setup, require explicit confirmation.

5. **Generate and apply**
   - Generate only the files that match the project and user intent.
   - Use existing project tone, language, package manager, test commands, and framework conventions.
   - Prefer concrete placeholders such as `<PROJECT_NAME>` only when the value is genuinely unknown.
   - Keep docs honest: do not claim tests, CI, security scans, API stability, or compatibility that was not verified.

6. **Final check**
   - Re-scan changed files for accidental sensitive content.
   - Run focused formatting, docs lint, build, or test commands when available and proportionate.
   - Deliver a concise readiness summary with remaining blockers and exact next steps.

## Default Deliverables

Generate or improve these when appropriate:

- `README.md`: project intro, features, quick start, usage, configuration, examples, FAQ/troubleshooting, contribution note, license note.
- `LICENSE`: choose MIT, Apache-2.0, BSD-3-Clause, GPL-3.0, AGPL-3.0, or a user-specified license; explain tradeoffs briefly before applying.
- `.gitignore`: cover language/framework/tooling, dependency directories, build outputs, logs, IDE files, OS files, temp files, local env files, and large generated artifacts.
- `CONTRIBUTING.md`: setup, branch/commit expectations, tests, issue/PR flow, code style, release process.
- `CODE_OF_CONDUCT.md`: include only if requested or suitable for a community-facing project; use Contributor Covenant as a common default.
- `.github/ISSUE_TEMPLATE/*` and `.github/PULL_REQUEST_TEMPLATE.md`: bug report, feature request, and PR checklist.
- `CHANGELOG.md`: use Keep a Changelog style when the project has versions or release notes.
- `SECURITY.md`: vulnerability reporting path and supported versions when the project expects external users.
- CI config: add minimal build/test/lint workflows only when requested and compatible with the repo.
- Readiness report/checklist: summarize what is ready, what changed, what remains risky, and what should be verified before publishing.

## Sensitive Content Strategy

When sensitive content is suspected:

1. Stop broad generation work until the risk is triaged.
2. Identify the file/path/category and reason without exposing the secret value.
3. Recommend immediate rotation/revocation for exposed keys, tokens, passwords, certificates, or private endpoints.
4. Move required configuration into environment variables and provide `.env.example` with comments.
5. Add or strengthen `.gitignore` so local secrets, logs, data dumps, build outputs, and private assets are excluded.
6. If history contains sensitive content, recommend the safer clean-repo migration path first:
   - Create a new private clean repository.
   - Copy only safe source files and generated public docs.
   - Recreate needed commits from the clean tree.
   - Validate again before making public.
7. Use destructive history rewrite tools such as `git filter-repo` or BFG only after explicit confirmation, a backup plan, and clear communication that clones/forks/tags may still contain old data.

## License Selection Guidance

- MIT: simple permissive default for broad reuse.
- Apache-2.0: permissive with explicit patent grant; often suitable for companies and SDKs.
- BSD-3-Clause: permissive with attribution and non-endorsement language.
- GPL-3.0: copyleft for projects that require derivative works to remain open.
- AGPL-3.0: stronger copyleft for network/server software.
- Proprietary or source-available: use only if the user does not actually want open-source terms.

Always ask for confirmation before writing a license if ownership, employer rights, third-party code, or intended commercialization is unclear.

## User Experience

- Present readiness as a checklist with status labels: `Ready`, `Needs work`, `Blocked`, `Unknown`.
- Keep recommendations actionable: include file paths, reasons, and the smallest next step.
- Separate "can publish now" from "should improve soon".
- If asked to auto-execute, make safe doc/config changes directly, then summarize exactly what changed.

## Reference

- For the complete checklist derived from the pre-open-source preparation flow, read `references/checklist.md`.
