# CTF Writeup: Insecure Login

**Challenge Name:** `Insecure Login`  
**Category:** `Web Security`  
**Difficulty:** `EASY`  
**Points:** `5`  
**Challenge URL:** `http://18.159.209.223:80`  
**Flag:** `MaaSec{24759cdd3e34e66b_flag}`

---

## Challenge description

The login page looked protected, but authentication logic was handled in front-end JavaScript.

## Steps

1. Open the page source:
   ```bash
   curl http://18.159.209.223:80
   ```
2. Find the linked script (`login.js`).
3. Open `login.js` in browser DevTools.
4. Read hardcoded credentials from the script:
   ```javascript
   const VALID_USERNAME = "sysadmin";
   const VALID_PASSWORD = "MegaFish999#!";
   ```
5. Log in with those credentials and capture the flag.

## Final flag

```text
MaaSec{24759cdd3e34e66b_flag}
```

## Tools used

- Browser DevTools
- `curl`
