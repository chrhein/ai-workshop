# ADR 0004 — Skill-oppgaven: «følg-vår-kodestil» utledet fra egen repo

**Status:** Vedtatt · **Dato:** 2026-06-28

## Kontekst
Nivå 2 trenger ett konkret skill å bygge. Det må treffe arbeidshverdagen og fungere på vilkårlig repo (se [ADR 0003](0003-own-repo.md)).

## Beslutning
Studentene bygger en **«følg-vår-kodestil»-skill** ved å **utlede** konvensjoner fra sin egen kodebase, ikke ved å håndskrive regler fra bunnen. Anbefalt verktøykjede (begge fra skills.sh):
- `write-coding-standards-from-file` (github/awesome-copilot) — analyserer repoet og genererer utkast.
- `grill-me` (mattpocock/skills) — `/grilling` stress-tester utkastet før det lagres.

Resultatet lagres som `.claude/skills/var-kodestil/SKILL.md`.

## Konsekvenser
- Dobbel pedagogisk gevinst: lærer å *finne/installere* skills (skills.sh) OG *lage* en.
- Viser meta-mønsteret: en agent leser kode for å bygge et verktøy den selv bruker senere.
- Krever nett-tilgang til `npx skills add`. Backup: håndskriv 3–5 regler hvis installasjon feiler.
