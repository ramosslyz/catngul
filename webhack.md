# Flow Hacking

## Web Hacking</br>
|Step|Deskripsi|Steps|
|---|---|---|
|Pre engagement|menentukan target dan scop apa saja yang akan kita pentest (web server, mobile, IOT, dll)|<ul><li>Tipe penetration test yang dilakukan ? (Black/Gray/White)</li><li>Berapa lama waktu penetration test ?</li><li>Bagaimana kompleksitas dari aplikasi dan servis yang akan dipentest ?</li><li>Berapa jumlah target yang akan dipentest ? (IP address, domain dll)</ul>|
|Reconnaissance|menggali informasi sebanyak-banyaknya mengenai target dan menentukan device apa saja yang berpotensi dapat exploitasi|<ul><li>Information Gathering (Social Enginnering)</li><ul><li>Nama dan email</li><li>Investor</li><li>Struktur manajerial</li><li>Lokasi dan branch</li></ul><li>Understanding company bussiness</li><ul><li>Core bisninya apa?</li><li>Menentukan apa yang critical dan vital bagi client</li></ul><li>Infrastructure</li><ul><li>IP address & IP block</li><li>Domain & Subdomain</li><li>Operation system</li><li>DNS</li></ul><li>Web Application (harus dipisah sendiri)</li><ul><li>Domain</li><li>Subdomain</li><li>Path/direktori</li><li>Teknologi</li><li>Framework</li></ul></ul>|
|Footprinting & Scanning|Menggali informasi lebih dalam mengenari OS dan servis|<ul><li>Fingerprinting OS (Check potential vulnerability based on OS version)</li><li>Port Scanning (Egress Checking)</li><li>Detecting service yang berjalan diport tersebut (cek UDP/TCP)</li></ul>
|Vulnerability Assessment|menentukan vulnerability apa saja yang ada berdasarkan target yang sudah ditemukan pada langkah sebelumnya, dapat menggunakan tools dan info dari outdated version of technology|<ul><li>Manual - menggunakan data dari step sebelumnya</li><li>Automated tools - menggunakan tools seperti nessus</li></ul>|
|Exploitation|Mengecek kebeneraran vulnerability target berdasarkan data yang didapat dari vulnerability assessment. Proses pengecekan selesai jika tidak ada lagi system dan service pada scop yang akan di exploit|
|Post Exploitation|melakukan privillege escallation atau gain permanent access dari device yang telah berhasil kita exploitasi|
|Reporting|membuat report berdasarkan temuan yang telah berhasil dan memberikan solusi bagaimana mengatasi temuan tersebut. Ingat solusi dan remediasi lebih diapresiasi dibandingkan skill yang anda gunakan!!!|<ul><li>Report</li><ul><li>Teknik yang digunakan</li><li>Vulnerability yang ditemukan</li><li>Eksploit yang digunakan</li><li>Impact dan resiko dari vulnerability yang ditemuka</li><li>Remedial tips dan rekomendasi dari masing-masing vulnerability</li></ul><li>Presentasi</li></ul>|


## Resource
- [INE-Penetration Testing Student](https://my.ine.com/CyberSecurity/learning-paths/a223968e-3a74-45ed-884d-2d16760b8bbd/penetration-testing-student)
- [A Starters Guide to Pentesting with OWASP](https://www.youtube.com/watch?v=AO_sqXb-gKE)
- [Burp Testing Methodologies](https://portswigger.net/support/burp-testing-methodologies)
