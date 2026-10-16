rea-agents: v6.4.0
## [6.4.0](https://github.com/morluto/rea/compare/rea-agents-6.3.0...rea-agents-6.4.0) (2026-10-11)

### Highlights

- Android: added device inspection, split-APK acquisition, logs, screenshots, file transfers and explicit app lifecycle actions through ADB, plus manifest and localized-string decoding with Apktool. ([#1552](https://github.com/morluto/rea/pull/1552), [#1556](https://github.com/morluto/rea/pull/1556)) Thanks @3QL.
- JEB: browse project units and decompile selected items through a caller-started local JEB MCP server. ([#1536](https://github.com/morluto/rea/pull/1536)) Thanks @3QL.
- Large analyses: discover retained Evidence without loading every payload, and inspect JavaScript graphs, binary layouts and function dossiers through summaries and selected views. ([#1682](https://github.com/morluto/rea/pull/1682), [#1568](https://github.com/morluto/rea/pull/1568), [#1570](https://github.com/morluto/rea/pull/1570), [#1345](https://github.com/morluto/rea/pull/1345), [#1507](https://github.com/morluto/rea/pull/1507), [#1247](https://github.com/morluto/rea/issues/1247)) Thanks @jhuang-tw, @kaoru0822-kitauji, @N0zoM1z0.
- JavaScript: isolate source analysis in an owned process with configurable heap and timeout limits; retain completed facts and explicit unknowns when analysis runs out of resources. ([#1651](https://github.com/morluto/rea/pull/1651), [#1563](https://github.com/morluto/rea/issues/1563), [#1565](https://github.com/morluto/rea/issues/1565)) Thanks @N0zoM1z0, @peter-research.
- Ghidra: configure import language/compiler specifications and seed functions, code and labels before auto-analysis. ([#1667](https://github.com/morluto/rea/pull/1667)) Thanks @sqmagellan.
- RPC discovery: recognize supported tRPC calls, HTTP-link URLs and named GraphQL operations in JavaScript applications and web bundles. ([#1670](https://github.com/morluto/rea/pull/1670)) Thanks @pompiliodonatoapp.

### Changes

- Added Ghidra support for Windows PE DLLs and bounded MIPS ELF analysis, including carved MIPS inputs with incomplete section tables. Windows P0 remains read-only. ([#1303](https://github.com/morluto/rea/pull/1303), [#1362](https://github.com/morluto/rea/pull/1362), [#1629](https://github.com/morluto/rea/pull/1629), [#1290](https://github.com/morluto/rea/issues/1290), [#718](https://github.com/morluto/rea/issues/718), [#1619](https://github.com/morluto/rea/issues/1619)) Thanks @bqw371, @jaelliot, @kvalls, @N0zoM1z0.
- Enabled `set_address_name` and `set_addresses_names` for Ghidra sessions with mutation authority, including namespace-aware data labels and per-address batch results. ([#1635](https://github.com/morluto/rea/pull/1635), [#1634](https://github.com/morluto/rea/issues/1634)) Thanks @giri256.
- Recovered additional signed AArch64 relative jump-table patterns. ([#1592](https://github.com/morluto/rea/pull/1592)) Thanks @RishTheFish21.
- Added PE resource inspection and read-only NativeAOT metadata parsing for supported x64 PE32+/.NET 8 RT
