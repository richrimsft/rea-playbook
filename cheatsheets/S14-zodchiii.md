# S14 — @zodchiii: "How to Turn Opus 5.5 Into Your Personal Reverse Engineer"

Origin: user-supplied image (t69u, Oct 13 2026 ET). Summary transcribed from the parent's reading; image not re-opened. Community claims = untrusted.

**Scope:** framework for codebase mapping, API reconstruction, deobfuscation and binary analysis with Claude Code + REA, for targets you **own or are authorized** to analyze.

## Loop
read-only target (repo, HAR, bundle, binary) → mechanical tools (webcrack, Ghidra, REA) → model analysis (trace, rename, explain) → findings log (CONFIRMED or GUESS, with file:line) → verified?
- **No:** new evidence via a cached follow-up prompt → back to analysis.
- **Yes:** ARCHITECTURE.md (map, data flows, open questions) → spec/client (`openapi.yaml`, `client.ts`, `format.ksy`, `parse.py`).

## Workspace
`target/`, `notes/`, `CLAUDE.md`, `.claude/settings.json`:
- allow `Read(./target/**)`, `Edit(./notes/**)`
- deny `Edit(./target/**)`, `WebFetch`, `WebSearch`, `curl`, `wget`
- A sandbox is needed for a hard network boundary (settings deny-lists are not one).

## Workflows
- **A. Codebase map:** start at entry points, trace the 5 main data flows, diagram, flag hardcoded secrets/dead code → ARCHITECTURE.md.
- **B. API rebuild:** from the user's **own** HAR, credentials redacted → OpenAPI 3.1 + typed TS client.
- **C. Deobfuscation:** webcrack first, then rename with a rename log.
- **D. Binary analysis:** via REA (Ghidra/IDA/JADX); stop after 30 functions to check direction.
- **Also:** file formats from 3–5 samples → Kaitai spec (`.ksy`) + parser.

## Cost claim: CONFIRMED (checked Oct 13 2026, 5:43 PM ET)
Sheet: $4/1M input, $20/1M output, $5/1M cache write, $0.20/1M cached read. 400K-token target + 25 cached follow-ups ≈ **$5.60** vs **$43.20** fresh.
- Official Opus 5.5 rates at https://www.anthropic.com/pricing (also https://claude.com/pricing): input $4/MTok, output $20/MTok, cache write $5/MTok, cache read $0.20/MTok (5-min TTL). **Match.**
- Recompute (26 passes over the 400K context, 80K output total):
  - Cached: 0.4M×$5 write = $2.00 + 25×0.4M×$0.20 read = $2.00 + 0.08M×$20 out = $1.60 → **$5.60** ✓
  - Fresh: 26×0.4M×$4 = $41.60 + $1.60 out → **$43.20** ✓
- Caveats: the cache TTL is 5 minutes, so follow-ups must land within 5 minutes of each other (each read refreshes it) or a re-write costs $2 each time. The page lists no >200K long-context surcharge for Opus 5.5. Follow-up prompt tokens are ignored in this math. US-only inference is 1.1×.

## Failure modes
1. Skipping the CONFIRMED/GUESS tags.
2. Raw HARs with tokens.
3. Letting the model write to `target/`.
4. A fresh session per question (kills cache savings).
5. Trusting renames without spot-checking ~10%.

## Flags
- "130K GitHub stars" for REA: **CORRECTED**. GitHub API (https://api.github.com/repos/morluto/rea) shows **204,103 stars** and 49,716 forks as of Oct 13 2026, 5:43 PM ET (repo created Apr 13 2026 ET). The ~143K seen earlier was also stale; the count is moving fast.
- Related source: S15 (@RoundtableSpace) appears to be a later, uncredited summary of this guide.
