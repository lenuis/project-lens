<p align="right">
  <a href="./README.en.md">Product overview</a> · <strong>User guide</strong> · <a href="./USAGE.md">中文教程</a>
</p>

# Project Lens User Guide

This quick guide is written for everyday users and vibe coders. You do not need to understand every line of code first. Project Lens connects direction, current work, linked explanations, and AI changes through the real Markdown files in your project.

## 1. Open a project for the first time

1. Install and open Project Lens.
2. Choose “Open Folder” in the upper-right corner and select the real project root.
3. If `PROJECT.md` is missing, Project Lens prepares a minimal project structure and shared rules without replacing the whole content of existing files.
4. If work is already underway but the document structure differs, Project Lens first shows a read-only overview derived from the real Markdown. Choose the actual AI tool below the overview and run “Recheck and organize.”
5. The project, chosen tool, and unfinished organization state remain available after restarting the app.

The overview is a live application view, not an `overview.html` file in your project:

- `PROJECT.md` is the main source of truth for features, phases, tasks, and substeps.
- Requirements, design, technical, and test Markdown provide details that can be opened at an exact location.
- Git changes, file times, tool connection, and rule-sync status are calculated by the app.
- Project Lens does not create an HTML overview that must be maintained; normal use always derives a live view from the real Markdown.

![Project Lens live overview](./assets/project-lens-demo-overview-en.png)

## 2. Understand the workspace

- **Live overview**: four equal columns—Not started, In progress, Pending acceptance, and Completed—show project direction and progress. Open cards with children to enter the next board, then use breadcrumbs to return.
- **Document list on the left**: the real Markdown files in the project. Selecting one opens it in the document area below.
- **Markdown area below**: read or edit one document. A leaf task first shows its source preview; choosing **Open document** opens and highlights the exact linked content. Close the whole dock when it is not needed.
- **Current round / History on the right**: see which files changed for a feature, then confirm or protect accepted work.
- **Tool connection at the lower left**: distinguishes file activity from whether code and project documentation are still in sync.

## 3. Express direction in `PROJECT.md`

Maintain the overview hierarchy only in the root `PROJECT.md`:

```md
## Product features

### User login

#### Email login

- [~] Complete email login [[docs/requirements.md#email-login|Requirements]]
  - [ ] Implement the form
  - [ ] Validate error messages
```

The mapping is simple:

- `###`: product feature.
- `####`: project phase.
- Top-level checkbox: task.
- Indented checkbox: substep.
- `[ ]`: not started; `[~]`: current; `[x]`: done.
- Keep only one `[~]` current step in the project.
- `[[relative/path#heading|Display label]]`: link a task to an exact heading in a real Markdown file.

Selecting a card with children opens another four-column board. Selecting a leaf task shows a source preview and can open the exact linked Markdown location instead of copying every detail into the overview.

![Open the exact linked Markdown](./assets/project-lens-linked-document-en.png)

## 4. Create project documents with clear jobs

Open “Settings → Project Documents.” “Create and enable” means: create a purpose-labelled template only when the file is missing, then allow AI tools to maintain it within the project rules. Project Lens does not create every template automatically and does not move or delete equivalent files you already have.

| Document | Purpose | When to use it |
| --- | --- | --- |
| `PROJECT.md` | Current direction, phases, tasks, and substeps | Required; cannot be disabled |
| `AGENTS.md` | Shared rules for Project Lens and AI tools | Managed by Project Lens |
| `CHANGELOG.md` | User-facing additions and changes for each release | Recommended by default |
| `docs/decisions.md` | Important product or technical choices and rationale | When a decision has lasting impact |
| `docs/architecture.md` | System boundaries, module relationships, and constraints | Medium or large projects |
| `docs/frontend.md` | Frontend structure, state, components, and UI conventions | Frontend projects |
| `docs/backend.md` | Services, jobs, permissions, and error handling | Backend projects |
| `docs/api.md` | Endpoints, requests, responses, and compatibility | Projects with APIs |
| `docs/data.md` | Data models, fields, mapping keys, and lifecycle | Projects with persistent data |
| `docs/testing.md` | Test scope, results, and remaining risks | Recommended before release |
| `docs/migrations.md` | Database, API, or configuration migration steps | When migration is required |
| `SECURITY.md` | Security policy and vulnerability handling | Recommended for public products |
| `CONTRIBUTING.md` | Team or open-source contribution rules | Collaborative projects |
| `.github/PULL_REQUEST_TEMPLATE.md` | Scope, validation, and risk template for PRs | GitHub collaboration |
| `.github/ISSUE_TEMPLATE/*.md` | Issue and feature-request templates | GitHub collaboration |
| `PROJECT_KEYS.md` | Local values for keys needed by this project | When secrets need purpose-based approval |

### Mark implementation state in non-checklist sections

Feature descriptions, design requirements, technical sections, and steps that are not written as checkboxes can keep a state immediately below an H2, H3, or H4 heading:

```md
## Booking form design
<!-- project-lens:status=todo -->

## Login API
<!-- project-lens:status=active -->

## Data migration plan
<!-- project-lens:status=done implemented=2026-08-18T10:00:00+08:00 -->
```

Project Lens displays **Not implemented**, **Implementing**, or **Implemented - local time**. Write the completion time only after real implementation and verification; never invent a time for an old section. Checkbox tasks keep using `[ ] / [~] / [x]` and their own task completion time.

Do not create `GIT_LOG.md`: Git is the real commit history. `CHANGELOG.md` only records what a formal release changes for users.

See the [complete English example project](./examples/en/README.md) for a practical structure.

## 5. Choose which documents AI may maintain

- `PROJECT.md` is the required source of project direction and cannot be disabled.
- `AGENTS.md` is managed by Project Lens, not by the ordinary document toggle.
- Other Markdown files can be enabled or disabled in “Settings → Project Documents.”
- Disabled means AI tools should not modify the file; the user can still read and edit it.
- Equivalent documents in sensible existing locations are preserved instead of being moved or duplicated.

## 6. Keep AI tools aligned with the rules

Project Lens prepares lightweight entry points for different AI tools, while shared truth remains in two places:

- `PROJECT.md`: project direction and current work.
- `AGENTS.md`: shared Project Lens working rules.

Tools should reread both files when work begins and before claiming completion. Project Lens also compares code activity with documentation updates:

- **Connected**: a tool is reading or writing project files.
- **Rule sync normal**: code, the current step, and related Markdown remain aligned.
- **Needs sync**: code keeps changing while project steps or explanations have not been updated.

Tools with hook support receive faster reminders. Other editors and AI tools can still be checked through real file activity.

### Organize a project that is already underway

1. Choose the AI tool you actually use below the overview. Project Lens does not guess from process names.
2. Select **Recheck and organize**. Project Lens prepares the rules, request, and complete instruction; it never sends a hidden background task.
3. Copy the instruction into an AI conversation that already has this project open.
4. The AI rereads existing Markdown, classifies requirement, design, technical, test, and release documents, and aligns the primary direction in `PROJECT.md`.
5. The handoff collapses after copying. Tool choice, the organization request, and completion state remain isolated per project and survive restarts.

## 7. Confirm and protect accepted features

When a feature matches your expectations, confirm and protect it from the Current Round panel. Protection is not an absolute lock: a later AI change must first describe its scope, affected files, and risks, then request one-time user approval.

Confirmed entries move into that project's own History and never mix with another project.

![Confirm and protect a feature](./assets/project-lens-feature-protection-en.png)

## 8. Approve project secrets by purpose

Never place real secrets in ordinary documentation, chat, or Git. Use this flow instead:

1. Create `PROJECT_KEYS.md` from “Settings → Project Documents.”
2. Enter values locally; AI cannot read this file by default.
3. AI requests only the key name, purpose, destination file, and destination field—never the value.
4. Review and approve the request in Project Lens.
5. Project Lens writes the value only to the exact approved location in the current project.

The destination must remain inside the current project and cannot be Git-tracked, a symbolic link, or an outside path.

![Approve a project key by purpose](./assets/project-lens-key-approval-en.png)

## 9. Edit, search, and locate Markdown

- Markdown can be edited directly in Project Lens and is saved automatically; a short confirmation appears after a successful save.
- Use the search button or `Command/Ctrl + F` to search all project Markdown.
- Selecting a result opens the file and jumps to the matching location.
- Right-click a document to choose a compatible local Markdown app or delete an eligible document.
- Highlights opened from tasks, changes, or search results are app state only and are never written into Markdown.

## 10. A practical daily workflow

1. Open the project and check the current step and overall direction.
2. Select a task and read its linked requirement, design, or technical note.
3. Let the AI tool work from `PROJECT.md` and `AGENTS.md`.
4. Review the feature and files shown in Current Round.
5. Validate the result; confirm and protect accepted work, or keep editing and ignore the record.
6. Update `CHANGELOG.md` for a formal release while Git remains the real commit history.

## 11. Update the app or remove a project

- Use “Settings → About” to check for updates. Download and replace the app; existing project files and records remain intact.
- Hover an existing project in the project switcher to remove it from the list.
- You can remove only the list entry or also clear Project Lens runtime records for that project. Real project files are never deleted.

## Need help?

- [Download the latest release](https://github.com/lenuis/project-lens/releases/latest)
- [Report an issue or share feedback](https://github.com/lenuis/project-lens/issues)
- [Explore the complete English example](./examples/en/README.md)
- [阅读中文教程](./USAGE.md)
