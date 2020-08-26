# b3lajar

## RECONNAISSANCE :crystal_ball:

### Subdomain Enumeration
- Macam2 subdomain enumerasi:
  - Link and JS discovery
    - Burpsuite - Crawler
    - [GoSpider](https://github.com/jaeles-project/gospider)
    - [Hakrawler](https://github.com/hakluke/hakrawler)
    - [SubDomainizer](https://github.com/nsonaniya2010/SubDomainizer) - And JS Discover
    - [Subscraper](https://github.com/Cillian-Collins/subscraper) - ada fitur recursive
  - Scrapping
    - [Amass enum](https://github.com/OWASP/Amass)
    - [Subfinder v2](https://github.com/projectdiscovery/subfinder)
    - [Github-search](https://github.com/gwen001/github-search)
    - Shobsugo
    - [Cloud Range](https://www.daehee.com/scan-aws-ip-ssl-certificates/)
    - [Project Sonar Forward DNS](https://opendata.rapid7.com/sonar.fdns_v2/) - Subdomains from Rapid7 FDNS
      ```
      zcat data-sonar.gz | grep -F '.uhuy.com"' | jq -r .name | grep '.uhuy.com$' | sort | uniq
      
      ```
  - Bruteforcing
    - Amass enum -brute
      ```
      amass enum -brute -d twitch.tv -src
      amass enum -brute -d twitch.tv -rf resolvers.txt -w bruteforce.list
      ```
    - [Async DNS Brute](https://github.com/blark/aiodnsbrute)
    - [shuffleDNS](https://github.com/projectdiscovery/shuffledns)
    - Brutes word list
      - [all.txt](https://gist.github.com/jhaddix/86a06c5dc309d08580a018c66354a056) - By Jason Haddix
      - [Custom Wordlist](https://www.twitch.tv/videos/649748420?t=0h28m34s) - By TomNomNom
      - [CommonSpeak2](#Wordlist)
      
- DNS Resolver
  - Httprobe - DNS resolver
  - Massdns - DNS resolver
    ```
    massdns -r ../lists/resolvers.txt -t A domain.txt -w output.txt -s 15000 -o S --flush
    ```
  - [Altdns](https://github.com/infosec-au/altdns) - permutasian subdomain
    ```
    python __main__.py -i domain.txt -o output.txt -w ../words.txt
    ```

### Path Discovery

 <p align="center"><img src="https://user-images.githubusercontent.com/52058660/90960320-1335ac00-e4cb-11ea-8887-70130a069fe3.png" width="800"></p>
 
- Dirsearch</br>
  ```
  python3 dirsearch.py -u http://uhuy.com:666/ -e .asp, .aspx, .jsp, .php, .csv, .doc, .docx, .xls, .xlsx, .ppt, .pptx, .pdf, .bak, .conf, .config, .old, .sql, .jar, .rar, .zip, .tar, .tar.gz, .apk, .ipa, .cgi, .do, .htm, .html, .js, .json, .rb, .xml, .yml, .svn, .git
  ```
- Dirb
- Dirbuster
- Gau
- Gobuster

### Port Scanning
- Masscan
```
masscan -p1-65535,U:1-65535 10.10.10.x --rate=1000 -e tun0
```
- Nmap
```
sudo nmap -Pn -f -sV -p 80 10.10.10.x
```
- [Quick Port Scan Tip](https://forum.hackthebox.eu/discussion/927/quick-port-scan-tip) - Hack The Box Forum

### Wordlist
- [SecLists](https://github.com/danielmiessler/SecLists)
- [FuzzDB](https://github.com/fuzzdb-project/fuzzdb)
- [Commonspeak2](https://github.com/assetnote/commonspeak2-wordlists) - Nice for subdomain
- [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings)
    
### API Enumeration
[How To Do Recon: API Enumeration](https://www.youtube.com/watch?v=fvcKwUS4PTE&t=267s) - by InsiderPhD
  
### Screenshot
[Eyeofwitness](https://github.com/FortyNorthSecurity/EyeWitness)

### Mapping
  - Company Information
    - [crunchbase](https://www.crunchbase.com) - info akuisisi
    - Amass intel - Website relation
    - [bgp.he.net](https://bgp.he.net) - ASN Enumeration
  - Reverse whois
    - [whoxy](https://www.whoxy.com/)
    - [DOMLink](https://github.com/vysecurity/DomLink)
  - IOT search engine
    - [Shodan](https://www.shodan.io/)
  - Web Technology
    - [Buildwith](https://pro.builtwith.com/)
    - [Wappalyzer](https://www.wappalyzer.com/)

### Time Management</br>
[TomatoTimer](https://tomato-timer.com/) - Pomodoro technique

### OTHERS
- [How To Shot Web - Jason Haddix's talk from DEFCON23](https://www.youtube.com/watch?v=VtFuAH19Qz0) - By Jason Haddix
- [The Bug Hunter’s Methodology Jason Haddix @jhaddix](https://www.youtube.com/watch?v=gIz_yn0Uvb8) - TBHM v4.02
