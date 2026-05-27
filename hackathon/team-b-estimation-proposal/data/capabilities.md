# BU Modern Apps — Capabilities

*Aktualizace: květen 2026. Reviewer: Dušan Řezníček (BU Lead). Příští review: srpen 2026.*

## Co děláme rutinně

### Web a portály
- **Front-end:** React 18, Next.js 14 (preferujeme), TypeScript
- **Backend:** Node.js (NestJS), .NET 8 (ASP.NET Core)
- **DB:** PostgreSQL, MS SQL, Redis
- **Auth:** Microsoft Entra (Azure AD), Auth0, vlastní s OIDC, SAML 2 pro enterprise
- **Hosting:** Azure App Service, AKS, on-prem Kubernetes (selektivně)
- **CMS:** Strapi, Contentful, Kentico (pro retained klienty)

### E-commerce
- Custom front-end nad headless platformami (Shoptet headless, Saleor, Magento Cloud)
- Vlastní checkout, košík, integrace plateb (**GoPay** preferovaný, ComGate, Stripe pro EU/US)
- **Doprava CZ/SK:** Zásilkovna, PPL, DPD, Česká pošta API, Balíkobot (aggregator)
- **ERP konektory:** Helios, Pohoda, Money S5, SAP (omezeně), Microsoft Dynamics 365

### Mobilní aplikace
- **React Native** (preferované) — ~80 % našich mobile projektů
- Native iOS (Swift), Native Android (Kotlin) — méně časté, jen velmi performance-critical apky
- **Push:** Firebase, OneSignal, APNs/FCM přímo
- **Distribuce:** App Store Connect, Play Console, Microsoft Intune (interní)
- **Security:** Keychain/Keystore pro auth tokeny (NE AsyncStorage), certificate pinning, biometric auth

### Integrace
- REST, gRPC, GraphQL, SOAP (legacy)
- **Message brokers:** RabbitMQ, Azure Service Bus, Kafka (selektivně, expertíza roste)
- **ESB / iPaaS:** Azure Integration Services, vlastní BFF vrstvy
- **Identity federace:** SAML 2, OAuth 2 / OIDC, mTLS

### Data a BI
- **Reporting:** Power BI (Premium i Pro), Metabase (OSS pro menší rozpočty), vlastní dashboardy
- **ETL:** Azure Data Factory, dbt (rozšiřujeme), n8n pro nízkokódní toky
- **Data warehouse:** Azure Synapse, PostgreSQL (rozšířený), Snowflake (omezené reference)

### DevOps a SRE
- **CI/CD:** Azure DevOps, GitHub Actions
- **IaC:** Terraform, Bicep, ARM (legacy)
- **Monitoring:** Application Insights, Grafana, Sentry, Datadog (pro vybrané klienty)
- **On-call:** PagerDuty (selektivně, na požádání klienta)

## Co děláme méně často / je to riziko

| Oblast | Reference | Riziko |
|---|---|---|
| Native iOS/Android (čistý) | 2 projekty 2022-2024 | Tým seniorů 2 osoby, kapacita omezená |
| AI / ML modely (vlastní trénink) | 0 | Děláme jako klienty cizích API (OpenAI, Anthropic) — vlastní modely netrénujeme |
| Realtime video / streaming | 0 | Žádný referenční projekt |
| IoT | 1 (2022) | Jediný projekt, není core kompetence |
| Snowflake, Databricks | 2 PoC | Zkušenost limited, učíme se |
| Kafka (vlastní cluster) | 3 projekty | Pro managed (Confluent, MSK) v pohodě, self-hosted = riziko |
| SAP S/4HANA integrace | 1 | Pro SAP Business One a starší SAP máme zkušenosti, S/4HANA je odlišný stack |

## Co rozhodně neděláme

- Hardware / firmware
- Hry, 3D, AR/VR
- Telekomunikační stacky (5G, SIP, atd.)
- Klasifikované systémy s certifikací NBÚ Tajné a vyšší
- Tradingové systémy (low-latency requirements pod 10ms)
- Blockchain / smart contracts (kromě běžných integrací na existující sítě)

## Partnerství a certifikace

- **Microsoft Partner** — Modern Work, Data & AI specializations
- **Azure Expert MSP** (audit 2025)
- **Atlassian Solution Partner** (Silver)
- **HubSpot Solutions Partner**
- **ISO 27001** certifikováno (audit 2024, recertifikace 2027)
- **SOC 2 Type II** (pro vybrané klienty s US/EU enterprise)
- **GDPR DPO** in-house
- **Microsoft Entra certified architects:** 3
- **AWS Certified Solutions Architect:** 2 (méně častý než Azure)

## Tým seniority profil

- 4 senior architekti (mohou vést projekt 1M+ Kč)
- ~25 mid/senior fullstack vývojářů
- ~10 medior FE specialistů (React/Next.js)
- ~6 mobile vývojářů (převážně RN)
- 3 DevOps inženýři
- 4 QA (2 manual, 2 automation — Playwright, Cypress)
- 2 UX designeři, 2 UI designeři
- 1 BI architekt + 2 BI specialistů
- 1 Tech writer (sdílený s ostatními BU)

**Geografická distribuce:** Praha (~40 %), Brno (~35 %), zbytek remote (CZ + SK)

## Sazby a billing

- **Standard MD rate:** 14 000 – 18 000 Kč (podle seniority a role)
- **Senior architekt:** 20 000 – 22 000 Kč
- **Junior:** 10 000 – 12 000 Kč
- **Discovery workshop:** 50 000 – 150 000 Kč fix (1-3 dny u klienta), výstup = roadmap + draft nabídka
- **Support / SLA:** od 30 000 Kč/měsíc + paušál podle reakční doby
- Pro velké projekty (3M+ Kč) možnost slevy 5-10 % nebo T&M s monthly cap

## Sezónnost a kapacita

- **Q1 (Jan-Mar):** přetížení (klienti přicházejí s novým rozpočtem), nové projekty start typicky 3-6 týdnů
- **Q2 (Apr-Jun):** normální kapacita
- **Q3 (Jul-Sep):** snížená v červenci-srpnu (dovolené), opět up od září
- **Q4 (Oct-Dec):** běžně rush na Vánoční kampaně (e-commerce), tlak na go-live před Black Friday

**Pro 2026 plánujeme:** nábor 4-6 FE/BE midů, 1 senior mobile, 1 senior BI specialista. Pohyb v týmu (rotace, povýšení) typicky Q1.

## Smluvní modely

- **Fix-price** — pro dobře definované projekty s discovery dokončeným (preferujeme)
- **T&M (Time & Materials)** — pro projekty s nejistým scope, integration s legacy systémy
- **Dedicated team / Body shop** — long-term retained klienti, monthly billing, vlastní velocity
- **Retainer + on-demand** — support kontrakty s flexibilní rozsahem

## Co BU NIKDY neslibuje

- Doručení do týdne (minimální discovery + analýza = 1 týden i pro malé projekty)
- 100% bezchybnost (akceptujeme P3 bugy v produkci, pokud má klient runbook)
- Nahrazení produktového ownera (klient musí mít na své straně rozhodovací osobu)
- Vývoj bez testů — testy jsou součást každé story, ne add-on
