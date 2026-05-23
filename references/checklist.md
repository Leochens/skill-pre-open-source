# Pre-Open Source Readiness Checklist

Use this when a user requests a complete readiness pass or when the repository has unclear public-release risk.

## 1. Project Basics

- Confirm project name and short description.
- Write a detailed project description: background, goal, value, and scope.
- Identify keywords, theme tags, and likely users: end users, developers, researchers, or operators.
- Note maturity: prototype, internal tool, library, production app, research artifact.

## 2. README

- Include project overview and positioning.
- List features and non-goals.
- Provide installation, setup, environment variables, and usage.
- Add screenshots, diagrams, CLI examples, API examples, or demo links when available.
- Add directory structure when it helps navigation.
- Add troubleshooting/FAQ when setup is non-trivial.
- Add support and contribution channels.
- Add license note.
- Use the project's language needs: Chinese, English, or bilingual.

## 3. License

- Ask for or infer the preferred license family.
- Compare likely options: MIT, Apache-2.0, BSD-3-Clause, GPL-3.0, AGPL-3.0.
- Check whether third-party code, datasets, fonts, media, generated assets, or templates impose license constraints.
- Generate `LICENSE` only after the user confirms the license choice or the project clearly states it.

## 4. Sensitive Content

- Check local secret files: `.env`, `.env.*`, `.secrets`, `config.*`, credentials, certificates, SSH keys, private keys, tokens, cookies, local database files.
- Search for API keys, tokens, passwords, private URLs, cloud credentials, webhook URLs, and service account files.
- Check logs, screenshots, recordings, exported data, test fixtures, and seed data for real user information.
- Check generated files and build artifacts for embedded secrets or private paths.
- Check Git history, tags, and branches when the repo has private development history.
- Check third-party dependencies or vendored files for private/commercial restrictions.
- Redact findings and recommend rotation for anything that may have been committed.

## 5. `.gitignore`

- Cover dependency directories, build outputs, caches, logs, editor/IDE files, OS files, temp files, local config, credentials, databases, generated media, and large artifacts.
- Match the actual stack: Node, Python, Rust, Go, Java, Swift, Electron, Next.js, Vite, Bun, Docker, mobile, or monorepo tooling.
- Avoid ignoring source files, public examples, or required lockfiles by accident.

## 6. Contributing

- Explain how to set up the project locally.
- Document branch, commit, formatting, lint, and test expectations.
- Explain issue, discussion, and pull request flow.
- Include a lightweight review and release process.
- Generate `CONTRIBUTING.md` when external contributions are expected.

## 7. Code of Conduct

- Recommend a code of conduct for public community projects.
- Use Contributor Covenant as the common default when appropriate.
- Generate `CODE_OF_CONDUCT.md` only if it fits the project or the user requests it.

## 8. Issue and PR Templates

- Add bug report and feature request templates.
- Add PR checklist: summary, linked issue, tests, screenshots/logs for UI/runtime changes, docs updates, breaking changes.
- Use `.github/ISSUE_TEMPLATE/` and `.github/PULL_REQUEST_TEMPLATE.md` by default for GitHub repositories.

## 9. Tests and Temporary Docs

- Identify Markdown drafts, scratch notes, experiment logs, temporary screenshots, and local planning docs that should not be public.
- Check whether tests contain secrets, real user data, private URLs, or paid API keys.
- Recommend keep/modify/delete decisions with reasons.

## 10. Examples and Demos

- Provide minimal usage examples.
- Add safe sample configuration.
- Add screenshots or GIFs only when they do not reveal private content.
- Add a demo path only if it can run without secrets or paid/private infrastructure.

## 11. Project Structure and Quality

- Confirm directory structure is understandable.
- Check for empty files, obsolete files, unused scripts, stale migration files, and dead docs.
- Check code style config and formatter/linter availability.
- Run focused tests or builds when possible.

## 12. Documentation Completeness

- Check API docs, CLI docs, config docs, architecture notes, changelog, and versioning policy.
- Recommend `CHANGELOG.md` when releases are expected.
- Recommend semantic versioning when users will depend on package versions or APIs.

## 13. Security and Compliance

- Run or recommend dependency/security scans when appropriate.
- Check license compatibility.
- Check for privacy-sensitive content and real user data.
- Check whether the project needs `SECURITY.md` or vulnerability reporting instructions.

## 14. CI/CD

- Add minimal CI only when requested or clearly useful.
- Prefer build/test/lint checks matching existing package scripts.
- Add badges only when the target services and workflow names are known.

## 15. Release and Promotion

- Recommend a target platform: GitHub, GitLab, Gitee, package registry, docs site, or release page.
- Suggest release notes, tags, package metadata, topics, and README badges.
- Keep promotion advice practical and non-spammy.

## Final Delivery Format

Use this structure for a complete report:

```markdown
## Open Source Readiness

Status: Ready | Needs work | Blocked | Unknown

### Blockers
- [path/category] Reason and smallest next step.

### Recommended Fixes
- [path/category] Reason and suggested change.

### Generated/Changed Files
- path: purpose

### Safe To Publish After
- concrete verification steps
```
