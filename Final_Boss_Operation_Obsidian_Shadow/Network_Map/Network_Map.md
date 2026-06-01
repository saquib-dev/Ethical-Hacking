# Target Network Map

The environment consists of four primary zones:

## Zone 1: The Perimeter (Public)
- **Target**: `web.securecorp.local`
- **Role**: Public website for customers.
- **Potential Entry**: Web vulnerabilities, misconfigurations.

## Zone 2: The Internal DMZ (Private)
- **Target**: `api.internal.securecorp.local`
- **Role**: Internal API server handling employee data.
- **Access**: Only accessible from the Perimeter Zone.

## Zone 3: The Corporate Core (AD Domain)
- **Target**: `dc01.securecorp.local` (Domain Controller)
- **Role**: Manages all corporate identities and permissions.
- **Access**: Only accessible from the Internal DMZ.

## Zone 4: The Cloud Vault (External)
- **Target**: `s3://securecorp-vault-secret`
- **Role**: Highly secure AWS S3 bucket containing the "Obsidian Key".
- **Access**: Requires a specific IAM Role/Key found somewhere in the network.
