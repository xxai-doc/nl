<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

Het wordt aanbevolen om eerst nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) en vervolgens `direnv allow` te installeren na het invoeren van de map ( [de .envrc](https://github.com/xxai-art/doc/blob/main/.envrc) wordt automatisch uitgevoerd na het invoeren van de map).

De betekenis is: Chinese vertaling naar Japans, Koreaans, Engels, Engelse vertaling naar alle andere talen. Als je alleen Chinees en Engels wilt ondersteunen, kun je gewoon `zh: en` schrijven.

De betekenis is: Chinese vertaling naar Japans, Koreaans, Engels, Engelse vertaling naar alle andere talen. Als je alleen Chinees en Engels wilt ondersteunen, kun je gewoon `zh: en` schrijven.

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

### Instructies voor automatisering van documentvertalingen

Zie coderepository [xxai-art/doc](https://github.com/xxai-art/doc)

Het wordt aanbevolen om eerst nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) en vervolgens `direnv allow` te installeren na het invoeren van de map ( [de .envrc](https://github.com/xxai-art/doc/blob/main/.envrc) wordt automatisch uitgevoerd na het invoeren van de map).

Om te voorkomen dat de grote codebasis in honderden talen wordt vertaald, heb ik voor elke taal een afzonderlijke codebasis gemaakt en een organisatie gemaakt om de codebasis op te slaan

Door de omgevingsvariabele `GITHUB_ACCESS_TOKEN` in te stellen en vervolgens [create.github.coffee](https://github.com/xxai-art/doc/blob/main/create.github.coffee) uit te voeren, wordt automatisch de coderepository gemaakt.

Je kunt het natuurlijk ook in een codebase stoppen.

Referentie voor vertaalscript [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

De scriptcode wordt als volgt geïnterpreteerd:

[bunx](https://bun.sh/docs/cli/bunx) is een vervanging voor npx, wat sneller is. Natuurlijk, als je bun niet hebt geïnstalleerd, kun je in plaats daarvan `npx` gebruiken.

`bunx mdt zh` geeft `.mdt` in de zh-directory weer als `.md` , zie de 2 gekoppelde bestanden hieronder

* [koffie_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [koffie_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` is de kerncode voor vertaling (als je alleen `nodejs` hebt geïnstalleerd, maar `bun` en `direnv` niet zijn geïnstalleerd, kun je ook `npx i18n` gebruiken om te vertalen).

Het zal [i18n.yml](https://github.com/xxai-art/doc/blob/main/i18n.yml) ontleden, de configuratie van `i18n.yml` in dit document is als volgt:

```
en:
zh: ja ko en
```

De betekenis is: Chinese vertaling naar Japans, Koreaans, Engels, Engelse vertaling naar alle andere talen. Als je alleen Chinees en Engels wilt ondersteunen, kun je gewoon `zh: en` schrijven.

De laatste is [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) , die de inhoud tussen de hoofdtitel en de eerste ondertitel van `README.md` van elke taal extraheert om een ​​item `README.md` te genereren. De code is heel eenvoudig, je kunt hem zelf bekijken.

Google API wordt gebruikt voor gratis vertaling. Als u geen toegang heeft tot Google, configureer en stel dan een proxy in, zoals:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

Het vertaalscript genereert een vertaalde cache in `.i18n` directory, controleer deze met `git status` en voeg deze toe aan de coderepository om herhaalde vertalingen te voorkomen.

Voer `bunx i18n` uit elke keer dat je de vertaling aanpast om de cache bij te werken.

Als de originele tekst en de vertaling tegelijkertijd worden gewijzigd, zal de cache in de war raken, dus als je wilt wijzigen, kun je er maar één wijzigen en vervolgens `bunx i18n` uitvoeren om de cache bij te werken.
