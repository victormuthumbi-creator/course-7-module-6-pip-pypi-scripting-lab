# Course 7 Module 6 — Pip, PyPI & Scripting Lab

A small OOP + CLI project built with Python's `argparse` and standard
library File I/O.

## Contents

- `generate_log.py` — writes a list of log entries to a timestamped file
  (`log_YYYYMMDD.txt`). Raises `ValueError` on non-list input, handles empty
  lists, and prints a confirmation message.
- `test_generate_log.py` — pytest suite covering every requirement above
  (filename pattern, exact content match, error handling, empty input,
  confirmation message, directory placement, and cleanup).
- `task_cli.py` — an OOP task manager CLI (`Task` and `TaskManager` classes)
  exposing `add-task`, `complete-task`, and `list-tasks` commands via
  `argparse`. State is persisted to `tasks.json`.
- `requirements.txt` — pinned dependencies (`pytest` for testing).

## Setup

```bash
python --version
pip --version
python -m venv venv
source venv/bin/activate        # on Windows: venv\Scripts\activate
pip install -r requirements.txt
```

## Running the log generator

```bash
python generate_log.py
```

This creates `log_YYYYMMDD.txt` in the current directory with the sample
log entries.

## Running the tests

```bash
pytest test_generate_log.py -v
```

All 7 tests should pass:

- creates the log file
- filename matches `log_YYYYMMDD.txt`
- file contents exactly match the input list
- raises `ValueError` for non-list input
- empty list still produces a valid empty file
- prints a confirmation message containing the filename
- file lands in the expected directory and is removed in teardown

## Running the task CLI

```bash
python task_cli.py add-task "Buy groceries"
python task_cli.py add-task "Finish lab report"
python task_cli.py complete-task 1
python task_cli.py list-tasks
```

Tasks persist across runs in `tasks.json`.

## Git workflow used for this lab

```bash
git checkout -b feature-automation-tool
git add .
git commit -m "Add automation script with API and file output"
git push origin feature-automation-tool
# open a PR, review, merge into main
git checkout main
git pull origin main
git branch -d feature-automation-tool
```