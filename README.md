# IEEE Alexandria CSC - Projects

This repository contains the automated evaluation workflows used by the IEEE Alexandria Computer Society Chapter educational platform.

Students complete programming projects locally and submit their solutions using the IEEE CLI. The CLI communicates with the backend, which dispatches the appropriate GitHub Actions workflow in this repository to evaluate the submission.

Each project is divided into multiple phases, allowing students to progress step by step while receiving automated feedback.

---

# Repository Structure

```
.
├── .github
│   └── workflows
│       ├── first_github_repo.yml
│       ├── ...
│
├── git_github
│   ├── phase1
│   │   └── README.md
│   ├── phase2
│   │   └── README.md
│   └── ...
│
└── ieee_cli.exe
```

## `.github/workflows`

Contains the GitHub Actions workflows responsible for evaluating student submissions.

Each workflow listens for a specific `repository_dispatch` event corresponding to a project phase.

Example:

```yaml
on:
  repository_dispatch:
    types:
      - first_github_repo
```

The backend dispatches the appropriate event based on the submitted phase.

---

## Project Directories

Each project has its own directory.

Example:

```
git_github/
```

Inside each project are the available phases.

Each phase contains a `README.md` describing:

- Learning objectives
- Requirements
- Submission instructions
- Expected output
- Notes and hints

Example:

```
git_github/
├── first_github_repo/
│   └── README.md
├── branches/
│   └── README.md
└── merge_conflicts/
    └── README.md
```

---

## IEEE CLI

```
ieee_cli.exe
```

This is the command-line application used by students.

Using the CLI, students can:

- Log in
- Browse available challenges
- View project phases
- Submit GitHub repositories
- Monitor evaluation status
- View submission results

The CLI communicates with the backend only.

Students never interact with GitHub Actions directly.

---

# Submission Flow

```
Student
    │
    ▼
IEEE CLI
    │
    ▼
Backend API
    │
repository_dispatch
    │
    ▼
GitHub Actions Workflow
    │
Runs evaluation
    │
Creates report
    │
    ▼
Backend Callback
    │
    ▼
Submission Updated
```

---

# Creating a New Project

1. Create a new project directory.

Example:

```
python_basics/
```

2. Create one directory for each phase.

Example:

```
python_basics/

├── variables/
│   └── README.md

├── loops/
│   └── README.md

└── functions/
    └── README.md
```

3. Create a workflow inside:

```
.github/workflows/
```

4. Register the workflow to listen for the corresponding phase tag.

Example:

```yaml
on:
  repository_dispatch:
    types:
      - python_variables
```

The backend will dispatch this event whenever a student submits that phase.

---

# Workflow Requirements

Every evaluation workflow must:

- Clone the student's repository.
- Run any required validation or tests.
- Generate a JSON report.
- Upload the report as an artifact.
- Send the report back to the backend.

The callback step **must always execute**, even if earlier steps fail.

Use:

```yaml
if: always()
```

for the callback step.

The checkout step should use:

```yaml
continue-on-error: true
```

to ensure an error report can still be generated if the repository cannot be cloned.

---

# Report Format

Every workflow must generate:

```
reports/<submission_id>.json
```

Example (Passed):

```json
{
    "submission_id": "...",
    "passed": 5,
    "total": 5,
    "results": {
        "message": "All tests passed."
    }
}
```

Example (Failed):

```json
{
    "submission_id": "...",
    "passed": 3,
    "total": 5,
    "results": {
        "message": "Two test cases failed."
    }
}
```

Example (Evaluation Error):

```json
{
    "submission_id": "...",
    "passed": 0,
    "total": 0,
    "error": "Repository could not be cloned."
}
```

---

# Private Test Repositories

Challenge authors may keep their evaluation scripts and test cases in a **private GitHub repository**.

This allows students to submit public repositories while keeping the grading logic and hidden test cases confidential.

Example:

```yaml
- name: Checkout student submission
  uses: actions/checkout@v4
  with:
    repository: ${{ github.event.client_payload.student_repo_link }}
    path: student-code

- name: Checkout private tests repository
  uses: actions/checkout@v4
  with:
    repository: owner/private-tests
    token: ${{ secrets.PRIVATE_REPO_TOKEN }}
    path: tests

- name: Run evaluation
  run: |
    python3 tests/fibonacci.py \
      ./student-code \
      ${{ github.event.client_payload.submission_id }}
```

The private repository may contain:

- Hidden test cases
- Evaluation scripts
- Docker environments
- Build tools
- Helper libraries
- Input/output datasets
- Any other resources required for grading

The private repository is cloned using a Personal Access Token stored as a GitHub Secret.

Example:

```yaml
token: ${{ secrets.PRIVATE_REPO_TOKEN }}
```

This token should have **read access** to the private repository only.

Keeping evaluation logic in a private repository prevents students from viewing hidden test cases while allowing challenge authors to update tests independently of student-facing documentation.

---

# Backend Status Rules

The backend determines the final submission status automatically.

| Report | Final Status |
|---------|--------------|
| `error` present | `ERROR` |
| `passed < total` | `FAILED` |
| `passed == total` and `total > 0` | `PASSED` |
| `total == 0` without an error | `ERROR` |

Workflow authors should only report evaluation results. The backend is responsible for assigning the final submission status.

---

# Supported Evaluation Methods

Challenge authors are free to implement their evaluation using any language or tooling, including:

- Bash
- Python
- Go
- Java
- C/C++
- Rust
- Docker
- Node.js
- Unit testing frameworks
- Custom scripts

The only requirement is that the workflow produces the required report and sends it back to the backend.

---

# Contributing

When adding a new challenge or phase:

1. Create the phase documentation.
2. Implement the evaluation workflow.
3. Ensure the workflow generates a valid report.
4. Verify that callbacks are always sent to the backend.
5. Test the workflow before merging.