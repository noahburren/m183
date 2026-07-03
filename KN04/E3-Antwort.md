# Schriftliche Antworten

## 1. Was ist der Unterschied zwischen dem tcpdump-Output auf Port 80 und Port 443? Was sieht ein Angreifer beim HTTPS-Traffic?

Bei **Port 80 (HTTP)** ist der gesamte Datenverkehr unverschlüsselt. Ein Angreifer kann den HTTP-Request inklusive Benutzername und Passwort direkt im Klartext lesen.

Bei **Port 443 (HTTPS)** ist der Datenverkehr verschlüsselt. Im tcpdump sind nur TLS-Handshake-Daten und verschlüsselte Bytes zu sehen. Benutzername, Passwort und andere Inhalte können nicht gelesen werden.

---

## 2. Was passiert beim TLS-Handshake, bevor die eigentlichen Daten übertragen werden?

Beim TLS-Handshake tauschen Client und Server zunächst Informationen aus und überprüfen das Server-Zertifikat.

Anschliessend wird mithilfe der **asymmetrischen Verschlüsselung** ein gemeinsamer Sitzungsschlüssel sicher ausgetauscht.

Erst danach werden die eigentlichen Daten (z. B. Benutzername und Passwort) mit einer schnellen **symmetrischen Verschlüsselung (AES)** übertragen. Dieses Verfahren nennt man **hybride Verschlüsselung**.

---

## 3. Sie sehen bei Port 443 noch immer die IP-Adressen von Client und Server im tcpdump-Output. Warum ist das so, obwohl die Verbindung verschlüsselt ist?

Die IP-Adressen gehören zum Netzwerkprotokoll (IP) und müssen sichtbar bleiben, damit die Daten überhaupt zwischen Client und Server übertragen werden können.

HTTPS verschlüsselt nur den **Inhalt der Verbindung** (z. B. HTTP-Anfragen und Antworten), nicht aber die Informationen, die für das Routing im Netzwerk benötigt werden, wie die Quell- und Ziel-IP-Adresse.