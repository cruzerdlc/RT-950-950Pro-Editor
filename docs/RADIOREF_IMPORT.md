# RadioRef Import

RadioRef Import is available from **File > RadioRef Import**.

## Search options

- ZIP Code: resolves the city, county, and state, then searches the county.
- City & State: resolves the county and places city-related results first when possible.
- County & State: uses the bundled county-ID cache for a direct county search.
- GMRS/FRS Channels: generates the 22 standard US simplex channel frequencies.
- NOAA Weather Channels: generates the seven standard NOAA Weather Radio frequencies.

No RadioReference API key is required. The feature renders JavaScript pages through Playwright when possible and falls back to standard HTML retrieval.

## Importing into the current file

1. Open or read the destination radio file first.
2. Open **File > RadioRef Import**.
3. Search and review the result table.
4. Select the rows to import.
5. Choose the destination zone.
6. Choose Append or Overwrite and, for Overwrite, the starting channel.
7. Click **Import Selected into Current File**.
8. Review every imported channel before writing the radio.

RadioRef results default to receive-only. Digital systems such as DMR, P25, NXDN, D-STAR, and C4FM may be listed, but the RT-950/950Pro cannot decode their digital audio.

## CSV and cache tools

The **CSV & Cache Tools** page can:

- Validate a CHIRP CSV.
- Filter an existing CHIRP CSV by mode.
- Convert CHIRP CSV to a human-readable TXT file.
- Refresh one state's county cache or rebuild all states.

The bundled `countyID.db` is a read-only seed. Refreshed cache data is stored in the user's RT950ProEditor application-data folder.

## Browser requirements

The packaged Windows build tries Microsoft Edge first, then Google Chrome, then a Playwright-managed Chromium installation. If no compatible browser is available, install Edge or Chrome. Source users may also run:

```text
python -m playwright install chromium
```

## Important

Website layout changes can temporarily break scraping. Use reasonable request rates, follow the website's terms, and comply with all radio laws and license requirements.
