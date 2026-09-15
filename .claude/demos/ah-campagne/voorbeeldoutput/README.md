# Voorbeeldoutput

Vooraf gedraaide resultaten van de keten, in precies de vorm die de agents opleveren. Twee
gebruiksmomenten:

1. **Vangnet.** Gaat de live-demo traag of valt het internet weg, open dan deze map en loop de
   blokken uit `../DRAAIBOEK.md` langs met deze bestanden.
2. **Verwachting.** Lees ze vooraf door, zodat je tijdens de demo weet waar je naartoe scrolt.

## Wat er ligt, en welk demoblok het dekt

| Bestand | Van | Dekt blok |
|---|---|---|
| `01-campagnebriefing.md` | `briefing-agent` | 2 — van rommel naar briefing |
| `03-concepten.md` | `concept-agent` | 3 en 4 — concepten en de keuze |
| `04-contentkalender.csv` | `kalender-agent` | 5 — de contentkalender |
| `05-copy.md` | `copy-agent` | 6 — productie |
| `06-compliance-check.md` | `compliance-agent` | 7 — de review |
| `07-mediaplan.md` | `media-agent` | 6 — media |
| `08-livegang.md` | `livegang-agent` | 8 — livegang |

Twee outputs ontbreken bewust, omdat het draaiboek er niet naartoe scrolt: `02-inzichten.md` van de
`inzicht-agent` en het rapport van de `merkbewaker`. Wil je die toch als vangnet hebben, draai de
keten dan een keer volledig en kopieer `project/output/` hierheen.

## Over de weeknotatie in de kalender

De kolom `week` in `04-contentkalender.csv` gebruikt twee notaties met opzet: `C-11` tot en met
`C-1` telt af naar de livegang (voorbereidingsweken), daarna tellen `1` tot en met `8` de
campagneweken. De kolom `datum_live` bevat de bijbehorende ISO-week (`2026-W14`) en is wél
sorteerbaar — gebruik die kolom als je de kalender in Excel of Monday op volgorde zet.

---

Live draaien geeft elke keer een ander resultaat. Dat is geen storing — zeg het gerust hardop.
Het is precies waarom een mens de output altijd naleest.

> Fictief oefenmateriaal.
