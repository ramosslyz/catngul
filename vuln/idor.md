# INSECURE DIRECT OBJECT REFERENCE
## Key
- UUID
- Burpsuite
- Features
- Hash
- Encode
## Tools
- Browser
  - Use the browser’s secret tab to quickly practically test IDOR vulnerabilities. So, when you use the regular tab as a normal user, you can use the secret tab as an attacker. This will ensure that you don’t logout.
- Burpsuite
  - Use burpsuite's HTTP history tab for checking all of requests.
  - Use burpsuite's scope feature for fast testing. Because the scope feature can be useful to make a target list and the scope feature allows showing only relevant data for your testing scope.
  - Use burpsuite’s compare tool. You should right-click on the request and choose “Send to Comparer” option. Then you can create the same request for using another object and send to comparer.
## Tips and trics
  - Focus on 1 feature (Pak Yokokho), klik semua button untuk mendapat
  - [How-To: Find IDOR (Insecure Direct Object Reference) Vulnerabilities for large bounty rewards](https://www.bugcrowd.com/blog/how-to-find-idor-insecure-direct-object-reference-vulnerabilities-for-large-bounty-rewards/)  
    - Capture all request
    - When API endpoints are not provided in IDOR vulnerability tests, `.html` source code or `.js` files are useful.
    - Search web application’s old version on “archive.org”.
    - Id values can be encoded or hashed value. In another case, you can access hashed value in `Referrer` header, so these scenarios can be replicated.
    - Manipulate the create requests.
    - Consider blind idor.
    - Combine idor with another bug.
    - Account takeover with idor
    - Test HPP (HTTP parameter pollution) bug
    - Create valid requests.

