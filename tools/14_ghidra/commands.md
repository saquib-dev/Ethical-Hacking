# Ghidra Cheat Sheet

## Basic Navigation & Shortcuts
*   **G:** Go to address/label.
*   **L:** Rename a variable, function, or label.
*   **T:** Change data type (e.g., change a generic integer to a specific struct pointer).
*   **; (Semicolon):** Add a comment (EOL comment).
*   **C:** Clear code/data at the current cursor position.
*   **D:** Disassemble code at the current cursor position.
*   **Ctrl + Shift + E:** Search for Strings.
*   **Ctrl + Shift + F:** Search for Program Text.

## Function Analysis
*   **F:** Create a function at the current cursor position.
*   **Ctrl + L:** Edit function signature (arguments, return type).
*   **Shift + [ / ]:** Navigate backward/forward in history (like browser back/forward).
*   **Alt + Right/Left Arrow:** Navigate cross-references (XREFs).

## Decompiler Interaction
*   **Ctrl + Mouse Wheel:** Zoom in/out in the decompiler or listing view.
*   **Right-Click -> "Find References to...":** Find where a variable, function, or address is used (XREFs).
*   **Right-Click -> "Commit Params/Return":** Force the decompiler to accept the currently inferred function signature.
*   **Double-Click:** Follow a function call or variable reference.

## Working with Types and Structs
*   **Data Type Manager:** Window -> Data Type Manager. Used to define and manage structures and enums.
*   **Auto-Create Struct:** Highlight variables in the decompiler, right-click -> "Auto Create Structure".
*   **Apply Struct:** Press 'T' on a variable and type the struct name.

## Scripting
*   **Window -> Script Manager:** Open the script manager to run Java or Python scripts.
