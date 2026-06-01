# Lab 1: Hunting for Public S3 Buckets

## Goal: Find sensitive files in public cloud storage.

## Tools to Try:
- **GrayHatWarfare**: A search engine for public buckets.
- **S3Scanner**: A tool to scan for buckets based on a company name.

## Steps:
1. Pick a target company.
2. Use an S3 scanner to find buckets starting with the company name.
3. Try to list the contents using the AWS CLI:
   `aws s3 ls s3://company-bucket-name --no-sign-request`
4. If it works, you have found an open bucket!

## Success Check:
- [ ] Successfully listed files in a public bucket.
- [ ] Understand why `--no-sign-request` is used (to access without an account).
