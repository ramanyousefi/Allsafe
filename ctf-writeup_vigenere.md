# CTF Writeup: Modified Vigenère Cipher

**Challenge Name:** `Modified Vigenère Cipher`  
**Category:** `Cryptography`  
**Difficulty:** `EASY`  
**Points:** `5`  
**Challenge URL:** `N/A (file-based challenge)`  
**Flag:** `FLAG{MODIFIED_VIGENERE_IS_BREAKABLE}`

---

## Challenge description

Ciphertext:

```text
HDAY{OGDAHAEV_XAGWPWRW_KK_BJGSKSDDE}
```

Hint: key length is 4.  
Given encryption rule:

```text
enc = (p + k + drift) % 26
```

So decryption is:

```text
p = (c - k - drift) % 26
```

## Steps

1. Assume CTF prefix `FLAG{` and compare with `HDAY{`.
2. Recover key letters using first 4 characters and drift `0,1,2,3`:
   - `H -> F` gives `C`
   - `D -> L` gives `R`
   - `A -> A` gives `Y`
   - `Y -> G` gives `P`
   Key = `CRYP`.
3. Use drift cycle `i % 4` and decrypt all letters with:
   ```text
   p = (c - key[i % 4] - (i % 4)) % 26
   ```
4. Keep `_`, `{`, `}` unchanged.

Decrypted output:

```text
FLAG{MODIFIED_VIGENERE_IS_BREAKABLE}
```

## Final flag

```text
FLAG{MODIFIED_VIGENERE_IS_BREAKABLE}
```

## Tools used

- Pencil-and-paper modular arithmetic
- Optional quick Python check
