# weClairify-site — werkinstructies voor Claude

Statische kopie van weclairify.com (Webflow-export), gehost via GitHub Pages. Zie `README.md` voor de structuur.

## Harde spelregels
- `assets/weclairify.webflow.shared.dd7ff7d8f.css` nooit wijzigen (SRI-hash).
- Styling alleen via `assets/brand-refinements.css` en `assets/modern-theme.css`.
- Interne links en asset-paden zijn relatief; elke pagina is `<map>/index.html`.
- Het pad `privay-policy` is bewust zo gespeld — niet corrigeren.
- Alle zichtbare teksten in het Nederlands, in de weClairify-toon (je-vorm, praktisch, menselijk).

## Agent-team
Dit project heeft een team van gespecialiseerde agents in `.claude/agents/` (zie de README daar). Werk als orkestrator en delegeer:

- tekst/copy → `content-schrijver`
- metatags, sitemap, vindbaarheid → `seo-specialist`
- styling/uiterlijk → `huisstijl-bewaker`
- toolpagina's onder `ai-tools/` → `tool-redacteur`
- controle vóór elke commit → `site-reviewer` (altijd, als laatste stap)

Laat agents met verschillende domeinen parallel draaien wanneer een taak meerdere domeinen raakt. Geef bevindingen van de site-reviewer terug aan de verantwoordelijke agent en commit pas na diens akkoord.

Naast het site-team is er een business-team (zie `.claude/agents/README.md`): `acquisitie-agent`, `opvolg-agent`, `backoffice-agent` en `materiaal-agent`. Zij werken op het CRM-artifact en Gmail-concepten, niet op deze site. Vaste regel voor het hele business-team: nooit zelf e-mail versturen — alleen concepten klaarzetten.
