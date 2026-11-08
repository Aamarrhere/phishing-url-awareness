# Test Results

Python version used: 3.9.6 | Operating system: macOS | Date: 8 Nov 2026


| # | Input | Expected result | Actual result | Pass/Fail |
|---|-------|-----------------|---------------|-----------|
| 1 | https://www.example.com/login | No listed warning signs | No listed warning signs found. This does NOT prove safety. | PASS |
| 2 | http://192.0.2.10/account | IP address + HTTP | Uses an IP address instead of a familiar domain. / Uses HTTP. HTTPS alone does not prove trust. | PASS |
| 3 | http://example.com@sample.invalid/login | @ symbol + HTTP | Contains an @ symbol; inspect carefully. / Uses HTTP. HTTPS alone does not prove trust. | PASS |
| 4 | https://a.b.c.d.e.example.invalid/path | Many hostname segments | Contains many hostname segments/subdomains. | PASS |
| 5 | https://xn--example.invalid/ | Punycode-style hostname | Contains a punycode-style hostname. | PASS |

## Bonus checks

| Input | Result |
|-------|--------|
| (empty, just Enter) | No URL entered. |
| www.example.com | Uses HTTP. HTTPS alone does not prove trust. |
| https://secure-login.example.invalid | No listed warning signs found. This does NOT prove safety. |
| http://[bad | This text is not a valid URL format. (no crash after Improvement C) |

## Notes

I learned that the tool only reads the text of a URL, so it can find clues but cannot prove a link is safe. The surprising one was https://secure-login.example.invalid: it looks suspicious by name, but none of the six checks flag it. After adding the try/except, the malformed input http://[bad no longer crashes the program.
