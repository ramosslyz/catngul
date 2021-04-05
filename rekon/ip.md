# ASN, IP, CIDR Enumeration
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
