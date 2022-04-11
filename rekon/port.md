# Port Scanning<br>
[<p align="center"><img src="https://user-images.githubusercontent.com/52058660/91376301-fb518580-e846-11ea-8289-173570f6b866.png" width="500"></p><br>](https://forum.hackthebox.eu/discussion/927/quick-port-scan-tip)

## Tips
- Nice port: 80, 443, 8443, 4443, 4080
- [Quick Port Scan Tip](https://forum.hackthebox.eu/discussion/927/quick-port-scan-tip)

## Tools
### Masscan
  ```
  masscan -p1-65535,U:1-65535 10.10.10.x --rate=1000 -e tun0
  ```
### Nmap
  - By me
    ```
    sudo nmap -Pn -f -sV -p 80 10.10.10.x
    ```
  - OS fingerprinting
    ```
    nmap -Pn -O <target>
    nmap -O --oscan-limit <target>
    ```
  - By Naffy
    ```
    nmap -T 4 -iL hosts -Pn --script=http-title -p80,4443,4080,443 --open 
    ```
  - Ping sweep, cek subnetmask terlebih dahulu untuk mengetahui cangkupan sweep
    ```
    nmap -sP 192.168.1.1-255
    ```
### Dnmasscan
  ```
  dnsmasscan example.txt dns.log -p80,443 -oG masscan.log
  ```
