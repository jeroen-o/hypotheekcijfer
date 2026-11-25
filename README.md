# Hypotheekcijfer

Standalone rekentool (één HTML-bestand, geen build-step, geen externe API's, geen localStorage) die de betaalbaarheid van een bestaande hypotheek scoort (1–10) en het rapport **‘Je hypotheek nu en later’** genereert.

Open `index.html` in de browser of embed het in Google Sites. Het rapport opent via `window.open()` en kan als PDF worden opgeslagen.

## Wat de tool berekent
- **Huidig inkomen** en **inkomen op pensioendatum** (aanvrager + optioneel partner, AOW-datum automatisch).
- **Eigen geld om af te lossen** (plus optioneel verwacht polis-kapitaal).
- **Belangrijke momenten**: einde rentevast, einde renteaftrek, einde looptijd, AOW-datum(s): maximale hypotheek vs. schuld.
- **Life events** op peildatum: arbeidsongeschiktheid, werkloosheid, overlijden (nabestaandenpensioen + ORV), scheiding.
- **Maandlasten** bruto/netto nu en op de momenten.

## Rekenregels
- Max. hypotheek = (woonquote × toetsinkomen / 12 − toetslasten verplichtingen) / annuïteitenfactor (30 jaar).
- Toetsrente per leningdeel: contractrente bij resterende rentevast ≥ 10 jaar, anders max(5%, contractrente); gewogen naar saldo.
- AOW binnen 10 jaar: contante waarde van de maandcapaciteit vóór en na AOW (zoals in `Hypotheekcijfer_berekend.xlsx`).
- Na einde renteaftrek: woonquote × box-3-factor (0,733) voor dat deel.
- Cijfer: geen overschrijding → 7 (<10% ruimte), 8 (<25%), 9 (<50%), 10; overschrijding → 5 (≤5%), 4 (≤10%), 3 (≤20%), 2 (≤35%), 1.

> **Let op:** de woonquotetabellen in de tool zijn een indicatieve benadering van de Nibud-normen 2026. Vervang ze (tab ‘Rapportinstellingen en normen’) door de officiële tabellen uit de Regeling hypothecair krediet voordat de uitkomst extern wordt gebruikt.
