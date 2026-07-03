# Mehrfaktorauthentifizierung (MFA)

## Tabelle

| Kategorie | Beschreibung | Beispiel 1 | Beispiel 2 |
|-----------|--------------|------------|------------|
| **Wissen** | Etwas, das Sie wissen | Passwort | PIN |
| **Besitz** | Etwas, das Sie besitzen | Smartphone mit Authenticator-App | Sicherheitsschlüssel (z. B. YubiKey) |
| **Inhärenz** | Etwas, das Sie sind | Fingerabdruck | Gesichtserkennung |
| **Ort** | Wo Sie sich befinden | Anmeldung aus dem Firmennetzwerk | GPS-Standort (z. B. Schweiz) |

---

# Antworten

## 1. Ist die Kombination «Passwort + PIN» echtes MFA?

**Nein.**

Passwort und PIN gehören beide zur Kategorie **Wissen**. Da keine unterschiedlichen Faktoren kombiniert werden, handelt es sich nur um eine Zwei-Schritt-Authentifizierung, aber nicht um echte Mehrfaktorauthentifizierung.

---

## 2. Ist die Kombination «Passwort + SMS-Code» echtes MFA?

**Ja.**

Das Passwort gehört zur Kategorie **Wissen**, der SMS-Code zur Kategorie **Besitz**, da der Benutzer Zugriff auf sein Mobiltelefon haben muss. Es werden zwei unterschiedliche Faktoren kombiniert und somit handelt es sich um echte MFA.

---

## 3. AWS STS (Security Token Service)

AWS STS ähnelt am meisten dem Prinzip **Besitz**.

Der Benutzer erhält ein **temporäres Sicherheitstoken**, das nur für eine begrenzte Zeit gültig ist. Wer dieses Token besitzt, kann sich damit authentifizieren. Nach Ablauf verliert es automatisch seine Gültigkeit und muss neu angefordert werden. Dadurch wird die Sicherheit erhöht und das Risiko bei einem kompromittierten Zugang reduziert.