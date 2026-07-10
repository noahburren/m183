## 1. Warum schickt der Browser den Session-Cookie mit, wenn die Anfrage von `csrf-attack.html` (einer lokalen Datei) kommt – obwohl das Opfer diese Seite nie bewusst besucht hat?

Der Browser sendet den **Session-Cookie automatisch** an die Ziel-Domain, für die der Cookie gespeichert wurde. Entscheidend ist nicht, von welcher Seite die Anfrage stammt, sondern an welche Domain sie gesendet wird. Ist der Benutzer noch bei WebGoat eingeloggt, wird der Session-Cookie automatisch mitgeschickt und der Server betrachtet die Anfrage als authentifiziert.

---

## 2. Was ist ein CSRF-Token und warum kann eine Angreifer-Seite ihn nicht einfach aus dem Formular lesen?

Ein **CSRF-Token** ist ein zufällig erzeugter, geheimer Wert, der in jedes Formular oder jede sicherheitsrelevante Anfrage eingebettet wird. Der Server prüft bei jeder Anfrage, ob der Token gültig ist.

Eine Angreifer-Seite kann den Token nicht auslesen, weil die **Same-Origin-Policy** verhindert, dass JavaScript Inhalte einer fremden Webseite oder deren Formulare lesen kann. Dadurch kennt der Angreifer den benötigten Token nicht und kann keine gültige Anfrage erzeugen.

---

## 3. Was bewirkt das `SameSite=Strict`-Flag bei einem Cookie und wie schützt es vor CSRF?

Das Cookie-Attribut **`SameSite=Strict`** sorgt dafür, dass der Browser Cookies **nur bei Anfragen von derselben Website (Same Site)** mitsendet.

Wird eine Anfrage von einer fremden Webseite oder einer lokalen HTML-Datei ausgelöst, wird der Session-Cookie nicht übertragen. Dadurch kann der Server den Benutzer nicht authentifizieren und der CSRF-Angriff schlägt fehl.

---

## 4. Welche OWASP Top 10 Kategorie (2025) beschreibt CSRF am ehesten? Nennen Sie Nummer und Bezeichnung.

CSRF gehört in den **OWASP Top 10:2025** zur Kategorie:

- **A01:2025 – Broken Access Control**

Die Kategorie umfasst unter anderem **CWE-352 (Cross-Site Request Forgery)**, da CSRF dazu führt, dass unberechtigte Aktionen im Namen eines angemeldeten Benutzers ausgeführt werden können. :contentReference[oaicite:0]{index=0}