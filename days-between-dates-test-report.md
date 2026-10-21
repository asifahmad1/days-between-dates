# Days Between Dates Calculator v1.0 — Test Report & Wix Listing

**File:** `~/workspace/your_files/days-between-dates/index.html` (19,379 bytes — well under the 150 KB limit)
**Version:** 1.0 · **Built:** 20 Oct 2026 · **Creator:** Dr. Asif Ahmad (Asif SaaS Studio)

## Short description
Count the exact days between two dates. Pick a start and end date and get the total days (with an option to include the end date), a true calendar breakdown into years, months and days, weeks, business days (Mon–Fri) and weekend days — plus each date's day of the week. A companion tool adds or subtracts days from any date. The batch mode reads pasted or uploaded text (one date pair per line, in ISO, day/month/year, or month-name formats), calculates every span, flags lines it cannot read instead of guessing, and exports the results as CSV. All maths uses true calendar arithmetic in UTC day numbers, so leap years and daylight-saving changes can never skew a count.

## Wix SaasProducts listing (ready to paste)
- **Title:** Days Between Dates Calculator
- **Category:** Productivity
- **Slug:** `days-between-dates`
- **Summary:** Exact days between two dates — calendar breakdown, business days, add/subtract days, and a batch mode that reads date pairs from pasted or uploaded text. CSV export included.
- **Version:** 1.0 · **Demo:** No

## Counting conventions (stated in the app)
- The difference is the number of midnights between the dates (20 Oct → 21 Oct = 1 day), the standard used by calendars and project tools. "Include the end date" adds 1 for inclusive counts (deadlines, hotel nights vs days, age-style counts).
- Slash dates that could be read two ways (05/06/2026) are read as **day/month/year** — the convention in Pakistan and most of the world — and the app says so. If one number is above 12, the format resolves itself (13 can only be a day).
- Business days count Mondays–Fridays in the span. Public holidays are country-specific and are **not** deducted — the app says this plainly rather than pretending to know your holiday calendar.
- No backend or API key is needed for anything; all date maths is exact integer arithmetic.

## What was tested (automated, against the shipped core)
**43 checks — all passed.**
- Core differences: 1-day spans, same-day 0, reversed dates, full-year spans (365), leap-year spans (366)
- Leap rules: Feb 2024 (2 days across), Feb 2023 (1), **1900 not a leap year**, 2000 a leap year
- Validation: 2026-02-30, 2023-02-29, month 13 and garbage input all rejected; 2024-02-29 accepted
- Add/subtract: year-end rollover, back across a leap February, +365 days, +0
- Calendar breakdowns: Jan 31 → Mar 1 in a leap year = 1 month 1 day (end-of-month clamping), 3 y 4 m 5 d span, leap-day anniversary = exactly 1 year
- Business days: Mon→Fri = 4 (or 5 inclusive), full week = 5, weekend-only spans = 0, reversed arguments give the same answer; weekday names verified (19 Oct 2026 is a Monday)
- Batch extraction: ISO pairs (68 days), slash pairs (8 days, parsed as day/month/year), both month-name styles (53 and 4 days), a line with no pair flagged with 0 dates found, an invalid 31 Feb skipped rather than guessed, ambiguous 05/06 read as 5 June, 06/13 resolved as month/day, CSV output format

## Testing checklist (after you upload it to the site)
1. Open the live page — it starts with today → today + 30 days and shows **30 days**, 4 weeks and 2 days, business days counted.
2. Set 28 Feb 2024 → 1 Mar 2024: the answer is **2 days** (leap year). Set the same dates in 2023: **1 day**.
3. Tick "Include the end date" — the total rises by exactly 1 and says so.
4. Press **Swap dates** — the count stays the same and a note explains the end is earlier than the start; "End = today" resets the end date.
5. In tool 2, add 365 days to 20 Oct 2025 → **Tuesday, 20 October 2026**; subtract them back again.
6. In batch mode press **Sample** — 3 lines calculate (68, 8 and 53 days) and the visa line is flagged "No date pair found"; download the CSV and open it.
7. Upload a .txt file of your own with two dates per line — results appear in the table.
8. Check on your phone — the two columns stack and the big day count stays readable.

## Upload steps (Wix CMS — same as the other tools)
1. Wix dashboard → CMS → **SaasProducts** → Add Item.
2. Fill the listing fields above; paste the full contents of `index.html` into **appHtml**.
3. Set **published** on, save, then open the live app page and run the checklist above.
