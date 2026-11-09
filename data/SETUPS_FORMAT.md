# Ares setups feed

This file tells a bot how to add a note to the Setups tab. The page reads one file:

`data/setups.json`

That path is from the root of this repo. GitHub Pages serves the `main` branch, so the note shows up on the site only after it is on `main`.

## What to do each time

1. Open `data/setups.json`.
2. Add the new note at the **end** of the `entries` array. Do not insert it at the top. Do not reorder older notes.
3. Set `updated` to the current time in Eastern Time, with the offset (`-04:00` in daylight time, `-05:00` in standard time).
4. Save the file as valid JSON. No comments, no trailing commas.
5. Leave older notes in place, including the example. Do not change an id that is already in the file.

The page sorts newest first. You still append at the end.

## Shape of the file

```json
{
  "version": 1,
  "updated": "2026-11-09T20:15:00-05:00",
  "entries": []
}
```

`version` stays `1`.

## Each entry

| Field | What to put |
| --- | --- |
| `id` | A new unique string. Use letters, numbers, and dashes. Never reuse an id. The page stores Taken / Skipped against this id. |
| `time_et` | Eastern wall time, like `2026-11-09 20:15 ET`. |
| `time_iso` | The same moment with an offset, like `2026-11-09T20:15:00-05:00`. |
| `market` | `gold` or `NAS100`. |
| `symbol` | The chart symbol, such as `GC=F` for gold. |
| `price` | A number. No quotes. |
| `kind` | `setup`, `big_move`, or `update`. |
| `icc` | Three steps: `indication`, `correction`, `continuation`. Each is `not_yet`, `in_progress`, or `met`. |
| `levels` | A list of `{ "label": "Prior Asian high", "price": 4010 }`. Use `[]` if there are none. |
| `direction` | `long`, `short`, or `null`. |
| `invalidation` | A number, or `null`. |
| `target` | A number, or `null`. |
| `note` | Plain English. One short paragraph is enough. |
| `source` | `Ares`. |

## Do not put these in the file

- Position size, contracts, lots, or how many to buy or sell.
- Risk as a percent of an account, or a dollar amount to risk.
- Times in UTC, London, or the writer's local zone. Times are Eastern.

The page will not show size or risk fields even if they are added. Leave them out anyway.

## Example

The first entry is a sample so the page can be checked. Its note is `Example entry — not a real setup`. Do not edit it and do not copy its id. Add real notes after it.

A real note looks like the example, with a new id, the real time, and a real plain-English note. `kind` of `setup` shows under the Setups filter. `kind` of `big_move` shows under the Big moves filter. `update` shows when the filter is All.
