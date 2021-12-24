# Penetration Testing, Step by Step</br>
|Step|Deskripsi|
|---|---|
|Pre engagement|menentukan target dan scop apa saja yang akan kita pentest (web server, mobile, IOT, dll)|
|Reconnaissance|menggali informasi sebanyak-banyaknya mengenai target dan menentukan device apa saja yang berpotensi dapat exploitasi|
|Footprinting & Scanning|Menggali informasi lebih dalam mengenari OS dan servis|
|Vulnerability Assessment|menentukan vulnerability apa saja yang ada berdasarkan target yang sudah ditemukan pada langkah sebelumnya, dapat menggunakan tools dan info dari outdated version of technology|
|Exploitation|Mengecek kebeneraran vulnerability target berdasarkan data yang didapat dari vulnerability assessment. Proses pengecekan selesai jika tidak ada lagi system dan service pada scop yang akan di exploit|
|Post Exploitation|melakukan privillege escallation atau gain permanent access dari device yang telah berhasil kita exploitasi|
|Reporting|membuat report berdasarkan temuan yang telah berhasil dan memberikan solusi bagaimana mengatasi temuan tersebut. Ingat solusi dan remediasi lebih diapresiasi dibandingkan skill yang anda gunakan!!!|

## Engagement
1. Tipe penetration test yang dilakukan ? (Black/Gray/White)
2. Berapa lama waktu penetration test ?
3. Bagaimana kompleksitas dari aplikasi dan servis yang akan dipentest ?
4. Berapa jumlah target yang akan dipentest ? (IP address, domain dll)

## Reconnaisance
1. Information Gathering (Social Enginnering)
    - Nama dan email
    - Investor
    - Struktur manajerial
    - Lokasi dan branch
2. Understanding company bussiness
    - Core bisninya apa?
    - Menentukan apa yang critical dan vital bagi client
4. Infrastructure
    - IP address & IP block
    - Domain & Subdomain 
    - Operation system
    - DNS
5. Web Application (harus dipisah sendiri)
    - Domain
    - Subdomain
    - Path/direktori
    - Teknologi
    - Framework

## Footprinting & Scanning
1. Fingerprinting OS
    - Check potential vulnerability based on OS version
2. Port Scanning
    - Egress Checking
3. Detecting service yang berjalan diport tersebut
    - cek UDP/TCP

## Vulnerability Assessment
1. Manual
    - menggunakan data dari step sebelumnya
2. Automated tools
    - menggunakan tools seperti nessus

## Exploitation

## Post Exploitation

## Reporting
1. Report
    - Teknik yang digunakan
    - Vulnerability yang ditemukan
    - Eksploit yang digunakan
    - Impact dan resiko dari vulnerability yang ditemuka
    - Remedial tips dan rekomendasi dari masing-masing vulnerability 
- Presentasi

## Tips N Trick
- Widening the attack surface more valuable than exploiting the target
- Solusi dan remediasi lebih dibutuhkan dibandingkan pamer skill hacking
- Information gathering and Reconnaisance is a key
- Cek consol (f12)
- Selalui cek reflected setelah injeksi dimasukkan

## Resource
- [INE-Penetration Testing Student](https://my.ine.com/CyberSecurity/learning-paths/a223968e-3a74-45ed-884d-2d16760b8bbd/penetration-testing-student)
- [A Starters Guide to Pentesting with OWASP](https://www.youtube.com/watch?v=AO_sqXb-gKE)
