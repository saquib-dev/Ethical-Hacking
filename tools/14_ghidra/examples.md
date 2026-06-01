# Ghidra Examples

## Scenario: Headless Automated Binary Analysis
Ghidra's headless analyzer allows security researchers to automate the reverse engineering process. This is particularly useful for extracting function names or analyzing multiple binaries automatically without opening the GUI.

**Command:**
```bash
analyzeHeadless /projects/GhidraProject TestProject -import sample_binary.exe -postScript ExtractFunctions.java
```

**Mocked Output:**
```text
INFO  Headless Analyzer (HeadlessAnalyzer)
INFO  Importing: sample_binary.exe
INFO  Analyzing: sample_binary.exe
INFO  Running Post-Script: ExtractFunctions.java
INFO  Found function: entry (0x401000)
INFO  Found function: check_debugger (0x401150)
INFO  Found function: decrypt_payload (0x401280)
INFO  Headless analysis complete.
```

**Explanation:**
- `/projects/GhidraProject TestProject`: Specifies the base Ghidra project directory and the project name to use for the analysis.
- `-import sample_binary.exe`: The target binary file to be imported and analyzed by Ghidra's auto-analysis engine.
- `-postScript ExtractFunctions.java`: Specifies a custom Java or Python script to execute after the automated analysis completes, useful for exporting findings to the terminal.
