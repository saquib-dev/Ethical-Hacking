# Lab 1: Hunting for Sudo Rights

## Goal: Find a way to become root via sudo.

## Steps:
1. **Check permissions**: Run `sudo -l`.
2. **Analyze**: Look for any command that says `(ALL) NOPASSWD: /usr/bin/...`
3. **The Hack (GTFOBins)**:
   - If you see a command like `vim` or `find` in that list, go to [GTFOBins](https://gtfobins.github.io/).
   - Search for that command under the "Sudo" section.
   - Copy the command provided to spawn a shell.
   - Example for `find`: `sudo find . -exec /bin/sh \; -quit`

## Success Check:
- [ ] I know how to check my sudo permissions.
- [ ] I know how to use GTFOBins to find a root exploit.
