# weClairify — statische site

Een volledige, statische kopie van [weclairify.com](https://www.weclairify.com), losgemaakt van Webflow zodat je hem gratis via **GitHub Pages** kunt hosten. De teksten en het ontwerp zijn 1-op-1 overgenomen, niets is inhoudelijk gewijzigd.

## Structuur

```
.
├── index.html                          # homepage  (/)
├── ai-nieuws/index.html                # /ai-nieuws
├── ai-trainingen/index.html            # /ai-trainingen
├── implementatie-automatisering/…      # /implementatie-automatisering
├── over/index.html                     # /over
├── tools/index.html                    # /tools
├── privay-policy/index.html            # /privay-policy  (typfout uit origineel bewust behouden)
├── assets/                             # alle CSS, JS, afbeeldingen, SVG's, fonts
│   ├── weclairify.webflow.shared…css   # originele Webflow-stijl (niet wijzigen: SRI-hash)
│   └── brand-refinements.css           # extra huisstijl-laag (zie onder)
├── robots.txt
├── sitemap.xml
└── .nojekyll                           # zegt GitHub Pages: serveer bestanden as-is
```

Elke pagina staat in een eigen map als `index.html`, zodat schone URLs (`/over`, `/tools`) op elke host werken. Alle assets verwijzen naar `/assets/…` (root-absoluut).

## Huisstijl-verfijningslaag (`brand-refinements.css`)
De originele Webflow-CSS is bewust **ongewijzigd** gelaten (die heeft een
SRI-integriteitshash). De huisstijl is verfijnd via een aparte, additieve
laag die ná de Webflow-stijl wordt geladen op elke pagina. Inhoud en layout
blijven gelijk; alleen de afwerking is gepolijst:

- **Brand-tokens** rond de kernkleur `#7f0545` (weClairify-paars/burgundy).
- **Knoppen** met consistente, tactiele hover/indruk-feedback (de bestaande
  neo-brutalistische "harde schaduw"-stijl blijft behouden).
- **Kaarten** (services, contact, FAQ) met een eenvormige hover-lift.
- **Navigatie** met een merk-gekleurde onderstreping voor hover/actief.
- **Toegankelijkheid**: zichtbare focus-ringen in de merkkleur, merk-`::selection`
  en respect voor `prefers-reduced-motion`.
- **"Vertrouwd door"-logo's** rustig in grijswaarden, oplichtend bij hover.

Wil je de verfijning uitzetten? Verwijder de `brand-refinements.css`-`<link>`
uit de `<head>` van de pagina's — de site valt dan terug op de pure Webflow-stijl.

## Wat blijft extern laden?
Dit is normaal en hoort zo (zelfde als bij Webflow):
- Google Fonts (`webfont.js`)
- jQuery (Webflow-runtime)
- Finsweet cookie-consent
- Google Analytics (`G-GT3ETM02WM`)

## Lokaal bekijken
```bash
cd weclairify-site
python3 -m http.server 8000
# open http://localhost:8000
```

## Hosten op GitHub Pages
1. Maak een repo op GitHub (bv. `weclairify-site`).
2. Push deze map:
   ```bash
   git remote add origin https://github.com/<jouw-account>/weclairify-site.git
   git branch -M main
   git push -u origin main
   ```
3. GitHub → **Settings → Pages** → Source: `Deploy from a branch` → branch `main` / folder `/ (root)` → Save.
4. Na ~1 min staat de site op `https://<jouw-account>.github.io/weclairify-site/`.

### Eigen domein (weclairify.com)
Wil je `weclairify.com` koppelen in plaats van Webflow:
1. Zet bij **Settings → Pages → Custom domain** je domein (bv. `www.weclairify.com`). GitHub maakt dan een `CNAME`-bestand aan.
2. Pas bij je domeinprovider de DNS aan:
   - `www` → CNAME naar `<jouw-account>.github.io`
   - apex (`weclairify.com`) → de 4 GitHub Pages A-records (185.199.108–111.153)
3. Zet de Webflow-publicatie pas uit als GitHub Pages live staat.

> Let op: omdat assets root-absoluut (`/assets/…`) zijn, werkt de site het beste op een eigen domein of op een user/org-root. Bij een project-URL met subpad (`/weclairify-site/`) moet je een custom domain gebruiken.
