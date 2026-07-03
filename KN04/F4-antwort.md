# Schriftliche Antworten

## 1. Welche Passwörter wurden geknackt, welche nicht? Was unterscheidet die knackbaren Passwörter von Franks Passwort?

Folgende Passwörter wurden erfolgreich geknackt:

| Benutzer | Passwort |
|----------|----------|
| alice | sunshine |
| bob | dragon |
| carol | iloveyou |
| dave | letmein |

Nicht geknackt wurden:

- **eve**
- **frank**

Franks Passwort lautet **`correcthorsebatterystaple`**. Es wurde nicht gefunden, weil es **nicht in der verwendeten Wortliste** enthalten ist. Die geknackten Passwörter sind dagegen häufig verwendete Wörter oder bekannte Passwörter, die in vielen Passwortlisten vorkommen.

---

## 2. Das Script hat nur 20 Wörter geprüft. Die bekannte rockyou.txt-Wortliste hat 14 Millionen Einträge. Schätzen Sie anhand der gemessenen Hashes/Sekunde: Wie lange würde der gleiche Angriff mit rockyou.txt dauern?

Gemessene Geschwindigkeit:

- **162'886 Hashes pro Sekunde**

Berechnung:

```text
14'000'000 ÷ 162'886 ≈ 86 Sekunden
```

Der Angriff würde mit der vollständigen **rockyou.txt** also nur etwa **86 Sekunden (ca. 1 Minute 26 Sekunden)** dauern.

---

## 3. Franks Passwort ist lang und steht in keiner Wortliste – trotzdem ist der MD5-Hash grundsätzlich knackbar. Welche zwei Massnahmen aus KN04 machen gestohlene Hashes unbrauchbar?

1. **Salt verwenden**

   Für jedes Passwort wird ein zufälliger Salt erzeugt und mit dem Passwort gespeichert. Dadurch haben gleiche Passwörter unterschiedliche Hashes und Rainbow Tables oder vorberechnete Hashlisten funktionieren nicht mehr.

2. **Moderne Passwort-Hashfunktion (Argon2ID)**

   Statt MD5 sollte eine sichere Passwort-Hashfunktion wie **Argon2ID** verwendet werden. Argon2ID ist absichtlich langsam und rechenaufwendig, wodurch Brute-Force- und Wörterbuchangriffe erheblich erschwert werden.