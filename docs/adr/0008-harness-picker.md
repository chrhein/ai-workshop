# ADR 0008 — Harness-velger (Claude Code + Copilot)

**Status:** Vedtatt · **Dato:** 2026-06-29

## Kontekst
Workshopen var låst til Claude Code. Deltakere bruker ulike agenter, og vi vil at tekster og kodesnutter skal tilpasse seg valgt verktøy (som leverandør-bytteren i den opprinnelige workshopen).

## Beslutning
- En **dropdown øverst til høyre** velger AI-harness. `body[data-harness="..."]` styrer visning.
- Harness-spesifikt innhold ligger i `.ho`-elementer (`.ho.claude`, `.ho.copilot`); skjult med `display:none`, vist med `display:revert` for valgt harness. `revert` gjør at samme mekanisme funker både for inline-spans (CLI-navn, filnavn, stier) og blokker (hele kodeeksempler).
- **Claude Code er default.** Valget huskes i `localStorage` (`ws_harness`).
- **Scope nå: Claude Code + GitHub Copilot.** Gemini CLI og Codex er research-verifisert (kommandoer, instruksjonsfil, skills-mappe, MCP) og kan legges til senere ved å utvide dropdownen og legge til `.ho.gemini`/`.ho.codex`-varianter.

## Harness-spesifikke punkter som byttes
CLI-start, instruksjonsfil (`CLAUDE.md` vs `AGENTS.md`), skills-mappe (`.claude/skills` vs `.github/skills`, global `~/.copilot/skills`), MCP-koble-på (`claude mcp add` vs `/mcp add` / `~/.copilot/mcp-config.json`), planmodus (Shift+Tab vs `/plan`), Figma-MCP-oppkobling.

## Konsekvenser
- Bredere relevans uten å fragmentere strukturen; delt innhold (baseline, vaner, skills.sh, tokenoptimalisering, sandboxing) forblir felles.
- openclaw-seksjonen er bevisst holdt som en Claude Code-rute (openclaw kjører `claude-cli` som runtime); ikke byttet med harness.
- Mer innhold å vedlikeholde per harness-spesifikt punkt. Verifiser kommandoene mot installert versjon før workshop, da CLI-ene endrer seg raskt.
