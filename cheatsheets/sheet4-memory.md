# S5 — Grok Bot Memory Engineering

**Source:** User-attached `sheet4-memory.png`  
**Title:** GROK BOT MEMORY ENGINEERING — HOW ONE AGENT LEARNS WITH A TEAM  
**Figure:** THE MEMORY ROUTING SYSTEM

## Flow

Teammate A (correction / decision · private conversation)  
→ **REVIEW GATE** (stable? shared? sourced?)  
→ branches:  
- **LIVE SOURCE** — changing facts · fetch again  
- **PRIVATE NOTE** — same person only · not shared  
- **APPROVED** → **TEAM MEMORY** (approved decision · owner + review date) → **REUSE** → Next Teammate  

**Principle:** SAVE THE DECISION · KEEP THE BOUNDARY · RECHECK THE FACT  

**Columns:** SOURCE | SCOPE | OWNER | EXPIRY

## REA application (see PLAYBOOK § Memory)

| Artifact | Gate outcome | Scope | Expiry |
|----------|--------------|-------|--------|
| Evidence record `ev_…` + SHA-256 of target | Team Memory (immutable observation) | Shared for that artifact digest | Until artifact changes (re-hash) |
| Residual unknown `unk_…` | Team Memory as open question | Shared | Until `verify_unknown_resolution` |
| Analyst decision ("feature X writes CSV via main.js") | Approved only if Evidence IDs cited | Shared | Review date; recheck after app update |
| Live market price / order book | Live Source | Never cache as truth | Fetch again |
| User private credentials / API keys | Private Note | Never shared | N/A — do not store in team memory |
| Provider readiness (`rea doctor`) | Live Source | Re-run before native work | Session |
