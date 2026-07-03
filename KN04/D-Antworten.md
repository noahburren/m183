# Schriftliche Antworten

## 1. Welche Informationen zeigt der Browser im Zertifikat-Dialog? Was davon haben Sie selbst in Aufgabe C definiert?

Der Browser zeigt unter anderem folgende Informationen an:

- **Allgemeiner Name (CN):** `18.207.166.235`
- **Organisation (O):** `TBZ-M183`
- **Aussteller (Issuer):** `M183 Root CA`
- **Organisation des Ausstellers:** `TBZ-M183-CA`
- **Gültigkeitsdauer:** 03.07.2026 bis 03.07.2027
- **Zertifikats-Fingerprint**
- **Öffentlicher Schlüssel**

Selbst definiert wurden:
- der **Common Name (CN)** des Servers,
- die **Organisation (O)**,
- der **Name der Root-CA**,
- die **Gültigkeitsdauer** des Zertifikats.

---

## 2. Warum erscheint trotz technisch korrektem Zertifikat eine Sicherheitswarnung?

Das Zertifikat ist technisch korrekt erstellt und gültig. Der Browser zeigt trotzdem eine Warnung, weil die verwendete **Root-CA nicht zu den vertrauenswürdigen Zertifizierungsstellen des Browsers gehört**.

Da die CA selbst erstellt wurde und nicht im Zertifikatsspeicher des Betriebssystems oder Browsers hinterlegt ist, kann der Browser die Echtheit des Zertifikats nicht automatisch bestätigen.

---

## 3. Erklären Sie anhand dieses Setups, wie hybride Verschlüsselung bei HTTPS funktioniert.

HTTPS verwendet eine **hybride Verschlüsselung**, also eine Kombination aus asymmetrischer und symmetrischer Kryptografie.

1. Der Server sendet sein Zertifikat mit dem **öffentlichen Schlüssel** an den Browser.
2. Der Browser überprüft das Zertifikat und verwendet den öffentlichen Schlüssel, um einen gemeinsamen Sitzungsschlüssel sicher auszutauschen.
3. Nach dem Schlüsselaustausch werden alle weiteren Daten mit einer **symmetrischen Verschlüsselung (z. B. AES)** übertragen.

Die **asymmetrische Verschlüsselung** wird nur für den sicheren Schlüsselaustausch verwendet, da sie rechenaufwendig ist. Die eigentliche Datenübertragung erfolgt mit **symmetrischer Verschlüsselung**, weil diese deutlich schneller ist.