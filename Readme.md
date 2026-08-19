# Network Change Set — IBM App Connect Enterprise (ACE) Project

This repository contains the IBM App Connect Enterprise (ACE) integration project used by the team. It's built and maintained using the **IBM App Connect Enterprise Toolkit**.

## Project Structure

| Folder | Purpose |
|---|---|
| `.git` | Git metadata for this repository. Do not edit manually. |
| `.metadata` | Eclipse/ACE Toolkit workspace metadata (project settings, build state, etc.). This is workspace-specific — **do not commit personal workspace changes here** if they're local-only preferences. |
| `Network_Change_Set` | The main ACE Application project. Contains the message flows, subflows, and integration logic for the network change process. |
| `SFTP_Policy` | An ACE Policy project. Contains the policy configuration controlling SFTP connection/behaviour used by the integration server(s). |
| `Shared_Resource_Lib` | An ACE Shared Resource Library. Contains common code, ESQL, schemas, or resources shared across the flows in `Network_Change_Set` and other projects. |
| `Readme.md` | This file — project overview and contribution guidelines. |

> If you add a new project/folder (e.g. a new Library, Policy Project, or Test Project), please add a row to the table above describing its purpose.

## ⚠️ Branching Rules — Read Before You Push

**No one pushes directly to `main`.** This includes small fixes, "quick" changes, or config tweaks. `main` is protected and reflects the current stable state of the integration — it must only be updated through a **reviewed Pull Request (PR)**.

Workflow for everyone on the team:

1. Create your own branch off `main`.
2. Make your changes on that branch.
3. Push your branch to the remote.
4. Open a Pull Request into `main`.
5. Get at least one review/approval before merging.

### Branch Naming Convention

All branches must follow this format:

```
<name of person/s>/<feature>
```

**Examples:**

```
john/sftp-retry-logic
john-sarah/network-change-validation
priya/fix-esql-null-check
```

Use lowercase, hyphens instead of spaces, and keep the feature part short and descriptive.

## Getting Started: Clone → Branch → Push → PR

Below is the full command sequence from cloning the repo to opening a Pull Request.

### 1. Clone the repository

```bash
git clone https://github.com/<your-org>/<your-repo>.git
cd <your-repo>
```

### 2. Make sure you're up to date with main

```bash
git switch main
git pull origin main
```

### 3. Create your branch

```bash
git switch -c john/sftp-retry-logic
```

### 4. Make your changes

Open the project in the **App Connect Enterprise Toolkit**, make your changes to the relevant project(s) (e.g. `Network_Change_Set`, `SFTP_Policy`, `Shared_Resource_Lib`), and save.

### 5. Stage and commit your changes

```bash
git add .
git commit -m "Add retry logic to SFTP policy for failed connections"
```

### 6. Push your branch to the remote

```bash
git push -u origin john/sftp-retry-logic
```

### 7. Open a Pull Request

- Go to the repository on GitHub (or your Git provider).
- You'll see a prompt to open a PR for the branch you just pushed — click it, or go to **Pull Requests → New Pull Request**.
- Set the base branch to `main` and compare branch to your feature branch (e.g. `john/sftp-retry-logic`).
- Add a clear title and description of your change.
- Request a review from at least one teammate.

### 8. After approval — merge

Merging is done through the PR interface (not locally pushed to `main`). Once approved:

- Use **Squash and merge** (or your team's preferred merge strategy) on the PR page.
- Delete the feature branch after merging to keep things tidy.

### 9. Sync your local main after merge

```bash
git switch main
git pull origin main
```

---

**Summary rule of thumb:** if you're about to run `git push origin main`, stop — you're on the wrong branch. Branch, push, PR, review, merge.
