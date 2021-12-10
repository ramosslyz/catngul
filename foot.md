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
menggunakan konsep three handway handshake, dimana jika port server terbuka `SYN->SYN-ACK->ACK` dan jika port server tertutup `SYN->RST-ACK`
- Nmap</br>
```
TCP connect scan, dapat direcord oleh server -> -sT
SYN scan. tidak direcord oleh server (stealthy), tp well-configured IDS masi dapat mendeteksinya -> -sS
Version scan, dapat direcord oleh server -> -sV
```

## Resource
- [INE - Penetration Testing Basics](https://my.ine.com/CyberSecurity/courses/6f986ca5/penetration-testing-basics)
