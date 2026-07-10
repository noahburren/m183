## 1. Was ist der zentrale Unterschied zwischen Reflected XSS und Stored XSS hinsichtlich Persistenz und Reichweite?

**Reflected XSS** wird nicht dauerhaft gespeichert. Der schädliche Code wird nur als Teil einer Anfrage (z. B. über einen manipulierten Link) zurückgegeben und betrifft nur Benutzer, die diesen Link öffnen.

**Stored XSS** wird dauerhaft auf dem Server gespeichert (z. B. in Kommentaren oder Datenbanken). Jeder Benutzer, der die betroffene Seite besucht, führt den Schadcode aus. Dadurch ist die Reichweite deutlich grösser.

---

## 2. Was unterscheidet DOM-based XSS von Reflected XSS – warum ist DOM-based XSS für serverseitige Filter schwieriger zu erkennen?

Bei **Reflected XSS** wird der Schadcode vom Server in der HTTP-Antwort zurückgegeben.

Bei **DOM-based XSS** verarbeitet der Browser den Schadcode vollständig clientseitig über JavaScript und schreibt ihn direkt in den DOM. Der Server sieht den Schadcode nie und kann ihn deshalb nicht filtern. Dadurch ist DOM-based XSS für serverseitige Schutzmechanismen schwieriger zu erkennen.

---

## 3. Was bedeutet Output Encoding und warum schützt es gegen XSS? Geben Sie ein konkretes Beispiel, wie `<script>` nach dem Encoding aussieht.

**Output Encoding** bedeutet, dass Sonderzeichen vor der Ausgabe in HTML in ihre HTML-Entitäten umgewandelt werden. Dadurch interpretiert der Browser die Eingabe als normalen Text statt als ausführbaren Code.

Beispiel:

```html
<script>
```

wird zu:

```html
&lt;script&gt;
```

Der Browser zeigt dann lediglich `<script>` als Text an und führt kein JavaScript aus.

---

## 4. Was ist der HTTP-Header Content-Security-Policy (CSP) und wie schränkt er XSS ein?

**Content-Security-Policy (CSP)** ist ein HTTP-Header, der festlegt, aus welchen Quellen Inhalte wie JavaScript, CSS oder Bilder geladen werden dürfen.

Dadurch können beispielsweise Inline-Skripte oder Skripte von unbekannten Webseiten blockiert werden. Selbst wenn ein Angreifer JavaScript einschleusen kann, verhindert CSP häufig dessen Ausführung.

---

## 5. Welche OWASP Top 10 Kategorie (2021) beschreibt XSS? Nennen Sie Nummer und Bezeichnung.

Cross-Site Scripting (XSS) gehört in den **OWASP Top 10 (2021)** zur Kategorie:

- **A03:2021 – Injection**

XSS wird seit 2021 nicht mehr als eigene Kategorie geführt, sondern ist Teil der Kategorie **Injection**, da dabei schädlicher Code in eine Anwendung eingeschleust wird.