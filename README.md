# Fær Øer 2027

PWA privata per il viaggio di giugno 2027 (Fær Øer + Edimburgo). Stesso schema di `tenerife-2026` e `islanda-2026`.

## File
- `faroe_2027.html` — l'app (HTML + CSS + JS in un file)
- `manifest.webmanifest`, `icon-*.png`, `apple-touch-icon.png`, `icon.svg` — installabile
- `robots.txt`, `_headers`, meta `robots` — anti-indicizzazione (vedi sotto)

## Tab
| Tab | Cosa c'è |
|-----|----------|
| Piano | 8 giorni, blocchi orari, tappe gratis/a pagamento, slot liberi con note salvate sul telefono |
| Idee | Tappe extra (Mykines, Kallur, castello…) con costo e dove ci stanno |
| Spese | Stime già compilate (~), budget modificabile, convertitore DKK/GBP → € |
| Meteo | Open-Meteo da ~16 giorni prima, prima medie di giugno |
| Info | Voli, documenti (ETA UK), alloggi, consigli per risparmiare, regole dei sentieri |

## Privacy / niente indicizzazione
- `<meta name="robots" content="noindex, nofollow, …">` + `googlebot`/`bingbot` su tutte le pagine
- `robots.txt` con `Disallow: /` (vale solo se servito alla radice del dominio)
- `_headers` con `X-Robots-Tag` (lo applicano Cloudflare Pages / Netlify; GitHub Pages lo ignora)
- Nessun link pubblico verso il sito, `Referrer-Policy: no-referrer`
- Con GitHub Pages il **repo deve essere privato**, altrimenti il codice è leggibile e indicizzato su github.com (Pages da repo privato richiede GitHub Pro)

## Come si modifica
Array `GIORNI` → `blocchi`. Uno slot libero: `{ id, ora, fine, tipo: 'libero', titolo, desc }`.
Per riempirlo: `tipo: 'noi'`, `costo: 'gratis' | '200 DKK a testa'`, `places: [{ label, q }]`.
Le spese di partenza sono in `BASE_SPESE` (`eur` = stima per 2 persone).
