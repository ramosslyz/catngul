# Footprinting

- Mapping a network
- OS FIngerprinting
- Port Scanning

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
- nmap</br>
```
nmap -Pn -O <target>
nmap -O --oscan-limit <target>
```
- [p0f - offline fingerprinting](https://lcamtuf.coredump.cx/p0f3/)

## Resource
- [INE - Penetration Testing Basics](https://my.ine.com/CyberSecurity/courses/6f986ca5/penetration-testing-basics)
