# AES-GCM Demo

## Programm

```python
import os
from cryptography.hazmat.primitives.ciphers.aead import AESGCM

# Schlüssel generieren (256 Bit = 32 Bytes)
key = AESGCM.generate_key(bit_length=256)
aesgcm = AESGCM(key)

# Nonce generieren (96 Bit = 12 Bytes, einmalig pro Verschlüsselung)
nonce = os.urandom(12)

# Klartextnachricht
plaintext = b"Dies ist eine geheime Nachricht fuer M183!"

# Verschlüsseln
ciphertext = aesgcm.encrypt(nonce, plaintext, None)

print(f"Klartext:        {plaintext.decode()}")
print(f"Schlüssel (hex): {key.hex()}")
print(f"Nonce (hex):     {nonce.hex()}")
print(f"Ciphertext (hex): {ciphertext.hex()}")
print(f"Ciphertext-Länge: {len(ciphertext)} Bytes\n")

# Entschlüsseln
decrypted = aesgcm.decrypt(nonce, ciphertext, None)
print(f"Entschlüsselt:   {decrypted.decode()}")

# Manipulations-Test
tampered = bytearray(ciphertext)
tampered[0] ^= 0xFF

try:
    aesgcm.decrypt(nonce, bytes(tampered), None)
except Exception as e:
    print(f"\nManipulations-Test: {e}")
    print("→ GCM-Modus hat die Manipulation erkannt!")
```

---

# Konsolenausgabe

```text
Klartext:        Dies ist eine geheime Nachricht fuer M183!
Schlüssel (hex): 46af6e0dd09b759ea57c3a5035290e5be3f8c6d8f3c3124032b85518fdab69c6
Nonce (hex):     df9b8d4dfbbd8cdb796669b9
Ciphertext (hex): ba4c5fa3d91af6ab4f4f959c3e20de2b6899344755b6f4c1280a1d92db73d299118aa3ec5768faf16899da66c278f73ad917792da8c5980ccf8f
Ciphertext-Länge: 58 Bytes

Entschlüsselt:   Dies ist eine geheime Nachricht fuer M183!

Manipulations-Test:
→ GCM-Modus hat die Manipulation erkannt!
```

---

# Beobachtung

Die Nachricht wurde erfolgreich mit **AES-256-GCM** verschlüsselt und anschliessend wieder korrekt entschlüsselt.

Der Klartext nach der Entschlüsselung stimmt vollständig mit dem ursprünglichen Text überein.

---

# Manipulations-Test

Anschliessend wurde das erste Byte des Ciphertexts absichtlich verändert:

```python
tampered[0] ^= 0xFF
```

Beim Entschlüsseln erkannte AES-GCM die Veränderung sofort und brach den Vorgang ab.

Es wurde folgende Meldung ausgegeben:

```text
→ GCM-Modus hat die Manipulation erkannt!
```

---

# Erklärung

AES-GCM bietet zwei wichtige Sicherheitsfunktionen:

- **Vertraulichkeit (Confidentiality):** Der Klartext wird verschlüsselt und kann ohne Schlüssel nicht gelesen werden.
- **Integrität (Integrity):** Jede Veränderung am Ciphertext wird erkannt. Manipulierte Daten werden nicht entschlüsselt.

---

# Fazit

AES-GCM ist ein moderner und sicherer Verschlüsselungsmodus, da er gleichzeitig:

- Daten verschlüsselt,
- die Integrität schützt,
- Manipulationen automatisch erkennt.

Dadurch eignet sich AES-GCM besonders für sichere Anwendungen wie HTTPS, VPNs oder verschlüsselte Kommunikation.