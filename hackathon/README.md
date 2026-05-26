# Hackathon BU Modern Apps — materiály

Jednodenní hackathon na téma AI agentů ve fungování BU. Leadership BU se rozdělí na dva týmy, každý postaví jednoho agenta lokálně přes Claude Code.

## Co je tady

```
hackathon/
├── README.md                          ← tenhle soubor
├── kickoff/                           ← materiály pro úvodní část dne
│   ├── slides.md                      ← obsah kickoff deku (10 slidů, markdown)
│   ├── slides.html                    ← totéž jako HTML deck (navigace šipkami)
│   ├── rules.md                       ← pravidla soutěže (1 strana)
│   ├── claude-code-manual.md          ← manuál pro začátečníky (rozeslat 1 týden předem)
│   ├── claude-code-manual.html        ← totéž v HTML (lépe se čte, dá se vytisknout)
│   ├── team-a-onepager.md             ← zadání pro Tým A
│   └── team-b-onepager.md             ← zadání pro Tým B
├── team-a-delivery-health/            ← starter repo pro Tým A
│   ├── CLAUDE.md
│   ├── README.md
│   ├── .claude/
│   │   ├── agents/risk-analyzer.md
│   │   ├── commands/health-check.md
│   │   └── settings.json
│   └── data/                          ← dummy data
│       ├── tickets.json
│       ├── pull_requests.json
│       ├── sprints.json
│       ├── team_calendar.csv
│       └── meeting_notes/
└── team-b-estimation-proposal/        ← starter repo pro Tým B
    ├── CLAUDE.md
    ├── README.md
    ├── .claude/
    │   ├── agents/effort-estimator.md
    │   ├── commands/make-proposal.md
    │   └── settings.json
    └── data/                          ← dummy data
        ├── inquiries/                 (5 fiktivních poptávek)
        ├── past_projects.json
        ├── case_studies/              (5 case studies)
        ├── capabilities.md
        └── proposal_template.md
```

## Před hackathonem (checklist pro organizátora)

### 2 týdny dopředu
- [ ] Pozvánky team leaderům s rozsahem dne a kritérii hodnocení
- [ ] Ověřit, že každý účastník má **Claude Code licenci a funguje mu lokálně** (pošli `rules.md` a požádej o ověření)
- [ ] Vybrat **Claude Code coache** (jeden člověk, kterému jde otázky odbavovat)
- [ ] Potvrdit **sponzora**, který přijde na demo (BU Lead nebo výš)
- [ ] Rezervovat **prostor, catering, projektor**

### 1 týden dopředu
- [ ] Rozeslat `rules.md` **a `claude-code-manual.md`** všem účastníkům
- [ ] Předat každému týmu jeho starter repo (zip / git repo / cokoli)
- [ ] Rozeslat `team-a-onepager.md` resp. `team-b-onepager.md` (každý tým vidí *svůj* one-pager, ne druhého — zachová napětí)
- [ ] Ověřit, že starter repo a dummy data fungují (otevři v Claude Code, pusť slash command)

### Den před / ráno
- [ ] Zkopírovat starter repa na notebooky účastníků nebo nasdílet přes USB / git
- [ ] Test internetu, projektoru, mikrofonu
- [ ] Připravit hodnotící formulář (papír nebo Google Form se třemi kritérii)

## Den D — co dělat

Postupuj podle `kickoff/slides.md`. Hlavně:

1. **09:00–09:30 kickoff** — slides 1-10, live demo Claude Code (10 min — ukaž jak vyvolat sub-agenta a slash command)
2. **Rozdělení týmů** — drž 5 + 5, mix seniorit, mix dev/PM/TL backgrounds
3. **Build phase** — minimální zásahy. Coach odbavuje technické otázky, ty drž tempo a energii.
4. **Demo** — 15 min per tým + 10 min Q&A. Hodnocení paralelně (papírové lístečky → Excel).
5. **Vyhlášení a follow-up** — vítěz si vezme ownership a my mu dáme rozpočet. **TOHLE NEVYNECHAT** — bez konkrétního dalšího kroku hackathon vyšumí.

## Po hackathonu

- Týden po: **retro** (30 min) — co fungovalo, co příště jinak
- 2 týdny po: **kick-off vítězného projektu** s ownerem, scope, milestone
- Měsíc po: **showcase pro celou BU** — 30 min demo na all-hands

## Bonus: po hackathonu zkonsolidovat

- `out/` výstupy obou týmů (health-report.md, proposal.md) — archivovat
- Vítězný kód → samostatný produktový repozitář
- Nápady z neformálních diskuzí během dne — sebrat 3-5 follow-up nápadů a zařadit do BU AI backlogu
