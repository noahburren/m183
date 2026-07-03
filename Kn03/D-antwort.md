# Schriftliche Antworten

## 1. Was bewirkt HttpOnly?

HttpOnly verhindert, dass JavaScript auf den Session-Cookie zugreifen kann. Dadurch kann ein Angreifer den Cookie nicht einfach mit `document.cookie` auslesen.

Es schützt vor Session-Diebstahl durch XSS-Angriffe.

---

## 2. Was bewirkt SameSite=Strict?

SameSite=Strict sorgt dafür, dass der Cookie nur bei Anfragen von derselben Webseite mitgeschickt wird. Bei Anfragen von fremden Webseiten wird der Cookie nicht gesendet.

Es schützt vor CSRF-Angriffen.

---

## 3. Warum PASSWORD_ARGON2ID statt MD5 oder SHA-1?

PASSWORD_ARGON2ID ist speziell für Passwortspeicherung gemacht. Es ist langsam, sicher und verwendet automatisch Salt.

MD5 und SHA-1 sind zu schnell und gelten als unsicher. Angreifer können damit Passwörter viel einfacher per Brute Force oder Wörterbuchangriff knacken.