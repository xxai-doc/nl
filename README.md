<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.art

Een deel van de websitecode is open source, welkom om de vertaling te helpen optimaliseren.

## front-end code

* [front-end code](https://github.com/xxai-art/web)
* [Taalpakketten voor de site als geheel](https://github.com/xxai-art/web/tree/main/i18n)
* [Taalpakketten voor inlogmodules](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Website Meertalige documentatie](https://github.com/xxai-doc)

De front-end programmeertaal is [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , die enkele functies toevoegt op basis van de coffeescript-syntaxis, zie [./coffee_plus.md](./coffee_plus.md) .

## Internationalisering van websites en documenten

Bouw voort op de volgende 3 projecten

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  Het achtervoegsel is `.mdt` , u kunt de syntaxis gebruiken die vergelijkbaar is met `<+ ./coffee_plus/import.js>` om naar externe bestanden te verwijzen en markdown genereren met het achtervoegsel `.md` .

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  Markdown-vertaling vertaalt geen codes en links en slaat vertaalde zinnen op in het cachegeheugen. Als de vertaling is gewijzigd maar de originele tekst niet is gewijzigd, zal het opnieuw uitvoeren van de bewerking de wijziging van de vertaling niet overschrijven.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  Taalbestanden voor het vertalen van `yaml` gegenereerde websites.
