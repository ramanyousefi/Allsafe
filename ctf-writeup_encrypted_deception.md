# CTF Writeup: Encrypted Deception

**Challenge Name:** `Encrypted Deception`  
**Category:** `Network Forensics`  
**Difficulty:** `MEDIUM`  
**Points:** `N/A`  
**Challenge URL:** `http://145.98.97.7:8080`  
**Flag:** `Flag{054bf724085f36a4_flag}`

---

## Challenge description

The PCAP mostly looked like TLS on port 443, but one flow was fake TLS carrying plaintext.

## Steps

1. List port 443 traffic and look for outliers:
   ```bash
   tcpdump -nn -r encrypted_deception_1772799732.pcap 'tcp port 443'
   ```
2. Spot suspicious tiny packets (`length 21` and `length 39`) on one flow.
3. Follow only that stream:
   ```bash
   tcpdump -A -s0 -nn -r encrypted_deception_1772799732.pcap 'tcp and host 127.20.0.30 and host 127.203.0.50 and port 41999'
   ```
4. Read plaintext in payload:
   ```text
   FLAG: Flag{054bf724085f36a4_flag}
   ```

## Final flag

```text
Flag{054bf724085f36a4_flag}
```

## Tools used

- `tcpdump -nn -r`
- `tcpdump -A -s0 -nn -r`
