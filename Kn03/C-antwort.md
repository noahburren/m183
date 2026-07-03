# Session-Fixation – Beobachtung

## 1. Was ist passiert?
Nachdem die Session-ID (PHPSESSID) aus dem ersten Browser in den zweiten Browser übernommen wurde, verwendeten beide Browser dieselbe Session. Nach dem Login im ersten Browser war der zweite Browser ebenfalls automatisch angemeldet und konnte auf dieselben Session-Daten zugreifen.

---

## 2. Konnte der zweite Browser auf die Session des ersten zugreifen?
Ja. Beide Browser verwendeten dieselbe Session-ID und hatten dadurch Zugriff auf dieselbe Session mit allen gespeicherten Daten (Benutzername, Rolle und weitere Session-Inhalte).

---

## 3. Warum ist das ein Sicherheitsproblem?
Ein Angreifer könnte einem Opfer eine bekannte Session-ID unterjubeln oder eine Session-ID stehlen. Meldet sich das Opfer anschliessend an, kann der Angreifer dieselbe Session verwenden und erhält Zugriff auf das Benutzerkonto, ohne das Passwort zu kennen. Dies ist ein **Session-Fixation-Angriff**.

---

## 4. Welche eine Massnahme hätte diesen Angriff verhindert?
Nach einem erfolgreichen Login muss die Session-ID erneuert werden, z. B. mit:

```php
session_regenerate_id(true);
```

Dadurch erhält der Benutzer nach dem Login eine neue Session-ID. Eine zuvor bekannte oder gestohlene Session-ID wird ungültig und kann nicht mehr für den Angriff verwendet werden.