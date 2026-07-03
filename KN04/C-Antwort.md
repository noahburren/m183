# Schriftliche Antworten

## 1. Was ist der Unterschied zwischen einem selbstsignierten Zertifikat und einem CA-signierten Zertifikat?

Ein **selbstsigniertes Zertifikat** wird vom Besitzer selbst erstellt und signiert. Es gibt keine unabhängige Stelle, die dessen Echtheit bestätigt.

Ein **CA-signiertes Zertifikat** wird von einer vertrauenswürdigen Certificate Authority (CA) signiert. Browser vertrauen solchen Zertifikaten, wenn die CA in ihrem Zertifikatsspeicher hinterlegt ist.

---

## 2. Was enthält ein CSR (Certificate Signing Request) und wozu dient er?

Ein **CSR** enthält den öffentlichen Schlüssel des Servers sowie Informationen wie den Common Name (Domain oder IP), Organisation und Land.

Der CSR wird an eine Certificate Authority gesendet, damit diese die Angaben prüft und daraus ein signiertes Zertifikat erstellt.

---

## 3. Warum vertraut ein normaler Browser Ihrem selbst erstellten Zertifikat nicht, obwohl es technisch korrekt erstellt wurde?

Der Browser vertraut dem Zertifikat nicht, weil die selbst erstellte Root-CA nicht im Zertifikatsspeicher des Browsers oder Betriebssystems enthalten ist.

Technisch ist das Zertifikat korrekt erstellt, aber es fehlt das Vertrauen zu einer bekannten und anerkannten Certificate Authority.