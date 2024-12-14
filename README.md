# SOA Projekt - Sistem za upravljanje dogodkov

## ❮🗨️ Opis projekta

Sistem za upravljanje dogodkov omogoča organizatorjem dogodkov, da učinkovito načrtujejo, upravljajo in promovirajo svoje dogodke, hkrati pa omogoča uporabnikom preprosto iskanje, rezervacijo in nakup vstopnic za dogodke.

### Glavni cilji projekta:
- Omogočiti enostavno **iskanje in rezervacijo dogodkov**.
- Organizatorjem omogočiti **upravljanje dogodkov** (vnos, urejanje in statistike).
- Zagotoviti **obveščanje uporabnikov** o novostih, spremembah in potrditvah rezervacij.

### Uporabniki sistema:
- **Obiskovalci dogodkov** – Iskanje in rezervacija dogodkov.
- **Organizatorji dogodkov** – Upravljanje dogodkov in spremljanje statistike.
- **Administratorji** – Nadzor nad celotnim sistemom.

---

## 💻 Mikrostoritve

Projekt temelji na **mikrostoritveni arhitekturi**, kjer vsaka mikrostoritev opravlja specifično nalogo in je ločeno razvita. Vse storitve uporabljajo **REST API** in **Express.js** na Node.js.

### Seznam storitev:

#### **1. User Service (Servis za uporabnike)**
- Upravljanje registracije in prijave uporabnikov (**JWT avtentikacija**).
- Profiliranje uporabnikov.
- **Primer API-jev:**
  - `POST /register` – Registracija novega uporabnika.
  - `POST /login` – Prijava uporabnika in generiranje JWT.
  - `GET /profile/:id` – Pridobitev podatkov o uporabniku.

#### **2. Event Service (Servis za dogodke)**
- Ustvarjanje, urejanje in brisanje dogodkov.
- Pridobivanje seznama dogodkov s filtriranjem.
- **Primer API-jev:**
  - `POST /events` – Ustvarjanje dogodka.
  - `GET /events` – Pridobivanje seznama dogodkov.
  - `PUT /events/:id` – Posodobitev dogodka.

#### **3. Reservation Service (Servis za rezervacije)**
- Upravljanje rezervacij in nakupov kart.
- Evidenca razpoložljivih kart.
- **Primer API-jev:**
  - `POST /reservations` – Rezervacija kart za dogodek.
  - `GET /reservations/:userId` – Pridobivanje rezervacij uporabnika.

#### **4. Notification Service (Servis za obvestila)**
- Pošiljanje obvestil uporabnikom o rezervacijah ali spremembah dogodkov.
- Integracija s storitvami za pošiljanje e-pošte ali SMS.
- **Primer API-jev:**
  - `POST /notifications` – Pošiljanje obvestila.

#### **5. Analytics Service (Servis za statistike)**
- Generiranje statističnih poročil o dogodkih (npr. število rezervacij, prodane karte).
- **Primer API-jev:**
  - `GET /analytics/:eventId` – Pridobivanje statistike za določen dogodek.

#### **6. API Gateway (Osrednji prehod)**
- Upravlja komunikacijo med mikroservisi in zagotavlja enotno vstopno točko za frontend.

---

## 📝 Skica storitev

```plaintext
                  +-------------------------+
                  |      FRONTEND           | <-- React
                  +-----------+-------------+
                              |
                              v
          +-------------------+-------------------+
          |     API Gateway (Express.js)         |
          +---------+---------+---------+--------+
                    |         |         |
     +--------------+   +-----+-----+   +--------------+
     |  User Service|   | Event Serv.|   | Reservation |
     | (Avtentikacija, | (Upravljanje|   | Service     |
     | Profiliranje)    |  dogodki)   |   | (Rezervacije)|
     +----------------+  +-----------+   +--------------+
                    |         |
                    v         v
           +-----------------------------+
           |      Notification Service   |
           | (Obvestila za uporabnike)   |
           +-----------------------------+
                    |
                    v
           +-----------------------------+
           |      Analytics Service      |
           | (Statistika o dogodkih)     |
           +-----------------------------+
```

---

## 🤵️ Razdelitev dela

| **Član skupine**            | **Naloge**                                      |
|-------------------------|------------------------------------------------|
| **Emilija Mitrović** (Frontend) | Razvoj frontenda (React/Vue) + Event Service. |
| **Maj Miklav** (Backend)     | Razvoj User Service in Reservation Service.   |
| **Nina Horvat** (Backend)    | Razvoj Notification Service in Analytics Service. |
| **Skupinsko delo**           | Integracija mikroservisov, testiranje in dokumentacija. |

---

## 🗓 Načrt razvoja

Razvoj projekta bo potekal v naslednjih fazah:

1. **Načrtovanje:**
   - Podrobna analiza funkcionalnosti.
   - Načrt strukture mikroservisov.

2. **Razvoj mikroservisov:**
   - Razvoj in testiranje posameznih mikroservisov.

3. **Razvoj frontenda:**
   - Priključitev frontenda na mikroservise prek API Gatewaya.

4. **Integracija in testiranje:**
   - Integracija vseh komponent.
   - Testiranje funkcionalnosti in odpravljanje napak.

5. **Dokumentacija in predstavitev:**
   - Zaključek dokumentacije.
   - Priprava za predstavitev projekta.

---

## 🌐 Zaključek

Sistem za upravljanje dogodkov omogoča organizatorjem in obiskovalcem prijazno platformo za upravljanje in udeležbo dogodkov. Projekt je zasnovan modularno, kar omogoča enostavno nadgradnjo in vzdrževanje.

**Tehnologije:**
- Backend: Node.js, Express.js
- Frontend: React.js / Vue.js
- Avtentikacija: JWT
- Podatkovna baza: MongoDB / MySQL

---

**⚙️ Verzija:** 1.0 
