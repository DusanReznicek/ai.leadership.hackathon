# BU Modern Apps — Capabilities

## Co děláme rutinně

### Web a portály
- React 18, Next.js 14, TypeScript
- Backend: Node.js (NestJS), .NET 8 (ASP.NET Core)
- DB: PostgreSQL, MS SQL, Redis
- Auth: Microsoft Entra (Azure AD), Auth0, vlastní s OIDC
- Hosting: Azure App Service, AKS, on-prem Kubernetes
- CMS integrace: Strapi, Contentful, Kentico

### E-commerce
- Custom front-end nad headless e-shop platformami (Shoptet headless, Saleor, Magento)
- Vlastní checkout, košík, integrace plateb (GoPay, ComGate, Stripe)
- Doprava: Zásilkovna, PPL, DPD, Česká pošta API
- ERP konektory: Helios, Pohoda, SAP (omezeně), Money S5

### Mobilní aplikace
- React Native (preferované), Native iOS (Swift), Native Android (Kotlin) — méně časté
- Push: Firebase, OneSignal, APNs
- Distribuce: App Store Connect, Play Console, Microsoft Intune (interní)

### Integrace
- REST, gRPC, GraphQL
- Message brokers: RabbitMQ, Azure Service Bus, Kafka (méně časté)
- ESB / iPaaS: Azure Integration Services, vlastní BFF vrstvy
- Identity federace: SAML 2, OAuth 2 / OIDC

### Data a BI
- Reporting: Power BI, Metabase, vlastní dashboardy
- ETL: Azure Data Factory, dbt (rozšiřujeme)
- Data warehouse: Azure Synapse, Snowflake (omezené reference)

### DevOps a SRE
- Azure DevOps, GitHub Actions
- IaC: Terraform, Bicep
- Monitoring: Application Insights, Grafana, Sentry

## Co děláme méně často / je to riziko

- Native iOS/Android (preferujeme RN; jeden tým seniorů, kapacita omezená)
- AI/ML modely (běžně používáme jako klienty cizích API; vlastní modely netrénujeme)
- Realtime video / streaming (žádný referenční projekt)
- IoT (jen 1 historický projekt, nikoli core kompetence)
- Snowflake, Databricks (zkušenost limited)

## Co rozhodně neděláme

- Hardware / firmware
- Hry, 3D, AR/VR
- Telekomunikační stacky (5G, SIP, atd.)
- Klasifikované systémy s certifikací (NBÚ Tajné a vyšší)

## Team seniority profil

- 4 senior architekti (mohou vést projekt 1M+ Kč)
- ~25 mid/senior fullstack vývojářů
- ~10 medior FE specialistů (React/Next.js)
- ~6 mobile vývojářů (převážně RN)
- 3 DevOps inženýři
- 4 QA (2 manual, 2 automation — Playwright, Cypress)
- 2 UX designeři, 2 UI designeři

## Rychlost (kalibrace odhadů)

- Mid-senior fullstack: 60-70 % efektivní time, ~6 SP/sprint (14 dní)
- Senior: ~8 SP/sprint
- Junior: ~4 SP/sprint
- 1 SP ≈ 1 MD (idealizováno), v realitě 1.2-1.4 kvůli code review, retro, schůzkám
