# 🎯 Bndo APP - Dashboard Gestione Pratiche Invitalia

**Sistema completo di gestione pratiche per bandi Invitalia con interfacce Cliente e Admin**

---

## 📋 Indice

1. [Caratteristiche](#caratteristiche)
2. [Demo Live](#demo-live)
3. [Struttura Progetto](#struttura-progetto)
4. [Funzionalità Cliente](#funzionalità-cliente)
5. [Funzionalità Admin](#funzionalità-admin)
6. [Installazione](#installazione)
7. [Utilizzo](#utilizzo)
8. [Workflow Completo](#workflow-completo)
9. [Tecnologie](#tecnologie)
10. [Sviluppo Futuro](#sviluppo-futuro)

---

## ✨ Caratteristiche

### 🎨 Design
- ✅ Design moderno e professionale
- ✅ Responsive mobile-first
- ✅ Colori: Navy, Verde, Blu (palette coerente)
- ✅ Animazioni fluide e transizioni
- ✅ Tipografia Inter (Google Fonts)

### 💾 Tecnologia
- ✅ **Zero dipendenze** (no framework)
- ✅ HTML5 + CSS3 + Vanilla JavaScript
- ✅ LocalStorage per persistenza dati
- ✅ Sincronizzazione real-time tra Cliente e Admin
- ✅ File standalone (no build process)

### 🔐 Funzionalità
- ✅ Dashboard Cliente completa
- ✅ Dashboard Admin con gestione clienti
- ✅ Chat bidirezionale
- ✅ Upload documenti (simulato)
- ✅ Sistema notifiche
- ✅ Richieste pratiche con form dettagliato
- ✅ Gestione stati e avanzamento

---

## 🌐 Demo Live

### URL Deployment
```
Homepage:  https://nataleletteriatornatora-art.github.io/Bndo-demo/
Cliente:   https://nataleletteriatornatora-art.github.io/Bndo-demo/cliente.html
Admin:     https://nataleletteriatornatora-art.github.io/Bndo-demo/admin.html
```

### Credenziali Test
- **Cliente:** Nessuna autenticazione richiesta
- **Admin:** Nessuna autenticazione richiesta (da implementare in produzione)

---

## 📁 Struttura Progetto

```
Bndo-demo/
│
├── index.html          # Homepage con scelta Cliente/Admin
├── cliente.html        # Dashboard Cliente (29.8 KB)
├── admin.html          # Dashboard Admin (47.9 KB)
└── README.md           # Questo file
```

**Nota:** Tutti i file sono standalone e non richiedono build o dipendenze esterne.

---

## 👤 Funzionalità Cliente

### 📊 Dashboard Principale
- Visualizzazione pratiche attive
- Card pratiche con:
  - Nome pratica e tipo bando
  - Stato (badge colorato)
  - Progress bar avanzamento %
  - Badge documenti richiesti
  - Badge nuovi messaggi

### 🔍 Ricerca
- Barra ricerca real-time
- Filtra pratiche per nome/tipo

### ➕ Nuova Richiesta
Form dettagliato con campi:
- Tipo di Bando (dropdown)
- Nome Progetto *
- Email *
- Telefono *
- Regione *
- Budget Previsto
- Descrizione Progetto * (min 50 caratteri)
- Note Aggiuntive

**Validazione:**
- Campi obbligatori (*)
- Validazione email/telefono
- Check lunghezza descrizione

### 📄 Dettaglio Pratica

#### Tab Documenti
- Lista documenti richiesti
- Stati: ⚠ Richiesto, ⏱ In Revisione, ✓ Approvato
- Upload area (drag & drop)
- Validazione: PDF/JPG/PNG max 10MB

#### Tab Chat
- Chat bidirezionale con consulente
- Invio messaggi (Enter o bottone)
- Timestamp messaggi
- Scroll automatico

#### Tab Timeline
- Storico completo attività pratica

### 🔔 Notifiche Intelligenti
- **Click notifica "Documenti Richiesti"** → Vai a tab Documenti
- **Click notifica "Nuovi Messaggi"** → Vai a tab Chat
- Toast notifications per ogni azione

---

## 👨‍💼 Funzionalità Admin

### 🎯 Struttura a 3 Livelli

#### LIVELLO 1: Lista Clienti (Vista Principale)
**Cosa vedi:**
- Grid card clienti
- Statistiche globali:
  - Totale Clienti
  - Pratiche Attive
  - Nuove Richieste
  - Completate
- Barra ricerca clienti (nome/email)

**Ogni card cliente:**
- Nome, Email, Telefono
- Azienda
- Statistiche: Totale Pratiche, Attive, Doc Richiesti

**Azione:** Click cliente → **LIVELLO 2**

---

#### LIVELLO 2: Pratiche del Cliente
**Breadcrumb:** `Clienti › [Nome Cliente]`

**Cosa vedi:**
- Lista pratiche del cliente selezionato
- Nome cliente + email in header
- Per ogni pratica:
  - Stato e avanzamento %
  - Badge: documenti richiesti, da approvare, nuovi messaggi

**Azione:** Click pratica → **LIVELLO 3**

---

#### LIVELLO 3: Dettaglio Pratica
**Breadcrumb:** `Clienti › [Cliente] › [Pratica]`  
(Click su cliente → Torna a LIVELLO 2)

**Controlli Admin:**
- **Dropdown Stato:**
  - In Lavorazione
  - In Valutazione
  - In Approvazione
  - Completata
  - Rifiutata

- **Input Avanzamento (0-100%):**
  - Aggiornamento manuale
  - Al 100% → Auto-completa pratica

- **Bottone Richiedi Documento:**
  - Modal con form
  - Aggiunge documento a lista cliente
  - Invia notifica automatica in chat

**Tab Documenti:**
- Lista documenti pratica
- Stati visibili
- Per documenti "Da Approvare":
  - ✓ Approva → Cliente riceve messaggio conferma
  - ✗ Rifiuta → Torna a "Richiesto" + messaggio

**Tab Chat:**
- Invia messaggi al cliente
- Leggi risposte cliente
- Messaggi salvati persistenti

---

### 🔔 Nuove Richieste (Sezione Separata)

**Menu laterale con badge rosso** → Numero richieste in attesa

**Visualizzazione:**
- Tutte le richieste non approvate
- Dati completi da form cliente:
  - Tipo bando, progetto, email, telefono
  - Regione, budget
  - Descrizione completa
  - Note

**Azioni:**
- ✅ **Approva e Crea Pratica:**
  1. Crea nuovo cliente (se email non esiste)
  2. Crea pratica associata al cliente
  3. Aggiunge 4 documenti base richiesti
  4. Invia messaggio benvenuto
  5. Cliente appare in Lista Clienti

- ❌ **Rifiuta:**
  - Elimina richiesta
  - Nessun cliente/pratica creata

---

## 🚀 Installazione

### Opzione 1: GitHub Pages (Consigliata)

```bash
# 1. Clona o fork il repository
git clone https://github.com/nataleletteriatornatora-art/Bndo-demo.git

# 2. Vai nella cartella
cd Bndo-demo

# 3. Push su GitHub
git add .
git commit -m "Initial commit"
git push origin main

# 4. Abilita GitHub Pages
# Settings → Pages → Source: main branch → Save

# 5. Aspetta 1 minuto → Sito live!
```

### Opzione 2: Locale

```bash
# 1. Download file
# Scarica cliente.html e admin.html

# 2. Doppio click sui file
# Si aprono direttamente nel browser

# 3. Nessun server necessario!
```

---

## 📖 Utilizzo

### Per Clienti

1. **Apri cliente.html**
2. **Dashboard:** Vedi le tue pratiche
3. **Nuova Richiesta:** Click bottone → Compila form → Invia
4. **Dettaglio Pratica:** Click su card
   - Carica documenti richiesti
   - Chatta con consulente
5. **Notifiche:** Click per andare alla sezione specifica

### Per Admin

1. **Apri admin.html**
2. **Lista Clienti:** Vista principale
   - Cerca cliente
   - Click per vedere pratiche
3. **Nuove Richieste:** Menu laterale (badge rosso)
   - Approva → Crea cliente + pratica
   - Rifiuta → Elimina richiesta
4. **Gestione Pratica:**
   - Cambia stato
   - Aggiorna avanzamento
   - Approva/rifiuta documenti
   - Richiedi nuovi documenti
   - Chatta con cliente

---

## 🔄 Workflow Completo

### Scenario: Nuovo Cliente Richiede Pratica

```
1. CLIENTE: Apre cliente.html
2. CLIENTE: Click "Nuova Richiesta"
3. CLIENTE: Compila form (8 campi)
4. CLIENTE: Invia → Notifica "Riceverai risposta entro 24h"

5. ADMIN: Apre admin.html
6. ADMIN: Menu "Nuove Richieste" (badge: 1)
7. ADMIN: Legge richiesta completa
8. ADMIN: Click "✓ Approva e Crea Pratica"

   → Sistema crea:
   - Nuovo cliente (se email nuova)
   - Nuova pratica associata
   - 4 documenti richiesti base
   - Messaggio benvenuto in chat

9. ADMIN: Torna a "Clienti"
10. ADMIN: Vede nuovo cliente nella lista
11. ADMIN: Click su cliente → Vede pratica

12. CLIENTE: Refresh cliente.html (F5)
13. CLIENTE: Vede nuova pratica attiva
14. CLIENTE: Vede notifica "4 Documenti Richiesti"
15. CLIENTE: Click notifica → Tab Documenti
16. CLIENTE: Carica documento PDF

17. ADMIN: Refresh admin.html
18. ADMIN: Vede badge "1 doc da approvare"
19. ADMIN: Apre pratica → Tab Documenti
20. ADMIN: Click "✓ Approva"

   → Cliente riceve messaggio automatico

21. CLIENTE: Refresh → Vede messaggio "Documento approvato"
22. ADMIN: Cambia avanzamento → 50%
23. ADMIN: Richiedi nuovo documento → "Certificato Residenza"

   → Cliente riceve notifica

24. CLIENTE: Refresh → Vede nuovo documento richiesto
25. [... processo continua ...]
26. ADMIN: Avanzamento → 100%

   → Pratica auto-completata

27. CLIENTE: Refresh → Vede pratica "Completata 100%" verde
```

---

## 🛠️ Tecnologie

### Frontend
- **HTML5:** Struttura semantica
- **CSS3:** 
  - Flexbox & Grid Layout
  - Custom Properties (variabili CSS)
  - Transizioni e animazioni
  - Media queries responsive
- **JavaScript (Vanilla):**
  - ES6+ features
  - DOM manipulation
  - Event handling
  - LocalStorage API

### Tipografia & Icone
- **Font:** Inter (Google Fonts)
- **Icone:** SVG inline (Lucide/Feather style)

### Persistenza Dati
- **LocalStorage:**
  - Chiave: `bandozen_data`
  - Formato: JSON
  - Struttura:
    ```json
    {
      "clienti": [...],
      "pratiche": [...],
      "documenti": [...],
      "messaggi": [...],
      "richiesteAdmin": [...]
    }
    ```

---

## 🔒 Note di Sicurezza

### Attuale (Demo)
- ❌ Nessuna autenticazione
- ❌ Dati in LocalStorage (lato client)
- ❌ Admin accessibile pubblicamente

### Per Produzione (Da Implementare)

#### Autenticazione
```javascript
// Suggerimento: Password admin semplice
const ADMIN_PASSWORD = "tuaPassword123";

function checkAdminAccess() {
  const password = prompt("Inserisci password admin:");
  if (password !== ADMIN_PASSWORD) {
    window.location.href = "cliente.html";
  }
}
```

#### Backend API
Sostituire LocalStorage con API REST:
- Database (PostgreSQL/MySQL/MongoDB)
- Authentication JWT
- File storage (AWS S3/Cloudinary)
- Email notifications (SendGrid/Mailgun)

---

## 📈 Sviluppo Futuro

### Fase 1: Sicurezza (Priorità Alta)
- [ ] Sistema autenticazione admin
- [ ] Backend API (Node.js/Express o Django)
- [ ] Database relazionale
- [ ] Hash password (bcrypt)
- [ ] JWT tokens

### Fase 2: Funzionalità (Priorità Media)
- [ ] Upload file reale (non simulato)
- [ ] Download documenti
- [ ] Notifiche email automatiche
- [ ] Export PDF report pratiche
- [ ] Calendario scadenze
- [ ] Multi-lingua (IT/EN)

### Fase 3: UX (Priorità Bassa)
- [ ] Dashboard analytics
- [ ] Grafici avanzamento
- [ ] Filtri pratiche avanzati
- [ ] Drag & drop documenti
- [ ] Dark mode
- [ ] PWA (Progressive Web App)

### Fase 4: Scaling
- [ ] Multi-tenant (più admin)
- [ ] Ruoli e permessi
- [ ] Audit log
- [ ] Backup automatico
- [ ] CDN per static files

---

## 🐛 Troubleshooting

### Problema: Non vedo le pratiche
**Soluzione:**
```javascript
// Apri Console Browser (F12)
localStorage.clear(); // Cancella dati
location.reload(); // Ricarica pagina
```

### Problema: Modifiche admin non appaiono al cliente
**Soluzione:**
- Premi F5 (refresh) su cliente.html
- Verifica che usi stesso browser/localStorage

### Problema: File troppo grande per upload
**Soluzione:**
- Limite attuale: 10MB
- Per aumentare, modifica in cliente.html:
  ```javascript
  const maxSize = 20 * 1024 * 1024; // 20MB
  ```

---

## 👥 Contributi

Contributi benvenuti! Per favore:
1. Fork il repository
2. Crea branch feature (`git checkout -b feature/NuovaFeature`)
3. Commit modifiche (`git commit -m 'Aggiunge nuova feature'`)
4. Push al branch (`git push origin feature/NuovaFeature`)
5. Apri Pull Request

---

## 📄 Licenza

Questo progetto è rilasciato sotto licenza MIT.

---

## 📞 Supporto

Per domande o supporto:
- 📧 Email: [tua@email.com]
- 🌐 Website: [tuo-sito.com]
- 💼 LinkedIn: [tuo-profilo]

---

## 🙏 Ringraziamenti

- Design ispirato a moderne SaaS dashboards
- Palette colori: Navy (#0B1136), Verde (#22C55F), Blu (#3B82F6)
- Font Inter by Rasmus Andersson
- Icone stile Lucide/Feather

---

**Creato con ❤️ per semplificare la gestione pratiche Invitalia**

*Versione: 2.0 - Gennaio 2026*
