# Branching and Collaboration Workflow

All team members use their own individual GitHub account. The `main` branch always contains reviewed work. Nobody pushes directly to `main`.

## 1. Branch naming

One branch per YouTrack task, named after the task ID and a short description:

```
IBS-<task number>-<short-description>
```

Examples: `IBS-1-user-interviews`, `IBS-6-project-proposal`, `IBS-8-architecture-diagrams`.

## 2. Commit messages

Start with the task ID, then a short imperative description:

```
IBS-6: Add project proposal
IBS-8: Add component diagram
```

## 3. Step-by-step workflow

1. Update main and create a branch from it:
   ```
   git switch main
   git pull
   git switch -c IBS-<n>-<short-description>
   ```
2. Make changes and commit:
   ```
   git add .
   git commit -m "IBS-<n>: <what was done>"
   ```
3. Push the branch:
   ```
   git push -u origin IBS-<n>-<short-description>
   ```
4. When the task is complete (all acceptance criteria are done), open a Pull Request into `main`.
5. In the PR description, write a summary, what was done, the related task, and the acceptance criteria checklist.
6. Another team member reviews the PR, leaves comments if needed, and approves it.
7. After approval, the reviewer clicks **Merge pull request**. The author does not merge their own PR.
8. The author updates the task status in YouTrack.

## 4. Rules

- Do not commit secrets (`.env`, passwords, tokens). Use `.env.example` for templates.
- Keep PRs focused: one task per PR.
- If a PR has review comments, fix them in the same branch and push again. The PR updates automatically.
- Resolve merge conflicts in your branch before asking for review.

## 5. Repository structure

| Folder | Content |
| --- | --- |
| `docs/` | Project documentation (proposal, technology comparison, architecture, workflow) |
| `diagrams/` | Diagram sources (`.mmd`) and exports (`exports/`) |
| `prototype/` | Prototype source code |
| `tests/` | Tests and test documentation |

## 6. Access

| Person | Role in repository |
| --- | --- |
| Arstanbek Fariza | Collaborator (write) |
| Yerzhan Syndaly | Collaborator (write) |
| Nabieva Ulzhan | Owner |
| Supervisor (Alshynov Shyngys Kairatuly) | Collaborator (read or write, as agreed) |
