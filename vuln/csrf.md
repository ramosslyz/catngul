# CSRF

Cross Site Request Forgery / Onelink Attack adalah serangan yang memaksa pengguna agar backend mengeksekusi perintah yang tidak seharusnya dizinkan, menipu website dari request user yang terpercaya dan mengirim Request palsu dari authenticate user.

## How to find them ?
```
The easiest way to check whether an application is vulnerable is to see if each link and form contains an unpredictable token for each user. Without such an unpredictable token, attackers can forge malicious requests. Focus on the links and forms that invoke state-changing functions, since those are the most important CSRF targets.
```
- Gunakan burpsuite untuk melihat dan merubah csrf token yang terkandung pada HTTP request
- Gonta-ganti method, POST ke GET, atau sebaliknya. Periksa kevalidan csrf token
- Hapus csrf token
- Contoh Payload,
  ```
  <form method="$method" action="$url">
    <input type="hidden" name="$param1name" value="$param1value">
  </form>
  <script>
    document.forms[0].submit();
  </script>
  ```

## Sumber
- [Portswigger Academy - Cross-site request forgery (CSRF)](https://portswigger.net/web-security/csrf)

## Write-up
- [CSRF at Kaskus.co.id](https://medium.com/@daffailhamr/csrf-at-kaskus-co-id-f8e31864807f)
