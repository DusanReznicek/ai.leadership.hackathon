# Zápis z prvního meetingu — Stavebka Brno: interní portál

**Date:** 2026-05-15
**Klient:** Stavebka Brno a.s. — středně velká stavební firma, ~800 zaměstnanců (z toho ~500 dělnické pozice na stavbách)
**Účast za klienta:** Robert Adamec (CIO), Petra Kalousová (HR ředitelka), Jan Vácha (IT manager)
**Účast za nás:** Dušan Řezníček

## Co klient chce

Mají chaos v interních systémech. Aktuálně:
- Sharepoint, kam nikdo nechodí
- Excelové žádanky o dovolenou
- Outlook templates na nahlášení absence
- WhatsApp skupiny per stavba pro provozní info
- Žádný jednotný self-service pro zaměstnance

Vize: **jeden portál** pro:
1. **Self-service zaměstnance**: profil, výplatní pásky (download z mzdového systému Pohoda PaM), žádost o dovolenou, nahlášení absence, čerpané benefity (Sodexo, MultiSport)
2. **Schvalovací workflow**: nadřízený schvaluje dovolené, žádanky o vybavení, cestovní příkazy
3. **Org chart** s vyhledáváním (kdo dělá co, telefon, e-mail) — důležité u 800 lidí
4. **Onboarding checklist** pro nové zaměstnance + jejich nadřízené a HR
5. **Document repository** pro interní směrnice s notifikací při změně
6. **Mobile-friendly** — dělníci nemají kanceláře, používají telefon

## Nepříjemné detaily

- Mzdový systém je **Pohoda PaM** (české), integrace je SOAP + nějaký nativní export
- HR systém je samostatný **Mzdovka HR** (interní, in-house vyvinutý 10 let zpátky) — nemají na to dokumentaci
- Auth — chtějí Microsoft 365 SSO (Entra), to mají
- 500 lidí na stavbách: někteří starší pánové, UX musí být brutálně jednoduchý
- Plánují migrovat na **SAP HR** v 2027-2028 — chtějí, aby portál šel "snadno přepojit"

## Časový horizont

- Pilot na 1 region (Jihomoravský) do **konce roku 2026**
- Celostátní rollout do **Q2 2027**

## Rozpočet

Nezmíněno. Mají schválen rozpočet pro 2026 na "digitalizaci zaměstnanecké zkušenosti" cca 4 mil Kč, na 2027 nějaký zbytek.

## Akce

- My pošleme hrubou nabídku do 31.5.
- Robert Adamec chce po nabídce další schůzku — případně chce vidět nějakou case study (Modela / InfoTech reference vhodné).
- Petra (HR) chce být v každém callu, kde se řeší self-service flow.
