# Pravidla hackathonu — 1 strana

## Čas

- **Start buildu:** 10:00
- **Konec buildu:** 16:00 (6 hodin čistého času + oběd)
- **Demo:** 16:00–17:00 (15 min per tým + 10 min Q&A)
- **Vyhlášení:** 17:00–17:30

## Týmy

- **2 týmy**, leadership BU se rozdělí na půl
- Každý tým si volí role v prvních 15 min (Tech lead, Builder(s), Domain expert, Demo wrangler)
- Žádné cross-team kopírování kódu během buildu

## Co máte

- Starter repo per tým s Claude Code configem
- Dummy data ve složce `data/`
- 1 Claude Code coach k dispozici oběma týmům (na otázky, ne na vývoj za vás)
- WiFi, energie, kafe

## Co dodáváte na konci

1. **Funkční MVP** — agent, kterého jde spustit a vyplivne výsledek
2. **15min demo** se "killer scénářem" (jeden konkrétní příklad, který ukazuje sílu)
3. **3 sliduy / talking points** — co jste postavili, co je hotovo, co zbývá

## Co se hodnotí

| Kritérium | Váha | Co znamená |
|---|---|---|
| **Užitečnost pro BU** | 40 % | Vyřeší to reálnou bolest? Kolik času/peněz ušetří? |
| **Demonstrabilita** | 30 % | Funguje to na datech, nebo je to mock? |
| **Reálnost nasazení do měsíce** | 30 % | Co zbývá, je vidět cesta? |

**Hodnotí:** každý člen druhého týmu (1 hlas) + BU Lead (1 hlas, váha 2× pro tie-break).

## Co je out of scope (nedělejte to)

- Napojení na reálnou Jiru, Bitbucket, Confluence atd. — používejte jen dummy data
- Pěkné HTML/PDF/branding — markdown úplně stačí
- Auth, multi-tenancy, scheduler — postavíme později
- Pokus o "univerzální" agenta, který umí všechno — fail mode

## Co je důležité

- **Domain expert v týmu** = klíč. Bez něj postavíte něco, co nikdo nepoužije.
- **Killer příklad** od dopoledne. Mějte konkrétní use-case, který v demo ukážete.
- **1 projekt / 1 poptávka hluboce** > N na povrchu.
- **Iterujte krátké cykly.** Každou hodinu kontrola "kdybychom končili teď, je to k něčemu?"

## Po hackathonu

- Vítězný projekt: PM + rozpočet, target produkce do 2 sprintů
- Druhý projekt: rozhodneme zda dotáhnout, parkovat, předat komunitě
- Showcase pro celou BU / firmu: 30 min demo na nejbližším all-hands

## Bezpečnost a etika

- Žádná reálná zákaznická data (ani v testovacích datech)
- Žádné odesílání obsahu mimo Claude Code (žádné mailování, posting do Slacku)
- Kód vzniklý dnes je BU vlastnictví, ne osobní

---

*Pravidla zveřejněna 1 týden před hackathonem. Případné dotazy → Dušan.*
