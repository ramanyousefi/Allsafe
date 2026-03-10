# CTF Writeup: Encrypted Whisper

**Challenge Name:** `Encrypted Whisper`  
**Category:** `Forensics / Encoding`  
**Difficulty:** `MEDIUM`  
**Points:** `N/A`  
**Challenge URL:** `N/A (terminal challenge)`  
**Flag:** `FLAG{WHISPER079-eryz-5180-DhG0Vn4jzE}`

---

## Challenge description

A cache file looked like random text, but the hints (`Legacy core: 079`) suggested hidden encoded content.

## Steps

1. List cache files:
   ```bash
   ls -la /srv/terminal/.cache
   ```
2. Inspect `terminal_fragment.txt` for hints and `cat` `.whisper`.
3. Notice `.whisper` starts with `H4sI...` (typical Base64-encoded gzip).
4. Decode and decompress:
   ```bash
   base64 -d /srv/terminal/.cache/.whisper > /tmp/whisper.gz
   gunzip -c /tmp/whisper.gz
   ```
5. Read decoded output and extract flag.

## Final flag

```text
FLAG{WHISPER079-eryz-5180-DhG0Vn4jzE}
```

## Tools used

- `ls`, `cat`, `file`
- `base64 -d`
- `gunzip -c`
