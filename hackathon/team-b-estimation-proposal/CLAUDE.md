# Estimation & Proposal Agent — Team B

## Co stavíme

Agenta, který z **krátkého zadání zákazníka** (e-mail, zápis z meetingu, 1-2 strany textu) vyrobí kompletní podklad pro nabídku BU Modern Apps:

1. **Scope** — co je in, co je out
2. **Předpoklady a rizika** — co očekáváme od zákazníka, co může pokazit timeline
3. **High-level architektura** — vrstvy, technologie, integrace
4. **Backlog** — rozdělený na epiky, hlavní user stories
5. **Hrubý odhad pracnosti** — člověko-dny per role, intervaly nejistoty, ukotveno v historických datech BU

Cíl: pre-sales práce, která dnes trvá 2-3 dny seniorům, dostatečně dobře za 30 minut.

## Vstupní data

Vše leží lokálně ve složce `data/`:

- `data/inquiries/*.md` — 5 fiktivních zadání zákazníka (různé domény). Vstup pro agenta.
- `data/past_projects.json` — 10 historických projektů BU s metadaty (rozsah, stack, role, plánované vs. skutečné hodiny). Klíčové pro kotvení odhadů.
- `data/case_studies/*.md` — 5 case studies (referenční úspěšné projekty)
- `data/capabilities.md` — co BU umí, stack, seniority lidí
- `data/proposal_template.md` — šablona nabídky, kterou má agent naplnit

## Výstup

Markdown podklad pro nabídku uložený do `out/proposal-<inquiry-id>.md`, který kopíruje strukturu `data/proposal_template.md`.

## Tipy ke stavbě

- **Začni s jednou poptávkou.** Až bude happy-path funkční, pusti agenta na další.
- **Sub-agent pro odhad pracnosti** (`.claude/agents/effort-estimator.md`) — dostane epik/story a vrátí odhad s odkazem na nejbližší historický projekt.
- **Sub-agent pro architekturu** (volitelné) — dostane scope a vrátí návrh stacku z `capabilities.md`.
- **Slash command** `/make-proposal <inquiry-file>` ať spouští celý pipeline.
- **Klíčový princip:** každý odhad MUSÍ ukazovat, **na jakém historickém projektu je založen**. Bez kotvy je to halucinace.
- **Riziková přirážka:** intervaly nejistoty by měly růst se vzdáleností od BU expertízy (nová doména, nový stack → větší interval).

## Out of scope pro hackathon

- Napojení na reálný CRM
- PDF export, branding, hezká grafika
- Schvalovací workflow / podpisy
- Komerční podmínky (cena za MD, garance, slevy) — agent nedělá cenotvorbu, jen rozsah a pracnost
