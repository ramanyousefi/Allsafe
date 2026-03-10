# CTF Writeup: ARP Storm

**Challenge Name:** `ARP Storm`  
**Category:** `Network Forensics / Layer 2`  
**Difficulty:** `HARD`  
**Points:** `20`  
**Challenge URL:** `N/A (PCAP challenge)`  
**Flag:** `Flag{4c17ef80d05827bd_flag}`

---

## Challenge description

The capture looked like noisy ARP traffic, but malformed ARP opcodes were carrying hidden data.

## Steps

1. Inspect ARP frames including Ethernet and hex dump:
   ```bash
   tcpdump -nn -e -r arp_storm_1773166019.pcap
   ```
2. Notice many ARP entries marked `Unknown(<number>)` with opcode-like hex values (`526d`, `7868`, ...).
3. Extract those hex pairs in order and convert to ASCII:
   ```bash
   tcpdump -nn -e -r arp_storm_1773166019.pcap | awk '/0x0000:/{print $5}' | tr -d '\n' | xxd -r -p
   ```
   Output:
   ```text
   RmxhZ3s0YzE3ZWY4MGQwNTgyN2JkX2ZsYWd9
   ```
4. Decode as Base64:
   ```bash
   tcpdump -nn -e -r arp_storm_1773166019.pcap | awk '/0x0000:/{print $5}' | tr -d '\n' | xxd -r -p | base64 -d
   ```

## Final flag

```text
Flag{4c17ef80d05827bd_flag}
```

## Tools used

- `tcpdump`
- `awk`, `tr`, `xxd`
- `base64`
