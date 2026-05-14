# Advisory Board Dashboard

Template riutilizzabile per dashboard di advisory board medici/scientifici.  
Cambia solo `data.json` — la dashboard si aggiorna automaticamente.

## Struttura del progetto

```
advisory-dashboard/
├── index.html      ← template dashboard (non modificare)
├── data.json       ← dati del meeting (modifica questo ad ogni meeting)
└── README.md
```

## Come usarlo per un nuovo meeting

1. Apri `data.json`
2. Sostituisci tutti i contenuti con l'output del tuo AskFred
3. Salva — la dashboard è aggiornata

### Struttura di `data.json`

```json
{
  "meta": {
    "title": "Advisory Board Dashboard",
    "subtitle": "Nome del meeting",
    "topic": "Argomento clinico",
    "date": "2025"
  },
  "evidenze": [
    {
      "titolo": "Titolo breve (max 5 parole)",
      "descrizione": "Finding clinico chiave (max 12 parole)",
      "fonte": "Nome studio, anno"
    }
    // ... fino a 5 evidenze
  ],
  "temi": [
    { "nome": "Nome tema", "valore": 14, "max": 15 }
    // ... fino a 5 temi, valore = frequenza discussione
  ],
  "drivers": [
    { "nome": "Nome driver", "pct": 92 }
    // ... fino a 6 driver, pct = % consenso
  ],
  "barriere": [
    { "nome": "Nome barriera", "pct": 72 }
    // ... fino a 6 barriere
  ],
  "takeaway": [
    {
      "titolo": "Titolo breve",
      "descrizione": "Spiegazione 2 righe"
    }
    // ... fino a 4 takeaway
  ],
  "distribuzione": [
    { "tema": "Nome tema", "pct": 28, "colore": "#CC0000" }
    // ... 6 celle, colori: #CC0000 #0D1B40 #6B7280 #991B1B #1F2937 #374151
  ],
  "quote": [
    {
      "testo": "Citazione verbatim",
      "speaker": "Nome speaker",
      "timestamp": "00:00–00:00"
    }
    // ... fino a 3 quote
  ]
}
```

## Come pubblicare su GitHub Pages

1. Crea un repository su GitHub (es. `advisory-dashboard`)
2. Carica `index.html` e `data.json`
3. Vai su **Settings → Pages → Source → main branch**
4. La dashboard è online all'indirizzo:  
   `https://tuousername.github.io/advisory-dashboard/`

## Per ogni nuovo meeting

1. Aggiorna solo `data.json` con i nuovi contenuti
2. Fai commit e push
3. La dashboard online si aggiorna in ~1 minuto

## Prompt da usare con Claude per generare data.json

Incolla questo prompt in Claude con l'output AskFred in fondo:

```
Analizza questo output di advisory board e restituisci SOLO un file JSON 
valido con questa struttura esatta (nessun testo aggiuntivo, nessun markdown):

{
  "meta": { "title": "Advisory Board Dashboard", "subtitle": "...", "topic": "...", "date": "..." },
  "evidenze": [{ "titolo": "...", "descrizione": "...", "fonte": "..." }],
  "temi": [{ "nome": "...", "valore": N, "max": 15 }],
  "drivers": [{ "nome": "...", "pct": N }],
  "barriere": [{ "nome": "...", "pct": N }],
  "takeaway": [{ "titolo": "...", "descrizione": "..." }],
  "distribuzione": [{ "tema": "...", "pct": N, "colore": "..." }],
  "quote": [{ "testo": "...", "speaker": "...", "timestamp": "..." }]
}

Usa questi colori in ordine per distribuzione: #CC0000, #0D1B40, #6B7280, #991B1B, #1F2937, #374151

OUTPUT ASKFRED:
[INCOLLA QUI]
```
