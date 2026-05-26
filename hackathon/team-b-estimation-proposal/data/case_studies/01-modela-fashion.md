# Case Study — Modela Fashion (PROJ-2024-01)

**Klient:** Modela Fashion s.r.o. — dámská móda, 5000 SKU, ČR + SK
**Doména:** E-commerce (headless)
**Délka:** 18 týdnů, 370 MD skutečných
**Tým:** 1 senior architekt, 2 FE, 2 BE, 1 DevOps, 1 QA, 1 UX, 1 PM

## Výchozí stav

Modela měla 7 let starý Shoptet, ale chtěla custom front-end s 360° prezentací produktu, vlastní lookbook stránky a rychlost (< 1.5s LCP). Brand byl premium, krabicový Shoptet limitoval prezentaci.

## Naše řešení

- **Front-end**: Next.js 14, app router, ISR pro PLP a PDP, edge runtime pro hot paths
- **Backend**: Saleor headless jako commerce engine, vlastní NestJS BFF pro orchestraci
- **Persistence**: PostgreSQL pro vlastní data (obsah, customizace), Saleor's storage pro commerce
- **Platby**: GoPay (karta, Apple/Google Pay)
- **Doprava**: Zásilkovna (Z-Point + adresa), DPD
- **CMS**: Saleor's storefront content + Strapi pro blog/lookbook
- **Mailing**: Klaviyo (integrace via webhooks)
- **Marketing**: GA4, Meta Pixel, Klaviyo profilování

## Výsledky

- LCP < 1.2s na PDP (před tím 3.4s)
- Konverzní poměr +27 % oproti Shoptetu (3 měsíce po launchi)
- Klient navázal druhou fází: vlastní loyalty program

## Klíčová ponaučení

- Custom front-end nad Saleor = sweet spot, když má klient SKU < 20k a chce design control
- Initial integrace Klaviyo trvala +2 týdny oproti plánu (špatně dokumentované webhook eventy)
- Klient potřeboval školení redaktorek na práci s CMS (přidat +3 dny)

## Použitý stack

Next.js 14, NestJS, PostgreSQL, Saleor, GoPay, Zásilkovna, DPD, Strapi, Klaviyo, Azure App Service
