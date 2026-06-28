# ADR 0005 — MCP som «velg den som passer din stack»-meny

**Status:** Vedtatt · **Dato:** 2026-06-28

## Kontekst
Nivå 3 skal koble på én MCP-server. Siden alle har ulik stack ([ADR 0003](0003-own-repo.md)), passer ikke én låst server for alle. Serveren må også kunne kobles på innen få minutter uten auth-helvete.

## Beslutning
Tilby en **meny på tre** — student velger den som matcher jobben:
- **Playwright** (lokal webapp)
- **Figma** (frontend/design)
- **Atlassian/Jira eller Linear** (issue-sporing)

Pluss en **null-auth fallback** (docs-lookup, Context7-aktig) for de som sitter fast.

## Konsekvenser
- Hver student gjør noe relevant for sin stack.
- Mer innhold å skrive (4 oppskrifter) og mer som kan gå galt på tvers av oppsett.
- Auth på Figma/Atlassian er en risiko → må verifiseres at det ikke spiser >5 min (se PLAN åpne punkter).
- "Hvordan finne servere" holdes kort (registries/Google), ikke eget dypdykk.
