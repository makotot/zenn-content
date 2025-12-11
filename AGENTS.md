# Repository Guidelines

## Project Structure & Module Organization

- `articles/`: Single-file articles in Markdown (Zenn ID filenames like `xxxxxxxxxxxx.md`). Use the CLI to create new entries; do not rename existing files.
- `books/<book-id>/`: Book content with chapter files such as `0.introduction.md`, `1.<topic>.md`, and a `config.yaml` for metadata.
- Tooling/config: `.textlintrc.json` (Textlint rules), `dprint.json` (formatter), `package.json` (scripts), `.github/` (CI, if present).

## Build, Test, and Development Commands

- `pnpm install`: Install dev dependencies (Node managed via Volta `24.11.1`).
- `pnpm preview`: Launch local Zenn preview to review articles/books.
- `pnpm run new:article`: Scaffold a new article with correct frontmatter.
- `pnpm run new:book`: Scaffold a new book directory and files.
- `pnpm run textlint` or `pnpm run lint`: Lint Markdown in `articles/*.md` using Japanese preset rules.
- `pnpm run format`: Format Markdown/JSON/TOML with dprint.

## Coding Style & Naming Conventions

- Write in Markdown. Prefer descriptive headings and concise sections. Use fenced code blocks with language tags (e.g., ```ts).
- Keep Zenn frontmatter minimal and accurate (title, topics, type). Ensure topics/tags align with the core content. Create files via the CLI to ensure correct structure.
- Do not change hashed filenames for articles or book directory IDs.
- Japanese prose follows Textlint rules; keep sentence length under 160 characters where practical.
- Run `pnpm run format` before committing to keep diffs clean.

## Testing Guidelines

- Treat linting as tests: run `pnpm run lint` and fix all errors/warnings before opening a PR.
- Manually preview with `pnpm preview` and verify links, images, code blocks, and overall layout.

## Content Quality Checklist

- Reader-first: define the target persona and assumed prior knowledge.
- Before reading: articulate the reader’s concrete pain points.
- After reading: show how the content resolves those pains with clear takeaways/actions.
- Title–content fit: the title sets accurate expectations and matches the pain resolved.
- Frontmatter topics/tags: ensure they reflect the central content; remove irrelevant or overly broad tags.

## Commit & Pull Request Guidelines

- Commits: imperative mood and scoped, e.g., `article: add React Aria table notes`, `book: update chapter 1`, `chore: format markdown`.
- PRs: include a clear description, affected paths (`articles/...`, `books/...`), screenshots or preview notes if helpful, and linked issues. Ensure lint/format pass.

## Agent-Specific Notes

- Make minimal, targeted changes; avoid renaming content files. Update docs if scripts or structure change.
- When adding content, prefer CLI scaffolding and run lint + format prior to submission.
