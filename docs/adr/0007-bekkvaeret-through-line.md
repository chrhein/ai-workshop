# ADR 0007 — Bekkværet som gjennomgående produkt

**Status:** Vedtatt · **Dato:** 2026-06-28 · **Erstatter:** [0003](0003-own-repo.md), [0004](0004-codestyle-skill-from-repo.md)

## Kontekst
[ADR 0003](0003-own-repo.md) la opp til at hver student jobbet på sin egen sommerjobb-repo, og [ADR 0004](0004-codestyle-skill-from-repo.md) gjorde skill-oppgaven til en «følg-vår-kodestil»-skill utledet fra den repoen. I praksis ga det heterogene oppgaver som var vanskelige å sammenligne, og en skill-oppgave som varierte mye i kvalitet avhengig av repoet.

## Beslutning
Alle oppgaver rettes mot å bygge **Bekkværet**, en liten værmeldingstjeneste, som én gjennomgående tråd:
- **Før vi begynner** lager en ustyrt baseline (samme prompt til alle, AI tar alle valg, ingen skills).
- **Skills** bygger konvensjons-skill(s) for Bekkværet: enheter og format for værdata (vind i m/s, temperatur i Celsius, nedbør i mm/t eller mm/døgn, tidspunkter på norsk format).
- **MCP** kobler på en server som er nyttig for Bekkværet (ekte værdata via docs-lookup, test via Playwright, design via Figma).

## Konsekvenser
- Konkrete, delte oppgaver: alle kan sammenligne kode og visuelt resultat.
- Skill-oppgaven blir om domenekonvensjoner (enheter/format), et tydeligere og mer overførbart eksempel enn kodestil-ekstraksjon.
- Mister koblingen til studentenes faktiske sommerjobb-kode. Akseptabelt: triksene er like overførbare, og en felles case er lettere å fasilitere og sammenligne.
- [ADR 0002](0002-real-code-not-personal-assistant.md) gjelder fortsatt: Bekkværet er ekte kode, ikke en personlig-assistent-case.
