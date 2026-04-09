# Casa Cavour — GEO/AEO Dashboard

Dashboard privata per il monitoraggio della visibilità AI di Casa Cavour Bertinoro.

## Struttura

```
cavour-dashboard/
├── index.html          ← dashboard principale
├── reports.json        ← dati storici (aggiornare manualmente)
├── reports/
│   ├── 2026-04-09.html ← report HTML di ogni run
│   └── ...
└── README.md
```

## Come aggiornare dopo ogni run N8N

1. Salva l'email HTML ricevuta come `reports/YYYY-MM-DD.html`
2. Apri `reports.json` e aggiungi una voce in cima all'array:

```json
{
  "data": "GG/MM/YYYY",
  "data_iso": "YYYY-MM-DD",
  "presenze": X,
  "punteggio_medio": X.X,
  "domande": [
    {"domanda": "...", "presente": true/false, "punteggio": X, "competitor": ["...", "..."]},
    ...
  ],
  "azioni": [
    "Azione 1...",
    "Azione 2...",
    "Azione 3..."
  ],
  "report_url": "reports/YYYY-MM-DD.html"
}
```

3. Fai commit e push su GitHub → Vercel aggiorna automaticamente

## Deploy su Vercel

1. Crea repo GitHub `cavour-dashboard` (privato)
2. Collega il repo a Vercel
3. Nessuna build configuration necessaria — è HTML statico
4. La dashboard non è indicizzata dai motori di ricerca (no sitemap, no robots.txt)

## Accesso

Condividi l'URL Vercel direttamente con Cesare e Anna — non è necessario login.
Per maggiore sicurezza puoi abilitare Vercel Password Protection nelle impostazioni del progetto.
