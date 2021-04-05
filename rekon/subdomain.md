# Subdomain Enumeration
<br><p align="center"><img src="https://user-images.githubusercontent.com/52058660/90480317-43dbb580-e15a-11ea-863d-f783f7f4236f.png" width="800"></p>
<br>
- [Subdomain Enumeration: 2019 Workflow](https://0xpatrik.com/subdomain-enumeration-2019/) - By Patrik Hudak
- [Filter Wildcard Domains](https://0xpatrik.com/wildcard-domains/)
- Link and JS discovery
  - [SubDomainizer](https://github.com/nsonaniya2010/SubDomainizer)
  - [Subscraper](https://github.com/Cillian-Collins/subscraper)
  - [crt.sh](scrt.sh)
  - [certspotter](https://sslmate.com/certspotter/)
- Scrapping
  - [Amass enum](https://github.com/OWASP/Amass)
  - [Subfinder v2](https://github.com/projectdiscovery/subfinder)
  - [Github-search](https://github.com/gwen001/github-search)
  - [Shobsugo](https://github.com/incogbyte/shosubgo)
  - [Cloud Range](https://www.daehee.com/scan-aws-ip-ssl-certificates/)
  - [Project Sonar Forward DNS](https://opendata.rapid7.com/sonar.fdns_v2/)
    ```
    zcat data-sonar.gz | grep -F '.uhuy.com"' | jq -r .name | grep '.uhuy.com$' | sort | uniq
      
    ```
- Bruteforcing
  - [Amass enum -brute](https://github.com/OWASP/Amass)
    ```
    amass enum -brute -d twitch.tv -src
    amass enum -brute -d twitch.tv -rf resolvers.txt -w bruteforce.list
    ```
  - [Async DNS Brute](https://github.com/blark/aiodnsbrute)
  - [shuffleDNS](https://github.com/projectdiscovery/shuffledns)
  - [Subdomain wordlist](#Wordlist)
- Others   
  - [Altdns](https://github.com/infosec-au/altdns)
    ```
    python __main__.py -i domain.txt -o output.txt -w ../words.txt
    ```
- Resolver
  - Httprobe
  - Massdns
    ```
    massdns -r ../lists/resolvers.txt -t A domain.txt -w output.txt -s 15000 -o S --flush
    ```
  - [Httpx](https://github.com/projectdiscovery/httpx)
