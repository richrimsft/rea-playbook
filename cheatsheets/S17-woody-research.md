# S17: @woody_research "154K STARS AND THE F*CKING PROMPTS WERE IN THE REPO THE WHOLE TIME"

- Post: https://x.com/woody_research/status/2110047307089530924 (Woody, @woody_research, not verified)
- Posted: 2026-10-13 16:37:35 UTC = Oct 13, 12:37 PM ET. Metrics at fetch (Oct 13, ~6:25 PM ET): 1,728 impressions, 35 likes, 36 bookmarks, 15 replies, 4 reposts.
- Media: 1 photo, 1920x2720, https://pbs.twimg.com/media/HUhkze5XwAA6tKy.png, saved as S17-woody-media.png (downloaded, HTTP 200, 803,068 bytes). **Not opened** (cheatsheet images are off-limits for this project), so its content is unverified. The post calls it "page 1 of 3", the same page count as the user's SKILL.md attachment (S16), so it is probably a screenshot of the REA skill or prompts, but that is inferred.
- Quotes: @0xMovez X Article "How to Reverse Engineer Anything with Opus 5.5 (Full-Course)", https://twitter.com/0xMovez/status/2109604520770548146 (2026-10-12 11:18 UTC = 7:18 AM ET; 180,098 impressions). Article link https://x.com/i/article/2109583646684315648 returned 404 in the API's unwound status, but the article text came back in the API payload.

## Post text (verbatim)
> 154K STARS AND THE F*CKING PROMPTS WERE IN THE REPO THE WHOLE TIME
> It's stupidly dangerous...
> One paste and your agent will:
> • follow a click all the way into the code
> • explain how a feature works, no source code needed
> • find why an app keeps crashing
> • list every tracker inside an APK
> • never call a guess a fact
> • and that's only page 1 of 3...
> Send it to Claude Code, Codex or Cursor and thank me later.

## Claim check against REA docs (clone f104500 / npm 6.4.0)
| Claim | Verdict |
|---|---|
| "154K stars" | 🔧 Stale/incorrect at fetch time: GitHub API showed 204,738 stars (Oct 13, 6:21 PM ET). |
| "prompts were in the repo" | ✅ Mostly right. The repo ships the agent skill `.agents/skills/reverse-engineer-anything/SKILL.md` (S16) and six MCP prompts in `docs/mcp-prompts.md` (investigate_feature, compare_application_versions, verify_reconstruction, trace_crash, audit_residual_unknowns, prepare_bounded_process_capture). They're documented, not hidden. |
| "follow a click into the code" | ✅ Matches documented browser/Electron tracing (inspect_web_event_listeners, trace_web_source_location, Notion clipboard showcase). |
| "explain how a feature works, no source code needed" | ✅ README: "inspect the app without its source code, explain how the feature works, show the evidence". |
| "find why an app keeps crashing" | ✅/⚠️ `trace_crash` prompt and `inspect_recorded_crash` exist. The latter is limited to supplied Linux x86-64 ELF cores. |
| "list every tracker inside an APK" | ❌ Not a documented REA feature. `inspect_android_package` returns package/SDK/permission declarations, the manifest and class counts; `search_android_classes` searches class names. "Tracker" appears in REA docs only as GitHub issue trackers (roadmap). Spotting tracker SDKs would be your own inference from class names, and "every" is not supported. |
| "never call a guess a fact" | ✅ The skill requires separating observations, inferences and unknowns and citing Evidence IDs. |
| "Send it to Claude Code, Codex or Cursor" | ✅ All three are supported setup clients (`claude_code`, `codex`, `cursor`). |
| "stupidly dangerous" | ⚠️ Hype. REA's DISCLAIMER limits use to lawful, authorized analysis. |

## Quoted @0xMovez article: notable claims
- "REA crossed 110,000 GitHub stars in days": ⚠️ unverifiable snapshot; the current count is 204,738.
- "Node.js 22 or newer": 🔧 imprecise. Docs: Node 22.x (>=22.19), 24.x (>=24.11) or 26+; 23, 25 and prereleases unsupported.
- `/mcp` listing "decompile, search, trace" as MCP tools: 🔧 those are **CLI** command names. The MCP tools are `procedure_pseudo_code`, `search_strings`/`search_procedures` and `trace_feature`. The 6.4.0 server on the box doesn't advertise tools named `decompile`/`search`/`trace`.
- "Everything runs locally… nothing is uploaded except the findings": ✅ roughly matches the README FAQ ("REA analyzes targets locally. Your agent receives the tool results, and its model provider has its own data policy").
- "The router - 20 target types, one tool each": ⚠️ The skill's routing list has more than 20 routes, some with conditions. The number is the author's own.
- DX-Ball showcase "3,205 original test cases… 63 compiled bytes": ✅ README says it "passes 3,205 original-x86 cases and reproduces all 63 compiled function bytes".
- Opus 5.5 effort levels, Elastic/Tigress benchmark numbers, the "Caveman removes ~75%" tool, WordCraft/ArtCraft "twelve apps": ⚠️ unverified, outside REA's docs. Not used.
- The clean-room rules (observe behavior, public specs, original assets, separate spec/implementation contexts): consistent with REA's DISCLAIMER ("copying proprietary software or reproducing its protected code and assets" is not supported). Useful as a practice, attributed to the author.
- Example output (`api.target.app`, 1,284 functions, 147 xrefs) is illustrative, not a real capture.
