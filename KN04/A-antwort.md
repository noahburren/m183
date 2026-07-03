# Schriftliche Antworten

## 1. Wie viele Versuche und wie viele Sekunden hat der Angriff benötigt? Was würde passieren, wenn die Passwortliste statt 20 Einträgen 1 Million hätte?

Der Angriff benötigte **13 Versuche** und **0.08 Sekunden**, um das Passwort **sunshine** zu finden.

Würde die Passwortliste statt 20 Einträgen **1 Million Passwörter** enthalten (z. B. `rockyou.txt`), würde der Angriff deutlich länger dauern. Ohne Schutzmechanismen könnte ein Angreifer trotzdem viele Passwörter automatisch ausprobieren und schwache Passwörter oft erfolgreich finden.

---

## 2. Welche zwei technischen Massnahmen hätten diesen Angriff verhindert oder erschwert?

1. **Rate Limiting / Login-Verzögerung**  
   Nach mehreren fehlgeschlagenen Anmeldeversuchen werden weitere Versuche verlangsamt oder für eine gewisse Zeit blockiert.

2. **Kontosperrung nach mehreren Fehlversuchen**  
   Nach einer bestimmten Anzahl falscher Passwörter wird das Benutzerkonto vorübergehend gesperrt oder eine zusätzliche Verifizierung (z. B. CAPTCHA oder MFA) verlangt.

---

## 3. Warum ist das Passwort `sunshine` schwach?

Obwohl **sunshine** nicht so offensichtlich ist wie **password** oder **123456**, handelt es sich um ein häufig verwendetes englisches Wort. Solche Wörter befinden sich in vielen Passwortlisten wie **rockyou.txt** und werden deshalb bei Wörterbuch- oder Brute-Force-Angriffen schnell gefunden.

Ein starkes Passwort sollte:
- lang sein (mindestens 12–16 Zeichen),
- Gross- und Kleinbuchstaben, Zahlen und Sonderzeichen enthalten,
- kein Wörterbuchwort oder häufig verwendetes Passwort sein.