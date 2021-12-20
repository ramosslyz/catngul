# Host Header Attack

## Resource
- [Portswigger Academy - Host Header Attack](https://portswigger.net/web-security/host-header)

## Tools
- [Para Miner](https://portswigger.net/bappstore/17d2949a985c4b7ca092728dba871943)

## Pendahuluan
host header adalah back-end website yang ingin dikunjungi oleh client. contoh:
```
GET / HTTP/1.1
Host: facebook.com <- host header
```
Dahulu satu IP hanya untuk satu domain, namun dengan berkebangnya teknologi cloud, sudah umum jika beberapa domain atau website dapat diakses menggunakan satu IP yang sama. Berikut skenario umum untuk aplikasi-aplikasi yang dapat diakses oleh IP yang sama.
  - __Virtual Host__<br>
    1 Server multiple website/aplication, biasanya menggunakan cloud based SaaS solution
  - __Routing trafic via an intermediary__<br>
    Tiap website/aplication berbeda backend server, tapi diakse melalui satu server yang sama (reverse proxy server atau load balancer)
    
## What Host Header Attack??

## Validasi??
- __Send ambigu request__
    - Inject duplicat host header
    ```
    GET /example HTTP/1.1
    Host: vulnerable-website.com
    Host: bad-stuff-here 
  
    atau dibalik
  
    GET /example HTTP/1.1
    Host: bad-stuff-here
    Host: vulnerable-website.com
    ```

    - Supply an absolute Url
    ```
    GET https://vulnerable-website.com/ HTTP/1.1
    Host: bad-stuff-here
    
    atau dengan http. bereksperimenlah dengan protokol yang berbeda, kadang menghasil hasil yang berbeda juga
    
    GET http://vulnerable-website.com/ HTTP/1.1
    Host: bad-stuff-here
    ```

    - Add line wrapping
    ```
    GET /example HTTP/1.1
     Host: bad-stuff-here <- tambahkan spasi disini
    Host: vulnerable-website.com
    ```

    - HTTP Request Smuggling
    
- __Inject host overides headers__<br>
Pada metode ini kita memanfaat reverse proxy atau load balancer yang ada pada website/application.
  ```
  GET /example HTTP/1.1
  Host: vulnerable-website.com
  X-Forwarded-Host: bad-stuff-here 
  ```
  Http header berikut juga memiliki fungsi yang sama dengan X-Forwarded-Host:<br>
    - X-Host
    - X-Forwarded-Server
    - X-Http-Host-Override
    - Forwaded
  
  


