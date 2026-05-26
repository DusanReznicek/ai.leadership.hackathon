# RFP úryvek — Distribuce Plus s.r.o.: Integrace ERP s e-shopem a WMS

**Datum doručení RFP:** 2026-05-12
**Klient:** Distribuce Plus s.r.o. — velkoobchod s elektroinstalačním materiálem, B2B
**Kontakt:** Martin Smutný, IT ředitel

---

## Předmět poptávky

Distribuce Plus provozuje:
- **ERP Helios Orange** (centrální systém — zboží, ceny, sklady, zákazníci, fakturace)
- **B2B portál pro odběratele** (vlastní vývoj 2019, technologie .NET Framework 4.7) — odběratelé objednávají, vidí ceníky, stav skladu, dokumenty
- **WMS** — nasazen 2024, vlastní vývoj od jiného dodavatele (= ne my). REST API. Provazba na Helios dnes je manuální exporty.

## Problém

- Stav skladu se v B2B portálu liší od reality (data jsou denně exportovaná z Heliosu, ale WMS odepisuje real-time)
- Objednávky z B2B se ručně přepisují do Heliosu (3 lidi to dělají full-time)
- Žádný jednotný "source of truth" pro stav zboží

## Cíl projektu

Zavést **integrační vrstvu**, která:
1. Synchronizuje **kmenová data** mezi Helios → B2B portál a Helios → WMS (zboží, ceníky, zákazníci)
2. Posílá **objednávky z B2B portálu** do Heliosu a z Heliosu do WMS pro expedici
3. Vrací **real-time stav skladu** z WMS do B2B portálu (cache, ne každý request)
4. **Audit log** všech přenesených zpráv s diagnostikou

## Technické požadavky (od klienta)

- Architektura s **message brokerem** (klient preferuje **RabbitMQ**, alternativu zváží)
- Vlastní service vrstva (.NET preferováno, klient má interně .NET kompetenci)
- Auth: mTLS + service accounts v AD
- Monitoring: Application Insights (klient má licenci na Azure)
- Hosting: Azure (klient má smlouvu)
- Dokumentace integračních kontraktů (OpenAPI, AsyncAPI)

## Co dodá klient

- Přístup do Heliosu (read/write přes COM/SOAP rozhraní — ano, je to staré)
- API dokumentaci WMS
- Testovací prostředí všech tří systémů
- Dedikovaný analytik na straně klienta (Pavel Komárek)

## Časový horizont

- Smlouva podepsaná do konce června 2026
- Start prací 1.7.2026
- Go-live nejpozději 30.11.2026 (před Vánoci, kdy je peak)

## Kritéria výběru

- Reference podobné integrace (Helios, ESB/iPaaS, RabbitMQ)
- Návrh architektury (klient chce vidět diagram)
- Cenová nabídka
- Tým — chceme znát konkrétní senior architekt

## Co očekávají v odpovědi

- Návrh architektury
- Hrubý časový plán
- Pracnost a tým
- Reference (min. 2 podobné projekty)
- Předpoklady a rizika
