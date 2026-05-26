# Case Study — FinReport Finanční Dashboard (PROJ-2024-12)

**Klient:** Mezinárodní výrobní skupina (NDA) — finanční reporting pro CFO suite
**Doména:** BI / Reporting
**Délka:** 10 týdnů, 161 MD skutečných
**Tým:** 1 BI architekt, 1 BE, 1 DevOps, 1 QA, 1 PM

## Výchozí stav

CFO a 4 finanční manažeři dostávali měsíční report v PDF od controllingu (40+ stran). Aktuálnost data 5-7 dnů, žádná drill-down možnost, žádný cross-region pohled.

## Naše řešení

- **BI nástroj**: Power BI (klient má E5 licence)
- **ETL**: Azure Data Factory orchestruje noční pipeline ze 4 zdrojů:
  - ERP SAP (přes RFC do staging schématu)
  - HR systém (CSV export, klient nedovolil API)
  - Banka (API)
  - Excel od regionálních CFO (uloženo na sdíleném SharePoint, sledováno)
- **Data warehouse**: Azure Synapse (dedicated SQL pool), dimenzionální model
- **Dashboardy**: 6 hlavních (P&L, Cash Flow, AR/AP, Margin, Headcount, KPIs)
- **Security**: Row-level security per region, Microsoft Entra auth

## Výsledky

- Aktuálnost dat: T+1 (oproti T+5)
- Měsíční report nahrazen — CFO suite chodí přímo do BI
- Drill-down do entity / regionu / nákladového střediska
- Klient v 2025 rozšiřuje na regionální entity (Slovensko, Polsko, Maďarsko)

## Klíčová ponaučení

- ETL z legacy ERP (zde SAP) je vždy 50 % projektu, i když to nezní
- Klient měl podceněnou kvalitu vstupních dat — první sprint jsme strávili čištěním a definicí "co je správně"
- Power BI je sweet spot, když klient už má licence; jinak Metabase vychází levněji

## Použitý stack

Power BI Premium, Azure Data Factory, Azure Synapse, PostgreSQL (staging), Microsoft Entra
