# Draaiboek — demo "35 weken campagne, met agents"

Voor het live-blok in de AH-training. Duur: **25 tot 30 minuten**. Alles wat je moet typen staat
er letterlijk in. Wat je zegt staat ertussen, zodat je niet hoeft na te denken over de tekst.

Tijdens de demo staat er één ding centraal, en dat is niet snelheid: **het proces blijft hetzelfde,
alleen het wachten verdwijnt.** Als de deelnemers dat meenemen, is de demo geslaagd.

---

## Vooraf (5 minuten, vóór de zaal binnenkomt)

```bash
cd .claude/demos/ah-campagne/project
rm -f output/*.md output/*.csv      # schoon beginnen
claude
```

Check:
- [ ] `/agents` toont negen campagne-agents.
- [ ] `output/` is leeg op `.gitkeep` na.
- [ ] `voorbeeldoutput/` staat open in een tweede venster — je vangnet als het live traag gaat.
- [ ] Terminal-lettergrootte omhoog. Wat jij leest, leest de achterste rij niet.

---

## Blok 0 — Het probleem op tafel (2 min)

> "Even terug naar wat je zei: 35 weken van eerste mail tot livegang. Wat is daarvan écht werk,
> en wat is wachten?"

Laat haar antwoorden. Het antwoord is bijna altijd: afstemrondes, wachten op een bureau, wachten
op legal, herschrijven omdat iemand laat aanhaakte. Schrijf dat op de flip-over. Daar ga je
straks één voor één langs.

> "Wat we nu gaan doen: ik geef Claude precies de rommel waarmee zo'n campagne begint. En dan
> kijken we wat er overblijft van die 35 weken."

---

## Blok 1 — Het team laten zien (2 min)

Typ in Claude:

```
/agents
```

> "Dit is geen chatbot met één rol. Dit zijn negen specialisten, elk met een eigen opdracht en
> eigen bevoegdheden. De briefing-agent mag schrijven. De merkbewaker mag alléén lezen — die kan
> jouw teksten dus niet stiekem aanpassen. Dat is met opzet zo."

Open kort `.claude/agents/compliance-agent.md` op het scherm.

> "Dit is de hele agent. Een tekstbestand. Geen software, geen implementatietraject. Dit is wat
> jij als projectmanager zelf schrijft en onderhoudt — het is jouw werkwijze, opgeschreven."

---

## Blok 2 — Van rommel naar briefing (4 min)

Open `briefing/ruwe-input.md` op het scherm en scroll er even doorheen.

> "Kijk hier even naar. Een doorgestuurde mail, notulen van een overleg dat uitliep, losse
> opmerkingen. Twee mensen die iets anders willen. Geen budget. Geen nulmeting. Herkenbaar?"

Typ dan:

```
/campagne-start
```

Terwijl het draait:

> "Let op wat hij níet doet. Hij verzint geen budget. Hij kiest niet stiekem tussen volume en
> merkvoorkeur. Die tegenspraak zet hij op de open-vragenlijst — want dat is jouw besluit."

Als de briefing er staat, scroll naar **Buiten scope** en **Open vragen**.

> "Dit is het stuk waar in het echt zes weken aan afstemming in gaat zitten. Niet omdat het zo
> moeilijk is, maar omdat niemand de eerste versie wil maken. Die eerste versie kost nu twee
> minuten. De discussie erover voer je nog steeds zelf — maar je begint hem op maandag in plaats
> van over zes weken."

---

## Blok 3 — Twee agents tegelijk (3 min)

De `/campagne-start` zet `inzicht-agent` en `concept-agent` in dezelfde beurt in. Wijs dat aan
in beeld.

> "Zie je dat er twee tegelijk draaien? Dat is het verschil tussen een assistent en een team.
> De inzichten en de concepten worden naast elkaar gemaakt, niet na elkaar. In het echte proces
> is dit twee vergaderingen en drie weken wachten op een bureau."

Als de concepten er zijn, ga naar de vergelijkingstabel onderaan.

> "Drie échte keuzes, met bij elk concept ook opgeschreven wat eraan misgaat. Dat laatste is het
> belangrijkste kopje van het hele document."

---

## Blok 4 — Hier stopt de machine (1 min) ⬅ **het kernmoment**

De keten stopt uit zichzelf en vraagt welk concept jullie kiezen.

> "Hier houdt het op. Claude kiest niet. Dat staat zo in de instructie: na de conceptfase stopt
> de keten en beslist een mens. Dat is geen beperking, dat is het ontwerp. Op de plekken waar het
> ertoe doet — concept, budget, een juridisch risico, go of no-go — zit jij aan de knop."

Laat de deelnemer zelf kiezen. Typ dan bijvoorbeeld:

```
We gaan verder met concept 2. Zet de kalender-agent in.
```

---

## Blok 5 — De contentkalender (4 min)

Als de kalender klaar is, open `output/04-contentkalender.csv`.

> "Markdown om te lezen, CSV om te gebruiken. Deze zet je zo in Excel, Monday of Asana."

Wijs drie dingen aan:
1. De kolom **`afhankelijk_van`** — "hier zit je kritieke pad in."
2. De rijen voor **merk- en compliancereview**, vóór de aanleverdeadline. — "Vorig jaar begon de
   juridische review pas aan het eind. Dat kostte drie herschrijfrondes. Nu staat hij ingepland
   als taak, met een eigenaar."
3. De **bufferweek**. — "Hij noemt hem ook gewoon buffer. Niet verstopt in de marges."

---

## Blok 6 — Productie en media, naast elkaar (3 min)

```
Zet de copy-agent en de media-agent nu tegelijk in.
```

> "Twee sporen tegelijk, want ze raken elkaars werk niet. De media-agent controleert wel of zijn
> aanleverdeadlines kloppen met de kalender — en klaagt als ze botsen."

Laat in `output/05-copy.md` de drie varianten per uiting zien, van veilig naar gedurfd.

> "Niet één tekst waar je het mee moet doen. Drie, met karaktertellingen erbij, zodat ze in het
> vakje passen. Jij kiest."

---

## Blok 7 — De review (4 min) ⬅ **de klapper**

```
/campagne-review
```

> "Merkbewaker en compliance-agent kijken nu tegelijk mee. Allebei alleen-lezen."

Ga naar het compliance-rapport en zoek de duurzaamheidsclaim uit de ruwe input op —
*"Samen maken we het klimaatneutraal op je bord."*

> "Die zin stond in de notulen. Iemand van duurzaamheid opperde hem tijdens de kick-off. In het
> vorige proces kwam die zin pas bij de juridische review naar boven, ergens rond week 28, en toen
> moest de halve campagne worden herschreven. Nu ligt hij er in week één, met de regel erbij, en
> met een alternatief dat wél mag."

Wijs ook het rode punt op de spaaractie voor kinderen aan, en de zin onderaan het rapport:

> "*Dit is een eerste screening, geen juridisch advies.* Dat staat er met opzet. De jurist
> beslist nog steeds — hij krijgt alleen een lijstje van acht punten in plaats van veertig
> pagina's ruwe tekst. Dát is waar de weken verdwijnen."

---

## Blok 8 — Livegang (2 min)

```
Zet de livegang-agent in.
```

Wijs de QA-lijst aan: prijzen gelijk in folder, app, site en winkel; winkelmateriaal aantoonbaar
aangekomen.

> "Weet je nog, die schapkaarten die vorig jaar drie weken te lang hingen? Dat staat in de
> campagnehistorie die ik hem heb meegegeven. Hij heeft het onthouden en er een checklistregel
> van gemaakt. Dat is het verschil met een chatbot: dit ding kent jullie vorige campagne."

---

## Blok 9 — Eerlijk zijn (2 min) ⬅ **niet overslaan**

Open `PROCES.md`, of toon de tijdlijn-pagina.

> "Wat ik je níet ga vertellen, is dat 35 weken 12 weken wordt omdat AI zo snel typt. De
> fotoshoot duurt nog steeds een dag. De drukdeadline schuift niet. Legal tekent nog steeds af.
> Media-inkoop heeft zijn eigen vensters."

> "Wat wél verdwijnt: het wachten op een eerste versie, de afstemrondes over een document dat er
> nog niet is, en het herwerk omdat iemand pas laat aanhaakte. Dat is in jullie eigen evaluatie
> vijftien weken. Dáár zit het."

---

## Blok 10 — Wat zij maandag doet (3 min)

> "Je hoeft dit niet in één keer te bouwen. Begin met één agent: die van jou waar de meeste
> wachttijd zit. Bij jullie is dat de briefing."

Drie stappen, geef ze mee:
1. Maak een map voor één campagne. Zet erin wat je al hebt: de ruwe input, het merkhandboek, de
   evaluatie van vorige keer.
2. Schrijf één agent — een tekstbestand met: wie ben je, wat lees je, wat lever je op, wat mag je
   niet. Een half A4 is genoeg.
3. Draai hem op een campagne die al klaar is en vergelijk. Klopt het? Voeg de volgende agent toe.

> "Deze hele map is negen tekstbestanden. Je krijgt hem mee."

---

## Als het live misgaat

| Wat er gebeurt | Wat je doet |
|---|---|
| Het duurt te lang | Praat door over blok 9 terwijl het draait; dat blok heeft geen scherm nodig. |
| De output is anders dan verwacht | Zeg dat. "Elke keer anders — dus jij leest het altijd na." Dat is een les, geen storing. |
| Geen internet of geen sessie | Open `voorbeeldoutput/` en loop dezelfde bloktjes langs met de kant-en-klare bestanden. |
| Vraag die je niet kunt beantwoorden | Noteer hem op de flip-over en neem hem mee in de opvolgmail. |
