# Demo — "Een campagne van 35 weken, met Claude en sub-agents"

Trainingsdemo voor een marketing-projectmanager die het campagneproces korter wil maken.
Een volledige, draaibare campagnemap met negen sub-agents, een rommelige startcasus en een
draaiboek voor op het scherm.

> Alle inhoud van de casus is **fictief oefenmateriaal**. Geen echte documenten, cijfers of
> personen.

## Wat zit erin

| | |
|---|---|
| `DRAAIBOEK.md` | Minuut-voor-minuut script voor het live-blok (25–30 min), inclusief de exacte prompts en wat je erbij zegt. **Begin hier.** |
| `PROCES.md` | De inhoudelijke onderbouwing: 35 weken versus 12 weken, waar de winst zit en wat AI níet korter maakt. |
| `project/` | De campagnemap zelf. Dit is wat je tijdens de demo opent. |
| `voorbeeldoutput/` | Vooraf gedraaide resultaten. Je vangnet als de live-demo hapert. |

## Zo start je de demo

```bash
cd .claude/demos/ah-campagne/project
rm -f output/*.md output/*.csv
claude
```

Dan `/campagne-start` en volg `DRAAIBOEK.md`.

## Het team in de map

Negen sub-agents in `project/.claude/agents/`, plus drie slash-commando's in
`project/.claude/commands/`.

```
1  briefing-agent      ruwe input      → campagnebriefing
2  inzicht-agent   ─┐  briefing        → onderbouwing        ┐ parallel
3  concept-agent   ─┘  briefing        → drie concepten      ┘
   ── mens kiest ──
4  kalender-agent      concept         → contentkalender + CSV
5  copy-agent      ─┐  kalender        → alle teksten        ┐ parallel
6  media-agent     ─┘  briefing        → mediaplan           ┘
7  merkbewaker     ─┐  alles           → merkrapport         ┐ parallel, alleen-lezen
8  compliance-agent─┘  alles           → claimrapport        ┘
9  livegang-agent      alles           → go/no-go + QA
```

| Commando | Doet |
|---|---|
| `/campagne-start` | briefing, daarna inzichten en concepten parallel, en stopt dan voor jouw keuze |
| `/campagne-review` | merk- en compliancecheck tegelijk over alles in `output/` |
| `/campagne-status` | waar staan we, wat is open, wie is aan zet |

## De vier dingen die deze demo moet overbrengen

1. **Specialisten, geen chatbot.** Negen agents met elk een eigen opdracht en eigen rechten. De
   merkbewaker mag alleen lezen — die kan je teksten niet stiekem aanpassen.
2. **Parallel werken.** Inzicht en concept tegelijk. Copy en media tegelijk. Merk en compliance
   tegelijk. Daar zit een groot deel van de tijdwinst.
3. **De mens beslist.** De keten stopt uit zichzelf bij de conceptkeuze, en compliance zegt zelf
   dat het geen juridisch advies is. Dat is ontwerp, geen beperking.
4. **Een agent is een tekstbestand.** Geen project, geen tool, geen inkooptraject. Open er één op
   het scherm en laat zien hoe kort het is.

## Meegeven aan de deelnemer

De hele map `project/` is kopieerbaar. Laat haar beginnen met één agent, op de fase waar bij haar
de meeste wachttijd zit — meestal de briefing. Draai die op een campagne die al afgerond is en
vergelijk. Werkt het, dan pas de volgende agent erbij.

Wil je de casus aanpassen naar een echte campagne van de deelnemer: vervang
`project/briefing/ruwe-input.md`, `project/merk/merkkader.md` en
`project/merk/campagnehistorie.md`. De agents hoeven niet mee te veranderen.
