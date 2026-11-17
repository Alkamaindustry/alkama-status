# alkama-status

Statussidan för alkamaindustry.com: <https://status.alkamaindustry.com>.

- **Vad den visar:** det som `alkama-infra` mätte vid senaste kontrollen (var sjätte timme):
  webbplatsen, appen och databasen, beställningsflödet (en testorder läggs på riktigt),
  säkerhetscertifikatet och domänregistreringen.
- **Data:** `data/status.json`, skrivs av alkama-infra via en deploy key med skrivrätt till
  bara det här repot.
- **Planerat underhåll:** `data/maintenance.json`, redigeras med en commit. Tider i UTC.
- **Hosting:** GitHub Pages. Medvetet någon annanstans än appen, så att sidan fungerar
  även när DigitalOcean inte gör det.

## Regeln

Sidan visar aldrig grönt utan en mätning bakom sig. Saknas data, eller är den äldre än
två kontrollintervall, står det **Inaktuell data** i stället för "Allt fungerar".

## Köra lokalt

```bash
python3 -m http.server 8000    # öppna sedan http://localhost:8000
```

Ingen build, inga beroenden. Bygger på [benbo-status](https://github.com/Benbo-se/benbo-status),
förenklad till en enda sajt.
