# Repository Guidelines

## Project Structure & Module Organization
This repository is a Hugo-based static blog.
- `content/`: Markdown source content (posts and pages). Example: `content/posts/team-collaboration-best-branching-practices.md`.
- `archetypes/`: Content templates used by `hugo new`.
- `layouts/`: Custom templates/overrides (currently minimal).
- `assets/` and `static/`: Source assets and static files copied to output.
- `data/` and `i18n/`: Structured data and translation files.
- `public/`: Generated site output (build artifacts).
- `hugo.toml`: Main site configuration (base URL, menu, theme, params).

## Build, Test, and Development Commands
Use Hugo CLI from repository root:
- `hugo server -D`: Run local dev server and include draft content.
- `hugo`: Build production output into `public/`.
- `hugo new posts/my-post.md`: Create a new post from archetypes.
- `git submodule update --init --recursive`: Initialize theme submodules when needed.

If `themes/` is empty, run the submodule command before local preview/build.

## Coding Style & Naming Conventions
- Write content in Markdown with clear front matter (`title`, `date`, `draft`, `tags`, `categories`).
- Use kebab-case for content filenames: `my-new-post.md`.
- Keep headings sequential (`##` under `#`) and avoid skipping levels.
- Keep configuration in `hugo.toml` consistent and grouped by section (`[params]`, `[menu]`, etc.).
- Prefer ASCII content unless non-ASCII is required.

## Testing Guidelines
There is no automated test suite in this repository. Validation is build-based:
- Run `hugo` and confirm no errors/warnings that block generation.
- Manually verify rendered pages with `hugo server -D`.
- Check links, menu entries, and taxonomy pages (`/tags/`, `/categories/`) before PR.

## Commit & Pull Request Guidelines
Git history shows short, imperative commit messages (for example, `Add welcome content to index.md`). Follow this style:
- Commit format: `Add/Update/Fix <what changed>`.
- Keep commits focused to one logical change.

PRs should include:
- A brief summary of content/config changes.
- Linked issue (if applicable).
- Screenshots for visible UI/theme/layout changes.
- Confirmation that `hugo` build and local preview were checked.

## Configuration Notes
Current `hugo.toml` sets `theme = "even"`. If using a submodule theme (for example `themes/PaperMod`), keep configuration and checked-out theme aligned before merging.
