# Practical Lab: Software Reverse Engineering with Ghidra

## Scenario
You have been provided with a suspicious Linux ELF binary named `crackme_01`. Your objective is to reverse engineer the binary to understand its logic, identify the hardcoded password, and successfully bypass the authentication mechanism.

## Objectives
1.  Import the binary into a Ghidra project and run auto-analysis.
2.  Locate the `main` function and analyze the control flow.
3.  Identify string comparisons or validation logic.
4.  Extract the correct password required by the binary.

## Lab Walkthrough

### Phase 1: Setup and Import
1.  Launch Ghidra and create a new non-shared project named "MalwareAnalysis".
2.  Drag and drop the `crackme_01` binary into the project window (or use File -> Import File).
3.  Accept the default import settings (Format: ELF, Language: x86/default).
4.  Double-click the imported file to open it in the CodeBrowser tool.
5.  When prompted, click "Yes" to analyze the file and leave the default analysis options selected.

### Phase 2: Locating Main and Initial Analysis
1.  In the **Symbol Tree** window on the left, expand the **Functions** folder.
2.  Find and double-click on the `main` function.
3.  Observe the **Decompile** window on the right. You should see C-like pseudocode representing the `main` function.
4.  Look for standard C library function calls like `printf` (prompting for input), `scanf` or `fgets` (reading input), and `strcmp` or `strncmp` (comparing strings).

### Phase 3: Deobfuscation and Logic Extraction
1.  Notice a call to `strcmp` comparing the user's input buffer with another string.
2.  Double-click the variable representing the other string (e.g., `DAT_00102008`).
3.  This will jump the Listing view to the `.rodata` section. You should see the hardcoded string (e.g., "Sup3rS3cr3tP4ssw0rd!").
4.  Return to the decompiler view (Shift + [).
5.  Rename variables to make the code clearer (e.g., rename `local_18` to `userInput` by selecting it and pressing 'L').
6.  Analyze the `if` statement following the `strcmp`. It likely prints a success message if the comparison returns 0 (strings match).

### Phase 4: Verification
1.  Open a terminal.
2.  Execute the binary: `./crackme_01`
3.  Enter the extracted password: `Sup3rS3cr3tP4ssw0rd!`
4.  Verify that the binary outputs the success message.
