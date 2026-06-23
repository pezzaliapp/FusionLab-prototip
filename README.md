# FusionLab ⚛️ — PWA

> Accendere una stella in tasca: muovi i parametri, raggiungi il break-even (**Q ≥ 1**).

FusionLab è un'app installabile (PWA) che funziona **offline**. Contiene tre livelli sicuri:

- **Simulatore** — sfida la fisica del plasma (temperatura, densità, confinamento, campo magnetico, perdite) fino all'accensione.
- **Manuale** — come costruire davvero la console-gioco, in piccolo e sicuro (5 V, LED).
- **ABC** — la fisica spiegata in modo semplice.

> **La regola d'oro:** si simula e si costruisce *il gioco* — il reattore reale no.

---

## Cosa c'è in questa cartella

| File | A cosa serve |
|------|--------------|
| `index.html` | L'app completa (un unico file autosufficiente). |
| `manifest.webmanifest` | Rende l'app installabile (nome, icone, colori). |
| `sw.js` | Service worker: salva l'app per l'uso **offline**. |
| `icons/` | Le icone dell'app (192, 512, maskable). |
| `.nojekyll` | Serve i file così come sono, senza elaborazioni. |

Tutti i percorsi sono **relativi**, quindi l'app funziona sia alla radice del sito sia in una sottocartella.

---

## Installare l'app

Apri il link dell'app su telefono o desktop:

- **Android / Chrome / Edge:** comparirà *«Installa app»* (o menu ⋮ → *Installa*).
- **iPhone / Safari:** tasto *Condividi* → *Aggiungi a Home*.
- **Desktop:** icona di installazione ⊕ nella barra degli indirizzi.

Dopo la prima apertura online, l'app resta disponibile **offline**.

---

## Aggiornare l'app

Quando modifichi `index.html` (o altri file), cambia **una riga** in `sw.js`:

```js
const CACHE = 'fusionlab-v1';   // → 'fusionlab-v2', 'fusionlab-v3', ...
```

Così i dispositivi già installati scaricano la nuova versione invece di servire quella vecchia dalla cache.

---

## Note tecniche

- Il service worker richiede **HTTPS**: va bene qualunque hosting che lo fornisca. In locale funziona solo via `http://localhost` (non aprendo il file con doppio clic `file://`).
- Per provare in locale: `python3 -m http.server` nella cartella, poi apri `http://localhost:8000`.
