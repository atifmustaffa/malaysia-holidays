# Malaysia Holidays

Free Malaysian public and school holiday data in static JSON, organized by **year and state**. No API server or API key required.

## Structure

```text
2027/
  JHR.json
  KDH.json
  TRG.json
  ...
README.md
```

Each file contains public holidays for its state and school holiday ranges for that year's KPM school group.

## Usage

Each file has a year/state-based raw JSON URL:

```text
https://raw.githubusercontent.com/atifmustaffa/malaysia-holidays/main/2027/TRG.json
```

Expected shape (empty arrays shown for illustration, **not verified holiday data**):

```json
{
  "year": 2027,
  "state": "TRG",
  "school_group": "A",
  "public_holidays": [],
  "school_holidays": []
}
```

A missing file means data is not published, **not** that there are no holidays.

## Sources

- [JPM/BKPP](https://www.kabinet.gov.my/hari-kelepasan-am/) — public holidays
- [Government gazettes](https://www.kabinet.gov.my/akta-dan-warta/) and official state portals — amendments and special holidays
- [KPM](https://www.moe.gov.my/index.php/kalendar-akademik-semasa) — school holidays

Maintained by an AI agent using official Malaysian government sources.
