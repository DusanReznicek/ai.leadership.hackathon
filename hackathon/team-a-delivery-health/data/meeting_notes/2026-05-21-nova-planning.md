# NOVA — Mid-sprint Replanning

**Date:** 2026-05-21 (Thursday)
**Attendees:** Lucie Černá (PM), Adam Veselý, Eva Horáková
**Trigger:** Client (Acme Retail) odeslal výsledky penetračního testu, vyžaduje fix před release 29.5.

## Context

Klient nám 21.5. ráno poslal výsledky pen-testu třetí strany. 3 high-severity findings:
1. Insecure local storage of auth tokens
2. Missing certificate pinning
3. SQL injection v debug endpointu (debug endpoint by neměl být v produkci vůbec)

Klient trvá na opravě před release 29.5., jinak release blokne.

## Decision

- Přidáme NOVA-306 (security audit fixes, 8 SP) do aktuálního sprintu
- Přidáme NOVA-307 (deep linking, klient požaduje pro marketing) a NOVA-308 (DE lokalizace, dohodli jsme dřív)
- **Celkem +14 SP do běžícího sprintu**, který původně měl 28 SP
- Co odebrat? **Nic.** Lucie říká, že vše zbylé je release-blocking nebo client commitment

## Risks (zaznamenané, neřešené)

- Sprint byl už před přidáním napůl plný, sotva stíháme původní rozsah
- Adam je 26.5. nemocný (sick day) — ztrácíme den
- Marek Dvořák je primary reviewer pro mobile PR, ale teď má na sobě 4 review requesty z NOVA + ATLAS

## Action items
- [ ] Eva začíná NOVA-306 v pondělí 26.5. ráno (vlastník: Eva)
- [ ] Adam přebírá NOVA-307 deep linking po návratu (vlastník: Adam, 27.5.)
- [ ] Lucie do pátku 23.5. potvrdí klientovi nový rozsah a upozorní na riziko skluzu (vlastník: Lucie) — **nesplněno k 26.5.**
