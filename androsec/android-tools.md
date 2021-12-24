# Tools

## adb
```
adb devices -> list device
adb shell -> masuk ke device
adb shell pm list packages -> list semua package aplikasi yang terinstall
adb shell pm path <namaPackageTanpa.apk>
adb install <namaPackage> -> install aplikasi
adb push foo.txt /sdcard/foo.txt -> copy dari local pc ke android
adb pull /sdcard -> copy dari android ke local pc
adb -s <emualator> shell -> pilih emulator tertentu
adb shell am start -n b3nac.injuredandroid/.b25lActivity -> menjalankan activity tertentu
```
## apktool
```
apktool d <namafileapk>
```

## Frida
```
adb root
adb push frida-server /data/local/tmp
adb shell "chmod 755 /data/local/tmp/frida-server"
adb shell "/data/local/tmp/frida-server &"

frida-ps -U -> melihat aplikasi apa saja yang berjalan (nanti akan ada PID)
frida-trace -U -i open Calendar -> melacak aktivitas aplikasi calendar

```

## Other
- MobSF
- Frida
- Objection
- Termux
- Mobexler
- Android Studio's built-in Device File Explorer
- Magisk -> Root Android device
- RootAVD -> Root Android emulator
- ghidra
