# Host Header Attack

## Pendahuluan
host header adalah back-end website yang ingin dikunjungi oleh client. contoh:
```
GET / HTTP/1.1
Host: facebook.com <- host header
```
Dahulu satu IP hanya untuk satu domain, namun dengan berkebangnya teknologi cloud, sudah umum jika beberapa domain atau website dapat diakses menggunakan satu IP yang sama. Berikut skenario umum untuk aplikasi-aplikasi yang dapat diakses oleh IP yang sama.
  - Virtual Host<br>
    1 Server multiple website/aplication, biasanya menggunakan cloud based SaaS solution
  - Routing trafic via an intermediary<br>
    Tiap website/aplication berbeda backend server, tapi diakse melalui satu server yang sama (reverse proxy server atau load balancer)
