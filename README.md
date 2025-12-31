# Todo Application - Phase I (In-Memory Python Console App)

**Version**: 1.0.0
**Phase**: Hackathon II - Phase I
**Status**: In-Memory Console Application with Core CRUD Features

---

## Overview

Command-line todo application for managing tasks in memory. Users can create, view, update, delete, and mark tasks as complete through a simple CLI interface.

**Features**:
- Add new tasks with title and description
- View all tasks in organized table format
- Update task title and/or description
- Delete tasks by ID
- Mark tasks as complete or incomplete
- User-friendly error messages and feedback

**Technology Stack**:
- **Language**: Python 3.13+
- **Package Manager**: UV
- **Architecture**: CLI → Services → Models (Clean separation of concerns)
- **Storage**: In-memory (data lost on application exit)

---

## Prerequisites

### 1. Install Python 3.13+

**Check Version**:
```bash
python --version
```

Expected output: `Python 3.13.x` or higher

**Download** (if needed):
- Windows: https://www.python.org/downloads/
- macOS/Linux: Use system package manager

### 2. Install UV Package Manager

**Install UV**:
```bash
# On Linux/macOS
pip install uv

# On Windows (PowerShell as Admin)
irm https://astral.sh/uv/install.ps1 | iex
```

**Verify Installation**:
```bash
uv --version
```

Expected output: `uv 1.x.x` or higher

---

## Setup Instructions

### 1. Clone and Navigate to Project

```bash
# Navigate to project directory
cd path/to/todo-app
```

### 2. Create Virtual Environment

```bash
# Create virtual environment
uv venv
```

### 3. Activate Environment

**Linux/macOS**:
```bash
source .venv/bin/activate
```

**Windows (PowerShell)**:
```powershell
.venv\Scripts\activate
```

**Verify Activation**:
You should see `(.venv)` in your command prompt.

### 4. Install Dependencies

```bash
# Install development dependencies
uv pip install --dev pytest
```

**Verify Installation**:
```bash
pip list | grep pytest
```

---

## Usage

### Start Application

```bash
# Run todo application
python -m src.cli.main help
```

This will display:
```
usage: python -m src.cli.main <command>

positional arguments:
  command          Available commands: {add,list,update,delete,complete,help}

optional arguments:
  -h, --help     show this help message and exit
```

## Commands

### Add Task

```bash
python -m src.cli.main add "Buy groceries" --description "Milk, eggs, bread"
```

Expected output:
```
✓ Task created: Buy groceries
```

### View All Tasks

```bash
python -m src.cli.main list
```

Expected output:
```
| ID | Title          | Description       | Status     |
|----|----------------|------------------|------------|
|  1  | Buy groceries | Milk, eggs, bread | ✗          |
```

### Update Task

```bash
python -m src.cli.main update 1 --title "Buy groceries (urgent)" --description "Milk, eggs, bread ASAP"
```

Expected output:
```
✓ Task updated: Buy groceries (urgent)
```

### Delete Task

```bash
python -m src.cli.main delete 1
```

Expected output:
```
✓ Task deleted: Buy groceries (urgent)
```

### Mark Task Complete

```bash
python -m src.cli.main complete 1
```

Expected output:
```
✓ Task 1 marked as complete
```

---

## Project Structure

```
todo-app/
├── src/
│   ├── models/
│   │   └── task.py              # Task entity definition
│   ├── services/
│   │   └── todo_service.py       # Business logic for task management
│   ├── cli/
│   │   ├── __init__.py
│   │   └── main.py              # CLI entry point and argument parsing
│   └── lib/
│       └── __init__.py
├── tests/
│   ├── contract/
│   ├── integration/
│   └── unit/
├── specs/
│   └── 001-phase1-cli-app/
│       ├── spec.md
│       ├── plan.md
│       ├── tasks.md
│       ├── data-model.md
│       └── quickstart.md
├── .specify/
│   ├── memory/
│   │   └── constitution.md
│   └── templates/
├── .claude/
│   └── context.md
├── pyproject.toml
└── README.md                  # This file
```

---

## Testing

Run the quickstart validation scenarios from quickstart.md:

```bash
# Add first task
python -m src.cli.main add "Buy groceries" --description "Milk, eggs, bread"

# List tasks
python -m src.cli.main list

# Update task
python -m src.cli.main update 1 --title "Buy groceries (urgent)"

# Mark complete
python -m src.cli.main complete 1

# Delete task
python -m src.cli.main delete 1

# View empty list
python -m src.cli.main list
```

---

## Troubleshooting

### Issue: "No module named 'src'"

**Cause**: Not running from project root or wrong PYTHONPATH

**Solution**:
```bash
# Run from project root
python -m src.cli.main <command>
```

### Issue: UV not found

**Cause**: UV not installed or not in PATH

**Solution**: Re-run UV installation or add UV to PATH

---

## Notes

- **In-Memory Storage**: All tasks are lost when application exits (this is Phase I limitation)
- **No Persistence**: Tasks will not persist across application restarts (this is expected for Phase I)
- **Phase II**: Next phase will add database persistence and web interface
- **Clean Code**: Implementation follows Python best practices with proper separation of concerns

---

## License

Copyright (c) 2025 Evolution of Todo Project. All rights reserved.
