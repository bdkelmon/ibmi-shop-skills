---
name: explain-rpgle-program
description: Use when the user wants to explain, trace, or walk through an RPGLE program — covers input sources, business rules, file access patterns, and output without inventing fields or logic.
---

# Explain an RPGLE Program

Follow these steps in order. Never describe fields, indicators, or logic that do not appear in the source you have read.

## Step 1 — Read the source in full

Use `read_member` (IBM i Developer mode) or `read_file` to load the complete RPGLE source. If the program spans multiple modules or service programs, ask the user to identify them before proceeding.

## Step 2 — Identify the program's purpose

State in one or two sentences what the program does, based only on what is visible in the source (program name, top-of-header comments, main loop structure).

## Step 3 — Trace inputs

List every input source in the order they are accessed:
- **Externally described files** — name, usage (input/update/output), key fields if declared.
- **Data structures** — identify `LIKEREC`, `LIKEDS`, or externally described DS; note the underlying file or structure.
- **Parameters** — list each parameter, its type, length, and direction (input/output/both).
- **User input** — if a display file is used, name each record format that accepts input and what fields it reads.

## Step 4 — Trace business rules

Walk the main procedure and subroutines in execution order. For each significant block:
- State what condition triggers it (indicator, `IF`, `SELECT`, `DOW/DOU`).
- Describe the transformation or decision performed.
- Call out any hard-coded values, date arithmetic, or numeric scaling that affects the outcome.

Do not paraphrase — quote short field names and op-codes directly from the source.

## Step 5 — Trace file access

For each database file used:
- List the read/write operations (`READ`, `READE`, `CHAIN`, `WRITE`, `UPDATE`, `DELETE`, `SETLL`, `SETGT`).
- Note any `%KDS` or positional key expressions.
- Flag any uncommitted I/O or missing `COMMIT`/`ROLLBACK` where transactions seem expected.

## Step 6 — Trace output

List every output path:
- **Files written** — record format, key, and any conditional logic around the write.
- **Display files** — which formats are written and under what conditions.
- **Return values / parameters** — what is passed back to the caller.
- **Printed or spooled output** — printer file name and structure if present.

## Step 7 — Surface concerns

Briefly flag anything that looks like a bug, dead code, or a maintenance risk — but only if supported by what you read. One bullet per concern, no speculation.

## Step 8 — Summarise

Provide a short plain-English summary (3–6 sentences) suitable for a developer who has not read the code.
