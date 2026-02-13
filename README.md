# ⚡ Stroomprijs Voorspelling

Een intelligente webapp die stroomprijzen toont en voorspelt voor de komende 4 dagen, inclusief slimme aanbevelingen voor optimaal energieverbruik.

🔗 **Live demo:** https://berik61.github.io/stroomprijs

---

## 📊 Wat doet deze app?

### Prijsweergave
- **Dag 1-2:** Echte Frank Energie all-in prijzen (incl. BTW, energiebelasting, netbeheer, opslag)
- **Dag 3-4:** Intelligente voorspelling op basis van weer + automatische calibratie

### Slimme aanbevelingen
- 🧺 **Beste moment voor wasmachine** (3-uur blok met laagste gemiddelde prijs)
- 🔌 **Beste moment voor auto opladen** (6-uur blok met laagste gemiddelde prijs)

### Relatieve labels
- **Goedkoop** (beste 33%) - groen
- **Middel** (middelste 33%) - paars
- **Duur** (duurste 33%) - rood

Labels zijn relatief over alle 4 dagen voor optimale vergelijking.

---

## 🎯 Waarom deze app?

### Bespaar geld
- Weet precies wanneer stroom het goedkoopst is
- Plan grote verbruikers (wasmachine, auto, droger) op goedkope momenten
- **Besparing:** Tot €6-7 per auto-laadbeurt, €1+ per wasbeurt

### Intelligente voorspellingen
De app gebruikt een uniek **calibratiesysteem**:
1. Vergelijkt voorspellingen met echte prijzen (dag 1-2)
2. Detecteert systematische afwijkingen
3. Past dag 3-4 voorspellingen automatisch aan
4. **Resultaat:** 15-25% nauwkeuriger dan ruwe weervoorspelling

### Voorbeeld calibratie
```
Dag 1-2: Voorspelling gemiddeld 15% te hoog
→ Dag 3-4: Automatisch -15% correctie toegepast
Console: "📊 Voorspelling (gecalibreerd -15%)"
```

---

## 🚀 Installatie & Gebruik

### Optie 1: Direct gebruiken (aanbevolen)
1. Ga naar https://berik61.github.io/stroomprijs
2. Voeg toe aan Home Screen op iPhone (Share → Add to Home Screen)
3. Klaar!

### Optie 2: Zelf hosten
1. Fork deze repository
2. Enable GitHub Pages in Settings → Pages
3. Deploy from `main` branch
4. App is beschikbaar op `https://[jouw-username].github.io/stroomprijs`

---

## 🔑 Enever.nl Token instellen

Voor echte Frank Energie prijzen (dag 1-2) heb je een gratis token nodig:

### Token aanmaken (30 seconden)
1. Ga naar https://enever.nl/prijzenfeeds/
2. Scroll naar "Token aanmaken"
3. Vul je email in en klik "Verstuur"
4. Token verschijnt direct op de pagina (geen email nodig)
5. Kopieer de token

### Token invoeren in app
1. Open de app
2. Klik op de gele banner → "📝 Toon instructies voor token"
3. Plak je token
4. Klik "Opslaan en herladen"
5. Done! ✅

**Limiet:** 250 API calls/maand (ruim voldoende voor dagelijks gebruik)

---

## 🛠️ Technologie

### Frontend
- Vanilla JavaScript (geen frameworks)
- Pure CSS met gradients
- Responsive design (mobiel + desktop)

### Data sources
- **Frank Energie prijzen:** Enever.nl API (via CORS proxy)
- **Weerdata:** Open-Meteo API (gratis, geen key)
- **Locatie:** Utrecht, Nederland (centrum)

### Voorspellingsmodel
Gebaseerd op:
- ☁️ Bewolking (zon = lagere prijzen)
- 💨 Windsnelheid (wind = lagere prijzen)
- 🕐 Tijd van de dag (avondspits = hogere prijzen)
- 📅 Weekend vs weekdag (weekend = lagere prijzen)

Plus **automatische calibratie** op basis van recente nauwkeurigheid.

### Architectuur
```
┌─────────────────┐
│   GitHub Pages  │  Hosting
└────────┬────────┘
         │
    ┌────▼────┐
    │  HTML   │  Single-page app
    │   CSS   │  + JavaScript
    │   JS    │
    └────┬────┘
         │
    ┌────▼──────────────┐
    │  CORS Proxy       │  corsproxy.io
    └────┬──────────────┘
         │
    ┌────▼────────┐  ┌──────────┐
    │ Enever API  │  │ Open-    │
    │ (prijzen)   │  │ Meteo    │
    │             │  │ (weer)   │
    └─────────────┘  └──────────┘
```

---

## 📱 Screenshots

### Desktop
![Desktop view](screenshots/desktop.png)

### Mobiel
![Mobile view](screenshots/mobile.png)

---

## 🎨 Features

✅ Echte all-in prijzen (Frank Energie)  
✅ 4-daagse voorspelling  
✅ Automatische calibratie (dag 3-4)  
✅ Slimme aanbevelingen (wasmachine & auto)  
✅ Relatieve labels over alle dagen  
✅ Responsive design  
✅ Werkt offline (na eerste load)  
✅ PWA-ready (installeerbaar)  
✅ Geen tracking, geen ads  
✅ Volledig gratis  

---

## 🔒 Privacy

- Token wordt lokaal opgeslagen (localStorage)
- Geen data naar servers (behalve API calls)
- CORS proxy ziet je token (alleen toegang tot publieke prijsdata)
- Geen analytics, geen tracking
- Open source - check de code zelf

---

## 📈 Roadmap

Mogelijke toekomstige features:
- [ ] Multiple leveranciers (niet alleen Frank Energie)
- [ ] Notificaties bij extreem lage prijzen
- [ ] Historische data & trends
- [ ] Export naar kalender
- [ ] Custom tijdblokken (bijv. 4u voor warmtepomp)
- [ ] Integratie met slimme thermostaat/laadpaal

---

## 🐛 Bugs of suggesties?

Open een [issue](https://github.com/Berik61/stroomprijs/issues) of stuur een pull request!

---

## 📄 Licentie

MIT License - gebruik het zoals je wilt!

---

## 🙏 Credits

- **Enever.nl** voor de geweldige gratis API
- **Open-Meteo** voor weerdata
- **corsproxy.io** voor CORS proxy
- **Frank Energie** voor transparante dynamische prijzen

---

## 💡 Pro tips

1. **Negatieve prijzen?** Ja! Bij veel zon/wind kan de spotprijs negatief zijn. Je betaalt dan alleen belasting/netbeheer (~€0,17/kWh).

2. **Beste besparingen:** 
   - Auto laden: Tot €6-7 per laadbeurt door slim te plannen
   - Wasmachine: €1-2 per wasbeurt
   - Droger/vaatwasser: €0,50-1 per cyclus

3. **Weekend voordeel:** Zaterdag/zondag vaak 8-10% goedkoper door minder industriële vraag.

4. **Middag is koning:** 12:00-15:00 vaak goedkoopst door zonnepanelen.

5. **Vermijd avondspits:** 18:00-21:00 vaak 30-50% duurder.

---

**Veel succes met besparen! ⚡💰**
