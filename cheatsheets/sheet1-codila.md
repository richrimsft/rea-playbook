# S1 — REA Engineering (working note, page 1)

**Source:** User-attached image `sheet1-codila.png`  
**Author mark:** @0xCodila · October 2026 · "2026 Working Note on Reverse Engineering Practice"  
**Title:** REA ENGINEERING — What is REA, how to reverse engineer anything, and where it actually gives you the 100x

## Fig. 1 — The REA investigation flow

1. **ASK (01)** — User question (e.g. "What happens when I click Export?"). Agent (Claude / Codex / Cursor) + local target (app / binary / browser).
2. **INSPECT & TRACE** — REA CLI / MCP hub. Status: `REA_CORE | LOCAL | EVIDENCE | VERIFIED`. Engines: GHIDRA · HOPPER · IDA · JADX · CHROME. Loop: "still unknown? Ask again."
3. **READ THE EVIDENCE (03)** — Output example: `main.js writes notes.csv`. Facets: CODE · REFERENCES · FILE:LINE · UNKNOWNS (files / calls / gaps).
4. **USE WHAT YOU LEARN (04)** — Explain · Implement · Test · Ask again. Outcome example: "Your own export, tests pass."

## Claims in the note (to verify against official docs)

- REA is an MCP server/CLI that lets agents inspect software they did not write.
- Analysis runs on the **user's machine**; nothing is uploaded by REA itself.
- High-value uses: how a feature works, what changed in an update, what an app sends on the network, smart-contract behavior.
- Subsequent pages (not provided) promised target maps, setup, prompts, implementation patterns.

## Conflicts / notes vs official REA

- Engine list matches README providers (Ghidra/Hopper/IDA) plus Android JADX and Chrome CDP — accurate at a high level.
- "100x" is marketing language from the note, not an official REA metric.
- Smart-contract work in REA is **offline EVM bytecode** (`inspect_evm_interface`), not live chain trading.
