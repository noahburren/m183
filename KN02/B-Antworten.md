## 1. SQL-Statement vor und nach dem Einschleusen des Payloads (B1)

**Vor der SQL Injection:**

```sql
SELECT * FROM users
WHERE name = 'Smith'
AND password = 'passwort';
```

**Nach dem Payload `' OR '1'='1`:**

```sql
SELECT * FROM users
WHERE name = 'Smith'
AND password = '' OR '1'='1';
```

**Erklärung:**

Der Ausdruck `'1'='1'` ist immer wahr. Dadurch wird die gesamte WHERE-Bedingung wahr und die Datenbank liefert alle passenden Datensätze zurück. Die Anwendung interpretiert dies als erfolgreichen Login, obwohl das richtige Passwort nicht bekannt ist. Dadurch wird die Authentifizierung umgangen.

---

## 2. Wie funktionieren Prepared Statements? Warum verhindern sie SQL Injection?

Prepared Statements (parameterisierte Abfragen) trennen den SQL-Befehl von den Benutzereingaben.

Beispiel:

```sql
SELECT * FROM users
WHERE name = ?
AND password = ?;
```

Die Datenbank kompiliert die SQL-Abfrage zuerst. Anschliessend werden die Benutzereingaben als reine Werte an die Platzhalter (`?`) übergeben. Dadurch werden Sonderzeichen wie `'`, `;` oder `--` nicht mehr als SQL-Code interpretiert, sondern als normaler Text behandelt.

Deshalb kann ein Angreifer keinen zusätzlichen SQL-Code einschleusen, wodurch SQL Injection verhindert wird.

---

## 3. OWASP Top 10 (2025)

**A03:2025 – Injection**

Diese Kategorie umfasst Schwachstellen, bei denen Benutzereingaben als Befehle oder Abfragen interpretiert werden. SQL Injection ist eines der bekanntesten Beispiele dafür.

---

## 4. Zwei weitere Injection-Varianten

### OS Command Injection

- **Was wird injiziert?** Betriebssystembefehle (z. B. `ls`, `cat`, `rm`).
- **Gefahr:** Ein Angreifer kann beliebige Befehle auf dem Server ausführen, Dateien lesen oder löschen oder sogar die vollständige Kontrolle über das System erlangen.

### LDAP Injection

- **Was wird injiziert?** LDAP-Abfragen an Verzeichnisdienste wie Active Directory.
- **Gefahr:** Ein Angreifer kann Suchabfragen manipulieren, Authentifizierungen umgehen oder auf vertrauliche Benutzer- und Verzeichnisdaten zugreifen.