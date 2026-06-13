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

Elke pagina staat in een eigen map als `index.html`, zodat schone URLs (`/over`, `/tools`) op elke host werken. Alle interne verwijzingen (assets én links tussen pagina's) zijn **relatief** (`assets/…` op de homepage, `../assets/…` op subpagina's). Daardoor werkt de site overal: op een eigen domein (`weclairify.com`), op een user/org-root én op een project-URL met subpad (`…github.io/weclairify-site/`).

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

**Snel:** dubbelklik gewoon op `index.html` — die opent direct in je browser.
Alle interne links wijzen naar expliciete `…/index.html`-bestanden, dus ook het
navigeren tussen pagina's werkt zonder webserver (via `file://`).

**Of via een mini-server** (dichter bij de live-situatie):
```bash
cd weclairify-site
python3 -m http.server 8000
# open http://localhost:8000
```

## Hosten op GitHub Pages

Er zit een kant-en-klare deploy-workflow in `.github/workflows/deploy.yml`.
Eenmalig instellen:

1. GitHub → **Settings → Pages** → onder *Build and deployment* → Source: **GitHub Actions**.
2. Klaar. Elke push naar `main` bouwt en publiceert de site automatisch; de
   workflow toont de live-URL bij *Actions → Deploy to GitHub Pages*.
3. Na ~1 min staat de site op `https://<jouw-account>.github.io/weclairify-site/`.

> Alternatief zónder Actions: **Settings → Pages → Source: Deploy from a branch**
> → branch `main`, folder `/ (root)`. Werkt ook, omdat de paden relatief zijn.

### Eigen domein (weclairify.com)
Wil je `weclairify.com` koppelen in plaats van Webflow:
1. Zet bij **Settings → Pages → Custom domain** je domein (bv. `www.weclairify.com`). GitHub maakt dan een `CNAME`-bestand aan.
2. Pas bij je domeinprovider de DNS aan:
   - `www` → CNAME naar `<jouw-account>.github.io`
   - apex (`weclairify.com`) → de 4 GitHub Pages A-records (185.199.108–111.153)
3. Zet de Webflow-publicatie pas uit als GitHub Pages live staat.

> Omdat alle paden relatief zijn, werkt de site zowel op een eigen domein als op
> de project-URL met subpad. Een `CNAME`-bestand is bewust **niet** toegevoegd,
> zodat het live domein (nu nog op Webflow) niet per ongeluk wordt omgeleid —
> voeg dat pas toe via *Settings → Pages → Custom domain* als de DNS klaarstaat.

> **Let op (volledigheid):** dit is een kopie van de 7 hoofdpagina's. Losse
> detailpagina's (`/ai-tools/…`, `/blog/…`) zijn niet mee-geëxporteerd; links
> daarnaartoe leiden dus nog nergens heen. De hoofdsite werkt volledig.
