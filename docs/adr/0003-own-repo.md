# ADR 0003 — Egen sommerjobb-repo, ikke felles sandbox

**Status:** Vedtatt · **Dato:** 2026-06-28

## Kontekst
Ekte-kode-oppgaver trenger en repo. To valg: (a) felles forberedt sandbox med plantede oppgaver, eller (b) studentens egen sommerjobb-kode. Studentene sitter på forskjellige steder med forskjellig stack.

## Beslutning
Hver student jobber på **sin egen sommerjobb-repo**.

## Konsekvenser
- Maksimal relevans; de øver på koden de faktisk skal jobbe i.
- **Oppgavene kan ikke anta noe om innholdet** — ingen plantede bugs. De må formuleres som "gjør X på DIN repo" og fungere på vilkårlig stack.
- Fasilitator kan ikke teste oppgavene på forhånd → trenger backup-task hvis en repo ikke bygger / er for stor (se PLAN åpne punkter).
- MCP-valget må også være stack-agnostisk → se [ADR 0005](0005-mcp-menu.md).
