# Malaysia Holidays

Free Malaysian public and school holiday data in static JSON, organized by **year and state**. No API server or API key required.

## Structure

```text
2027/
  JHR.json
  KDH.json
  TRG.json
  ...
AGENTS.md
README.md
```

Each file contains public holidays for its state and school holiday ranges for that year's KPM school group.

## Usage

Once this repository is public, fetch a year/state file directly:

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

The supported state codes and full record schema are defined in [AGENTS.md](AGENTS.md). A missing file means data is not published, **not** that there are no holidays.

## Sources

- [JPM/BKPP](https://www.kabinet.gov.my/hari-kelepasan-am/) — public holidays
- [Government gazettes](https://www.kabinet.gov.my/akta-dan-warta/) and official state portals — amendments and special holidays
- [KPM](https://www.moe.gov.my/index.php/kalendar-akademik-semasa) — school holidays

Data is maintained against **official Malaysian government sources only**, with verified changes committed as needed. See [AGENTS.md](AGENTS.md) for source priority, validation and update rules.
