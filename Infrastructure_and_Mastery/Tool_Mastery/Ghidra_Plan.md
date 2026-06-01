# Ghidra Mastery Plan (4 Weeks)

Ghidra is for turning binary "gibberish" into readable logic.

## Week 1: Static Analysis Basics
- **Goal**: Navigate the interface.
- **Tasks**:
  - Import a binary and run the auto-analyzer.
  - Learn the "Symbol Tree" and "Function Graph".
  - Identify the `main` function and entry points.

## Week 2: Understanding Assembly
- **Goal**: Read x86/x64 Assembly.
- **Tasks**:
  - Learn common instructions: `MOV`, `PUSH`, `POP`, `CALL`, `CMP`, `JMP`.
  - Understand the **Stack** and **Registers** (`RAX`, `RSP`, `RIP`).
  - Use the "Decompiler" to see C-like code.

## Week 3: Data Analysis & Strings
- **Goal**: Find secrets in the binary.
- **Tasks**:
  - Use the "Defined Strings" window to find passwords/URLs.
  - Trace "Cross References" (XREFs) to see where a specific string is used.
  - Identify hardcoded encryption keys.

## Week 4: Patching & Manipulation
- **Goal**: Change how a program behaves.
- **Tasks**:
  - Use the "Patch Instruction" feature to bypass a password check (e.g., change `JZ` to `JNZ`).
  - Export the patched binary and run it.
