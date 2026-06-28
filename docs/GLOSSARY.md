# Ordliste — AI-utviklerverktøy-workshop

Korte definisjoner brukt i workshoppen. Tyngre forklaring ligger i forhåndspresentasjonen.

- **Agent** — et AI-system som setter delmål, bruker verktøy, leser resultatet og korrigerer seg selv i en loop, i motsetning til en chatbot som kun svarer på én melding av gangen.
- **Chatbot** — modell som genererer ett svar på input uten å handle i omverdenen. Kontrast til *agent*.
- **Feedback-loop** — syklusen mål → handling (verktøykall) → observasjon → ny handling. Kjernen i agentisk oppførsel.
- **Kontekst / kontekstvindu** — alt modellen "ser" akkurat nå (instruksjoner, filer, samtalehistorikk). Begrenset størrelse; fylles det opp, blir svarene dårligere.
- **Verktøy (tools)** — funksjoner agenten kan kalle: lese/skrive filer, kjøre shell, søke, kalle MCP-servere. Det som gjør den agentisk.
- **Claude Code** — Anthropic sin CLI-agent som kjører i terminalen mot en lokal mappe/repo. Workshoppens verktøy.
- **Skill** — en gjenbrukbar instruksjonspakke (`SKILL.md` med `name` + `description`) som agenten laster automatisk når den er relevant. Åpen standard på tvers av Claude/Codex/Copilot/OpenCode.
- **`SKILL.md`** — fila som definerer en skill: frontmatter (`name`, `description`) + instruksjoner i brødteksten.
- **skills.sh** — markedsplass for å finne og installere skills. Install: `npx skills add <repo-url> --skill <navn>`.
- **MCP (Model Context Protocol)** — åpen standard for å koble agenten til eksterne verktøy/datakilder via en liten "server" (kalender, browser, Jira, docs …).
- **MCP-server** — prosessen som eksponerer et sett verktøy til agenten over MCP. Kobles på med f.eks. `claude mcp add <navn> -- <kommando>`.
- **Prompt-injection** — angrep der ondsinnede instruksjoner gjemmes i data agenten leser (en issue, nettside, avtale). Mottiltak: behandle hentet innhold som *data, ikke kommandoer*, og hold skrivende handlinger bak godkjenning.
- **Token** — minste tekstenhet modellen regner i. Flere tokens = høyere kostnad og mer fylt kontekstvindu.
- **Tokenoptimalisering** — å holde token-bruk nede: `/clear`, unngå å dumpe hele filer, bruke subagents, være spesifikk.
- **rtk (Rust Token Killer)** — CLI-proxy som komprimerer output fra dev-kommandoer (f.eks. `git status`) for å spare tokens. Vises som demo i Nivå 4.
- **Subagent** — en underordnet agent-økt som gjør en avgrenset deloppgave (f.eks. et stort søk) og returnerer kun konklusjonen — sparer hovedkonteksten.
- **openclaw** — avansert verktøy/oppsett, plassholder i Nivå 4. Innhold TBD.
