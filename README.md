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
| `.nojekyll` | Dice a GitHub Pages di servire i file così come sono. |

Tutti i percorsi sono **relativi**, quindi l'app funziona anche in una sottocartella (es. `tuonome.github.io/FusionLab/`).

---

## Pubblicare su GitHub Pages (ottenere il link)

### Metodo A — dal sito, senza terminale (consigliato)

1. Vai su **github.com** → **New repository**. Dai un nome, es. `FusionLab`. Mettilo **Public**. Crea.
2. Nella pagina del repo clicca **Add file → Upload files**.
3. Trascina **tutto** il contenuto di questa cartella (`index.html`, `manifest.webmanifest`, `sw.js`, la cartella `icons/`, e `.nojekyll`). ⚠️ Carica i *file*, non la cartella che li contiene: alla radice del repo devi vedere direttamente `index.html`.
4. **Commit changes**.
5. Vai in **Settings → Pages**. Sotto *Build and deployment* scegli **Deploy from a branch**, branch **`main`**, cartella **`/ (root)`**. Salva.
6. Dopo ~1 minuto in cima alla pagina Pages comparirà il link:
   **`https://TUONOME.github.io/FusionLab/`** ← questo è il link da condividere.

### Metodo B — da terminale (git)

```bash
cd fusionlab                      # entra nella cartella con i file
git init
git add .
git commit -m "FusionLab PWA"
git branch -M main
git remote add origin https://github.com/TUONOME/FusionLab.git
git push -u origin main
```

Poi attiva le Pages come al passo 5 del Metodo A.

---

## Installare l'app

Apri il link su telefono o desktop:

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

- Il service worker richiede **HTTPS**: GitHub Pages lo fornisce automaticamente. In locale funziona solo via `http://localhost` (non aprendo il file con doppio clic `file://`).
- Per provare in locale: `python3 -m http.server` nella cartella, poi apri `http://localhost:8000`.
