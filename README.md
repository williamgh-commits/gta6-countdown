# GTA VI nedtælling til OBS

En nedtællingswidget til GTA VI til brug som Browser-kilde i OBS. Baggrunden er gennemsigtig, og indstillingerne kan ændres live via `config.json`.

## Opsætning i OBS

1. Tilføj en **Browser**-kilde (Kilder → + → Browser).
2. Sæt **Lokal fil** fra.
3. Indsæt linket i **URL**-feltet:
   `https://williamgh-commits.github.io/gta6-countdown/gta6-countdown.html`
4. Sæt bredde til **800** og højde til **300**.
5. Lad **Tilpasset CSS** stå som standard.

Det er det hele. Widgetten opdaterer sig selv, når `config.json` ændres.

## Indstillinger (`config.json`)

| Felt | Betydning | Eksempel |
| --- | --- | --- |
| `date` | Tidspunktet for udgivelsen. Skriv tidszonen med, så den er ens for alle. | `2026-11-19T00:00:00+01:00` |
| `title` | Overskriften i widgetten. | `GTA VI` |
| `subtitle` | Teksten over nedtællingen. | `Udkommer om` |
| `doneText` | Teksten, når tiden er løbet ud. | `Velkommen til Vice City!` |
| `opacity` | Hvor synlig widgetten er, fra 0 til 1. `0.8` er 80 %. | `0.8` |
| `scale` | Størrelse. `1` er normal, `1.2` er 20 % større. | `1` |

Rediger filen direkte på GitHub (blyant-ikonet) og tryk **Commit changes**. Ændringen vises normalt inden for et par minutter, fordi widgetten henter filen igen hvert 30. sekund, og GitHub Pages har lidt forsinkelse.

## Ændringer med det samme

Hvis du ikke vil vente, kan du i OBS højreklikke på kilden og vælge **Egenskaber → Opdater cache for den aktuelle side**.

## Tilsidesæt via URL

Du kan også sætte indstillinger i selve linket. De vinder over `config.json`:

```
.../gta6-countdown.html?opacity=0.6&scale=1.2
```

Det virker for `date`, `title`, `subtitle`, `doneText`, `opacity` og `scale`.

## Fejlfinding

- **Siden er tom eller viser 404:** Vent et par minutter efter at have slået GitHub Pages til, og tjek at repositoryet er **public**.
- **Ændringerne vises ikke:** Tryk på **Opdater cache for den aktuelle side** i OBS.
- **Forkert tidspunkt:** Tjek at `date` indeholder tidszonen (`+01:00` for dansk normaltid).
- **Fonten ser anderledes ud:** Fonten hentes fra Google Fonts. Uden internet bruges en reservefont, og widgetten virker stadig.
- **"Ugyldig dato" i widgetten:** Datoen i `config.json` har et forkert format. Brug formatet `ÅÅÅÅ-MM-DDTHH:MM:SS+01:00`.

## Filer

- `gta6-countdown.html` er selve widgetten.
- `config.json` er indstillingerne.
