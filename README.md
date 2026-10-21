# Days Between Dates Calculator

By **Dr. Asif Ahmad** — Asif SaaS Studio

Category **Productivity** · Version **1.0** · MIT License

Count the exact days between two dates — with calendar breakdowns, business days, and a batch mode that reads date pairs from pasted or uploaded text. **100% in your browser**: no uploads, no accounts, and no date ever leaves your device.

**▶ Live on Asif SaaS Studio:** open the tools catalogue and choose *Days Between Dates Calculator* (slug `days-between-dates`).

## Run it

Open `index.html` in any modern browser — or from this repo via any static host. No build step, no dependencies, no server.

## What it does

1. **Two-date calculator** — pick a start and an end date and get the total days, with an *include the end date* option (+1) for inclusive counts. Reversed dates are handled openly: the same span is reported, with a note.
2. **Calendar breakdown** — the span expressed as whole years, months and days, computed by real calendar steps (whole years → whole months with end-of-month clamping → remaining days), never by dividing by 365 or 30. Example: 31 Jan 2024 → 1 Mar 2024 = 1 month, 1 day.
3. **Weeks, business days, weekend days** — whole weeks plus remaining days; business days counted Monday–Friday; total hours; and the weekday name of each date (19 Oct 2026 is a Monday).
4. **Add / subtract days** — what date is 90 days from today, or 45 days before a deadline? Month-ends, year-ends and leap Februaries roll over automatically.
5. **Batch mode** — paste text (or upload a .txt / .csv / .md file) with one date pair per line; the app finds the pairs, calculates every span, flags the lines it cannot read, and exports the results as CSV (`line,start_date,end_date,days_between`, dates normalised to ISO).

## Counting conventions

- **Midnights between dates.** The difference is the number of midnights crossed: 20 Oct → 21 Oct = 1 day — the standard used by calendars and project tools. *Include the end date* adds exactly 1.
- **Ambiguous slash dates are read day/month/year** — the convention in Pakistan and most of the world (05/06/2026 = 5 June 2026). If one number is above 12, the format resolves itself: 13/06 can only be day-first, 06/13 only month-first.
- **Invalid dates are never guessed.** A "date" like 31 Feb fails validation and is skipped; a batch line left without a valid pair is flagged, not repaired.
- **Public holidays are not deducted.** Business days means Monday–Friday. Holidays are country-specific; the app says this plainly rather than pretending to know your holiday calendar.
- **Leap years follow the full Gregorian rule** — divisible by 4, except century years, which are leap only if divisible by 400 (1900 was *not* a leap year; 2000 was).

## Files

- `index.html` — the complete app, self-contained: all CSS and JavaScript inline, 19,379 bytes. All maths is exact integer arithmetic on UTC day numbers, so leap years and daylight-saving changes can never skew a count. No localStorage, no service workers, no browser permissions, no parent-window access — safe in a sandboxed iframe, and it works fully offline.
- `days-between-dates-test-report.md` — the full test report, counting conventions and the Wix listing details.
- Documentation (PDF) → `docs/days-between-dates-docs.pdf`

## Testing

43 automated checks run against the shipped PURE CORE — all passed. They cover core differences (1-day spans, same-day 0, reversed dates, 365/366-day years), the century leap rules (1900 vs 2000), validation (2026-02-30 and 2023-02-29 rejected; 2024-02-29 accepted), add/subtract rollovers, clamped calendar breakdowns (including the leap-day anniversary = exactly 1 year), business-day counts, and batch extraction (the built-in sample calculates 68, 8 and 53 days; a line with no pair is flagged; an invalid 31 Feb is skipped). Full report: `days-between-dates-test-report.md`.

## Documentation

Complete user guide and technical documentation — counting conventions, the breakdown algorithm, batch-format rules, worked examples and the tested core verbatim: `docs/days-between-dates-docs.pdf`.

Created by Dr. Asif Ahmad · Asif SaaS Studio · v1.0
