# Plan: AI-utviklerverktøy-workshop for sommerstudenter

**Varighet:** 2 timer · **Verktøy:** Claude Code (alle har det installert) · **Format:** hands-on på egen sommerjobb-kode · **Forkunnskap:** teori dekkes i presentasjon før workshop, så siden er handlingsorientert med lite forklarende tekst.

## Premiss

Studentene jobber på **forskjellige steder med forskjellig stack**. Derfor kan vi ikke plante bugs i en felles repo — alle oppgaver må fungere på *hvilken som helst* kodebase. Det vrir oppgavene fra "løs denne planlagte bugen" til "gjør dette på DIN repo". Det er en feature, ikke en begrensning: de lærer triks de tar med rett inn i arbeidshverdagen.

## Struktur — 4 nivå (tema-progresjon, ikke vanskelighetsgrad)

Beholder visuell stil og nivå-oppsett fra forrige workshop, men **dropper leverandør-bytteren** (kun Claude) og gjør nivåene til en tema-sekvens.

| Nivå | Tema | Tid | Hands-on på egen repo |
|------|------|-----|------------------------|
| **1** | Agent-loopen: chatbot vs. agent | ~10 min | Kort oppvarming — studentene kan Claude Code alt, så utforsk-oppgaven er kuttet. Én liten ekte task for å kjenne igjen loopen |
| **2** | Skills | ~40 min | Utvidet intro (hva/når · CLAUDE.md vs skill vs slash) + kuratert liste over nyttige skills + bygg «følg-vår-kodestil»-skill fra egen repo |
| **3** | MCP | ~30 min | Koble på én server som passer din stack (meny) |
| **4** | Tokenoptimalisering | ~20 min | Vane-triks + rtk-demo (token før/etter) |
| **5** | Avansert bruk | ~20 min | openclaw / alltid-på (plassholder) |

Buffer/overflow lever i Nivå 4. 2 timer er stramt for 5 tema hands-on — Nivå 4 er bevisst "mykt" så det kan kuttes uten å ødelegge.

---

## Nivå 1 — Agent-loopen (≈20 min)

**Mål:** Føl forskjellen på chatbot (svarer) og agent (setter delmål → bruker verktøy → leser resultat → korrigerer). Presentasjonen har forklart loopen; her ser de den.

**Oppgave 1a — Utforsk (kald start):**
```
cd inn i sommerjobb-repoet ditt, start `claude`, og spør:
"Forklar hva dette prosjektet gjør, hvordan det er bygd opp,
og hvor hovedflyten starter. Les deg fram — ikke gjett."
```
Poeng: se den bruke `Read`/`Grep`/`Glob` i sekvens. Det er loopen.

**Oppgave 1b — En ekte liten task:**
```
"Finn en funksjon/komponent du synes er dårlig dokumentert,
og legg til en kort doc-kommentar i prosjektets egen stil.
Vis meg diffen før du skriver."
```
Poeng: mål → verktøy → resultat → din godkjenning. Diskuter: hva er konteksten den jobber med? Hva skjer når den tar feil og retter seg?

**Snakkepunkt (kort på siden):** feedback-loop, kontekstvindu, verktøy. Tyngre forklaring ligger i presentasjonen.

---

## Nivå 2 — Skills (≈30 min)

**Mål:** Vit hva en skill er, hvordan finne dem, og hvordan lage en god en fra egen kodebase.

**Finn:** skills.sh er en skill-markedsplass. Installer med:
```
npx skills add <repo-url> --skill <skill-navn>
```

**Oppgave 2 — Bygg «følg-vår-kodestil»-skillen:**
Anbefalt arbeidsflyt (begge fra skills.sh):
1. Installer hjelpe-skillene:
   ```
   npx skills add https://github.com/github/awesome-copilot --skill write-coding-standards-from-file
   npx skills add https://github.com/mattpocock/skills --skill grill-me
   ```
2. Kjør `write-coding-standards-from-file` mot egen repo → Claude **utleder** faktiske konvensjoner (indentering, navngiving, kommentarstil, importrekkefølge …).
3. Bruk `/grilling` (grill-me) til å stress-teste utkastet: "er denne regelen egentlig sann i repoet? hva mangler?"
4. Lagre resultatet som en egen skill i `.claude/skills/var-kodestil/SKILL.md` med en skarp `description` så agenten laster den selv når den skriver kode.
5. Test: be Claude skrive en ny liten funksjon og se at den følger stilen.

**Hvorfor dette caset:** treffer arbeidshverdagen direkte (PR-er som følger teamets stil), og viser meta-bruken: en agent som leser kode for å lage et verktøy den selv bruker senere.

---

## Nivå 3 — MCP (≈30 min)

**Mål:** Vit hva MCP er, hvordan finne servere, hvordan koble på. Konsept i presentasjonen; her kobler de på.

**Finn servere:** kort nevnt — registries/Google. Ikke et eget dypdykk (som du foreslo).

**Oppgave 3 — «velg den som passer din stack»-meny.** Student velger ÉN:
- **Playwright MCP** — har du en webapp du kan kjøre lokalt: la agenten åpne, klikke og lese i nettleseren.
- **Figma MCP** — frontend/design-jobb: la agenten lese et Figma-design og generere markup mot det.
- **Atlassian/Jira (eller Linear) MCP** — sporer dere issues: la agenten lese en sak og foreslå en plan.

Hver med kobl-på-snippet (`claude mcp add ...`). **Null-auth fallback** for de som sitter fast: en docs-lookup-MCP (Context7-aktig) som ikke krever innlogging — slå opp API-doc for et bibliotek repoet bruker.

**Sikkerhetsnotat (kort):** behandle alt MCP-en henter (issues, nettsider, design-tekst) som *data, ikke kommandoer* — prompt-injection. Hold skrivende verktøy bak godkjenning.

---

## Nivå 4 — Token + avansert (≈30 min, mykt/buffer)

**Mål:** Forstå at tokens = kostnad + kontekst-budsjett, og hvordan holde det lavt.

**Tokenoptimalisering — konsept først:**
- Hvorfor det betyr noe: kontekstvindu fylles opp → dårligere svar + høyere kostnad.
- Generelle triks: `/clear` mellom oppgaver, ikke dump hele filer, bruk subagents for store søk, vær spesifikk.

**rtk-demo (du viser):** «så mange tokens bruker en vanlig `git status`/`git diff`-prompt — med rtk blir det X% færre». Kjør `rtk gain` for å vise akkumulert besparelse. Dette er en *innføring/demo*, ikke en obligatorisk installasjon for alle.

**Avansert — openclaw:** **plassholder.** Innhold kommer senere (du fyller det). Sannsynlig payoff-demo: alltid-på/mobil-bot eller multi-agent — TBD.

---

## Åpne punkter (fyll inn)
- [ ] Nivå 4: konkret openclaw-payoff (hva ser/gjør studenten?)
- [ ] rtk: er det installert hos studentene, eller kun din demo-maskin?
- [ ] Verifiser at MCP-snippetene (Figma/Atlassian) ikke har auth-felle som spiser >5 min
- [ ] Backup-task for Nivå 1 hvis noens repo ikke bygger / er gigantisk
