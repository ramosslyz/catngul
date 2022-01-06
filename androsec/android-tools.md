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
adb logcat | grep "$(adb shell ps | grep com.senyumkubank.rekeningonline.rc | awk '{print $2}')" -> melihat android system log
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

## Objection
```
Harus ada frida server dahulu
objection -g <nama-packages> explore , lalu pilih env, akan menampilkan data direktori env
```


## Memorydump
- r2frida
- fridump
- objection

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
- jwt_tool
- drozer

## Reverse
- radare2
- r2frida
- http://apk-deguard.com/
- Jadx
  ```
  jadx -deobf
  ```

## Log Analysis
- Pidcat
- adb logcat

## SSL pinng
- refluuter

## Dynamic Analysis Online
- appetize.io
