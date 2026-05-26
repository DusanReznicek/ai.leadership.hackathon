# Delivery Health Agent — Team A

## Co stavíme

Agenta, který každé pondělí ráno projde napříč projekty a připraví pro team leadera **1stránkový přehled zdraví doručování**:

- **Rizika** — skluz vs. plán, klíčový člověk OOO, growth scope, nestíhané sprinty
- **Blokery** — PR čekající na review, externí závislosti, otevřené impedimenty
- **Doporučené zásahy** s prioritou — s kým mluvit, co eskalovat, kde přealokovat lidi

Cíl: TL přijde v pondělí ráno do práce a místo 90 minut prohrabávání Jiry/Bitbucketu má 1 stránku s tím nejdůležitějším.

## Vstupní data

Vše leží lokálně ve složce `data/` — pro hackathon žádné napojení na reálnou Jiru. Struktura:

- `data/tickets.json` — fiktivní Jira tickety přes 2-3 projekty (~60 ticketů). Pole: `id`, `project`, `summary`, `status`, `priority`, `assignee`, `story_points`, `sprint`, `created`, `updated`, `due`, `labels`
- `data/pull_requests.json` — otevřené PR (~20). Pole: `id`, `project`, `title`, `author`, `reviewers`, `status`, `created`, `last_activity`, `waiting_on`, `linked_ticket`
- `data/sprints.json` — definice sprintů per projekt, target/done body, kapacita týmu
- `data/team_calendar.csv` — kdo je OOO kdy (sloupce: `person, start, end, reason`)
- `data/meeting_notes/*.md` — markdown zápisy ze standupů, retro, planningů

## Výstup

Markdown report uložený do `out/health-report.md` se sekcemi:

1. **Executive summary** (3-5 řádků)
2. **Per-project status** (jeden blok per projekt: stav sprintu, top rizika, top blokery)
3. **Doporučené zásahy** (seřazené podle priority, s konkrétním ownerem a deadline)

## Tipy ke stavbě

- **Začni s 1 projektem**, ne se všemi. Až bude happy-path funkční, rozšiř.
- **Použij sub-agenta** pro analýzu jednoho projektu (`.claude/agents/risk-analyzer.md`) a hlavního agenta nech orchestrovat.
- **Slash command** `/health-check` ať spouští celý pipeline.
- **Hooks**: PostToolUse hook může logovat každou analýzu pro reprodukovatelnost.
- **Korelace**: nejcennější insights vznikají korelací více zdrojů (např. PR visí 4 dny + autor je OOO + linked ticket je blocking pro release → eskaluj).

## Out of scope pro hackathon

- Napojení na reálnou Jiru/Bitbucket
- Notifikace do MS Teams / mailem
- Scheduler (cron) — stačí, že agent funguje na vyžádání
- Hezké HTML/PDF — markdown stačí
