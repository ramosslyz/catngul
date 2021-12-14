# Footprinting

**Table of content**
1. Mapping a network
2. OS FIngerprinting
3. Port Scanning

## Mapping a Network
Misalkan saat kita melakukan pentest, kita diberi scope berupa ip block sebagai berikut 200.200.0.0/16. 
```
range -> 200.200.0.0 - 200.200.255.255
2^16 -> 65536 host
```
Kita harus menentukan dari host-host tersebut mana saja yang aktif (assign to node). Salah satu caranya adalah dengan pingsweep.
- [fping](https://github.com/schweikert/fping)</br>
```
fping -a -g 200.200.0.0/16
fping -a -g 200.200.0.0 200.200.0.255
fping -a -g 200.200.0.0 200.200.0.255 2>/dev/null
```
- nmap</br>
```
nmap -sn 200.200.0.*
nmap -sn 200.200.0.1-12
nmap -sn 200.200.0.0/16
```
## OS Fingerprinting
Send network requests to the live host and then analyze the responses you get back, like: routers, firewalls, hosts, servers, printers, and so on..
- Nmap</br>
```
nmap -Pn -O <target>
nmap -O --oscan-limit <target>
```
- [p0f - offline fingerprinting](https://lcamtuf.coredump.cx/p0f3/)

## Port Scanning
menggunakan konsep Three Way Handshake
- Nmap</br>
  - TCP Connect Scan, jika terkoneksi `SYN->SYN+ACK->ACK->RST+ACK`, jika tidak terkoneksi `SYN->RST+ACK`. Dapat direcord oleh server
    ```
    nmap -sT <target>
    ```
  - TCP Connect Scan, jika terkoneksi `SYN->SYN+ACK->RST`, jika tidak terkoneksi `SYN->RST+ACK`. Tidak direcord oleh server (stealthy), tp well-configured IDS masi dapat mendeteksinya
    ```
    nmap -sS <target>
    ```
  - Version detection scan, tcp connect scan dengan banner grabbing
    ```
    nmap -sV <target>
    ```
Berikut adalah beberapa port umum yang mendikasikan bahwa port tersebut alive: 22, 445, 80, 443
Anda harus memperhitungkan firewal, berikut adalah tanda-tanda bahwa firewall menghambat port scannning
- Nmap scanning tidak selesai, nmap seharusnya tidak akan kesusahan untuk sV (banner grabbing) pada host. Pada host yang menggunakan firewall, version nya tidak dikenali. untuk menganalisanya gunakan `--reason`
- State status adalah filtered, kemungkinan ada IDS atau firewall

## Resource
- [INE - Penetration Testing Basics](https://my.ine.com/CyberSecurity/courses/6f986ca5/penetration-testing-basics)
