
Project Work in **Tecnologia web per la sostenibilità d'impresa**. Corso di laurea in **Informatica per le aziende digitali (L-31)**, Università Telematica Pegaso.

> ⚠️ **Nota:** questo è un progetto accademico con finalità didattiche. Il sito si ispira al modello cooperativo di **CONAPI (CONsorzio Nazionale APIcoltori)**, ma non è affiliato al sito ufficiale e non lo sostituisce.

---

## Indice

- [Descrizione del progetto](#descrizione-del-progetto)
- [Obiettivi](#obiettivi)
- [Struttura del sito](#struttura-del-sito)
- [Tecnologie utilizzate](#tecnologie-utilizzate)
- [Struttura delle cartelle](#struttura-delle-cartelle)
- [Funzionalità JavaScript](#funzionalità-javascript)
- [Design e stile](#design-e-stile)
- [Responsive design e accessibilità](#responsive-design-e-accessibilità)
- [Come avviare il progetto](#come-avviare-il-progetto)
- [Fonti dei dati](#fonti-dei-dati)
- [Licenza](#licenza)

---

## Descrizione del progetto

Il progetto è un **sito web one-page dimostrativo** che mostra come le tecnologie web possono comunicare la sostenibilità di un'impresa. Il caso di studio è **CONAPI**, la più grande cooperativa apistica d'Europa, fondata nel 1979, con oltre 600 apicoltori e più di 100.000 alveari in Italia.

Il sito presenta il modello cooperativo, le attività della filiera del miele (dall'apiario alla tavola) e i principali indicatori **ESG** (ambientali, sociali e di governance) tratti dal primo Bilancio di Sostenibilità della cooperativa. Offre inoltre un collegamento diretto al report ufficiale in PDF.

## Obiettivi

- Comunicare in modo chiaro e trasparente l'impegno di un'impresa verso la sostenibilità.
- Rendere i dati del bilancio di sostenibilità leggibili e coinvolgenti tramite indicatori visivi e contatori animati.
- Realizzare un sito leggero, veloce e responsive, senza framework complessi né processi di build.
- Applicare buone pratiche di sviluppo web: HTML semantico, CSS con variabili, JavaScript modulare e attenzione all'accessibilità.

## Struttura del sito

Il sito è composto da un'unica pagina ([index.html](index.html)) divisa in sezioni, raggiungibili dal menu di navigazione:

| Sezione | Ancora | Contenuto |
|---|---|---|
| **Banner accademico** | — | Chiarisce la natura didattica e non ufficiale del sito |
| **Header / Navbar** | `#top` | Logo esagonale in SVG, nome del consorzio e menu (con versione "hamburger" su mobile) |
| **Home** | `#home` | Titolo, descrizione della filiera, pulsanti di invito all'azione e numeri chiave animati (apicoltori, alveari, tonnellate di miele) |
| **Chi siamo** | `#chi-siamo` | Storia del consorzio, modello di filiera corta e controllata, punti di forza, Mission e Valori |
| **Attività** | `#attivita` | Sei schede sulle fasi della filiera: produzione, controllo e lavorazione, biologico, prodotti dell'alveare, commercializzazione, ricerca e biodiversità |
| **Parametri di crescita** | `#parametri` | Indicatori di sostenibilità (governance, comunità, ambiente, parità di genere, riduzione CO₂) e sezione "Verso il futuro" |
| **Report** | `#report` | Link per scaricare il Bilancio di Sostenibilità 2024/2025 ufficiale |
| **Footer** | — | Link rapidi, canali social ufficiali (LinkedIn, sito web, Facebook) e anno aggiornato automaticamente |

## Tecnologie utilizzate

- **HTML5** – struttura semantica (`header`, `nav`, `main`, `section`, `article`, `footer`).
- **CSS3** – foglio di stile personalizzato con variabili CSS (custom properties), CSS Grid, Flexbox e media query.
- **JavaScript (ES6+)** – codice vanilla, senza librerie esterne.
- **Bootstrap 5.3** (via CDN) – foglio di stile di base.
- **Font Awesome 6** (via CDN) – icone dei social nel footer.
- **Google Fonts** – *Fraunces* per i titoli e *Inter* per il testo.

## Struttura delle cartelle

```
ProjectWork_Unipegaso_L31-Demo/
├── index.html          # Pagina principale del sito
├── css/
│   └── style.css       # Foglio di stile personalizzato
├── js/
│   └── script.js       # Script: menu mobile, anno nel footer, contatori animati
├── img/
│   ├── logo.png        # Favicon
│   └── img_header.png  # Immagine della sezione Home
├── LICENSE             # Licenza MIT
├── .gitignore
└── README.md
```

## Funzionalità JavaScript

Il file [js/script.js](js/script.js) si avvia all'evento `DOMContentLoaded` ed esegue tre funzioni:

1. **`initMobileNav()`** – gestisce il menu "hamburger" su schermi piccoli: apre e chiude il menu, aggiorna l'attributo `aria-expanded` per gli screen reader e chiude il menu quando si clicca su un link.
2. **`setFooterYear()`** – inserisce automaticamente l'anno corrente nel copyright del footer.
3. **`initCounters()`** – anima i numeri con attributo `data-count` (e suffisso opzionale `data-suffix`, es. `+`, `%`, ` t`). L'animazione parte solo quando il numero entra nell'area visibile, grazie all'**IntersectionObserver**, dura circa 1,4 secondi con effetto di rallentamento finale (*ease-out*) e formatta i numeri in stile italiano (es. `100.000`).

## Design e stile

La palette richiama il mondo dell'apicoltura e della natura ed è definita come variabili in `:root` dentro [css/style.css](css/style.css):

| Variabile | Colore | Uso |
|---|---|---|
| `--color-forest` / `--color-forest-dark` | Verde bosco | Titoli, sezioni scure, footer |
| `--color-amber` / `--color-amber-dark` | Ambra / miele | Pulsanti, evidenziazioni, sezioni alternate |
| `--color-bg` / `--color-cream` | Crema | Sfondo generale e schede |

Tra gli elementi grafici principali:

- **logo esagonale** in SVG, che richiama la cella del favo;
- **header fisso** (*sticky*) con effetto sfocato sullo sfondo;
- **schede** con leggero sollevamento al passaggio del mouse;
- **pulsanti** arrotondati con transizioni morbide;
- **scorrimento fluido** tra le sezioni (`scroll-behavior: smooth`).

## Responsive design e accessibilità

Il layout si adatta a tre fasce di schermo:

- **Desktop** (oltre 900px): griglie a 3 colonne, Home e "Chi siamo" su due colonne.
- **Tablet** (fino a 900px): griglie a 2 colonne, layout a colonna singola per le sezioni divise.
- **Smartphone** (fino a 640px): menu a scomparsa con pulsante "hamburger" e griglie a colonna singola.

Accorgimenti per l'accessibilità:

- attributi `aria-label`, `aria-expanded` e `aria-controls` sul menu e sui link social;
- `aria-hidden="true"` sugli elementi puramente decorativi (icone, logo);
- testo alternativo (`alt`) sulle immagini;
- link esterni aperti in una nuova scheda con `rel="noopener noreferrer"` per sicurezza.

## Come avviare il progetto

Il sito è statico e non richiede installazioni né processi di build.

**Opzione 1 – Apertura diretta:** fare doppio clic su `index.html` per aprirlo nel browser.

**Opzione 2 – Server locale (consigliato):** dalla cartella del progetto, con Python installato:

```bash
python -m http.server 8000
```

Poi aprire `http://localhost:8000` nel browser. In alternativa si può usare l'estensione **Live Server** di Visual Studio Code.

> È necessaria una connessione a Internet per caricare font, icone e Bootstrap dai CDN.

## Fonti dei dati

I dati e gli indicatori riportati nel sito provengono dal primo **Bilancio di Sostenibilità di CONAPI** («Il nostro volo verso la sostenibilità», esercizio 2024/2025), riadattati a fini didattici per il Project Work.

- Sito ufficiale: [conapi.it](https://conapi.it/)
- Report ufficiale: [CONAPI Bilancio di Sostenibilità 2024-2025 (PDF)](https://conapi.it/wp-content/uploads/2026/06/CONAPI_Bilancio-di-Sostenibilita_2024-2025.pdf)

Marchi, nomi e dati citati appartengono ai rispettivi proprietari.

## Licenza

Il codice è distribuito con **licenza MIT**. Per i dettagli si veda il file [LICENSE](LICENSE).