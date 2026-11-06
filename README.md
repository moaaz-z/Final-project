# Terminal Bank Management System

[![C](https://img.shields.io/badge/Language-C-00599C?logo=c&logoColor=white)](https://en.wikipedia.org/wiki/C_(programming_language))
[![Platform](https://img.shields.io/badge/Platform-Cross--Platform-lightgrey)](#)
[![Systems Programming](https://img.shields.io/badge/Systems-File%20I%2FO%20%26%20Memory-informational)](#)

A modular C command-line application implementing a secure banking system with user authentication, file-based persistence, and input sanitation.

---

## System Overview

The system is designed for robust terminal operation, demonstrating fundamental low-level concepts:
- **Authentication and Access Control:** Secure user login mechanism comparing credentials against an internal database (`users.txt`).
- **Buffer Sanitation and Overflow Protection:** Implements constrained scanning (`scanf("%49s", ...)`) to guarantee bounds safety on 50-byte character buffers.
- **Input Stream Cleanup:** Clears standard input streams (`while ((c = getchar()) != '\n' && c != EOF);`) to prevent cascading buffer failures on invalid non-numeric selections.
- **Session Security:** Strictly terminates execution upon detecting invalid authorization attempts.

---

## Repository Structure

```text
Final-project/
├── main.c # Core application entry point, authentication and menu logic
├── accounts.txt # Account balances and transaction records
├── users.txt # Credential store containing authorized username/password pairs
└── README.md # Technical documentation
```

---

## Architecture and Execution Flow

```text
[Start Application]
        │
        ▼
 [Main Menu] ──(Choice: 0)──> [Exit]
        │
 (Choice: 1)
        ▼
 [Login Prompt]
 - Read username (%49s)
 - Read password (%49s)
        │
        ▼
 [File Verification (users.txt)]
        │
 ┌────┴───────────────────────────┐
 ▼ ▼
[Success (1)] [Failure (0)]
User Confirmed Unauthorized User
Proceed to Account Actions Terminate Process
```

---

## Compilation and Execution

### Prerequisites
- GCC or Clang compiler
- Standard C library (libc)

### Build
Compile the application with optimization and warning flags:
```bash
gcc -Wall -Wextra -O2 main.c -o bank_system
```

### Run
Ensure `users.txt` and `accounts.txt` reside in the working directory, then launch the binary:
```bash
./bank_system
```
