# Case Study — Logoval ERP↔WMS Integration (PROJ-2024-04)

**Klient:** Logoval s.r.o. — velkoobchod, vlastní WMS, ERP Helios
**Doména:** Integrační projekt
**Délka:** 12 týdnů, 169 MD skutečných
**Tým:** 1 senior architekt, 2 BE, 1 DevOps, 1 QA, 1 PM

## Výchozí stav

Logoval měl Helios Orange jako centrální ERP a vlastní WMS od jiného dodavatele. Mezi systémy chyběla integrace — sklady se "vyrovnávaly" jednou denně ručním exportem. Stav skladu v ERP nesouhlasil se skutečností, B2B portál ukazoval falešnou dostupnost.

## Naše řešení

- **Integrační vrstva**: NestJS služba s RabbitMQ jako message broker
- **Schéma**: čistá inbound/outbound queue per systém, vlastní normalizovaný interní formát
- **Persistence**: PostgreSQL pro audit log, idempotency keys, DLQ
- **Auth**: mTLS mezi službami, service accounts v Helios
- **Helios integrace**: COM/SOAP wrapper (legacy, jiná cesta není), retry s exp. backoff
- **WMS integrace**: REST API, OAuth client credentials
- **Monitoring**: Application Insights + custom dashboard pro DLQ a re-play
- **Hosting**: Azure (App Service + Service Bus jako záloha pro RabbitMQ)

## Výsledky

- Sklady synchronizované do 30 sekund (z původních 24 hodin)
- 0 ručních zápisů od go-live (před tím 3 lidi full-time)
- DLQ za prvních 6 měsíců: 12 zpráv, všechny vyřešitelné re-playem
- Klient v 2025 plánuje rozšíření o e-shop integraci

## Klíčová ponaučení

- Helios COM/SOAP rozhraní je pomalé — všechny dotazy přes cache, retry, idempotency
- Vlastní normalizovaný formát uvnitř integrační vrstvy = klíč k extensibilitě (přidání 3. systému není rewrite)
- Klientův analytik (jejich, ne náš) byl klíčový pro rychlou diagnostiku Helios podivností

## Použitý stack

NestJS, RabbitMQ, PostgreSQL, Azure Service Bus (DR), Helios Orange (COM/SOAP), Application Insights, Terraform
