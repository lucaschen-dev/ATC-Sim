# CSV traffic schedules

In v1.1, CSV scheduling remains separate from generated demand. Free duty, timed duty and the completion challenge can use an imported schedule; traffic-wave demand applies to generated traffic, so selecting CSV replaces that mode with a timed duty. A scheduled time is a demand time, not permission to bypass occupancy, weather or spacing checks.

CSV schedules let you choose the identities and planned times of simulated flights. They do not import real radar tracks or validate an airline's real published timetable. The included files are **fictional training schedules**.

## Import a schedule

1. Start Game → choose an airport → choose **GND**, **APP** or **ACC**.
2. In duty setup, choose **CSV Schedule** under Traffic.
3. Set the **UTC service date** before importing. This date applies to `HH:mm` values.
4. Choose a UTF-8 CSV file and inspect the preview. Check errors, warnings and which rows this position will use.
5. Confirm the valid preview, then start the duty.

Use **Save position template** to export a template for the selected airport/position. If you change the UTC date, import again. CSV mode generates only the accepted schedule, without mixing in endless traffic.

## Columns

```csv
call_sign,aircraft_type,departure_icao,arrival_icao,scheduled_time_utc,stand,payload_kg,airline,radio_language
CSN3718,AJ27,ZGGG,ZSSM,08:00,,8400,China Southern Airlines,zh
THA875,A333,VTBS,ZGGG,2026-11-09T08:12:00Z,,36000,Thai Airways,en
```

The **first five columns are required**. Optional fields may be blank; retain their commas when using the nine-column layout. The old seven-column layout remains supported.

| Column | Value and validation |
|---|---|
| `call_sign` | 2–7 ASCII letters/digits, starting with a letter; converted to uppercase. This checks syntax, not airline ownership. |
| `aircraft_type` | ICAO-style aircraft type, 2–4 letters/digits starting with a letter, such as `A320`, `B738`, `B789`. A valid code does not guarantee a dedicated performance model. |
| `departure_icao` | Four-letter departure airport code. |
| `arrival_icao` | Four-letter destination airport code; must differ from departure. Syntactic validity does not verify the airport or the real route. |
| `scheduled_time_utc` | `HH:mm` on the selected UTC date, or ISO 8601 with an explicit `Z`/time-zone offset. A timezone-free ISO date/time is rejected. Read the position-specific timing below. |
| `stand` | Optional, up to 16 letters/digits/spaces or `/`, `-`, `_`. Blank lets GND assign a supported stand. A specified unavailable/unverified/occupied stand can make a flight wait. |
| `payload_kg` | Optional numeric payload in kg, including passengers/baggage/cargo. It is not fuel, passenger count or load factor. Input range 0–1,000,000 filters malformed values; it is not aircraft performance approval. |
| `airline` | Optional display name, up to 80 characters; names may be English or Chinese. |
| `radio_language` | `en`, `zh`, `auto` or blank. Auto uses Chinese for mainland-to-mainland flights and English when an endpoint is outside that group, including Hong Kong, Macau or Taiwan. This affects routine crew radio; system text follows its own localization. |

All times are **UTC**. For example, 08:00 UTC is 16:00 China Standard Time.

## What the time means in each position

| Position | Rows admitted | Meaning of the time |
|---|---|---|
| GND | Arrivals/departures at the selected airport | Departure enters the stand/request flow at its planned time. An arrival can be announced 60 seconds before its planned landing and is sequenced with runway occupancy. The clock begins at the first relevant local planned movement. |
| APP | Arrivals/departures at the selected airport | Arrival enters about 20 minutes before its planned landing. Departure enters about 10 minutes after its planned takeoff. The clock begins 30 seconds before the earliest computed admission. |
| ACC | Supported arrivals, departures and overflights | The column is the **planned sector-entry time**, not takeoff/landing time. Two endpoints outside the selected airport classify a row as an overflight. The clock begins 30 seconds before the earliest admission. |

Capacity, weather, entry separation, stand availability and an already-active same callsign can delay actual admission. A repeated callsign at a different time is allowed, but the earlier active flight must clear before that identity is reused.

Entry/exit fixes and simulated tracks are supplied by the airport and training-sector configuration. The CSV does not carry a filed real-world route. A destination airport is not the same as a sector exit fix.

## Included examples

| File | Flights | Use |
|---|---:|---|
| [Domestic balanced](../examples/01-domestic-balanced.csv) | 20 | 10 arrivals/10 departures at ZGGG, varied domestic destinations and Chinese radio. |
| [International diverse](../examples/02-international-diverse.csv) | 20 | 10 arrivals/10 departures at ZGGG, varied international carriers and English radio. |
| [Mixed peak](../examples/03-mixed-peak.csv) | 32 | 16 arrivals/16 departures at ZGGG, domestic/international mix. |
| [Regional overflights](../examples/04-regional-overflights.csv) | 24 | ZGGG ACC practice, overflights with neither endpoint at ZGGG. |

The four examples contain **96 fictional flights**. They preserve the game's existing sample identities and languages. For another playable airport, export that position's own template rather than merely assuming a ZGGG sample is compatible. If you reuse a local-flight sample for ACC, rewrite its times as sector-entry times.

## File limits and troubleshooting

The importer supports UTF-8 (with or without BOM), LF/CRLF, quoted commas/newlines and doubled quotes inside quoted fields. Some explicit header aliases are accepted; the standard English names above are the safest format.

Files are limited to **5 MB** and **10,000 data rows**. Each GND/APP/ACC duty uses at most **2,000 relevant plans**, with a relevant time span of **less than 31 days**. Split a larger period into separate files.

Missing/duplicate required headers, malformed quotes, invalid values and duplicate callsign/time pairs block confirmation. Errors retain source-row information; the game does not silently discard bad rows and start with an unexplained subset. Other valid but irrelevant rows can remain in the source schedule without being admitted to the selected position.
