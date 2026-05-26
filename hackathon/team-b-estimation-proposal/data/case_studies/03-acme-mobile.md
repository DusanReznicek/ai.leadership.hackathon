# Case Study — Acme Retail Loyalty App (PROJ-2024-09)

**Klient:** Acme Retail — síť 60 prodejen, FMCG
**Doména:** Mobilní aplikace (RN), věrnostní program
**Délka:** 20 týdnů, 343 MD skutečných
**Tým:** 2 mobile (RN), 1 BE, 1 DevOps, 1 QA (manual + automation), 1 UX, 1 PM

## Výchozí stav

Acme měl plastové kartičky pro věrnostní program — 180k zákazníků, ale aktivních jen 22 %. Akvizice nových klesala. Chtěli digitalizovat a propojit s e-shopem.

## Naše řešení

- **Mobile**: React Native (iOS + Android), Native modules pro QR scanner a push tokens
- **Backend**: NestJS, PostgreSQL — uživatelé, body, transakce
- **Integrace**: Stávající POS (přes webhook při transakci), Stripe pro budoucí předplatné
- **Push**: Firebase Cloud Messaging
- **Auth**: vlastní s OTP via SMS, plus Apple/Google Sign-In
- **Hosting**: Azure AKS

## Výsledky

- 95k stažení v prvním kvartále
- Aktivní uživatelé 47 % (vs. 22 % na plastových kartách)
- Průměrná frekvence nákupů u app uživatelů +18 %
- Klient v 2025 plánuje rozšíření na BLE beacons (lokalizační kupóny v prodejně)

## Klíčová ponaučení

- RN s nativními moduly = správná volba pro tento scope; čistě native by stálo +30 %
- iOS App Store review hodil 2× zpátky (privacy nutrition labels, sign-in možnosti) — počítat min. 2 týdny rezervu před launchem
- POS webhook byl chronicky nestabilní (POS dodavatel) — museli jsme přidat reconciliation joby

## Použitý stack

React Native, NestJS, PostgreSQL, Firebase, Stripe, Azure AKS, Sentry, App Store Connect, Play Console
