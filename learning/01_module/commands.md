# Module 01: Setup Commands

Once you have imported your Kali VM, use these commands to ensure it is healthy and updated.

### Updating the System
Kali is a "rolling release," meaning it updates constantly.
```bash
# Update the package list (What is available?)
sudo apt update

# Upgrade the installed packages (Install the updates)
sudo apt full-upgrade -y
```
*Note: `full-upgrade` is preferred over `upgrade` in Kali to handle dependency changes.*

### Basic System Health
```bash
# Check disk space to ensure you have room for tools
df -h

# Check memory usage
free -m

# Check if the network is working
ping -c 4 google.com
```
