# RECONNAISSANCE :crystal_ball:

## Table Of Contents
- Subdomain Enumeration
- Directory Discovery
- Content Discovery
- Port Scanning
- Github Recon
- ASN, IP, CIDR Enumeration
- Recon Framerwork
- Wordlist
- Scanner
- Api Enumeration
- Screnshooter
- Information Mapping
- Time Management
- Others

## Subdomain Enumeration
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
## Resolver
  - Httprobe
  - Massdns
    ```
    massdns -r ../lists/resolvers.txt -t A domain.txt -w output.txt -s 15000 -o S --flush
    ```
  - [Httpx](https://github.com/projectdiscovery/httpx)
  
## Path and Content Discovery
 
 <p align="center"><img src="https://user-images.githubusercontent.com/52058660/90960320-1335ac00-e4cb-11ea-8887-70130a069fe3.png" width="700"></p>
 
- Dirsearch</br>
  ```
  python3 dirsearch.py -u http://uhuy.com:666/ -e .asp, .aspx, .jsp, .php, .csv, .doc, .docx, .xls, .xlsx, .ppt, .pptx, .pdf, .bak, .conf, .config, .old, .sql, .jar, .rar, .zip, .tar, .tar.gz, .apk, .ipa, .cgi, .do, .htm, .html, .js, .json, .rb, .xml, .yml, .svn, .git
  ```
- Dirb
- Dirbuster
- Gau
- Gobuster
- [Scantastic-tools](https://github.com/maK-/scantastic-tool)
- [GoSpider](https://github.com/jaeles-project/gospider)
- [Hakrawler](https://github.com/hakluke/hakrawler)
- [Arjun](https://github.com/s0md3v/Arjun)
- [waybackurls](https://github.com/tomnomnom/waybackurls/)
- [Static Analysis of Client-Side JavaScript for pen testers and bug bounty hunters](https://blog.appsecco.com/static-analysis-of-client-side-javascript-for-pen-testers-and-bug-bounty-hunters-f1cb1a5d5288)
- [How to look for JS files Vulnerability for fun and profit?](https://medium.com/@Skylinearafat/how-to-look-for-js-files-vulnerability-for-fun-and-profit-78bfdfbd6731)

## Fuzzing
- [FuFF](https://codingo.io/tools/ffuf/bounty/2020/09/17/everything-you-need-to-know-about-ffuf.html)

## Port Scanning<br>
[<p align="center"><img src="https://user-images.githubusercontent.com/52058660/91376301-fb518580-e846-11ea-8289-173570f6b866.png" width="500"></p><br>](https://forum.hackthebox.eu/discussion/927/quick-port-scan-tip)
- Nice port: 80, 443, 8443, 4443, 4080
- [Quick Port Scan Tip](https://forum.hackthebox.eu/discussion/927/quick-port-scan-tip)
- [Masscan](https://danielmiessler.com/study/masscan/)
```
masscan -p1-65535,U:1-65535 10.10.10.x --rate=1000 -e tun0
```
- Nmap
  - By me
  ```
  sudo nmap -Pn -f -sV -p 80 10.10.10.x
  ```
  - By Naffy
  ```
  nmap -T 4 -iL hosts -Pn --script=http-title -p80,4443,4080,443 --open 
  ```
- [Dnmasscan](https://github.com/rastating/dnmasscan)
```
dnsmasscan example.txt dns.log -p80,443 -oG masscan.log
```
## Infomartion Leaked

### Github Recon

<p align="center"><img src="https://user-images.githubusercontent.com/52058660/91649439-5204cc80-ea9e-11ea-86aa-59102c5a20bf.png" width="470"> <img src="https://user-images.githubusercontent.com/52058660/91649418-208c0100-ea9e-11ea-9b0d-a642eef06a2b.png" width="470"><img src="https://user-images.githubusercontent.com/52058660/100175682-73d8e880-2f01-11eb-9f09-ea6e3bdfd5a5.png"></p><br>

- Tools
  - [Gitrob](https://michenriksen.com/blog/gitrob-now-in-go/)
  - [Github Dorks](https://github.com/techgaun/github-dorks) 
  - [Gitleaks](https://github.com/zricethezav/gitleaks) 
  - [github-search](https://github.com/gwen001/github-search) 
  - [Gdorklinks.sh](https://gist.github.com/jhaddix/1fb7ab2409ab579178d2a79959909b33)
- Bacaan
  - [Top GitHub Dorks and Tools Used to Scan GitHub Repositories for Sensitive Data](https://securitytrails.com/blog/github-dorks)
  - [GitHub Recon and Sensitive Data Exposure](https://www.youtube.com/watch?v=l0YsEk_59fQ)
  - [GitHub for Bug Bounty Hunters](https://gist.github.com/EdOverflow/922549f610b258f459b219a32f92d10b)
  - [GitHub tools collection](http://10degres.net/github-tools-collection/)

### Google Dork
- [site:yammer.com inurl:'access_token'](https://www.vulnerability-lab.com/get_content.php?id=1003)

## ASN, IP, CIDR Enumeration
  - [Amass intel](https://danielmiessler.com/study/amass/)
    ```
    amass intel -asn 12345
    amass intel -ip -src -cidr 104.154.0.0/15
    ```
  - [bgp.he.net](https://bgp.he.net)
  - [bgpview.io](https://bgpview.io)
  - [Yougetsignal](https://www.yougetsignal.com)
  - [nmap ping sweep](https://www.wildantechnoart.net/2017/06/penggunaan-ping-scanning-nmap.html)
    ```
    nmap -sn -PS/PA/PE/PP/PM/PU/PO/PR --packet-trace 192.168.100.0-10 -v
    
    ket:
    -sn -> scan no port
    -PS -> Ping Scan TCP SYN
    -PA -> Ping Scan TCP ACK
    -PE -> Ping Scan ICMP
    -PP -> Ping Scan ICMP timestamp reply 
    -PM -> Ping Scan ICMP Address mark reply
    -PU -> Ping Scan UDP
    -PO -> Ping Scan Protokol IP, menggunakan IGMP
    -PR -> Ping Scan ARP, ampuh untuk jaringan lokal
    ```
## Recon Framework
- intrigue.io
```
sudo docker run -e LANG=C.UTF-8 -v ~/intrigue-core-data:/data -p 0.0.0.0:7777:7777 -i -t intrigueio/intrigue-core:latest --privileged

```
## Wordlist
- Pre-baked:
  - [FuzzDB](https://github.com/fuzzdb-project/fuzzdb)
  - [SecLists](https://github.com/danielmiessler/SecLists)
  - [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings)
  - [all.txt](https://gist.github.com/jhaddix/86a06c5dc309d08580a018c66354a056)
  - [Commonspeak2](https://github.com/assetnote/commonspeak2-wordlists)
- Custom
  - [Who, What, Where, When, Wordlist](https://www.youtube.com/watch?v=W4_QCSIujQ4)
  - [Cewl](https://www.hackingarticles.in/comprehensive-guide-on-cewl-tool/) 

## Scanner
   - Nikto
   - [VIrus Total](https://www.virustotal.com)

## API Enumeration
[How To Do Recon: API Enumeration](https://www.youtube.com/watch?v=fvcKwUS4PTE&t=267s)
  
## Screenshot
- [Eyeofwitness](https://github.com/FortyNorthSecurity/EyeWitness)
- Aquatone

## Information Mapping
  - Company Information
    - [crunchbase](https://www.crunchbase.com)
  - Reverse whois
    - [whoxy](https://www.whoxy.com/)
    - [DOMLink](https://github.com/vysecurity/DomLink)
  - IOT search engine
    - [Shodan](https://www.shodan.io/)
  - Web Technology
    - [Buildwith](https://pro.builtwith.com/)
    - [Censys](https://censys.io/)
    - [Wappalyzer](https://www.wappalyzer.com/)

## Time Management</br>
[TomatoTimer](https://tomato-timer.com/) - Pomodoro technique

## Others
- [How To Shot Web - Jason Haddix's talk from DEFCON23](https://www.youtube.com/watch?v=VtFuAH19Qz0)
- [Hacking on Bug Bounties for Four Years](https://blog.assetnote.io/2020/09/15/hacking-on-bug-bounties-for-four-years/)
- [The Bug Hunter’s Methodology Jason Haddix @jhaddix](https://www.youtube.com/watch?v=gIz_yn0Uvb8)
- [Awesome Asset Discovery](https://github.com/redhuntlabs/Awesome-Asset-Discovery)
- [Awesome Web Security](https://github.com/qazbnm456/awesome-web-security)
- [Just another Recon Guide for Pentesters and Bug Bounty Hunters](https://www.offensity.com/de/blog/just-another-recon-guide-pentesters-and-bug-bounty-hunters/)
