# CTF Writeup: Subscribe to Read More

**Challenge Name:** `Subscribe to Read More`  
**Category:** `Web Security / API Exposure`  
**Difficulty:** `EASY`  
**Points:** `5`  
**Challenge URL:** `http://145.98.97.3`  
**Flag:** `FLAG{L0NG_L1V3_W0RK1N6_CL4SS}`

---

## Challenge description

A paywalled article was shown in the UI, but the backend API endpoint was still directly accessible.

## Steps

1. Open the challenge page in browser.
2. Open DevTools and inspect JS/network requests.
3. Identify article endpoint:
   ```text
   /api/fetch
   ```
4. Open the endpoint directly:
   ```text
   http://145.98.97.3/api/fetch
   ```
5. Read full article content and extract the flag.

## Final flag

```text
FLAG{L0NG_L1V3_W0RK1N6_CL4SS}
```

## Tools used

- Browser DevTools
- Direct endpoint access in browser
