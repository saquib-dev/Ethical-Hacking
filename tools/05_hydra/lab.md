# Hydra Practice Lab

## Scenario
You are performing a security assessment on an internal network. You have discovered an SSH service running on a target server and suspect weak credentials might be in use. Your task is to perform an online password guessing attack using Hydra.

## Objectives
1. Identify the target service and port.
2. Prepare a short list of potential usernames and passwords.
3. Execute a dictionary attack against the SSH service using Hydra.
4. Verify the discovered credentials.

## Steps

### Step 1: Preparation
1. Create a file named `users.txt` containing usernames (e.g., admin, root, user, test).
2. Create a file named `passwords.txt` containing weak passwords (e.g., password, 123456, admin, root).

### Step 2: Running Hydra
Execute Hydra targeting the SSH service (assuming target IP is `10.10.10.5`):
```bash
hydra -L users.txt -P passwords.txt 10.10.10.5 ssh -t 4 -V -f
```
*(Note: `-t 4` limits threads to avoid overwhelming the service, `-V` shows attempts, `-f` stops on first success).*

### Step 3: Analysis
Observe the output. Hydra will highlight any successful logins in green text (e.g., `[22][ssh] host: 10.10.10.5   login: root   password: password`).

### Step 4: Verification
Attempt to log into the target using the discovered credentials:
```bash
ssh root@10.10.10.5
```

## Warning
Only perform this lab against systems you own or have explicit permission to test. Brute-forcing production systems can cause account lockouts or denial of service.
