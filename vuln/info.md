# INFORMATION DISCLOSURE

## Google Dork
- `site:yammer.com inurl:'access_token'`[1](#write-up)
- `site:xoom.com inurl:'@gmail.com'`[2](#write-up)
- `site:*.example.com inurl:redirect` eskalasi dengan XSS, contoh `example.com/social?redirect=javascript://alert(1)`[3](#write-up)

## Write-up
1. [Microsoft Yammer - oAuth Bypass Session Vulnerability](https://www.vulnerability-lab.com/get_content.php?id=1003)
2. [Information Disclosure at PayPal and Xoom (PayPal Acquisition) via Simple Google Dork - 1,000 USD](https://infosecwriteups.com/information-disclosure-at-paypal-and-xoom-paypal-acquisition-via-simple-google-dork-1-000-usd-b726fe628a05)
3. [Story of a uri based xss with some simple google dorking](https://nandwanajatin25.medium.com/story-of-a-uri-based-xss-with-some-simple-google-dorking-e1999254aa55)
