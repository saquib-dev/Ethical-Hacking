# Ghidra: Theoretical Overview and Notes

## Introduction
Ghidra is a powerful, open-source software reverse engineering (SRE) framework developed by the National Security Agency (NSA) Research Directorate. It is used to analyze compiled code (binaries) when source code is unavailable. It is a direct competitor to commercial tools like IDA Pro.

## Core Capabilities
*   **Disassembly:** Translating machine code (binary zeros and ones) into human-readable assembly language specific to the target architecture (x86, ARM, MIPS, etc.).
*   **Decompilation:** The most significant feature of Ghidra is its advanced decompiler, which attempts to translate assembly language back into high-level C-like pseudocode. This drastically speeds up the analysis process.
*   **Scripting:** Supports automation through Java and Python scripting, allowing analysts to write custom tools to unpack, decrypt, or analyze specific patterns.
*   **Collaborative Reverse Engineering:** Allows multiple analysts to work on the same project simultaneously via a shared Ghidra server.

## Key Components and Views
*   **CodeBrowser:** The primary tool where analysis takes place.
*   **Listing View:** Displays the traditional disassembly, memory addresses, and raw bytes.
*   **Decompiler View:** Displays the generated C pseudocode for the currently selected function.
*   **Symbol Tree:** Lists imported/exported functions, labels, classes, and namespaces.
*   **Data Type Manager:** Manages structures, enumerations, and typedefs, which are crucial for applying meaning to raw memory access in the decompiler.
*   **Function Graph:** Provides a visual representation of a function's control flow (basic blocks and branches), useful for understanding complex logic.

## The Reverse Engineering Process in Ghidra
1.  **Import:** Load the binary. Ghidra determines the format (PE, ELF, Mach-O) and architecture.
2.  **Auto-Analysis:** Ghidra runs various analyzers to identify functions, strings, cross-references, and data types automatically.
3.  **Manual Analysis:** The analyst navigates the code (often starting from `main` or exported functions), renames variables, defines structures, and adds comments to understand the program's behavior.
4.  **Refinement:** As understanding grows, the analyst refines function signatures and data types, causing the decompiler to generate more accurate and readable pseudocode.

## Use Cases in Ethical Hacking
*   **Vulnerability Research:** Analyzing closed-source applications or firmware to find memory corruption bugs (buffer overflows) or logic flaws.
*   **Malware Analysis:** Dissecting malicious executables to understand their capabilities, C2 infrastructure, and persistence mechanisms.
*   **Patch Analysis (Diffing):** Comparing two versions of a binary (pre-patch and post-patch) to identify exactly what vulnerability was fixed, aiding in developing 1-day exploits.
