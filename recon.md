# RECONNAISSANCE :crystal_ball:

## Online Resources
- [Subdomain Enumeration: 2019 Workflow](https://0xpatrik.com/subdomain-enumeration-2019/) - By Patrik Hudak
- [How To Shot Web - Jason Haddix's talk from DEFCON23](https://www.youtube.com/watch?v=VtFuAH19Qz0) - By Jason Haddix

## Subdomain Enumeration
<p align="center"><img src="https://user-images.githubusercontent.com/52058660/90480317-43dbb580-e15a-11ea-863d-f783f7f4236f.png" width="800"></p>

- Amass - My primary subdomain enumeration tools
- Subfinder - seceond choice
- Sublist3r - third choice
- [Project Sonar Forward DNS](https://opendata.rapid7.com/sonar.fdns_v2/) - Subdomains from Rapid7 FDNS
  ```
  zcat data-sonar.gz | grep -F '.uhuy.com"' | jq -r .name | grep '.uhuy.com$' | sort | uniq
  ```
- Massdns - DNS resolver
  ```
  massdns -r ../lists/resolvers.txt -t A domain.txt -w output.txt -s 15000 -o S --flush
  ```
- Altdns - permutasi
- Gobuster - Traditional bruteforce
    
## Path Discovery

 <p align="center"><img src="https://user-images.githubusercontent.com/52058660/90960320-1335ac00-e4cb-11ea-8887-70130a069fe3.png" width="800"></p>
 
- Dirsearch</br>
  ```
  python3 dirsearch.py -u http://uhuy.com:666/ -e .asp, .aspx, .jsp, .php, .csv, .doc, .docx, .xls, .xlsx, .ppt, .pptx, .pdf, .bak, .conf, .config, .old, .sql, .jar, .rar, .zip, .tar, .tar.gz, .apk, .ipa, .cgi, .do, .htm, .html, .js, .json, .rb, .xml, .yml, .svn, .git
  ```
- Dirb
- Dirbuster
- Gau
- Gobuster

## Port Scanning
- Nmap
- Masscan

## Wordlist
- Seclist
- Fuzzdb
- Commonspeak2 - Nice for subdomain
    
## API Enumeration
[How To Do Recon: API Enumeration](https://www.youtube.com/watch?v=fvcKwUS4PTE&t=267s) - by InsiderPhD
  
## Screen Shooter
Eyeofwitness

## Time Management</br>
[TomatoTimer](https://tomato-timer.com/) - Pomodoro technique

