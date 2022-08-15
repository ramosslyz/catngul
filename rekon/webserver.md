# Web Server
Fingerprinting Web server merupakan kegiatan untuk menentukan jenis dan versi web server yang sedang berjalan. Dengan menemukan jenis web server tempat aplikasi berjalan, pentester dapat menentukan apakah aplikasi rentan terhadap vulnerabilty tertentu. Umumnya, server yang menggunakan aplikasi lama rentan terhadap well-know eksploit.

## How to
- Salah satu cara untuk menentukan tipe dan tipe web server adalah dengan banner grabbing pada response header yang dapat dilakukan dengan menggunakan aplikasi burp suite, telnet, dan ssh request.
- Mengirimkan malformed request, biasanya akan menghasilkan error pada response body yang mempubliKASIKAN teknology apa yang digunakan pada server.
- Menggunakan automation tools, seperti nikto dan nmap

## Risk
Meskipun informasi jenis dan tipe server bukan merupakan sebuah vulnerability, informasi tersebut dapat membantu hacker dalam mengeksploitasi kerentanan lain yang mungkin ada. Informasi mengenai tipe dan jenis server yang terekspos dapat mengarahkan hacker untuk menemukan vulnerability server tertentu yang dapat digunakan untuk mengeksploitasi server yang belum dipatch.

## Rekomendasi
- Menghilangkan informasi server pada header
- Menggunakan reverse proxy server
- Memastikan server up-to-date
