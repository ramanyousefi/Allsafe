# CTF Writeup: Multi-step Transformations

**Challenge Name:** `Multi-step Transformations`  
**Category:** `Cryptography / Encoding`  
**Difficulty:** `EASY`  
**Points:** `5`  
**Challenge URL:** `N/A (file-based challenge)`  
**Flag:** `FLAG{3NCRYPT1ON_4ND_3NC0DING_ARE_FUN}`

---

## Challenge description

The provided `output.txt` had 5 lines, each using a different transformation. The solution was to decode each line and combine the parts.

## Steps

Input:

```text
SYNT{
3UJYFWA1VU_4UK_3UJ0K
M05DMERJTg==
T_ZIV_
00000111 00010111 00001101 00111001 ^ 01000001 01000010 01000011 01000100
```

1. `SYNT{` → apply ROT13 → `FLAG{`
2. `3UJYFWA1VU_4UK_3UJ0K` → Caesar shift 7 left → `3NCRYPT1ON_4ND_3NC0D`
3. `M05DMERJTg==` → Base64 decode → `3NC0DIN`
4. `T_ZIV_` → Atbash → `G_ARE_`
5. XOR binary bytes:
   - `7 ^ 65 = 70 = F`
   - `23 ^ 66 = 85 = U`
   - `13 ^ 67 = 78 = N`
   - `57 ^ 68 = 125 = }`
   → `FUN}`
6. Merge parts in order and resolve overlap (`3NC0D` + `3NC0DIN` → `3NC0DING`).

## Final flag

```text
FLAG{3NCRYPT1ON_4ND_3NC0DING_ARE_FUN}
```

## Tools used

- CyberChef (ROT13, Caesar, Base64, Atbash)
- Basic XOR math
