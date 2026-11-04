# Het Levend Monument — portaal

**De website van [hetlevendmonument.nl](https://hetlevendmonument.nl): een digitaal monument waar nazaten van tot slaaf gemaakten hun verhalen, kunst en kennis delen, bewaren en doorgeven.**

Een initiatief van Stichting Ketikotivlaardingen.NL. Deze repository bevat de broncode van het portaal (de webapplicatie die bezoekers, vertellers, docenten, leerlingen en curatoren gebruiken), open source onder de MIT-licentie.

> *English summary: the public web portal of Het Levend Monument ("The Living Monument"), a Dutch digital heritage platform where descendants of enslaved people share and preserve stories, art and knowledge. React + TypeScript, MIT-licensed.*

## Wat het portaal doet

| Voor wie | Wat |
|---|---|
| Publiek | Verhalen ontdekken per categorie en op een kaart (Nederland, Suriname, Curaçao en verder). |
| Vertellers | Een verhaal insturen met tot tien foto's, geluidsopnames, video's of documenten en een plek op de kaart; inloggen met een link per e-mail, geen wachtwoord. Status volgen onder *Mijn inzendingen*. |
| Leerlingen | Lessen en werkbladen openen met een klascode, zonder account. |
| Docenten | Klassen en klascodes beheren, lessen kiezen, antwoorden lezen en feedback geven. |
| Curatoren | Inzendingen bekijken en beoordelen, meldingen afhandelen, het archief exporteren. |

Toegankelijkheid (WCAG 2.1 AA als doel), privacy (geen trackingcookies, locatiegegevens worden uit foto's en video's verwijderd) en zorgvuldige curatie zijn uitgangspunten.

## Techniek

- React 18, TypeScript, Vite, Tailwind CSS
- MapLibre GL voor de kaart
- hCaptcha tegen misbruik van formulieren
- Vitest, Testing Library en vitest-axe (toegankelijkheidstests)
- Productie: statische build achter nginx (`Dockerfile`, `nginx.conf`, `security-headers.conf`)

Het portaal praat met de API van Het Levend Monument (`/api/v1/{tenant}/foundation/...`). Die backend is geen onderdeel van deze repository.

## Lokaal draaien

```bash
npm ci
npm run dev        # ontwikkelserver op http://localhost:5173
npm test           # tests, inclusief toegankelijkheid
npm run build      # productiebuild in dist/
```

Bij het bouwen kunnen `VITE_HCAPTCHA_SITE_KEY` (de publieke sitekey) en `VITE_ENVIRONMENT` worden meegegeven. De API wordt op hetzelfde domein aangesproken onder `/api`; in ontwikkeling stuurt Vite die door (zie `vite.config.ts`). Er staan geen geheimen in deze repository.

## Licentie en rechten

- **Broncode:** MIT-licentie, zie [LICENSE](LICENSE). Copyright SanskritiSetu.org.
- **Inhoud en merk:** de naam en het beeldmerk van Het Levend Monument, de foto's in `public/` en alle verhalen en teksten op het platform zijn eigendom van Stichting Ketikotivlaardingen.NL of van de makers, en vallen **niet** onder de MIT-licentie. Zie [NOTICE](NOTICE).

## Bijdragen en contact

Fouten of ideeën: open een issue. Beveiligingsproblemen niet in een openbaar issue melden, zie [SECURITY.md](SECURITY.md).

Contact: [info@hetlevendmonument.nl](mailto:info@hetlevendmonument.nl)
