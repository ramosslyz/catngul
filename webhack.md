# Flow Hacking

## Web Hacking</br>
1. Pre engagement -> menentukan target dan scop apa saja yang akan kita pentest (web server, mobile, IOT, dll)
   - Tipe penetration test yang dilakukan ? (Black/Gray/White)
   - Berapa lama waktu penetration test ?
   - Bagaimana kompleksitas dari aplikasi dan servis yang akan dipentest ?
   - Berapa jumlah target yang akan dipentest ? (IP address, domain dll)
2. Reconnaissance -> menggali informasi sebanyak-banyaknya mengenai target dan menentukan device apa saja yang berpotensi dapat exploitasi
   - Information Gathering (Social Enginnering) -> Nama dan email, Investor, Struktur manajerial, Lokasi dan branch
   - Understanding company bussiness -> Core bisninya apa?, Menentukan apa yang critical dan vital bagi client
   - Infrastructure -> IP address & IP block, Domain & Subdomain, Operation system, DNS
   - Web Application (harus dipisah sendiri) -> Domain, Subdomain, Path/direktori, Teknologi, Framework
3. Footprinting & Scanning -> Menggali informasi lebih dalam mengenari OS dan servis
   - Fingerprinting OS (Check potential vulnerability based on OS version)
   - Port Scanning (Egress Checking)
   - Detecting service yang berjalan diport tersebut (cek UDP/TCP)
4. Vulnerability Assessment -> menentukan vulnerability apa saja yang ada berdasarkan target yang sudah ditemukan pada langkah sebelumnya, dapat menggunakan tools dan info dari outdated version of technology
   - Manual - menggunakan data dari step sebelumnya
   - Automated tools - menggunakan tools seperti nessus
5. Exploitation -> Mengecek kebeneraran vulnerability target berdasarkan data yang didapat dari vulnerability assessment. Proses pengecekan selesai jika tidak ada lagi system dan service pada scop yang akan di exploit|
6. Post Exploitation -> melakukan privillege escallation atau gain permanent access dari device yang telah berhasil kita exploitasi
7. Reporting -> membuat report berdasarkan temuan yang telah berhasil dan memberikan solusi bagaimana mengatasi temuan tersebut. Ingat solusi dan remediasi lebih diapresiasi dibandingkan skill yang anda gunakan!!!
   - Report -> Teknik yang digunakan, Vulnerability yang ditemukan, Eksploit yang digunakan, Impact dan resiko dari vulnerability yang ditemuka, Remedial tips dan rekomendasi dari masing-masing vulnerability
   - Presentasi ->


## Resource
## Web Hacking
   - [INE-Penetration Testing Student](https://my.ine.com/CyberSecurity/learning-paths/a223968e-3a74-45ed-884d-2d16760b8bbd/penetration-testing-student)
   - [A Starters Guide to Pentesting with OWASP](https://www.youtube.com/watch?v=AO_sqXb-gKE)
   - [Burp Testing Methodologies](https://portswigger.net/support/burp-testing-methodologies)
