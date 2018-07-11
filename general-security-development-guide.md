# General Security Development guide

> All of this point in random order, help me to order this right~

- [ ] Don't use GET method to send any sensitive data
- [ ] Enable Header `X-XSS-Protection`, best config : "X-XSS-Protection: 1; mode=block" , this X-XSS-Protection is build within modern web browser designed to filter cross-site scripting attack
- [ ] Enable Header `X-Frame-Options`, best config : "X-Frame-Options "SAMEORIGIN" always"
- [ ] Enable Header `X-Content-Type-Options`, best config : "X-Content-Type-Options "nosniff" always"
- [ ] Enable Header `Content-Security-Policy`
- [ ] Enable Header `Referrer-Policy`
- [ ] SSL Configuration best wtih `TLS v1`, `TLS v1.1` dan `TLS v1.2`
- [ ] Don't use `TLS v3` for SSL Configuration
- [ ] Access SSH with root is prohibited
- [ ] Remove default password
- [ ] Don't store any api key, password or secret key hardcoded, you can use environment variable
- [ ] `Bcrypt` is fairly enough for hashing your password
- [ ] No phpmyadmin deployed on production server
- [ ] Don't give any clue when user is fail authentication, by simply "Wrong email or password" is enough.
- [ ] Limit File size when uploading file
- [ ] Always check file upload directory from unwanted file
- [ ] Always check vulnerability dependencies
- [ ] Disable experiment/ unuse plugin
- [ ] Disable Directory Listing
- [ ] Any resource related with sensitive data ex: cart, journal transaction, reedem voucher, etc must be check the session and user privilege action
- [ ] Sanitize File name after upload
- [ ] File Content(First byte extenstion) and file type must be match on file validation
- [ ] Disable public access for robot.txt
- [ ] Sanitize `EXIF` data while uploading image file
- [ ] Make sure no file backup (`.bak`) in every file
- [ ] Don't create any archive backup where the public can access it
- [ ] Don't create any file database backup where the public can access it
- [ ] Remove unused routes
- [ ] HTML input type autocomplete=off
- [ ] Error handling in production didn't print any debug
- [ ] use `prepared statement` for DB Query