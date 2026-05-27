# NOVA sprint 8 — mid-sprint retro (mimořádné)

**Datum:** pá 23.5.2026, 16:00–16:45
**Účastníci:** Lucie Č. (PM), Adam V., Eva H.
**Důvod:** mid-sprint kontrola po přidání pen-test scope. Ne pravidelná retro.

## Mood check (1-5)

- Lucie: 2 — "Mám pocit, že tlačíme na šňůru. Klient si přidává a my říkáme ano, protože nechceme být ti zlí."
- Adam: 2 — "Stíhám tak tak. Pen-test fixy = další 4-5 dní. Můj scope -307 (deep linking) prakticky nezačal."
- Eva: 1 — "Honestly, jsem dost vyhořelá. -306 je hodně, na security audit potřebuju seniora a Marek je vytížený."

## Co funguje

- PR review s Markem je rychlé, když je dostupný (typicky < 4h response)
- Sentry už chytá real-time crashes — pomáhá s -309 debug
- Lucie tlumí kontakt s klientem dobře, my máme klid na práci

## Co nefunguje

- **Scope creep**: 14 SP přidaných mid-sprint. Sprint původně 28 SP, teď 42 SP. Velocity z předchozích sprintů: 22-26 SP.
- **Eva přetížená na -306** — pen-test findings vyžadují security expertise, Eva je medior. Adam to dělat nemůže (má -301, -303, -309 + nově -307).
- **Marek jako jediný mobile reviewer** je dlouhodobě neudržitelné. Tento týden má 4 review requesty z NOVA + vlastní práci na ATLAS sprintu (-202 SSO migrace).
- **Komunikace s klientem o trade-offech** — když klient něco přidá, neděláme explicitní "tohle vypadne". Vše zůstane = nic se nestihne.

## Co příště jinak

- [ ] **Lucie ozve klientovi v po 26.5.** že release 29.5. je at-risk. Scénáře:
  - A) release bez DE lokalizace (-308 vyhodit) — Adam jí to ráno potvrdí
  - B) release s pen-test fixy 1+2 (tokens + cert pinning), debug endpoint smazat (3) jako hotfix v 1.2.1
  - C) posun release o týden na 5.6.
- [ ] **Eva dostane párovou pomoc na -306** — Lucie domluví s BU Lead (DR), zda někdo ze sousedního teamu (TP nebo PK) pomůže s security
- [ ] **Druhý mobile reviewer** — eskalujeme na BU sync 26.5. Bez něj nejsme schopni doručovat NOVA + ATLAS současně
- [ ] **Hard rule pro klienta**: cokoli mid-sprint = něco jiného vypadne. Lucie to vepíše do smlouvy o spolupráci pro Q3.

## Akce z minulé retro (kontrola)

- [x] Sentry integrace ✓ (-305 done)
- [x] Crash repro pro -309 ✓
- [ ] Updatovat README s novým flow pro nové developery — **neuděláno**, převalí se do dalšího sprintu

## Příště

- Standardní retro po sprintu: 28.5. odpoledne (po release demu nebo posunu)
- Standup po 9:00 jako vždy

---
*Zapsala: Lucie Č.*
