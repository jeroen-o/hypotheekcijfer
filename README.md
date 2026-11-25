# Hypotheekcijfer

Statische site (GitHub Pages) in Blinqx-huisstijl met het Hypotheekcijfer-logo. Elke pagina is één losse HTML-file, zonder build-step of externe API's.

| Pagina | Pad |
|---|---|
| Home | `index.html` |
| Bepaal je hypotheekcijfer (de rekentool) | `bepaal-uw-hypotheekcijfer/index.html` |
| Voor consumenten | `voor-consumenten/index.html` |
| Voor hypotheekadviseurs | `voor-hypotheekadviseurs/index.html` |
| Voor geldverstrekkers | `voor-geldverstrekkers/index.html` |
| Use cases | `voor-geldverstrekkers/use-cases/index.html` |
| Contact (formulier opent e-mailprogramma) | `contact/index.html` |
| HypotheekCijfer.nl-variant van de tool (Sketch-ontwerp, u-vorm) | `hypotheekcijfer-nl.html` |

## Stappenplan
1. Over jou en je huidige inkomen (aanvrager + optioneel partner)
2. Inkomen op pensioendatum (AOW + pensioen, AOW-datum automatisch)
3. Eigen geld om af te lossen en financiële verplichtingen
4. Hypotheek (leningdelen, woningwaarde, energielabel)
5. Life events (arbeidsongeschiktheid, werkloosheid, overlijden, scheiding)
6. Resultaat: hypotheekcijfer, belangrijke momenten, grafiek, maandlasten
7. Wat ga je doen? → rapport downloaden (PDF via printvenster)

## Leennormen
Financieringslastpercentages uit de **Wijzigingsregeling hypothecair krediet 2027** (Stcrt. 2026, 38415), tabellen 1–4, ingebouwd en gecontroleerd tegen de PDF (350 rijen identiek). Verder: + € 18.000 voor alleenstaanden met toetsinkomen > € 31.000, extra bedrag per energielabel (Nibud-advies 2027), toetsrente 5% bij rentevast < 10 jaar.

## Rekenregels
- Max. hypotheek = (financieringslastpercentage × toetsinkomen / 12 − toetslasten verplichtingen) / annuïteitenfactor (30 jaar).
- Toetsrente per leningdeel: contractrente bij resterende rentevast ≥ 10 jaar, anders max(5%, contractrente); gewogen naar saldo.
- AOW binnen 10 jaar: contante waarde van de maandcapaciteit vóór en na AOW (zoals in `Hypotheekcijfer_berekend.xlsx`).
- Na einde renteaftrek: tabel 3/4 (niet-aftrekbaar) naar rato van het saldo.
- Cijfer (3 t/m 8): geen overschrijding → 7 (<10% ruimte), 8 (≥10%); overschrijding → 5 (≤5%), 4 (≤10%), 3 (daarboven).
