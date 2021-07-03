![PAP/API Lite](https://papilite.se/papapi-lite-github-en.png)

# PAP/API Lite

[**PAP/API Lite**](https://papilite.se/) or abbreviated to *PAPILITE* is an open REST API with all of Sweden's postal codes and postal cities. By using this API, the user gets free access to current information for postal codes and postal cities. There are over 16,000 postal codes in Sweden. The number of postal codes is constantly changing. Postal codes are added or dropped every now and then.
PAPILITE contains not only information about postal codes and postal cities, but also about states, counties and GPS-coordinates for all postal codes. Additionally streets for those users who choose to upgrade by a "one-time donation".
This is a complete API that fulfills its purpose and can be used in many applications. PAPILITE facilitates and helps in processes where current and correct information is crucial.

## Background

PAPILITE is a lite version of [PAP/API](https://www.papapi.se/). The predecessor or the original PAP/API was launched in early 2015, but since the end of 2017, the project has fallen asleep and currently contains outdated information. This API is much the same but not as comprehensive, but improved. PAPILITE is intended to be a full-fledged complement to PAP/API but without addresses.

Behind PAPILITE, but also PAP/API stands full stack-developer [Nille](https://nillewebb.se/) with over 12 years of experience in development both front- och back-end. The development of this project is his way of bringing out the spark again for what he once burned for.

## Getting Started

PAPILITE is open and free to use. [Registration](https://papilite.se/#registrera) (in Swedish) is required for use and a maximum of 500 request per day is allowed. It's possible to receive up to 5,000 or 10,000 request per day and more possibilities and functions through [donation](https://papilite.se/#priser) (in Swedish). After a "one-time donation", you are forever upgraded to the selected package. No monthly or annual cost will be added.

*When you registering you accept the following [terms and conditions](https://papilite.se/Anvandarvillkor-for-PAPAPI-Lite.pdf) (in Swedish)*

## Usage

### Request

#### Postal code

Retrieving data based on postal code is performed as below.

| Parameter | Description                       | Example                                      |
| --------- | --------------------------------- | -------------------------------------------- |
| query     | Full postal code with five digits | *11434* (without spaces or other characters) |
| format    | Response format                   | *json*, *xml* or *csv*                       |
| apikey    | API-key by registration           | *f21a1127be93feae4efc13dbb7bc587627b22114*   |

**Request example**

`https://api.papapi.se/lite/?query=11434&format=json&apikey=f21a1127be93feae4efc13dbb7bc587627b22114`

#### Postal city

Retrieving data based on postal city is performed as below.

| Parameter | Description                                              | Example                                    |
| --------- | -------------------------------------------------------- | ------------------------------------------ |
| query     | Full or incomplete postal city but at least four letters | *Stockholm* or *Stoc*                      |
| format    | Response format                                          | *json*, *xml* or *csv*                     |
| apikey    | API-key by registration                                  | *f21a1127be93feae4efc13dbb7bc587627b22114* |

**Request example**

`https://api.papapi.se/lite/?query=Stockholm&format=json&apikey=f21a1127be93feae4efc13dbb7bc587627b22114`

### Response

Returned data on a correct request contains *<u>postal code</u>*, *<u>postal city</u>*, *<u>latitude</u>*, *<u>longitude</u>*, *<u>county code</u>*, *<u>county</u>*, *<u>state code</u>*, *<u>state</u>*, *<u>streets</u>*, *<u>notes</u>* and *<u>updated</u>*.

#### Response codes

Request will provide the following response codes which are standard HTTP Status Codes.

| HTTP Status Codes  | Description                                          |
| ------------------ | ---------------------------------------------------- |
| 200 — OK           | Correct request with response                        |
| 400 — BAD REQUEST  | Incorrect/bad request                                |
| 401 — UNAUTHORIZED | Incorrect API-key                                    |
| 403 — FORBIDDEN    | Limit reached for request per day or blocked API-key |
| 404 — NOT FOUND    | Correct request without response                     |

#### Daily request quota

By custom HTTP-headers you get an overview of your daily request quota.

| HTTP-headers       | Description                                          |
| ------------------ | ---------------------------------------------------- |
| UserDailyLimit     | Maximum number of requests per day                   |
| UserDailyQuota     | Used requests for the day                            |
| UserDailyRemaining | Remaining requests for the day                       |

#### Response examples

Response by postal code request contains only one entry, while response by postal city request contain up to 100 entries.

**JSON**

```json
{"api":{"name":"PAP/API Lite","url":"https://papilite.se","version":"X.X","updated":"YYYY-MM-DD HH:MM:SS","encoding":"UTF-8"},"results":[{"postal_code":"10004","city":"Stockholm","latitude":"59.3293235","longitude":"18.0685808","county_code":"0180","county":"Stockholm","state_code":"01","state":"Stockholm","streets":["Test"],"note":"","updated":"YYYY-MM-DD HH:MM:SS"},{"postal_code":"10005","city":"Stockholm","latitude":"59.3293235","longitude":"18.0685808","county_code":"0180","county":"Stockholm","state_code":"01","state":"Stockholm","streets":["Leveranspunkt"],"note":"","updated":"YYYY-MM-DD HH:MM:SS"},{"postal_code":"10012","city":"Stockholm","latitude":"59.3293235","longitude":"18.0685808","county_code":"0180","county":"Stockholm","state_code":"01","state":"Stockholm","streets":["Riksdagen"],"note":"","updated":"YYYY-MM-DD HH:MM:SS"} [...]
```

**XML**

```xml
<results>
	<api>
		<name>PAP/API Lite</name>
		<url>https://papilite.se</url>
		<version>X.X</version>
		<updated>YYYY-MM-DD HH:MM:SS</updated>
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
		<streets>
			<street>Test</street>
		</streets>		
		<note></note>
		<updated>YYYY-MM-DD HH:MM:SS</updated>
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
		<streets>
			<street>Leveranspunkt</street>
		</streets>		
		<note></note>
		<updated>YYYY-MM-DD HH:MM:SS</updated>
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
		<streets>
			<street>Riksdagen</street>
		</streets>		
		<note></note>
		<updated>YYYY-MM-DD HH:MM:SS</updated>
	</result>
[...]
```

**CSV**

```
postal_code;city;latitude;longitude;county_code;county;state_code;state;streets;note;updated
10004;Stockholm;59.3293235;18.0685808;0180;Stockholm;01;Stockholm;Test;;YYYY-MM-DD HH:MM:SS
10005;Stockholm;59.3293235;18.0685808;0180;Stockholm;01;Stockholm;Leveranspunkt;;YYYY-MM-DD HH:MM:SS
10012;Stockholm;59.3293235;18.0685808;0180;Stockholm;01;Stockholm;Riksdagen;;YYYY-MM-DD HH:MM:SS
[...]
\### PAP/API Lite | https:///docs | v X.X | YYYY-MM-DD HH:MM:SS | UTF-8 ###
```

#### For donors

Everyone who makes a *"one-time donation"* gets more features, including returned streets grouped by postal code in the response result, requests with incomplete postal codes, request with fewer letters for postal cities and retrieving data based on latitude and longitude. Information regarding this can be found on the [official website](https://papilite.se/) (in Swedish).

## FAQ

- ##### How current is the information that can be retrieved?

  *All information is updated regularly and to be more precise, this happens every 14 days.*

- ##### Is there any information about addresses?

  *This is a lite version of the original [PAP/API](https://papapi.se/) and that is what separates the versions. So there is no information about addresses.*

- ##### What information can I retrieve?

  *Besides postal codes and postal cities, you also get information about latitude, longitude, county, county code, state, state code for every postal code.*

- ##### What formats can I retrieve the information in?

  *For the moment, it's JSON, XML and CSV.*

- ##### Can I retrieve all postal codes and postal cities at once?

  *No, it's not possible to make a one request and get all information at once.*

## News & Updates

News, updates, maintenance and similar things regarding PAPILITE, please subscribe to our [RSS](https://papilite.se/rss.xml).

## Operating Status

The goal is to deliver the best service with 100% availability and without operational disruptions.

[Operating Status](https://stats.uptimerobot.com/NxzP7FNVD9) (UptimeRobot)

## License

Distributed under the MIT License. See `LICENSE` for more information.

## Contact & Support

There are different ways to contact us (see below) regarding PAPILITE. This may involve feedback, problems, errors, bugs, ideas or similar. Responses within 24 hours, but usually faster than that and donors are prioritized.

[E-mail](mailto:info@papilite.se)

[Contact Form](https://papilite.se/#kontakt)

[GitHub](https://github.com/aliasnille/papilite/issues)