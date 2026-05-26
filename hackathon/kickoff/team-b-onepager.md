# Tým B — Estimation & Proposal Agent

## Mise

Postavit agenta, který z **krátké poptávky zákazníka** (1-2 strany textu) vyrobí **kompletní podklad pro nabídku** — scope, předpoklady, rizika, high-level architekturu, backlog a hrubý odhad pracnosti.

Cíl: pre-sales práce, která dnes stojí seniora 2-3 dny, dostatečně dobře za 30 minut.

## Vstupy (vše lokálně v `data/`)

- `data/inquiries/*.md` — 5 fiktivních poptávek (různé domény)
- `data/past_projects.json` — 10 historických projektů BU (planned vs actual MD per role) — **kotva odhadů**
- `data/case_studies/*.md` — 5 case studies pro reference
- `data/capabilities.md` — co BU umí, stack, seniorita
- `data/proposal_template.md` — šablona výstupu

## Výstup

Markdown podklad pro nabídku v `out/proposal-<inquiry-id>.md` podle struktury `proposal_template.md`.

## Definice úspěchu

| Úroveň | Kritérium |
|---|---|
| **Bronz** | Agent z 1 poptávky vygeneruje vyplněnou šablonu s rozumným scope |
| **Stříbro** | Backlog rozdělený na epiky + odhad zakotvený v historii (každý odhad cituje konkrétní past project) |
| **Zlato** | Agent identifikuje out-of-scope a otevřené otázky, doporučuje konkrétní stack z `capabilities.md`, intervaly nejistoty rostou se vzdáleností od BU expertízy |
| **Killer** | Agent vyrobí podklad, který by senior musel jen "scan & sign-off" — bez podstatného přepisu |

## Killer příklad pro demo (doporučení)

V poptávkách jsou záměrně schované patterny — agent by je měl chytit:

- **`02-internal-portal.md` (Stavebka Brno)**: scope ~ InfoTech (PROJ-2023-05), ale **+ Pohoda PaM** (riziko, BU s tím nemá referenci) a **+ Mzdovka HR bez dokumentace** (těžké riziko)
- **`04-erp-integration.md` (Distribuce Plus)**: skoro 1:1 jako Logoval (PROJ-2024-04), velmi přesný odhad, **NetCore preference klienta — pasuje BU stack**
- **`05-bi-dashboard.md` (Sedmihrady)**: rozpočet 500-700k vs. FinReport stál 161 MD → agent by měl říct, že rozpočet je tight a **Excel zdroje + Money S5 jsou potenciální skluz** (FinReport měl skluz na ETL z legacy)
- **`03-mobile-loyalty.md` (Café Verde)**: skoro 1:1 Acme Retail (PROJ-2024-09), klient je velmi otevřený scope změnám → příležitost pro phased přístup

## Tipy

- **Začněte jednou poptávkou.** Doporučení: `02-internal-portal.md` — má dobrou kotvu (InfoTech) i dobrá rizika (Mzdovka).
- **Sub-agent pro odhad pracnosti** (`effort-estimator`) je v kitu — každý odhad přes něj a vyžadujte citaci historie.
- **Out-of-scope je důležitější než scope.** "Co není v ceně" rozhoduje o spokojenosti klienta.
- **Rizika konkrétně.** "Pokud klient nedodá X do týdne Y, posun o Z týdnů" je hodnota; "různá rizika" je nuda.

## Out of scope pro hackathon

- Reálný CRM, schvalovací workflow, podpisy
- PDF, branding, hezká grafika
- Cenotvorba (Kč/MD, slevy, garance) — agent dělá scope a pracnost, ne cenu
- Multi-tenant, auth, role
