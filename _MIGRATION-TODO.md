# Migratie-TODO: tool-pagina's overzetten

> Tijdelijk werkdocument. Verwijderen zodra de tool-migratie klaar is.

## Context
De statische kopie van weclairify.com staat op deze branch (`claude/quirky-faraday-jvftya`).
De 7 hoofdpagina's zijn gemigreerd, de huisstijl is verfijnd (`assets/brand-refinements.css`),
alle paden zijn relatief, SRI-hashes zijn van lokale assets gestript, en de site werkt
zowel via `file://` als op een webserver. De "Lezen"/blog (`ai-nieuws/` + alle `/blog/`-links)
is op verzoek verwijderd.

## Wat nog moet gebeuren: alle tool-pagina's overzetten
De live site heeft **422 tool-pagina's** (`/ai-tools/<slug>`) als Webflow-CMS-pagina's.
Die zitten nog niet in de kopie, waardoor ~50 tool-links op de homepage en `tools/index.html`
nergens heen leiden. Webflow code-export bevat geen CMS, dus ze worden van de live site gehaald.

### Voorwaarde
De netwerk-allowlist van de cloud-omgeving moet `www.weclairify.com`, `*.website-files.com`
en `*.webflow.com` toelaten. Dit is ingesteld, maar geldt pas voor een **nieuw gestarte sessie**
(verse container). Test eerst:
```bash
curl -s -o /dev/null -w "%{http_code}\n" -A "Mozilla/5.0" https://www.weclairify.com/ai-tools/midjourney
```
200 = klaar om te kopiëren. 403 = nog steeds oude policy → start een nieuwe sessie.

### Stappen (zodra de site bereikbaar is)
1. Lees alle tool-URL's uit `sitemap.xml` (de `<loc>`-entries met `/ai-tools/`).
2. Haal voor elke slug de raw HTML op (browser-User-Agent) en sla op als `ai-tools/<slug>/index.html`.
3. Pas per pagina dezelfde bewerkingen toe als bij de hoofdpagina's:
   - root-absolute paden (`/assets/`, interne links) → relatief (`../../assets/` op diepte 2).
   - `integrity`/`crossorigin` van **lokale** assets strippen.
   - interne paginalinks → expliciete `index.html`-bestanden.
   - "Lezen"/blog-links en de `ai-nieuws`-navlink verwijderen (consistent met de rest).
4. Download alle nieuwe afbeeldingen die de tool-pagina's gebruiken (Webflow-CDN +
   `/assets/`-verwijzingen) naar `assets/` en herschrijf de verwijzingen.
5. Controleer dat de ~50 tool-links op `index.html` en `tools/index.html` nu naar
   bestaande `ai-tools/<slug>/index.html` wijzen.
6. Verwerk ook de tool-tag-overzichten (`/ai-tools-tags/...`) als de tools-pagina daarop filtert
   (controleer of de directory-filtering client-side werkt zonder die pagina's).
7. Bouw een nieuwe, kloppende `sitemap.xml` op basis van de daadwerkelijk aanwezige bestanden.
8. Test lokaal (subpad + root), commit en push, en werk PR #1 bij.

### Aandachtspunten
- 422 pagina's is veel: doe het scriptmatig en in batches, met nette voortgang.
- Formulieren werken nog niet (Webflow ving die op) — los apart op (form-service of mailto).
- Werk altijd op branch `claude/quirky-faraday-jvftya`.
