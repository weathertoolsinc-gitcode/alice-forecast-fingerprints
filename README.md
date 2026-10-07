# ALICE forecast fingerprints

Weather Tools, Inc. publishes, on the day each seasonal forecast is issued, a **fingerprint** of that forecast in
this repository. A fingerprint is the SHA-256 hash of a small record file. It reveals nothing about the forecast
itself: each record contains a long random value, so the forecast cannot be worked out from the fingerprint.

## What this proves
Each file here is captured by the Internet Archive (web.archive.org) on the day it is published, and its
fingerprints are also anchored in the Bitcoin blockchain through OpenTimestamps. Together these show, without
having to trust Weather Tools:

- **when** the forecast was fixed: it existed no later than the date of the capture and the anchor; and
- **that it was not changed**: one fingerprint per record, published once, cannot be swapped later.

## How to check a forecast
When a record file is published, compute its SHA-256 over the file's exact bytes and compare it with the line
here. For example:

```
sha256sum WY2027_record1.json        # Linux / macOS
certutil -hashfile WY2027_record1.json SHA256    # Windows
```

The hash must equal the fingerprint published here for that water year and record. The archived copy of this
repository's file (search for its address at web.archive.org) shows that the same line was public on the day of
issue.

## Layout
`california/WY<year>.txt` — one line per record: `record <n> <sha256>`.
`dry-run/` — a labelled test of the publishing steps; not a forecast.

Weather Tools, Inc.
