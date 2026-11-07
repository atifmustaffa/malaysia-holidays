# AGENTS.md — Malaysia Holidays

## Purpose

Maintain accurate Malaysian public and school holidays as static JSON, organized by year and state.

**Accuracy > Completeness > Freshness. Never guess, fabricate, or silently publish unverified data.**

## Sources

Use **official Malaysian government sources only**:

- **JPM/BKPP:** https://www.kabinet.gov.my/hari-kelepasan-am/ — federal and state public holidays.
- **Government gazettes:** https://www.kabinet.gov.my/akta-dan-warta/ — special holidays, amendments and cancellations.
- **Official state government portals:** state-specific announcements.
- **KPM:** https://www.moe.gov.my/index.php/kalendar-akademik-semasa — school terms, breaks and festive holidays.

Official amendments supersede earlier schedules. Never treat third-party sites, repos, estimates or generated dates as evidence.

## Files and Schema

Path: `{year}/{STATE_CODE}.json`

Allowed uppercase codes: `JHR, KDH, KTN, MLK, NSN, PHG, PRK, PLS, PNG, SBH, SWK, SGR, TRG, KUL, LBN, PJY`.

```json
{
  "year": 2027,
  "state": "TRG",
  "school_group": "A",
  "public_holidays": [
    {
      "date": "2027-01-01",
      "name": "Example Holiday",
      "type": "state",
      "is_tentative": false,
      "source_url": "https://example.gov.my/document.pdf"
    }
  ],
  "school_holidays": [
    {
      "name": "Example School Break",
      "start_date": "2027-03-01",
      "end_date": "2027-03-07",
      "type": "term",
      "source_url": "https://example.gov.my/document.pdf"
    }
  ]
}
```

**Example records are placeholders, not verified holidays.** Do not publish them.

- Public types: `federal`, `state`, `additional`, `replacement`.
- School types: `term`, `festive`.
- Dates: `YYYY-MM-DD`; school ranges include both endpoints.
- Use official Malay names and direct official document/announcement URLs (not generic landing pages when a direct link is available).
- `is_tentative: true` only when the official source marks a date subject to change.
- Keep identical field names and types across all files. Schema changes require maintainer approval.

## Data Rules

1. Include only holidays legally applicable to the state; federal categories do not automatically apply everywhere.
2. Verify replacement holidays against official rules/announcements; never infer from weekdays.
3. Determine `school_group` from that **year's** KPM calendar, never historical assumptions.
4. Keep public and school holidays separate; include KPM term and additional festive breaks, not every public holiday as a school break.
5. Keep distinct events on the same date, but no duplicate records.
6. Sort public holidays by date then name; school holidays by start date then name.
7. Never publish incomplete/unverified files. Empty arrays must mean officially confirmed absence, not unavailable data.
8. Preserve verified data until superseded by official evidence. Every record needs a traceable official source.
9. Flag conflicting or unclear evidence for maintainer review; never guess.

## Update and Completion Rules

1. Read existing files, then verify official JPM/BKPP, gazettes, state portals and KPM schedules **for every requested year and state**.
2. If a source fails, retry and search alternate official URLs, official gazettes, state government publications and KPM notices. A failed PDF fetch alone is **not** a reason to stop.
3. Compare additions, removals, date/name changes, state applicability, replacements, and school-group/festive changes. Check later official amendments before updating.
4. Change only verified entries; preserve unrelated records. Never treat unavailable or incomplete sources as evidence of deletion.
5. Validate JSON/schema, dates, state codes, applicable states, school groups/ranges, official document URLs, duplicates, sorting, and unexpected deletions.
6. **Completion gate:** For each requested year, verify **all 16 state/territory JSON files**, including both holiday categories, before declaring that year's work complete. Report exact coverage (e.g. `16/16`).
7. If any state cannot be verified after checking the official alternatives, **do not mark the year complete** and do not publish guessed/placeholder data. Report each missing state, attempted sources and the precise blocker. Partial-year publication needs explicit maintainer approval.
8. Commit only verified changes with meaningful messages. No changes = no commit or notification. Notify after successful commits; alert on unresolved conflicts or incomplete requested scope.
9. Do not change schema, repository visibility/settings, automation schedules or hosting without approval.

**Government records are the source of truth. Unresolved conflicts require maintainer review, never inference.**
