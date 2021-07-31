![PAP/API Lite - Alla Sveriges postnummer & postorter](https://papilite.se/papilite-some-github.jpg)

# PAP/API Lite

**[PAP/API Lite](https://papilite.se)** eller *PAPILITE* som det förkortas till, är ett oberoende och öppet REST API med alla Sveriges postnummer och postorter samt gator. Användare får fri tillgång till aktuella uppgifter om bland annat postnummer och postorter. I Sverige finns det över 16.000 postnummer, 1.740 postorter och ungefär 400.000 gator. Antalet postnummer förändras ständigt, nya tillkommer medan andra faller bort. PAPILITE innehåller bara inte uppgifter om postnummer, postorter och gator utan även om kommuner, län och GPS-koordinater för samtliga postnummer. Detta är ett komplett, flexibelt och användbart API som sparar tid och pengar när aktuella och riktiga uppgifter är avgörande.

[![Vimeo | PAP/API Lite - Alla Sveriges postnummer & postorter](https://papilite.se/papilite-promo-thumb.jpg)](https://vimeo.com/467677806)

## Bakgrund

PAPILITE är föregångaren till [PAP/API](https://www.papapi.se/), som är avsomnat sedan slutet av 2017. Detta API är en smalare och mer trimmad version än dess föregångare, men flera gånger bättre och snabbare. Skillnaden mellan dem bägge är ytterst små och därav är PAPILITE ett fullvärdigt komplement till PAP/API och andra liknande tjänster.

Grundaren och utvecklaren av PAPILITE är full stack-utvecklaren [Nille](https://linktr.ee/aliasnille) med nästan 15 års erfarenhet av front och back-end i varierande omfattning. Efter flera års både fysisk ock psykisk ohälsa har detta projekt blivit hans sätt att locka fram gnistan för det han en gång brann för.

## Komma igång

PAPILITE är öppet och fritt att använda, nu och för alltid. Det krävs dock [registrering](https://papilite.se/#registrera) för att kunna använda. Gratisvarianten ger möjlighet till maximalt 500 anrop per dag och saknar tillgång till bland annat gator. Om man vill ta del av tjänstens fulla potential kan man göra "engångsdonation". Det finns två olika [donationspaket](https://papilite.se/#priser) att välja på, beroende på vad behovet är. Det handlar endast om "engångsdonation", inga andra kostnader tillkommer någonsin, såsom månads- eller årskostnader.

I samband med registrering godkänner användaren följande [användarvillkor](https://papilite.se/Anvandarvillkor-for-PAPAPI-Lite.pdf).

## Användning

### Anrop

#### Postnummer

Hämta data baserat på postnummer utförs enligt nedan. Endast fullständiga postnummer med fem siffror, ex. 12345 (utan mellanslag eller andra tecken) kommer att ge svar.

**[Endast för donatorer]** *Anrop med ofullständiga postnummer är möjligt, dock minst tre siffror, ex. 123 eller 1234 (utan mellanslag eller andra tecken).*

| Parameter | Beskrivning                                                  | Exempel                                                      |
| --------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| query     | Fullständigt postnummer med fem siffror<br />*[Ofullständiga postnummer med minimum tre siffror]* | *11434*, *[1143]* eller *[114]* (utan mellanslag eller andra tecken) |
| format    | Format på svaret                                             | *JSON* eller *XML*                                           |
| apikey    | API-nyckel som tillhandahålls vid registrering               | *f21a1127be93feae4efc13dbb7bc587627b22114*                   |

**Exempel på anrop**

`https://api.papapi.se/lite/?query=11434&format=json&apikey=f21a1127be93feae4efc13dbb7bc587627b22114`

#### Postort

Hämta data baserat på postort utförs enligt nedan. Postortens namn kan vara ofullständigt men minst fyra bokstäver krävs för att ge svar.

**[Endast för donatorer]** *Anrop med mindre antal bokstäver. Det är möjligt med endast två bokstäver, istället för minimum fyra bokstäver.*

| Parameter | Beskrivning                                                  | Exempel                                    |
| --------- | ------------------------------------------------------------ | ------------------------------------------ |
| query     | Fullständig eller ofullständig postort med minst fyra bokstäver<br />*[Ofullständig postort med minimum två bokstäver]* | *Stockholm*, *Stoc* eller *St*             |
| format    | Format på svaret                                             | *JSON* eller *XML*                         |
| apikey    | API-nyckel som tillhandahålls vid registrering               | *f21a1127be93feae4efc13dbb7bc587627b22114* |

**Exempel på anrop**

`https://api.papapi.se/lite/?query=Stockholm&format=json&apikey=f21a1127be93feae4efc13dbb7bc587627b22114`

#### Latitud och longitud *[Endast för donatorer]*

Hämta data baserat på latitud och longitud utförs enligt nedan. Både latitud och longitud (ex. 59.329323,18.068581) krävs för att ge svar.

| Parameter | Beskrivning                                            | Exempel                                    |
| --------- | ------------------------------------------------------ | ------------------------------------------ |
| query     | Fullständiga GPS-koordinater, dvs latitud och longitud | *59.329323,18.068581*                      |
| format    | Format på svaret                                       | *JSON* eller *XML*                         |
| apikey    | API-nyckel som tillhandahålls vid registrering         | *f21a1127be93feae4efc13dbb7bc587627b22114* |

**Exempel på anrop**

`https://api.papapi.se/lite/?query=59.329323,18.068581&format=json&apikey=f21a1127be93feae4efc13dbb7bc587627b22114`

### Svar

Datan som returneras vid korrekt anrop innehåller följande **postnummer** (*postal_code*), **postort** (*city*), **latitud** (*latitude*), **longitud** (*longitude*), **kommunkod** (*county_code*), **kommun** (*county*), **länskod** (*state_code*), **län** (*state*), [**gator** (*streets*)], **notering** (*note*) och **uppdaterad** (*updated*).

#### Svarkoder

Anrop kan ge följande svarskoder som är standard HTTP-statuskoder.

| HTTP-statuskod         | Beskrivning                                           |
| ---------------------- | ----------------------------------------------------- |
| **200 — OK**           | Korrekt anrop med svar                                |
| **400 — BAD REQUEST**  | Felaktigt anrop                                       |
| **401 — UNAUTHORIZED** | Felaktig API-nyckel                                   |
| **403 — FORBIDDEN**    | Gräns nådd för anrop per dag eller spärrad API-nyckel |
| **404 — NOT FOUND**    | Korrekt anrop men utan svar                           |

#### Daglig anropskvot

Följande special HTTP-headers kan användas för överblick av daglig anropskvot.

| HTTP-header        | Beskrivning                 |
| ------------------ | --------------------------- |
| UserDailyLimit     | Max antal anrop per dag     |
| UserDailyQuota     | Använda anrop för dagen     |
| UserDailyRemaining | Kvarvarande anrop för dagen |

#### Exempel på svar

Svar på anrop för postnummer innehåller endast en post medan svar på anrop för postort kan innehålla upp till 100 poster.

**[Endast för donatorer]** *Svar på anrop för ofullständiga postnummer eller postort kan innehålla upp till 100 poster. Svar på anrop baserat på latitud och longitud (GPS-koordinater) innehåller max 50 poster och sorterat efter kortast distans. Svaret innehåller även gator (streets) som är grupperade per postnummer.*

**JSON**

```json
{"api":{"name":"PAP/API Lite","url":"https://papilite.se","version":"X.X","updated":"ÅÅÅÅ-MM-DD TT:MM:SS","encoding":"UTF-8"},"results":[{"postal_code":"11434","city":"Stockholm","latitude":"59.3337496","longitude":"18.0757887","county_code":"0180","county":"Stockholm","state_code":"01","state":"Stockholm","streets":["Birger Jarlsgatan", "Engelbrektsplan", "Ingmar Bergmans Gata", "Nybrogatan"],"note":"","updated":"ÅÅÅÅ-MM-DD TT:MM:SS"}]}
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
        <postal_code>11434</postal_code>
        <city>Stockholm</city>
        <latitude>59.3337496</latitude>
        <longitude>18.0757887</longitude>
        <county_code>0180</county_code>
        <county>Stockholm</county>
        <state_code>01</state_code>
        <state>Stockholm</state>
        <streets>
            <street>Birger Jarlsgatan</street>
            <street>Engelbrektsplan</street>
            <street>Ingmar Bergmans Gata</street>
            <street>Nybrogatan</street>
        </streets>
        <note></note>
        <updated>ÅÅÅÅ-MM-DD TT:MM:SS</updated>
    </result>
</results>
```

## FAQ

- **Hur aktuella är uppgifterna som tillhandahålls av tjänsten?**
  *Alla uppgifter uppdateras regelbundet och för att vara mer exakt så sker detta var 14:de dag.*
- **Vilken är källan till uppgifterna?**
  *Flera tillförlitliga och oberoende register är källan till uppgifterna som tjänsten tillhandahåller. Registerna samkörs med varandra och eventuella differenser kontrolleras.*
- **Finns det några adressuppgifter?**
  *Det beror lite på. Det finns gator eller gatunamn men inga husnummer. Gatorna är grupperade per postnummer. Tillgång till gator är endast för dem som har donerat.*
- **Hur exakta är GPS-koordinaterna?**
  *Ungefär 70-80 % av GPS-koordinaterna har högre exakthet än resterande. GPS-koordinaterna återspeglar en central position inom området där exempelvis ett postnummer eller postort ligger. Storleken på postnummerområden varierar.*
- **Kan jag få ut alla postnummer och postorter på en och samma gång?**
  *Det finns ingen möjlighet till en "bulk-hämtning" av alla uppgifter. Om det hade varit möjligt hade hela tjänsten som API förlorat sitt syfte.*
- **Vad används donationerna till?**
  *Alla pengar från donationer återinvesteras i tjänsten för att göra den ännu bättre. Bra kan bli bättre, och bättre kan bli bäst. Medan andra ord är inte tjänsten vinstdrivande.*

## Nyheter

Nyheter, uppdateringar, underhåll och dylikt för PAPILITE går att prenumerera på som [RSS](https://papilite.se/rss.xml).

## Driftstatus

Tillgängligheten för tjänsten är viktig och strävan är 100 % tillgänglighet. Eventuella akuta driftstörningar rapporteras [här](https://stats.uptimerobot.com/NxzP7FNVD9).

## Licens

Distribueras under MIT-licensen. Se `LICENSE` för mer information.

## Kontakt & support

Frågor, idéer, feedback, problem, fel, buggar eller liknande besvaras via nedanstående kontaktvägar. Svar inom 24 timmar, men oftast snabbare. Alla donatorer har prioriterad support med svar inom 4-6 timmar.

[E-post](mailto:info@papilite.se)

[Discord](https://discord.gg/NSjB2uPq2z)

[Kontaktformulär](https://papilite.se/#kontakt)

[GitHub](https://github.com/aliasnille/papilite/issues)