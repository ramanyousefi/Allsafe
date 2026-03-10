# CTF Writeup: Silent Exfiltration

**Challenge Name:** `Silent Exfiltration`  
**Category:** `Network Forensics / HTTP`  
**Difficulty:** `MEDIUM`  
**Points:** `10`  
**Challenge URL:** `http://145.98.97.8:8080`  
**Flag:** `Flag{fc078463666cd003_flag}`

---

## Challenge description

The secret was split across multiple HTTP requests and headers to look like normal API traffic.

## Steps

1. Open payloads in ASCII:
   ```bash
   tcpdump -A -s0 -nn -r silent_exfiltration_1773165775.pcap
   ```
2. Filter lines with obvious parts:
   ```bash
   tcpdump -A -s0 -nn -r silent_exfiltration_1773165775.pcap | grep -a -n -E 'X-Flag-Part|part2:|part 3:|part 4:'
   ```
3. Extract fragments:
   - `part 1: Flag{fc`
   - `part2:0784636`
   - `part 3: 66cd003`
   - `part 4: _flag}`
4. Concatenate in timeline order.

## Final flag

```text
Flag{fc078463666cd003_flag}
```

## Tools used

- `tcpdump`
- `grep`
