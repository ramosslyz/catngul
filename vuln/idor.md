# INSECURE DIRECT OBJECT REFERENCE

## Tools
- Browser
  - PwnFox/AutoChrome
- Burpsuite
  - Burpsuite's HTTP history tab for checking all of requests.
  - Burpsuite's scope feature for fast testing.
  - Burpsuite’s compare tool.
  - AuthMAtrix
 
## Tips and trics
  - Focus on 1 feature (Pak Yokokho)
  - [How-To: Find IDOR (Insecure Direct Object Reference) Vulnerabilities for large bounty rewards](https://www.bugcrowd.com/blog/how-to-find-idor-insecure-direct-object-reference-vulnerabilities-for-large-bounty-rewards/)
  - [Everything You Need to Know About IDOR (Insecure Direct Object References)](https://aysebilge.com/2020/04/17/everything-you-need-to-know-about-idor)
    - Log in to the same application with 2 different user roles. If you’d like to you can use different to perform this action or you can log in with user-1 to regular window and with user-2 to incognito window.
    - List all endpoints in the application.
    - Try perform on endpoints for cross user roles. You can use AuthMatrix in BurpSuite.
    - If you can read, update, create or delete an endpoint you’re not authorized then there is an IDOR.
  - [Learning about Insecure Object Reference (IDOR)](https://www.bugbountyhunter.com/vulnerability/?type=idor)
    -  opt out all links, contoh: signup to all newsletter, receive forgot email link, etc
    -  80% idors findigs are from mobile app
    -  Updating account setting
    -  Reset Password
  - [How I made it to Google HOF?](https://infosecwriteups.com/how-i-made-it-to-google-hof-f1cec85fdb1b)
    - Paramspider good for find parameter
    - knxx by tomnomnom good for find reflected word

## Case
- [IDOR via Websockets allow me to takeover any users account](https://mokhansec.medium.com/idor-via-websockets-allow-me-to-takeover-any-users-account-23460dacdeab), Always play with login, signup, and change info functionality. There is always something for you 
