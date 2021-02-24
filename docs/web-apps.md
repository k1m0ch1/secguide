## OSINT (Open Source Intelligence)

why OSINT ? for the application that already cached on the internet usually there is many "undetectable" sensitive information publicy on the internet, like the subdomain that shouldn't be public, trello URL that shouldn't be public, or "unlisted" link that listed by crawler.
To understand how much secure our data on internet we can use the OSINT

### theHarvester
with the OSINT you can start by using [theHarvester](https://github.com/laramies/theHarvester)
- [ ] There is no sensitive link listed on theHarvester
- [ ] IPs found on theHarvester is not sensitive
- [ ] Hosts/ subdomain listed on theHarvester is not sensitive to be on public
- [ ] Trello link listed on theHarvester is not senstive to be on public

### Github Surfing
you only need to use the search engine, and search the sensitive keyword and find the sensitive data 
for example with keyword "remove password" "hapus password"
- [ ] make sure there is no sensitive result related with application that you develop


## Tech Stack
### [Wapplyzer](https://chrome.google.com/webstore/detail/wappalyzer/gppongmhjkpfnbhagpmjfkannfbllamg?hl=id)
This tool will reveal all the tech stack on the website, you just simply click the plugin button and all the tech stack will reveal
- [ ] Available tech stack did not reveal the version
- [ ] CMS Section is not reveal on Wapplyzer 
- [ ] Database Section is not reveal on Wapplyzer
- [ ] Blog section is not reveal the version
- [ ] Programming language section is not reveal the version 
- [ ] Javascript libraries section is not reveal the version, it will be much better if this section is not reveal on the Wapplyzer
https://snyk.io/

## Web Server

- [ ] [Security Header](https://securityheaders.com/) Score minimum B
- [ ] TLS Configuration using `TLS v1.2` and `TLS v1.3` check on [TLS Test Tool](https://gf.dev/tls-test)

## File Upload

- [ ] make sure you have a specific rule to upload the file, for example if you want to upload image, only allow image
- [ ] validation not only with the MIME Type, also with the extension file
- [ ] make sure you have a limit file size to upload

## URL Fuzzer

[Git Scanner](https://github.com/HightechSec/git-scanner.git)
- [ ] make sure the dir `.git` is not accessible
https://github.com/AyoobAli/pyfuzz/tree/master/lists
https://github.com/avilum/smart-url-fuzzer

## Application Development

- [ ] Turn off the Development Mode
you can test if the application is on development mode, by making error on the application, the error will show different
a single error with the information of the directory, is the gold mine for hacker.

[Backup File Scanner](https://github.com/mazen160/bfac0)
[Backup Dir Scanner](https://github.com/tismayil/ohmybackup)
- [ ] make sure there is no backup file `.bak` or temporary save file `.save`
- [ ] make sure there is no backup application archive file `.zip` `.rar` `.tar.gz` 