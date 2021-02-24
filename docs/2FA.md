# 2FA Security Checklist

Refference on how hacker bypass this Function [2FA Bypass](https://github.com/daffainfo/AllAboutBugBounty/blob/master/Bypass/Bypass%202FA.md)

- [ ] frontend/ application client to verify user input the right code 2FA from comparing the code, don't use the state of `true/ false` or the `HTTP status code` to validate the 2FA code
- [ ] don't put the "right" code on the 2FA request

example:

Request
```
POST /req-2fa/
Host: vuln.com
...
email=victim@gmail.com
```

Response
````
HTTP/1.1 200 OK
...
{"email": "victim@gmail.com", "code": "101010"}
```

- [ ] always set the time limit every time the user want to request the 2FA
- [ ] ban the user fro long time limit, every time the user fail attempt for every 5 times
- [ ] every 2FA code is unique for every user, so there is must be a integrity validation for every user
- [ ] always enable CSRF Protection even when user disable the 2FA
- [ ] when email or password is changed, the 2FA is not disabled
- [ ] 2FA tools instead sent the code to SMS
- [ ] 2FA code shouldn't be reused
- [ ] sequence code or same code shouldn't, for example prohibit the code 12345 or 00000
