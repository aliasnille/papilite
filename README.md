![PAP/API Lite - Alla Sveriges postnummer & postorter](https://papilite.se/papilite-some.png)

# PAP/API Lite

**[PAP/API Lite](https://papilite.se)** eller *PAPILITE* som det förkortas till, är ett oberoende och öppet REST API. API-tjänsten tillhandahåller alla Sveriges postnummer och postorter samt gator, men även postnummer och postorter för Danmark, Norge och Finland. Användare får kostnadsfri tillgång till aktuella uppgifter såsom postnummer och postorter för Sverige och uppgraderade användare får fullständig tillgång. I Sverige finns det över 16.000 postnummer, 1.740 postorter och ungefär 400.000 gator. Antalet postnummer förändras ständigt, nya tillkommer medan andra faller bort. PAPILITE innehåller bara inte uppgifter om postnummer, postorter och gator, utan även kommuner, län och GPS-koordinater för samtliga postnummer. Detta gäller även för Danmark, Norge och Finland, bortsett ifrån gator. Detta är alltså ett komplett, flexibelt och användbart API som sparar tid och pengar när aktuella och korrekta uppgifter är avgörande.

[![Vimeo | PAP/API Lite - Alla Sveriges postnummer & postorter](https://papilite.se/papilite-promo-thumb.png)](https://vimeo.com/467677806)

## Bakgrund

PAPILITE är efterträdaren till föregångaren **PAP/API**, som är helt avsomnad sedan slutet av 2017. Detta API är en betydligt mer kraftfull version än av dess föregångare. Det är flera gånger bättre och snabbare. Skillnaden mellan dem bägge är ytterst små och därav är PAPILITE ett fullvärdigt komplement till föregångaren PAP/API.

Grundaren och utvecklaren av PAPILITE är Senior Fullstack-utvecklaren [Nille](https://linktr.ee/aliasnille) med 15 års erfarenhet av front och back-end i varierande omfattning.

## Komma igång

PAPILITE är öppet och fritt att använda, nu och för alltid. Det krävs dock [registrering](https://papilite.se/komma-igang) för att kunna använda. Gratisvarianten ger möjlighet till maximalt 1.000 anrop per månad och saknar tillgång till bland annat gator i Sverige samt uppgifter från Danmark, Norge och Finland. Om man vill ta del av tjänstens fulla potential kan man uppgradera till betalande användare. Välj [paket](https://papilite.se/priser) efter behov. De första 1.000 anropen varje månad är alltid kostnadsfria. Du betalar därefter bara för det som du använder. Inga månadsavgifter eller bindningstid. Avsluta eller nedgradera när som helst.

I samband med registrering godkänner användare följande [användarvillkor](https://papilite.se/anvandarvillkor).

## Användning

### Anrop

#### Postnummer

Hämta data baserat på postnummer utförs enligt nedan. Endast fullständiga postnummer med fem siffror, ex. 11434 (utan mellanslag eller andra tecken) kommer att ge svar.

**[Endast för uppgraderade användare]** *Anrop med ofullständiga postnummer är möjligt, dock minst tre siffror, ex. 114 eller 1143 (utan mellanslag eller andra tecken).*

| Parameter | Beskrivning                                                  | Exempel                                                      |
| --------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| query     | Fullständigt postnummer med fem siffror<br />*[Ofullständiga postnummer med minimum tre siffror]* | *11434*, *[1143]* eller *[114]* (utan mellanslag eller andra tecken) |
| format    | Format på svaret                                             | *JSON* eller *XML*                                           |
| apikey    | API-nyckel som tillhandahålls vid registrering               | *f21a1127be93feae4efc13dbb7bc587627b22114*                   |

**Exempel på anrop**

`https://api.papapi.se/lite/?query=11434&format=json&apikey=f21a1127be93feae4efc13dbb7bc587627b22114`

#### Postort

Hämta data baserat på postort utförs enligt nedan. Postortens namn kan vara ofullständigt men minst fyra bokstäver krävs för att ge svar.

**[Endast för uppgraderade användare]** *Anrop med mindre antal bokstäver. Det är möjligt med endast två bokstäver, istället för minimum fyra bokstäver.*

| Parameter | Beskrivning                                                  | Exempel                                    |
| --------- | ------------------------------------------------------------ | ------------------------------------------ |
| query     | Fullständig eller ofullständig postort med minst fyra bokstäver<br />*[Ofullständig postort med minimum två bokstäver]* | *Stockholm*, *Stoc* eller *St*             |
| format    | Format på svaret                                             | *JSON* eller *XML*                         |
| apikey    | API-nyckel som tillhandahålls vid registrering               | *f21a1127be93feae4efc13dbb7bc587627b22114* |

**Exempel på anrop**

`https://api.papapi.se/lite/?query=Stockholm&format=json&apikey=f21a1127be93feae4efc13dbb7bc587627b22114`

#### Gata och postort *[Endast för uppgraderade användare]*

Hämta data baserat på gata och postort utförs enligt nedan. Endast fullständigt gatunamn och postort, ex. Birger Jarlsgatan och Stockholm (separerat med "|") kommer att ge svar.

| Parameter | Beskrivning                                            | Exempel                                    |
| --------- | ------------------------------------------------------ | ------------------------------------------ |
| query     | Fullständigt gatunamn och postort | *Birger Jarlsgatan|Stockholm*                      |
| format    | Format på svaret                                       | *JSON* eller *XML*                         |
| apikey    | API-nyckel som tillhandahålls vid registrering         | *f21a1127be93feae4efc13dbb7bc587627b22114* |

**Exempel på anrop**

`https://api.papapi.se/lite/?query=Birger Jarlsgatan|Stockholm&format=json&apikey=f21a1127be93feae4efc13dbb7bc587627b22114`

#### Latitud och longitud *[Endast för uppgraderade användare]*

Hämta data baserat på GPS-koordinater eller latitud och longitud utförs enligt nedan. Både latitud och longitud (ex. 59.329323,18.068581) krävs för att ge svar.

| Parameter | Beskrivning                                            | Exempel                                    |
| --------- | ------------------------------------------------------ | ------------------------------------------ |
| query     | Fullständiga GPS-koordinater, dvs latitud och longitud | *59.329323,18.068581*                      |
| format    | Format på svaret                                       | *JSON* eller *XML*                         |
| apikey    | API-nyckel som tillhandahålls vid registrering         | *f21a1127be93feae4efc13dbb7bc587627b22114* |

**Exempel på anrop**

`https://api.papapi.se/lite/?query=59.329323,18.068581&format=json&apikey=f21a1127be93feae4efc13dbb7bc587627b22114`

#### Nordiska länderna *[Endast för uppgraderade användare]*

Hämta data baserat på land utförs enligt nedan. Notera dock att det går inte att genomföra anrop med gata och postort, utan endast postnummer, postort och GPS-koordinater.

Använd **se** för Sverige, **dk** för Danmark, **no** för Norge och **fi** för Finland. Endast små bokstäver kan användas för landsförkortning. Notera dock att det inte är obligatoriskt att använda **se** för Sverige för det är standard.

| Parameter | Beskrivning                                            | Exempel                                    |
| --------- | ------------------------------------------------------ | ------------------------------------------ |
| query     | Enligt ovan, postnummer, postort och GPS-koordinater  | *0010*, *Oslo* eller *59.917100,10.727400* |
| country | Landsförkortning | *no* |
| format    | Format på svaret                                       | *JSON* eller *XML*                         |
| apikey    | API-nyckel som tillhandahålls vid registrering         | *f21a1127be93feae4efc13dbb7bc587627b22114* |

**Exempel på anrop**

`https://api.papapi.se/lite/?query=0010&country=no&format=json&apikey=f21a1127be93feae4efc13dbb7bc587627b22114`

### Svar

Datan som returneras vid korrekt anrop innehåller följande **postnummer** (*postal_code*), **postort** (*city*), **latitud** (*latitude*), **longitud** (*longitude*), **kommunkod** (*county_code*), **kommun** (*county*), **länskod** (*state_code*), **län** (*state*), **gator** (*streets*), **land** (*country*), **kartlänkar** (*maps*), **notering** (*notes*), **skapad** (*created*) och **uppdaterad** (*updated*).

| Anrop med | Svar *GRATIS* | Svar *BETAL* |
| ----------|---------------|--------------|
| **Postnummer** | Endast en post | Max 100 poster |
| **Postort** | Max 100 poster | Max 100 poster |
| **Gata och postort** | - | Max 100 poster |
| **GPS-koordinater** | - | Max 50 poster |

#### Svarkoder *HTTP-statuskoder*

Anrop kan ge följande svarskoder som är standard HTTP-statuskoder.

| HTTP-statuskod         | Beskrivning                                           |
| ---------------------- | ----------------------------------------------------- |
| **200 — OK**           | Korrekt anrop med svar                                |
| **400 — BAD REQUEST**  | Felaktigt anrop                                       |
| **401 — UNAUTHORIZED** | Felaktig API-nyckel                                   |
| **403 — FORBIDDEN**    | Gräns nådd för anrop per dag eller spärrad API-nyckel |
| **404 — NOT FOUND**    | Korrekt anrop men utan svar                           |

#### Anropskvot *Custom HTTP-headers*

Följande special HTTP-headers kan användas för överblick av anropskvot, antingen dagligen för uppgraderade användare eller måntligen för gratisanvändare.

| HTTP-header        | Beskrivning                 |
| ------------------ | --------------------------- |
| **UserDailyLimit**     | Max antal anrop per dag     |
| **UserDailyQuota**     | Använda anrop för dagen     |
| **UserDailyRemaining** | Kvarvarande anrop för dagen |
| **UserMonthlyLimit**     | Max antal anrop per månad     |
| **UserMonthlyQuota**     | Använda anrop för månaden     |
| **UserMonthlyRemaining** | Kvarvarande anrop för månaden |

#### Svar i JSON

```json
{"api":{"name":"PAP-API Lite","url":"https://papilite.se","version":"X.X","updated":"ÅÅÅÅ-MM-DD TT:MM:SS","encoding":"UTF-8"},"results":[{"postal_code":"11434","city":"Stockholm","latitude":"59.3337496","longitude":"18.0757887","county_code":"0180","county":"Stockholm","state_code":"01","state":"Stockholm","streets":["Birger Jarlsgatan","Engelbrektsplan","Ingmar Bergmans Gata","Nybrogatan"],"country":"SE","maps":["https:\/\/www.google.com\/maps\/@59.3337496,18.0757887,17z","https:\/\/www.openstreetmap.org\/#map=17\/59.3337496\/18.0757887"],"note":"","created":"ÅÅÅÅ-MM-DD TT:MM:SS","updated":"ÅÅÅÅ-MM-DD TT:MM:SS"} [...] ]}
```

#### Svar i XML

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
    <country>SE</country>
    <maps>
      <map>https://www.google.com/maps/@59.3337496,18.0757887,17z</map>
      <map>https://www.openstreetmap.org/#map=17/59.3337496/18.0757887</map>
    </maps>
    <note></note>
    <created>ÅÅÅÅ-MM-DD TT:MM:SS</created>
    <updated>ÅÅÅÅ-MM-DD TT:MM:SS</updated>
  </result>
  [...] 
</results>
```

## FAQ

- **Hur aktuella är uppgifterna som tillhandahålls av tjänsten?**
  *Alla uppgifter uppdateras regelbundet för att alltid vara aktuella.*
- **Vilken är källan till uppgifterna?**
  *Flera tillförlitliga och oberoende register är källan till uppgifterna som tjänsten tillhandahåller. Registerna samkörs med varandra och eventuella differenser kontrolleras	för att säkerställa att det är korrekta uppgifter.*
- **Finns det några adressuppgifter?**
  *Det beror lite på. Det finns gator eller gatunamn men inga husnummer. Gatorna är grupperade per postnummer. Tillgång till gator är endast för betalande användare.*
- **Hur exakta är GPS-koordinaterna?**
  *Ungefär 80-85 % av GPS-koordinaterna har högre exakthet än resterande del. GPS-koordinaterna	återspeglar en central position inom området där exempelvis ett postnummer eller postort ligger. Storleken på postnummerområden varierar.*
- **Kan jag få ut alla postnummer och postorter på en och samma gång?**
  *Det finns ingen möjlighet till en "bulk-hämtning" av alla uppgifter. Om det hade varit möjligt	hade hela tjänsten som API förlorat sitt syfte.*
- **Finns det uppgifter för flera länder?**
  *Aktuella uppgifter för Danmark, Norge och Finland finns för alla betalande användare, men utan gator/gatunamn.*
- **Hur använder jag tjänsten?**
  *Vissa e-handelsystem och CRM-system har koppling till PAP/API Lite. Om det inte finns något förberett så behöver du ha programmeringskunskaper. I vilket programmeringsspråk är helt oväsentligt, då denna tjänst är oberoende av det. En annan väg är att kontakta leverantören av din hemsida,	webbshop, CRM-system eller dylikt för att framföra önskan om att kunna använda PAP/API Lite.*  
- **Vad gäller för postnummer över kommun- och/eller länsgränser?**
  *Det är så att det finns postnummer som sträcker sig utanför kommun- och/eller länsgränser. Sveriges administrativa indelning av kommuner och län följer tyvärr inte alltid det gällande postnummersystemet. Därför har vi valt (än så länge) att ett postnummer som stäcker sig utanför, får kommun och län tilldelat beroende på vart större delen av postnummerområdet är lokaliserat.*

## Nyheter

Nyheter, uppdateringar, underhåll och dylikt för tjänsten kommuniceras först och främst via mail eller [hemsidan](https://papilite.se/). Alternativt via sociala medier [Facebook](https://www.facebook.com/papilitese), [Instagram](https://instagram.com/papilite_se) eller [Twitter](https://twitter.com/papilite_se).

## Driftstatus

Tillgängligheten för tjänsten är viktig och strävan är 100 % tillgänglighet. Eventuella akuta driftstörningar rapporteras [här](https://stats.uptimerobot.com/NxzP7FNVD9).

## Licens

Distribueras under MIT-licensen. Se `LICENSE` för mer information.

## Kontakt & support

Frågor, idéer, feedback, problem, fel, buggar eller liknande besvaras via nedanstående kontaktvägar. Svar inom 24 timmar, men oftast snabbare. Alla uppgraderade användare har prioriterad support med svar inom 6 timmar.

[E-post](mailto:info@papilite.se)

[Kontaktformulär](https://papilite.se/kontakt)

[GitHub](https://github.com/aliasnille/papilite/issues)