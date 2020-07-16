![PAP/API Lite](https://papilite.se/papapi-lite-github-se.png)

# PAP/API Lite

[**PAP/API Lite**](https://papilite.se/) eller förkortat till *PAPILITE* är ett öppet REST API med alla Sveriges postnummer och postorter. Genom att använda detta API får användaren fri tillgång till aktuella uppgifter för postnummer och postorter. Det finns över 16.000 postnummer i Sverige. Antalet postnummer förändras ständigt. Postnummer tillkommer eller faller bort.
PAPILITE innehåller inte bara uppgifter om postnummer och postorter utan även om kommuner, län samt gps-koordinater för samtliga postorter.
Detta är ett komplett API som fyller sitt syfte och kan användas inom många användningsområden. PAPILITE underlättar och hjälper i processer där aktuella och riktiga uppgifter är avgörande.

## Bakgrund

PAPILITE är en smalare version av [PAP/API](https://www.papapi.se/). Föregångaren eller originalet PAP/API lanserades tidigt 2015 men sedan i slutet av 2017 är projektet avsomnat och innehåller i dagsläget oaktuella uppgifter. Detta API är i mångt och mycket det samma men inte lika omfattande, men förbättrat. PAPILITE är tänkt att vara ett fullvärdigt komplement till PAP/API men utan adresser.

Bakom PAPILITE precis som PAP/API ligger full stack-utvecklaren [Nille](https://nillewebb.se/) med över 12 års erfarenhet av utveckling både front- och back-end i varierande omfattning. Utvecklingen av detta projekt är hans sätt att locka fram gnistan igen för det han en gång brann för.

## Komma igång

PAPILITE är öppet och fritt att använda. Det krävs dock [registrering](https://papilite.se/#registrera) för att använda och max 500 anrop per dag är tillåtet. Det är dock möjligt att genom [donation](https://papilite.se/#priser) få upp till 5.000 eller 10.000 anrop per dag och fler möjligheter och funktioner. Det handlar endast om engångsdonation. Det ska dock tilläggas att gränsen för gratis använding av PAPILITE inte är skrivit i sten. Det är möjligt att få gränsen förhöjd med en tillräckligt god motivering eller dylikt.

## Användning

### Anrop

#### Postnummer

Hämta data baserat på postnummer utförs enligt nedan.

| Parameter | Beskrivning                                    | Exempel                                      |
| --------- | ---------------------------------------------- | -------------------------------------------- |
| query     | Fullständigt postnummer med fem siffror        | *11434* (utan mellanslag eller andra tecken) |
| format    | Format på svaret                               | *json*, *xml* eller *csv*                    |
| apikey    | API-nyckel som tillhandahålls vid registrering | *f21a1127be93feae4efc13dbb7bc587627b22114*   |

**Exempel på anrop**

`https://api.papapi.se/lite/?query=11434&format=json&apikey=f21a1127be93feae4efc13dbb7bc587627b22114`

#### Postort

Hämta data baserat på postort utförs enligt nedan.

| Parameter | Beskrivning                                                  | Exempel                                    |
| --------- | ------------------------------------------------------------ | ------------------------------------------ |
| query     | Fullständigt eller ofullständigt postort men minst fyra bokstäver | *Stockholm* eller *Stoc*                   |
| format    | Format på svaret                                             | *json*, *xml* eller *csv*                  |
| apikey    | API-nyckel som tillhandahålls vid registrering               | *f21a1127be93feae4efc13dbb7bc587627b22114* |

**Exempel på anrop**

`https://api.papapi.se/lite/?query=Stockholm&format=json&apikey=f21a1127be93feae4efc13dbb7bc587627b22114`

### Svar

Datan som returneras vid ett korrekt anrop innehåller följande **postnummer** (*postal code*), **postort** (*city*), **latitud** (*latitude*), **longitud** (*longitude*), **kommunkod** (*county code*), **kommun** (*county*), **länskod** (*state code*), **län** (*state*), **notering** (*notes*) och **uppdaterad** (*updated*).

#### Svarskoder

Anrop kan ge följande svarskoder som är standard HTTP-statuskoder.

| HTTP-statuskod     | Beskrivning                                           |
| ------------------ | ----------------------------------------------------- |
| 200 — OK           | Korrekt anrop med svar                                |
| 400 — BAD REQUEST  | Felaktigt anrop                                       |
| 401 — UNAUTHORIZED | Felaktig API-nyckel                                   |
| 403 — FORBIDDEN    | Gräns nådd för anrop per dag eller spärrad API-nyckel |
| 404 — NOT FOUND    | Korrekt anrop men utan svar                           |

#### Exempel på svar

Svar på anrop för postnummer innehåller endast en post medan svar på anrop för postort kan innehålla upp till 100 poster.

**JSON**

```json
{"api":{"name":"PAP/API Lite","url":"https://papilite.se","version":"X.X","updated":"ÅÅÅÅ-MM-DD TT:MM:SS","encoding":"UTF-8"},"results":[{"postal_code":"10004","city":"Stockholm","latitude":"59.3293235","longitude":"18.0685808","county_code":"0180","county":"Stockholm","state_code":"01","state":"Stockholm","note":"","updated":"ÅÅÅÅ-MM-DD TT:MM:SS"},{"postal_code":"10005","city":"Stockholm","latitude":"59.3293235","longitude":"18.0685808","county_code":"0180","county":"Stockholm","state_code":"01","state":"Stockholm","note":"","updated":"ÅÅÅÅ-MM-DD TT:MM:SS"},{"postal_code":"10012","city":"Stockholm","latitude":"59.3293235","longitude":"18.0685808","county_code":"0180","county":"Stockholm","state_code":"01","state":"Stockholm","note":"","updated":"ÅÅÅÅ-MM-DD TT:MM:SS"} [...]
```

**XML**

```xml
<results>

	<api>

		<name>PAP/API Lite</name>

		<url>https://papilite.se</url>

		<version>X.X</version>

		<updated>ÅÅÅÅ-MM-DD TT:MM:SS</updated>

		<encoding>UTF-8</encoding>

	</api>

	<result>

		<postal_code>10004</postal_code>

		<city>Stockholm</city>

		<latitude>59.3293235</latitude>    

		<longitude>18.0685808</longitude>	

		<county_code>0180</county_code>

		<county>Stockholm</county>

		<state_code>01</state_code>

		<state>Stockholm</state>

		<note></note>

		<updated>ÅÅÅÅ-MM-DD TT:MM:SS</updated>

	</result>

	<result>

		<postal_code>10005</postal_code>

		<city>Stockholm</city>

		<latitude>59.3293235</latitude>

		<longitude>18.0685808</longitude>

		<county_code>0180</county_code>

		<county>Stockholm</county>

		<state_code>01</state_code>

		<state>Stockholm</state>

		<note></note>

		<updated>ÅÅÅÅ-MM-DD TT:MM:SS</updated>

	</result>

	<result>

		<postal_code>10012</postal_code>

		<city>Stockholm</city>

		<latitude>59.3293235</latitude>

		<longitude>18.0685808</longitude>

		<county_code>0180</county_code>

		<county>Stockholm</county>

		<state_code>01</state_code>

		<state>Stockholm</state>

		<note></note>

		<updated>ÅÅÅÅ-MM-DD TT:MM:SS</updated>

	</result>

[...]
```

**CSV**

```
postal_code;city;latitude;longitude;county_code;county;state_code;state;note;updated
10004;Stockholm;59.3293235;18.0685808;0180;Stockholm;01;Stockholm;;ÅÅÅÅ-MM-DD TT:MM:SS
10005;Stockholm;59.3293235;18.0685808;0180;Stockholm;01;Stockholm;;ÅÅÅÅ-MM-DD TT:MM:SS
10012;Stockholm;59.3293235;18.0685808;0180;Stockholm;01;Stockholm;;ÅÅÅÅ-MM-DD TT:MM:SS
[...]
\### PAP/API Lite | https:///docs | v X.X | ÅÅÅÅ-MM-DD TT:MM:SS | UTF-8 ###
```

#### För donatorer

Alla som gör engångsdonation får fler funktioner, bland annat anrop med ofullständiga postnummer, anrop med mindre antal bokstäver för postorter och hämta data baserat på latitud och longitud. Information gällande detta återfinns på [officiella webbplatsen](https://papilite.se/).

## FAQ

- ##### Hur aktuella är uppgifterna som kan hämtas ut?

  *Alla uppgifter uppdateras regelbundet och för att vara mer exakt så sker detta var 14:de dag.*

- ##### Finns det några adressuppgifter?

  *Detta är en lite-version av avsomnade [PAP/API](https://papapi.se/) och det är det som skiljer versionerna åt. Det finns alltså inga adressuppgifter.*

- ##### Vilka uppgifter kan jag hämta ut?

  *Förutom postnummer och postort får du även uppgifter om latitud, longitud, kommun, kommunkod, län och länskod för varje enskilt postnummer.*

- ##### Vilka format kan jag hämta ut i?

  *I dagsläget är det JSON, XML och CSV som gäller.*

- ##### Kan jag få ut alla postnummer och postorter på en och samma gång?

  *Det finns ingen möjlighet till en "bulk-hämtning" av alla uppgifter.*

## Nyheter

Nyheter, uppdateringar, underhåll och dylikt gällande PAPILITE går att prenumera på som [RSS](https://papilite.se/rss.xml).

## Driftstatus

Målet är att leverera den bästa tjänsten med 100% tillgång utan driftstörningar. 

[Driftstatus](https://stats.uptimerobot.com/NxzP7FNVD9) (UptimeRobot)

## Licens

Distribueras under MIT-licensen. Se `LICENSE` för mer information.

## Kontakt & support

Oavsett vad det gäller angående PAPILITE så finns det olika kontaktvägar, se nedan. Det kan handla om feedback, problem, fel, buggar, idéer eller dylikt. Svar inom 24 timmar, men oftast snabbare än så och donatorer är prioriterade.

[E-post](mailto:lite@papapi.se)

[Kontaktformulär](https://papilite.se/#kontakt)

[GitHub](https://github.com/aliasnille/papilite/issues)