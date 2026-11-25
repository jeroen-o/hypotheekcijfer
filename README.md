# Hypotheekcijfer

- `index.html` – **Hypotheekcheck – bepaal je hypotheekcijfer** in Blinqx-huisstijl volgens het Figma-ontwerp (Quion): start, invoerkeuze, je situatie, gegevens (4 stappen), life events, controle, resultaat met "Meer informatie" per moment, "Wat ga je nu doen?" met afspraakvoorkeur, rapport.
- `hypotheekcijfer-nl.html` – **HypotheekCijfer.nl**-site volgens het Sketch-ontwerp (u-vorm) met dezelfde rekentool en "Bereken uw mogelijkheden".

Standalone rekentool (één HTML-bestand, geen build-step, geen externe API's, geen localStorage) die de betaalbaarheid van een bestaande hypotheek scoort (1–10) en het rapport **‘Je hypotheek nu en later’** genereert.

Open `index.html` in de browser of embed het in Google Sites. Het rapport opent via `window.open()` en kan als PDF worden opgeslagen.

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
- Cijfer: geen overschrijding → 7 (<10% ruimte), 8 (<25%), 9 (<50%), 10; overschrijding → 5 (≤5%), 4 (≤10%), 3 (≤20%), 2 (≤35%), 1.
