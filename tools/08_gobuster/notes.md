# Gobuster Notes

## Overview
Gobuster is a fast, multi-threaded tool written in Go, used for brute-forcing URIs (directories and files) in web sites, DNS subdomains, and Virtual Host names on target web servers.

## Key Features
- **Speed:** Being written in Go, it is significantly faster than other script-based tools like DirBuster or dirb.
- **Modes:** Supports `dir` (directory/file), `dns` (subdomain), `vhost` (virtual hosts), and `s3` (AWS S3 buckets) modes.
- **Flexibility:** Allows filtering by status codes, custom headers, cookies, and specific file extensions.

## Best Practices & Considerations
- **Wordlist Selection:** The success of Gobuster heavily relies on the quality of the wordlist used. SecLists is a highly recommended collection.
- **Thread Count:** While higher threads (`-t`) increase speed, they can also overwhelm the target server or cause network congestion, leading to false negatives. Adjust thread count based on network stability.
- **Rate Limiting:** Some servers may ban your IP if you send too many requests too quickly. If you encounter errors, slow down the scan or use a different tool with better rate-limiting capabilities if Gobuster is too aggressive.
- **False Positives:** Servers using wildcard DNS or custom 404 pages might return a 200 OK for every request. Use the `--wildcard` flag in DNS mode or carefully filter status codes to mitigate this.
