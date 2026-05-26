# MAVEN — Daily Standup

**Date:** 2026-05-22 (Friday)
**Attendees:** Petr Novák (TL), Jana Svobodová, Pavel Krejčí

## Updates

### Petr
- MAVEN-101 (checkout step 2) — done, PR up (MAVEN-PR-89), čekám na review od Jany
- MAVEN-109 (Zásilkovna) — **BLOCKER**: čekáme 6 dní na produkční credentials od jejich integration teamu. Eskaloval jsem klientovi 2× emailem, zatím bez odpovědi.
- Příští týden jsem OOO (dovolená 25.–29.5.) — informoval jsem PM už 2 týdny dozadu

### Jana
- MAVEN-103 (Stripe webhook) — stojí, narazila jsem na nečekanou logiku u refundů. Potřebuju párovat s někým seniornějším, ale Petr odjíždí
- MAVEN-104 (inventory race) — done, PR up (MAVEN-PR-87) — čeká na review od Petra
- Mám obavu, že nestihneme release 29.5.

### Pavel
- MAVEN-108 — dnes dodělám
- MAVEN-105 — startnu příští týden

## Risks raised
- Petr OOO příští týden, payment a shipping nedokončené
- Zásilkovna API nereaguje
- Jana cítí blokátor na MAVEN-103, ale nemá s kým párovat

## Action items
- [ ] PM eskaluje Zásilkovna integration k jejich account managerovi (vlastník: PM)
- [ ] Petr před odjezdem napíše handover document pro MAVEN-101, -102, -109 (vlastník: Petr, do pondělí ráno)
- [ ] Domluvit pair-programming Jana × někdo (Tomáš z ATLAS?) na MAVEN-103 (vlastník: TL)
