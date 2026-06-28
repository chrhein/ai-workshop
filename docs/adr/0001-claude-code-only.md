# ADR 0001 — Kun Claude Code (drop leverandør-bytteren)

**Status:** Vedtatt · **Dato:** 2026-06-28

## Kontekst
Forrige workshop støttet 4 leverandører (Claude/OpenAI/Copilot/lokal) med en bytter i UI. Ny agenda (skills, MCP, rtk, openclaw) er Claude-sentrert, og studentene har allerede Claude Code installert.

## Beslutning
Standardiser på **Claude Code i terminal**. Fjern leverandør-bytteren fra siden.

## Konsekvenser
- 4x mindre innhold å vedlikeholde; ingen forvirring om hvilken fane som gjelder.
- Kan bruke Claude-spesifikke ting fritt (`.claude/skills/`, `claude mcp add`, `/clear`, subagents).
- Mister multi-provider-bredden — akseptabelt, da alle har samme verktøy.
