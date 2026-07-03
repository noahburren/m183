# Sicherheitslücken in `index.php`

## 1. Passwort wird nicht geprüft
**Problem:**  
Das eingegebene Passwort (`$_POST['password']`) wird beim Login nicht überprüft. Jeder Benutzer kann sich mit einem beliebigen Passwort anmelden.

**Verletztes Schutzziel / OWASP:**  
- **CIA:** Confidentiality (Vertraulichkeit)
- **OWASP:** A07 – Identification and Authentication Failures

---

## 2. Admin-Rechte nur anhand des Benutzernamens
**Problem:**  
Wenn als Benutzername `admin` eingegeben wird, erhält der Benutzer automatisch die Rolle `admin`. Es findet keine Berechtigungsprüfung statt.

**Verletztes Schutzziel / OWASP:**  
- **CIA:** Integrity (Integrität)
- **OWASP:** A01 – Broken Access Control

---

## 3. Session-ID wird nach dem Login nicht erneuert
**Problem:**  
Nach erfolgreichem Login wird keine neue Session-ID erstellt (`session_regenerate_id(true)` fehlt). Dadurch ist ein Session-Fixation-Angriff möglich.

**Verletztes Schutzziel / OWASP:**  
- **CIA:** Confidentiality und Integrity
- **OWASP:** A07 – Identification and Authentication Failures

---

## 4. Session-Daten werden angezeigt
**Problem:**  
Mit `var_dump($_SESSION)` werden alle Session-Daten direkt auf der Webseite ausgegeben. Dadurch können vertrauliche Informationen sichtbar werden.

**Verletztes Schutzziel / OWASP:**  
- **CIA:** Confidentiality (Vertraulichkeit)
- **OWASP:** A02 – Cryptographic Failures / Sensitive Data Exposure

---

## 5. Kein CSRF-Schutz
**Problem:**  
Die Formulare für Login, Logout und Speichern besitzen keinen CSRF-Token. Dadurch können Anfragen von einer fremden Webseite im Namen des Benutzers ausgeführt werden.

**Verletztes Schutzziel / OWASP:**  
- **CIA:** Integrity (Integrität)
- **OWASP:** A01 – Broken Access Control (CSRF)