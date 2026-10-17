<div align="center">

# 🎧 AscoltaTesto

**Il tuo lettore vocale personale.**
Incolla un testo o carica un PDF, scegli la voce e ascoltalo. L'app ricorda da sola dove sei arrivato.

![Versione](https://img.shields.io/badge/versione-2.2-2563eb?style=flat-square)
![PWA](https://img.shields.io/badge/PWA-installabile-4f46e5?style=flat-square)
![Offline](https://img.shields.io/badge/funziona-offline-059669?style=flat-square)
![Nessun server](https://img.shields.io/badge/nessun-server-ea580c?style=flat-square)
![JavaScript](https://img.shields.io/badge/JavaScript-vanilla-f7df1e?style=flat-square&logoColor=black)

</div>

<!--
  Aggiungi qui qualche screenshot, ad esempio:
  <p align="center"><img src="docs/lettura.png" width="260"> <img src="docs/archivio.png" width="260"></p>
-->

---

## ✨ Cosa fa

AscoltaTesto è una **Progressive Web App** in un unico file: si apre dal browser, si installa sul telefono come una vera app e legge ad alta voce i tuoi testi usando le voci già presenti sul dispositivo. Non serve registrarsi e **nessun testo lascia il tuo telefono**.

### 📥 Da dove arriva il testo
- **Incolla testo**: scrivi o incolla, con titolo facoltativo e conteggio di parole, caratteri e minuti di ascolto.
- **PDF**: anche libri interi di centinaia di pagine. Il testo viene estratto sul dispositivo, con avanzamento e pulsante Annulla.
  - toglie intestazioni e piè di pagina che si ripetono e i numeri di pagina;
  - ricompone le parole spezzate col trattino a fine riga;
  - avvisa se il PDF è una scansione fatta di sole immagini (senza testo non si può leggere).
- **TXT**: legge sia UTF-8 sia i vecchi file Windows.

### 🔊 Lettura
- **Frase per frase**, con la frase corrente evidenziata e quelle già lette attenuate.
- **Pause solo a fine frase**: la voce legge il periodo intero e non si ferma sulle virgole. Numeri (`10.000`, `3,14`), orari (`10:30`), sigle (`S.p.A.`), indirizzi web e abbreviazioni (`dott.`, `ecc.`) non vengono spezzati.
- **Frasi in coda**: la voce passa alla frase successiva senza attese, quindi la pausa tra una frase e l'altra è minima.
- Tocca una frase per ascoltare da lì; avanti e indietro di una frase; barra per spostarti nel testo.
- **Voce, velocità (0,5×–2×) e tono** a scelta, con *Prova voce*. La velocità si cambia anche con un tocco dalla schermata di lettura.
- **Timer di spegnimento** (15, 30 o 60 minuti).
- **Schermo acceso** durante l'ascolto (opzionale) e **controlli dalla schermata di blocco** del telefono.

### 🔖 Segnalibri e pagine
- **Segnalibro automatico**: riapri un testo e riparti da dove eri.
- **Segnalibri multipli** con anteprima della frase: salvane quanti vuoi, tocca per riprendere, elimina quando non servono.
- **Numero di pagina sempre visibile** in alto ("Pagina 63 di 373 · 14%"), anche mentre scorri a mano.
- Nei PDF le pagine sono **quelle vere**, con divisori nel testo e **Vai a pagina**. Negli altri testi lunghi le pagine sono stimate (circa 2000 caratteri ciascuna, indicate con la tilde).

### 🗂️ Archivio
- Testi divisi in due gruppi: **📄 PDF** e **✍️ Testi incollati e TXT**.
- Ricerca per titolo, percentuale letta, numero di frasi e di pagine.
- **Rinomina** con la matita e **play / pausa** direttamente dall'elenco: il testo in lettura è evidenziato e il suo pulsante diventa Pausa.
- **Backup** in JSON (esporta e importa, scegliendo se unire o sostituire) ed **esporta TXT** del testo aperto.

### 🎨 Aspetto
- **6 temi di colore**: Blu Notte, Tramonto, Aurora, Foresta, Rosa, Mono.
- **Chiaro / scuro** che segue il sistema, oppure scelto a mano dal menu ⋮.
- Dimensione del testo e interlinea regolabili, con anteprima.
- Schermata di lettura a tutta altezza con **tendine a scomparsa**: in alto restano pagina e avanzamento, in basso i comandi principali; il resto (titolo, Modifica, Vai a pagina, voce, timer, segnalibri, esporta) si apre con una freccia, e aprendo una tendina l'altra si chiude per lasciare spazio al testo.

### ⌨️ Comodità
- Sul computer: **Spazio** per play e pausa, **← / →** per le frasi.
- Su Android il tasto **Indietro** chiude prima menu e pannelli, poi torna alla Home.

---

## 📲 Come si usa

1. Apri l'indirizzo dell'app nel browser (consigliato Chrome su Android).
2. Dal menu **⋮** scegli **Installa app**, oppure usa *Aggiungi a schermata Home* del browser.
3. In **Home** tocca **Nuovo testo**, incolla il testo o carica un file e premi **Salva e apri**.
4. In **Lettura** premi play. Dal menu **⋮** trovi Guida, Impostazioni, Info e il cambio tema.

---

## 🗃️ Struttura del progetto

```text
.
├── index.html            # tutta l'app: HTML, CSS e JavaScript
├── manifest.json         # nome, colori e icone della PWA
├── sw.js                 # service worker: cache e funzionamento offline
├── icons/
│   ├── icon-192.png
│   ├── icon-512.png
│   ├── maskable-192.png
│   └── maskable-512.png
└── lib/                  # motore PDF (pdf.js), caricato solo quando serve
    ├── pdf.min.js
    ├── pdf.worker.min.js
    └── pdfjs-LICENSE.txt
```

I percorsi sono tutti relativi (`./`), quindi l'app funziona con qualsiasi nome di repository.

---

## 🚀 Pubblicazione su GitHub Pages

1. Copia tutti i file nella radice del repository (le cartelle `icons/` e `lib/` comprese).
2. Su GitHub vai in **Settings → Pages**, scegli il branch (`main`) e la cartella **/ (root)**.
3. Dopo qualche minuto l'app è online su `https://<utente>.github.io/<repository>/`.

> **Dopo ogni aggiornamento** apri l'app e ricaricala **due volte**: la prima scarica il nuovo service worker, la seconda lo attiva.

### Come aggiornare la versione

A ogni modifica significativa cambia **insieme** queste tre cose, con lo schema 1.0 → 1.1 → … → 2.0 → 2.1 → 2.2:

| Dove | Cosa |
|---|---|
| `index.html` | `const APP_VERSION='…'` e il commento iniziale dello script |
| `index.html` | il testo di `<span id="app-version">…</span>` (sezione Info) |
| `sw.js` | `const CACHE = 'ascoltatesto-v…'` |

---

## 🔧 Come funziona

| Argomento | Dettagli |
|---|---|
| **Voce** | Web Speech API (`speechSynthesis`): le voci sono quelle del dispositivo. Le frasi vengono messe in coda con due di anticipo per eliminare le attese. |
| **Divisione in frasi** | Si divide su `. ! ? …` e `:`; mai sulle virgole. Numeri, orari, sigle, indirizzi e abbreviazioni sono protetti. Solo oltre i 3500 caratteri una frase viene tagliata sullo spazio più vicino. I testi salvati con versioni precedenti vengono riallineati da soli (segnalibri, pagine e posizione). |
| **Dati** | Titoli, posizione, segnalibri e pagine in `localStorage` (chiave `ascoltatesto_v2`); il contenuto dei testi in **IndexedDB** (database `ascoltatesto`), così anche i libri lunghi non riempiono lo spazio. |
| **PDF** | [pdf.js](https://mozilla.github.io/pdf.js/) 3.11.174 da `lib/`. Se la cartella manca, l'app prova a caricarlo da internet (cdnjs); se non ci riesce lo segnala. |
| **Offline** | La pagina arriva prima dalla rete (così gli aggiornamenti sono immediati) e poi dalla copia salvata; tutto il resto è servito dalla cache. Vengono salvate solo risposte valide. |
| **Schermo e blocco** | Wake Lock per tenere lo schermo acceso e Media Session per i controlli multimediali, dove il browser li supporta. |

---

## ⚠️ Limiti noti

- Le **voci disponibili dipendono dal dispositivo**: se manca una voce italiana, aggiungila dalle impostazioni di sintesi vocale del telefono.
- Su alcuni telefoni la lettura può fermarsi quando lo schermo si spegne: tieni attiva l'opzione *Tieni lo schermo acceso*.
- I **PDF scansionati** (solo immagini) non si possono leggere: non c'è riconoscimento dei caratteri (OCR).
- Intestazioni e note a piè di pagina molto particolari possono restare nel testo; puoi sistemarli da *Modifica*.
- Nei testi che non sono PDF le pagine sono **stimate**, non quelle di un libro stampato.
- Alcune funzioni (schermo acceso, controlli dalla schermata di blocco) dipendono dal browser.

---

## 🔒 Privacy

Tutto avviene sul tuo dispositivo: testi, PDF, posizioni e segnalibri non vengono inviati a nessun server. L'unica connessione possibile è il caricamento di pdf.js da internet, solo se la cartella `lib/` non è presente.

---

## 🕓 Cronologia

| Versione | Novità principali |
|---|---|
| **2.2** | Tendine più compatte: Modifica e Vai a pagina affiancati, una sola tendina aperta alla volta, comandi in basso sempre completi. |
| **2.1** | Evidenziazione più pulita: angoli arrotondati, niente alone, stesso giallo in tema chiaro e scuro. |
| **2.0** | Lettura con tendine a scomparsa in alto e in basso, più spazio al testo. |
| **1.9** | Schermata di lettura a tutta altezza: pagina e avanzamento sempre visibili. |
| **1.8** | Impostazioni in due schede (Voce / Testo e colori); frasi in coda per ridurre la pausa tra una frase e l'altra. |
| **1.7** | Pause solo a fine frase; pulsante Pausa dall'archivio; Home più compatta. |
| **1.6** | Numeri e abbreviazioni non spezzano più le frasi (`10.000`); riallineamento dei testi già salvati. |
| **1.5** | Controllo di integrità sicuro, tasto Indietro corretto, schermo acceso e icone nelle notifiche migliorati. |
| **1.4** | Archivio diviso tra PDF e testi, indicatore di pagina, rinomina, pagine stimate. |
| **1.3** | Schede Incolla testo / Da file, segnalibri multipli, Vai a pagina, import TXT, interlinea, esporta TXT. |
| **1.2** | Importazione PDF e archivio su IndexedDB per i testi lunghi. |
| **1.1** | Menu ⋮, pannelli a scorrimento, dialoghi e notifiche rifatti, motore di lettura più solido. |
| **1.0** | Prima versione: incolla un testo e ascoltalo, con segnalibro e voci a scelta. |

---

## 🙌 Crediti

Creata da **Miki** con **Claude**.
Il motore PDF è [pdf.js](https://mozilla.github.io/pdf.js/) di Mozilla, distribuito con licenza Apache 2.0 (vedi `lib/pdfjs-LICENSE.txt`).
