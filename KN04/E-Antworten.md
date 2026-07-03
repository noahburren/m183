## Was zeigt nmap über Port 80 und Port 443? Welche Information erhält ein Angreifer bereits durch einen Port-Scan, bevor er auch nur eine einzige Anfrage an die App gestellt hat?

Der Port-Scan zeigt:

- **Port 80:** geöffnet, HTTP-Dienst mit **Apache httpd 2.4.67 (Debian)**
- **Port 443:** geöffnet, HTTPS-Dienst mit **nginx 1.31.2**

Zusätzlich erkennt Nmap:
- Das Betriebssystem ist **Linux**.
- Auf **Port 22** läuft **OpenSSH 9.6p1**.

Ein Angreifer erhält dadurch bereits wichtige Informationen, ohne die Webanwendung direkt anzugreifen:

- welche **Ports** geöffnet sind,
- welche **Dienste** laufen (HTTP, HTTPS, SSH),
- welche **Software und Versionen** verwendet werden (Apache, nginx, OpenSSH),
- welches **Betriebssystem** vermutlich eingesetzt wird.

Mit diesen Informationen kann ein Angreifer gezielt nach bekannten Sicherheitslücken oder Exploits für die erkannten Softwareversionen suchen und seine Angriffe entsprechend vorbereiten.