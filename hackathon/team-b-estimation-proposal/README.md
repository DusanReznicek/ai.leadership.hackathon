# Team B — Estimation & Proposal Agent

## First 30 minutes

1. **Otevři tenhle adresář v Claude Code**
2. **Přečtěte si `CLAUDE.md`** — co stavíte a jaká máte data
3. **Mrkněte na dummy data**:
   - `data/inquiries/` — 5 fiktivních poptávek (vyberte si jednu jako "happy path")
   - `data/past_projects.json` — historické projekty pro kalibraci odhadů
   - `data/case_studies/` — reference
   - `data/capabilities.md` — co umíme
   - `data/proposal_template.md` — struktura výstupu
4. **Vyzkoušejte slash command**: `/make-proposal data/inquiries/01-eshop-fashion.md`
5. **Mrkněte na sub-agenta**: `.claude/agents/effort-estimator.md`

## Doporučený postup

### Iterace 1 — happy path (do oběda)
- Vyberte si **jednu** poptávku (doporučení: `02-internal-portal.md`, je nejstandardnější)
- Extrahujte z ní scope + funkční požadavky
- Najděte 1-2 nejpodobnější historické projekty v `past_projects.json`
- Vygenerujte podklad podle šablony s odhadem zakotveným v historii

### Iterace 2 — robustnost (po obědě)
- Pusťte agenta na všech 5 poptávek
- **Rozsah scope:** explicitně vyjmenujte out-of-scope (= co zákazník neuvidí v ceně)
- **Předpoklady a rizika:** ukotvete v capability matrixu — co BU nedělá běžně, je riziko
- **Architektura:** vyberte stack z `capabilities.md`, nevymýšlejte nové
- **Backlog:** rozdělte na epiky → user stories. Cíl: ~5-10 epiků, ~30-50 stories per projekt
- **Odhady:** každý odhad MUSÍ mít odkaz na konkrétní past_project (id) a krátké odůvodnění. Interval nejistoty (low/likely/high MD).

### Iterace 3 — demo polish (poslední hodina)
- Vyberte **jednu** poptávku, na které ukážete sílu agenta
- Doladit prompty, ať výstup čte se jako něco od seniora, ne jako šablona
- 15min demo: vstup poptávka → agent běží → výstup → srovnání s tím, jak by to dělali lidi

## Co máte k dispozici

- `.claude/agents/effort-estimator.md` — sub-agent pro odhad pracnosti (stub k rozšíření)
- `.claude/commands/make-proposal.md` — slash command
- `.claude/settings.json` — minimal config
- `data/` — dummy data s reálnými patterny

## Kritéria hodnocení (připomínka)

- **Užitečnost pro BU** 40 % — fakt by to zrychlilo pre-sales?
- **Demonstrabilita** 30 % — vstupní poptávka → funkční výstup, ne mock?
- **Reálnost nasazení do měsíce** 30 % — co zbývá, je vidět cesta?

## Tipy

- **Bez kotvy v historii = halucinace.** Každý odhad musí říct "podobné jako PROJ-2025-XX (skutečně Y MD)".
- **Out-of-scope je důležitější než scope.** Když zákazník neví, co NENÍ v ceně, hádá to a hádá špatně.
- **Rizika nejsou alibi.** "Rizika: cokoli se může pokazit" je k ničemu. "Pokud klient nedodá data do týdne 2, posune se vše o N týdnů" je hodnota.
- **Backlog do takové hloubky, aby šel ukázat klientovi, ne do takové, ať vypadáte chytře.**
