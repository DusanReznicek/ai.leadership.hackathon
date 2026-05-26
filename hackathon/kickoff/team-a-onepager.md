# Tým A — Delivery Health Agent

## Mise

Postavit agenta, který **každé pondělí ráno** připraví pro team leadera **1stránkový přehled zdraví projektů** — rizika, blokery, doporučené zásahy.

Cíl: TL místo 90 minut prohrabávání Jiry / Bitbucketu / Slacku má v inboxu hotovou stránku.

## Vstupy (vše lokálně v `data/`)

- `data/tickets.json` — fiktivní Jira tickety (~60, 3 projekty)
- `data/pull_requests.json` — otevřené PR
- `data/sprints.json` — sprinty a kapacity
- `data/team_calendar.csv` — OOO
- `data/meeting_notes/*.md` — zápisy ze standupů a planning meetingů

## Výstup

Markdown report v `out/health-report.md` se sekcemi:

1. **Executive summary** (3-5 řádků)
2. **Top interventions this week** (5 nejdůležitějších akcí napříč projekty)
3. **Per-project status** (jeden blok per projekt, red/yellow/green)

## Definice úspěchu

| Úroveň | Kritérium |
|---|---|
| **Bronz** | Agent načte data jednoho projektu, vypíše top 3 rizika a 3 blokery v markdownu |
| **Stříbro** | Agent zpracuje všechny 3 projekty, korreluje 2 zdroje (např. PR + kalendář) |
| **Zlato** | Agent dělá netriviální korelace (PR čeká + reviewer OOO + ticket release-blocking → eskalace), výstup je čtivý a actionable |
| **Killer** | Agent najde věc, kterou TL neviděl — třeba blocker zmíněný v meeting notes, který nemá vlastní ticket |

## Killer příklad pro demo (doporučení)

V dummy datech jsme záměrně schovali tyhle korelace — ukažte je na demu:

- **MAVEN release 29.5. je ohrožený**, protože: TL Petr je OOO 25.–29.5., 2 P1 tickety nezahájené nebo blocked, Zásilkovna API blokovaná 6 dní bez odpovědi externího týmu
- **NOVA má 14 SP scope creepu mid-sprint** (security audit od klienta), tým junior-mid, Adam sick day → release 29.5. ohrožen
- **Marek (TL ATLAS) je single point of failure pro mobile review** — má 4 review requesty z NOVA + vlastní práci na ATLAS sprintu

## Tipy

- **Začněte 1 projektem (MAVEN).** Korelace ukažte na něm. Až bude perfect, rozšiřte.
- **Sub-agent per projekt** je v starter kitu — rozšiřte ho. Hlavní agent jen aggreguje.
- **Korelace > výpisy.** Seznam ticketů zvládne Jira. *"Petr odjíždí a 3 P1 tickety jsou nezahájené"* je hodnota.
- **Hooks můžete použít** pro audit log nebo formátování výstupu.

## Out of scope pro hackathon

- Reálná Jira / Bitbucket / Confluence
- MS Teams / mail notifikace
- Scheduler / cron
- Hezké HTML, PDF, branding
