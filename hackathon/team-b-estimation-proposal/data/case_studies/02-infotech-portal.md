# Case Study — InfoTech Interní Portál (PROJ-2023-05)

**Klient:** InfoTech a.s. — IT služby, 1200 zaměstnanců, ČR + SK pobočky
**Doména:** Interní portál pro zaměstnance
**Délka:** 14 týdnů, 235 MD skutečných
**Tým:** 1 senior architekt, 1 FE, 2 BE, 1 DevOps, 1 QA, 1 UX, 1 PM

## Výchozí stav

InfoTech měl rozdrobenou IT krajinu: Sharepoint, separátní HR systém, Outlook templates, různé Excel žádanky. Žádný self-service. Onboarding nového zaměstnance trval 3 dny administrativy.

## Naše řešení

- **Front-end**: React + TypeScript, design system na bázi Mantine
- **Backend**: NestJS, PostgreSQL
- **Auth**: Microsoft Entra (SSO), role-based access podle AD skupin
- **Integrace**:
  - HR systém (interní, REST API) — sync zaměstnanců a struktury
  - Mzdový systém — read-only sync dovolených a zůstatků
  - Microsoft Graph — fotky, kontakty, kalendář
- **Schvalovací workflow**: vlastní workflow engine (jednoduchý — žádný BPMN), s notifikacemi mail + MS Teams
- **Audit log**: append-only s exportem do CSV pro HR

## Výsledky

- 92 % zaměstnanců aktivních v prvním měsíci
- Onboarding zkrácený z 3 dnů na 0.5 dne
- 4 osoby HR uvolněny z administrativy na strategičtější práci
- Projekt často citován jako reference pro střední firmu

## Klíčová ponaučení

- Mobile-friendly bylo klíčové i pro "kancelářské" zaměstnance (60 % dovolenek se zadává mobilem)
- Vlastní workflow engine byl dobrá volba — komerční (Camunda, atd.) by byl overkill na náš scope
- HR ředitelka být v týmu jako product owner = klíč k úspěchu

## Použitý stack

React, NestJS, PostgreSQL, Microsoft Entra, MS Graph API, Azure App Service, Application Insights
