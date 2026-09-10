# Foyen AI-ligan

Statisk sida (ren HTML/JS, ingen byggprocess) som visar månadens AI-tävling på Foyen. Deploya som "Other" på Vercel med rotkatalogen `./` – inga inställningar behövs.

## Lägga till en ny månad

1. Exportera **Members analytics** som CSV från Claude-adminpanelen för perioden.
2. Lägg filen i `data/csv/`. Behåll datumen i filnamnet (`...20260910to20261009.csv`) – perioden och månadsnamnet läses därifrån.
3. Lägg till filnamnet i `data/index.json` under `"csv"`.
4. Committa. Vercel publicerar om automatiskt.

Vill du sätta egen rubrik för en månad, lägg till under `"labels"` i `index.json`:

```json
"labels": { "membersanalytics_20260910to20261009.csv": { "label": "Oktober 2026", "period": "10 sep – 9 okt" } }
```

## Administrera

Knappen *Administrera* är låst med lösenordet `admin` (konstanten `ADMIN_PASSWORD` i `index.html`). Det är ett enkelt lås mot oavsiktliga ändringar, inte ett säkerhetsskydd – all data på sidan är ändå läsbar för den som har länken.

## Deltagare och poängvikter

- `data/roster.json` – kontor, arbetsområde och titel per e-postadress, samt `excluded` för den som står utanför prisjakten. Nya personer i en CSV som saknas här visas som "Ej placerad".
- `data/settings.json` – poängvikter, antal i topplistan och hur ofta skärmläget byter vy.

Båda kan redigeras direkt i GitHub, eller via kugghjulet på sidan: gör ändringarna, provkör dem, och ladda ner filen som ersätter den i repot.

## Obs

Sidan innehåller namn på medarbetare. Alla med länken kan se den – aktivera Deployment Protection i Vercel (eller håll adressen intern) om det behövs.
