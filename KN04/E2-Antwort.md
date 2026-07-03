# Schriftliche Antworten

## 1. Was genau ist im tcpdump-Output sichtbar? Markieren Sie die Zeile, die das Passwort im Klartext enthält.

Im `tcpdump`-Output ist der komplette HTTP-Request im Klartext sichtbar. Dazu gehören unter anderem:

- HTTP-Methode (POST)
- Zielpfad
- Host
- Header
- Formulardaten (Benutzername und Passwort)

Die Zeile mit dem Passwort lautet:

```text
username=admin&password=sunshine
```

Hier ist das Passwort **sunshine** unverschlüsselt im Klartext sichtbar.

---

## 2. Was müsste ein Angreifer in einem realen Netzwerk tun, um diesen Traffic mitzulesen?

Ein Angreifer müsste sich zwischen den Client und den Server schalten, also einen **Man-in-the-Middle (MitM)-Angriff** durchführen.

Eine häufige Methode dafür ist **ARP-Spoofing**. Dabei täuscht der Angreifer den Geräten im lokalen Netzwerk vor, dass sein eigener Computer der Router ist. Dadurch wird der gesamte Netzwerkverkehr über den Angreifer geleitet und kann mitgelesen werden.

Bei unverschlüsseltem HTTP können dabei Benutzernamen, Passwörter und andere Daten im Klartext ausgelesen werden.