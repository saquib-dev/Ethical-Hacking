# Lab 1: Google Dorking

## Goal: Find sensitive information using only Google.

## Try these Dorks (Replace `example.com` with a target or leave it blank for general search):

1. **Find PDF files**: `site:example.com filetype:pdf`
2. **Find Login Pages**: `site:example.com inurl:login`
3. **Find Exposed Log Files**: `filetype:log "error"`
4. **Find Config Files**: `filetype:env "DB_PASSWORD"`

## Success Check:
- [ ] Found a PDF or document from a specific site.
- [ ] Found a login page using `inurl:login`.
- [ ] Understand how `site:` and `filetype:` work.
