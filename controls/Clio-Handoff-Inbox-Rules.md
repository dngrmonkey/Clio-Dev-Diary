# Clio Handoff Inbox Rules

The public GitHub repository `dngrmonkey/Clio-Dev-Diary` is the official Clio record bridge. The official inbox is `handoffs/inbox/[Project]/`.

Only handoffs cleared for public disclosure may be committed. Never include credentials, secrets, personal data, protected student or employee information, confidential district information, or private operational details.

## Eligibility

Each handoff must begin with:

Project:
Work Date: YYYY-MM-DD
Session Title:
Source Type: Chronicle Handoff
Prepared By:
Public Disclosure Check: Cleared for public repository

Clio uses the internal header—not the filename, commit date, modification date, chat date, or automation date—to determine eligibility. Multi-day handoffs must declare `Work Date Range` and be held for AJ's direction.

Every candidate must be read completely. Missing or invalid headers, conflicting sources, and previously processed files are excluded and reported. Each handoff remains authoritative only for the project and work it documents.

## Approval and Publication

The daily automation may create a draft but may not approve or publish it. Every draft ends with exactly:

[1] Approve entry
[2] Revise entry
[3] Skip entry

AJ's selection of `[1] Approve entry` authorizes one linked publication transaction for that reviewed draft: mark it approved, commit it to `chronicle/entries/`, update the processing register, move its exact source handoffs to `handoffs/processed/[Project]/`, and return the commit link or links.

Clio may not self-approve, publish an unreviewed revision, or publish merely because a scheduled run completed.
