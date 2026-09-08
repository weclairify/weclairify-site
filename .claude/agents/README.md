# Het weClairify agent-team

Dit project heeft een team van gespecialiseerde Claude-agents. Elke `.md` in deze map definieert één agent: de YAML-frontmatter bepaalt naam, inzetmoment (`description`), toegestane tools en het model; de tekst eronder is de systeeminstructie van die agent. Er zijn twee teams: het **site-team** (onderhoudt deze website) en het **business-team** (acquisitie, opvolging, backoffice en materiaal voor weClairify als bedrijf).

## Site-team

| Agent | Rol | Mag wijzigen |
|---|---|---|
| `content-schrijver` | Nederlandse copy in de weClairify-toon | tekst in HTML-pagina's |
| `seo-specialist` | titles, meta/OG-tags, canonical, sitemap, robots | metatags, `sitemap.xml` |
| `huisstijl-bewaker` | styling binnen de huisstijl | alleen `brand-refinements.css` / `modern-theme.css` |
| `tool-redacteur` | de 421 toolpagina's + overzicht | `ai-tools/`, `tools/`, `sitemap.xml` |
| `site-reviewer` | kwaliteitscontrole vóór commit | niets — alleen-lezen |

## Business-team

| Agent | Rol | Spelregel |
|---|---|---|
| `acquisitie-agent` | brancheverenigingen & keynotes researchen, pitchmails, pipeline | mails alleen als Gmail-concept; geen klanten van tussenpartijen benaderen |
| `opvolg-agent` | bedankmail + abonnement-aanbod na elke directe training | mails alleen als Gmail-concept |
| `backoffice-agent` | wekelijkse check: facturatie, openstaand, planningsgaten, % via tussenpartijen | alleen-lezen |
| `materiaal-agent` | slides, handouts, offertes, one-pagers in huisstijl | bedragen alleen na akkoord van Claire |

Anders dan het site-team werken de business-agents met een denylist (`disallowedTools`) in plaats van een tools-allowlist: hun toolbehoefte is breed (Gmail-concepten, Artifact/CRM, websearch, Gamma), dus alles is toegestaan behalve wat expliciet geblokkeerd is — met versturen van e-mail als hardste blokkade.

Het business-team leest het CRM (het Weclairify CRM-artifact) via de Artifact-tool en houdt eigen werklijsten bij in de collecties `pipeline` en `opvolging` van datzelfde CRM. Geen enkele agent verstuurt zelf e-mail — alles wordt als concept klaargezet, Claire beslist en verstuurt. De backoffice-agent draait daarnaast elke maandagochtend automatisch als Routine en mailt zijn weekrapport.

## Zo werken ze samen

**1. Automatische delegatie.** Claude kiest zelf de juiste agent op basis van de `description`. Vraag gewoon: *"Herschrijf de tekst op de over-pagina"* → de content-schrijver pakt het op.

**2. Gericht aanroepen.** Noem een agent expliciet of gebruik een @-mention:

```
@content-schrijver maak de FAQ op de homepage korter
Gebruik de site-reviewer om mijn wijzigingen te controleren
```

**3. Parallel werken.** Agents met verschillende domeinen kunnen tegelijk draaien, omdat ze verschillende bestanden raken:

```
Voeg de tool "Claude Code" toe aan de bibliotheek en werk ondertussen
de meta descriptions van de trainingspagina bij
```
→ tool-redacteur en seo-specialist draaien naast elkaar.

**4. Vaste werkstroom (orchestrator-patroon).** De hoofd-sessie is de orkestrator:

1. inhoudelijk werk → `content-schrijver`, `tool-redacteur` en/of `huisstijl-bewaker` (parallel waar mogelijk)
2. daarna → `seo-specialist` werkt metatags en sitemap bij
3. als laatste, altijd → `site-reviewer` controleert; bevindingen gaan terug naar de verantwoordelijke agent
4. pas na "klaar om te committen" van de reviewer wordt gecommit

**5. Agent teams (experimenteel).** Voor grote klussen kunnen agents als volwaardige, zelfstandige teamgenoten draaien die elkaar berichten sturen en taken van een gedeelde takenlijst pakken. Zet daarvoor in `~/.claude/settings.json`:

```json
{
  "env": { "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1" }
}
```

en vraag bijvoorbeeld: *"Spawn een team: één teammate herziet alle trainingspagina's, één doet de toolbeschrijvingen, één reviewt alles."* Zie [code.claude.com/docs/en/agent-teams](https://code.claude.com/docs/en/agent-teams.md).

## Zelf een agent toevoegen

Maak een nieuw `.md`-bestand in deze map:

```markdown
---
name: mijn-agent
description: Wanneer moet Claude deze agent inzetten? Wees concreet — hierop kiest Claude.
tools: Read, Grep, Glob, Edit
model: sonnet
---

Systeeminstructie: wie is deze agent, wat zijn de spelregels, wat levert hij op?
```

Tips: houd de `description` 50–100 woorden met inzetmoment + taken + wat de agent teruggeeft; geef alleen de tools die echt nodig zijn (een reviewer krijgt geen `Edit`); voeg *"Gebruik deze agent proactief …"* toe als Claude hem uit zichzelf moet inzetten.

Documentatie: [subagents](https://code.claude.com/docs/en/sub-agents.md) · [agent teams](https://code.claude.com/docs/en/agent-teams.md)
