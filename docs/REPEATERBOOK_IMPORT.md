# RepeaterBook Import

RT-950/950Pro Editor uses RepeaterBook's approved Export API for a narrowly scoped, user-triggered radio-programming workflow. It does not scrape public pages, mirror RepeaterBook, or create a reusable offline repeater database.

## Get a personal token

1. Open **File > RepeaterBook Import**.
2. Click **Generate / manage my token**.
3. Sign in to RepeaterBook.
4. Select **RT-950/950Pro Editor** from the approved applications list.
5. Generate a personal app-bound token.
6. Copy the complete token when it is shown. It begins with `rbuapp_`.
7. Paste it into the importer.

A personal token is tied to one RepeaterBook account and this application. Do not share it. Revoke or rotate it from the same RepeaterBook dashboard if it is exposed.

The editor intentionally rejects shared tokens beginning with `app_`. No shared RepeaterBook credential is embedded in the source, installer, or executable.

## Token storage

When **Remember securely** is enabled on Windows, the token is encrypted with Windows Data Protection. The encrypted value is stored in the editor's local settings and can normally be decrypted only by the same Windows user account.

Use **Clear saved token** to remove it. Disabling **Remember securely** keeps the token only for the current session.

The token is sent in the `X-RB-App-Token` HTTP header. It is not placed in request URLs, logs, screenshots, release files, or source code.

## Search

### United States

The importer uses RepeaterBook's North America endpoint for United States searches and supports these documented parameters:

- State
- City
- County
- Callsign, including RepeaterBook `%` wildcards
- Frequency
- Landmark
- Mode: Analog, DMR, NXDN, P25, or TETRA
- Emergency-service classification: ARES, RACES, SKYWARN, or CANWARN
- Amateur or GMRS service

For a US ZIP search, the editor first resolves the ZIP to a city and state, then performs the RepeaterBook API search. ZIP resolution is not a distance-radius search.

### Rest of world

The rest-of-world endpoint supports country, region, city, callsign, frequency, landmark, and mode filters. Access depends on the scopes assigned to the user's token.

## Importing

1. Open or read the destination radio configuration.
2. Open **File > RepeaterBook Import**.
3. Enter search filters and click **Search RepeaterBook**.
4. Review the returned rows and select the desired repeaters.
5. Choose the destination zone.
6. Choose **Append after last used channel** or **Overwrite starting at channel**.
7. Choose how digital-only repeaters should be handled.
8. Click **Import Selected**.
9. Review every imported channel before writing the radio.

Analog-capable repeaters use the published output frequency for RX, input frequency for TX, uplink tone for TX tone, and downlink tone for RX squelch when those fields are available.
If an analog result does not include a published input frequency, the editor imports it receive-only rather than assuming the repeater output is also a valid transmit frequency.

The RT-950/950Pro cannot decode DMR, NXDN, P25, TETRA, D-Star, or System Fusion digital voice. Digital-only results are therefore imported receive-only by default or may be skipped.

## Errors

- **Token rejected:** Generate a new complete `rbuapp_` token from the API Apps dashboard.
- **Application inactive or revoked:** Check the RepeaterBook dashboard and application status.
- **Scope denied:** The token is not approved for the selected North America or rest-of-world endpoint.
- **User-Agent mismatch:** Update to the latest editor release; the application uses the approved User-Agent prefix.
- **Rate limited:** Stop searching and wait before trying again. Do not repeatedly retry.

## Data use

RepeaterBook results are retrieved only after the user clicks Search and are used for the current radio-programming operation. The editor does not create a public directory, map, bulk feed, secondary API, or reusable offline database.

**Data courtesy of RepeaterBook.com.**
