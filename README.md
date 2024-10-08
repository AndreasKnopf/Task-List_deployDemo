## Umgebungsvariablen

- Normalerweise benötigst du unterschiedliche Konfigurationen für Entwicklung und Produktion

  - In der Produktion könntest du andere API-Schlüssel verwenden
  - In der Produktion könntest du ein anderes Logging verwenden

- Angenommen, du erstellst eine eCommerce-Seite zum Kauf von Kunst

  - Entwicklung: Du sendest deine Produktbestellungen an eine Test-Zahlungs-API-URL
  - Produktion: Du sendest deine Produktbestellungen an die echte Zahlungs-API-URL

- Umgebungsvariablen sind sehr beliebt für diese Konfiguration
- Du hast eine Menge Umgebungsvariablen in deinem System

  - env
  - Diese Werte sind für deine Node-Programme zugänglich
  - Du kannst das gleiche Programm mit unterschiedlichen Umgebungsvariablen starten
  - Eine gängige Umgebungsvariable ist NODE_ENV

- Wir können eine Umgebungsvariable für einen einzelnen Programmstart setzen:
- `NODE_ENV=production node main.js`

- Um eine dauerhafte zu setzen, müsstest du Konfigurationsdateien ändern
- Eine sehr gängige Methode ist das Laden von Umgebungsvariablen aus einer .env Datei

-Früher wurde ein Paket benötigt:

```js
npm install dotenv -D

import dotenv from "dotenv";
dotenv.config();

const PORT = process.env.PORT || 3000;
```

## Geheimnisse

- Es ist sehr üblich, dass eine API keinen anonymen Zugriff erlaubt
- Eine gängige Strategie ist, dass du einen API-Schlüssel erhältst
  - Du musst dann diesen API-Schlüssel bei jeder Anfrage, die du machst, bereitstellen
- Es ist auch sehr einfach, sich von einer API blockieren zu lassen
  - Du machst versehentlich zu viele Anfragen
  - Dein API-Schlüssel wird versehentlich auf GitHub committed und jemand stiehlt ihn
  - COMMITTE KEINE GEHEIMNISSE WIE API-SCHLÜSSEL
  - `.env` gehört in `.gitignore`
  - Du könntest aber .env.example (oder .env.sample) in git haben, um Entwicklern bei der Einrichtung zu helfen!
