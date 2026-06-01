# Module 2: Common Cloud Attacks

## Public Bucket Hunting
Many companies forget to set their storage buckets to "Private".
- **Attack**: Use tools to guess bucket names (e.g., `company-backup`, `company-dev`) and list the files.

## IAM Role Misconfiguration
If a developer gives a VM "Administrator" access, and you compromise that VM, you now have Administrator access to the entire cloud account.

## Metadata Service Exploitation
Cloud VMs have a special internal IP (`169.254.169.254`) that provides information about the instance.
- **The Hack**: If you find an SSRF vulnerability, you can request this IP to steal temporary security tokens (Access Keys).
