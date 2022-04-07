# ANDROID HACKING

## Tips
- Decompile apk, grep -nr https:// atau http
- Cek androidmanifest.xml, ferivy debuggable, allowbackup
- Cek activity exported, jika true coba panggil activity nya menggunakan adb
- Cek strings.xml, cari sensitif data (grep secret, apisecret, api_secret tergantung kreativitas anda)
- Cek firebaseio
- Cek shell android, cek db, shared_pref,
- Cek root detection, bypass root detection dengan magisk dan module nya
- Cek sensitif data di memory dump
- Jalankan aplikasi di dua device android, tukarkan shared_pref antar device tersebut apakah akun nya juga berubah ?
- Cek ssl pinning, bypass ssl pinning dengan frida atau objection
- Scan apk dengan mobsf
- Cek apakah ui app ngeblur saat kita melihat current running app
- Cari string base64, biasanya diawali dengan base64.decode("<string>")

## Learn Frida
- [Learning Frida](https://nibarius.github.io/learning-frida/)
- [Introduction to Frida](https://medium.com/infosec-adventures/introduction-to-frida-5a3f51595ca1)
- [Hacking Android Apps with Frida](https://www.youtube.com/watch?v=iMNs8YAy6pk&t=1s)
  
## Learn Ghidra
- [How to use Ghidra to Reverse Engineer Mobile Application](https://infosecwriteups.com/how-to-use-ghidra-to-reverse-engineer-mobile-application-c2c89dc5b9aa)
