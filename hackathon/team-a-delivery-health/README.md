# Team A — Delivery Health Agent

## First 30 minutes

1. **Otevři tenhle adresář v Claude Code** (`claude` v terminálu, nebo přes IDE plugin)
2. **Přečtěte si `CLAUDE.md`** — popisuje co stavíte a jaká máte data
3. **Mrkněte na dummy data**:
   - `data/tickets.json` — fiktivní Jira tickety
   - `data/pull_requests.json` — otevřené PR
   - `data/sprints.json` — sprinty s kapacitami
   - `data/team_calendar.csv` — OOO
   - `data/meeting_notes/` — zápisy
4. **Vyzkoušejte slash command**: napište `/health-check` — uvidíte základní stub, který je potřeba dopracovat
5. **Mrkněte na sub-agenta**: `.claude/agents/risk-analyzer.md` — můžete ho rozšiřovat nebo si přidat další

## Doporučený postup

### Iterace 1 — happy path (do oběda)
- Načíst data pro 1 projekt (např. "MAVEN")
- Detekovat top 3 rizika (skluz sprintu, čekající PR > 2 dny, kritický owner OOO)
- Vyplivnout markdown report do `out/health-report.md`

### Iterace 2 — robustnost a korelace (po obědě)
- Přidat zbylé projekty
- **Korelace mezi zdroji** — tady je hlavní hodnota:
  - PR čeká na review + reviewer je OOO → eskaluj k jinému reviewerovi
  - Ticket "in progress" > 5 dní + bez updatu → spánkový ticket, zkontaktuj assignee
  - Sprint má 80 % bodů otevřených a zbývá < 30 % času → red flag
  - Meeting notes obsahují "blocker" který se neobjevuje jako ticket → chybí evidence
- Seřadit doporučené zásahy podle impact × urgency

### Iterace 3 — demo polish (poslední hodina)
- Doladit prompt sub-agenta, ať výstup je čitelný
- Připravit "killer" příklad — jeden scénář, na kterém ukážete sílu agenta na demu
- 15min demo: ukázat vstupy → agent běží live → výstup → vysvětlení korelací

## Co máte k dispozici

- `.claude/agents/risk-analyzer.md` — sub-agent pro per-project analýzu (stub k rozšíření)
- `.claude/commands/health-check.md` — slash command (stub k rozšíření)
- `.claude/settings.json` — minimal config s povolenými nástroji
- `data/` — dummy data (nelžou, vytvořena tak, aby v nich byly reálné patterny rizik)

## Kritéria hodnocení (připomínka)

- **Užitečnost pro BU** 40 % — vyřeší to reálnou bolest TL?
- **Demonstrabilita** 30 % — funguje na datech, není to mock?
- **Reálnost nasazení do měsíce** 30 % — co zbývá doladit, je vidět cesta?

## Tipy

- **Nesnažte se postavit všechno.** 1 projekt, hluboko, > 3 projekty na povrchu
- **Domain expert v týmu je klíčový.** Když agent řekne "tohle je riziko", musí to někdo schválit, jinak budete trénovat halucinace
- **Korelace > seznamy.** Vyjmenovat 20 ticketů "in progress" umí každý dashboard. Říct *"Jirka má 8 ticketů otevřených, ale je další týden OOO — přerozdělit"* je hodnota
