# CTF Writeup: The Generator

**Challenge Name:** `The Generator`  
**Category:** `Reverse Engineering`  
**Difficulty:** `UNKNOWN (not shown in prompt)`  
**Points:** `N/A`  
**Challenge URL:** `N/A (local binary challenge)`  
**Flag:** `FLAG{EBCCAAAB}`

---

## Challenge description

A local binary (`lock`) validates a key. Goal: recover a valid key and submit it as `FLAG{<key>}`.

## Steps

1. Identify binary type:
   ```bash
   file lock
   ```
   Result: 64-bit ELF, not stripped.

2. Extract obvious hints:
   ```bash
   strings lock | grep -E '(seed|key|valid|usage)'
   ```
   Found seed hint: `0x1234`.

3. Inspect validation function in r2:
   ```bash
   r2 -q -c 'aaa; afl; pdf @ sym.validate_key' lock
   ```

4. Recover constraints from `validate_key`:
   - key length must be 8
   - only uppercase `A-Z`
   - custom hash must equal seed (`0x1234`)
   - positional checksum must equal `0x940`

5. Solve constraints with a short brute-force + pruning script.
   Resulting valid key: `EBCCAAAB`.

6. Submit as flag format.

## Final flag

```text
FLAG{EBCCAAAB}
```

## Tools used

- `file`
- `strings`
- `radare2`
- Python (small constraint solver)
