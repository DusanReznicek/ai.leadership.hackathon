# Kickoff slides — Hackathon BU Modern Apps

> Obsah po slideech. Renderuj v Marpu / Slidev / čemkoli, nebo přepiš do PowerPointu — text je hotový.

---

## Slide 1 — Titulní

**Hackathon BU Modern Apps**
AI agenti pro fungování naší BU

Datum: *<doplň>*
Místo: *<doplň>*

---

## Slide 2 — Proč to děláme

- AI nás přestává jen překládat; **začíná dělat práci**
- BU Modern Apps stojí a padá s tím, jak rychle umíme pre-sales, delivery, support, hiring
- Pokud agenti utáhnou opakovanou práci → senioři dělají to, na co je platíme
- Dnes si **postavíme dva agenty**, kteří mají potenciál ušetřit BU desítky člověko-dní měsíčně

---

## Slide 3 — Co dnes vznikne

Dva týmy, dva agenti, jeden den:

| Tým A | Tým B |
|---|---|
| **Delivery Health Agent** | **Estimation & Proposal Agent** |
| Týdenní přehled rizik a blokerů per projekt | Z poptávky vyrobí podklad pro nabídku |
| Vstupy: tickety, PRs, kalendář, zápisy | Vstupy: poptávka + historie BU |

Cíl dne: **funkční MVP + 15min demo**. Vítěz → reálná cesta do produkce.

---

## Slide 4 — Pravidla a rozpis

| Čas | Co se děje |
|---|---|
| 09:00–09:30 | Kickoff (teď) |
| 09:30–10:00 | Rozdělení do týmů, seznámení s kit-em |
| 10:00–12:00 | Build #1 |
| 12:00–13:00 | Oběd |
| 13:00–15:30 | Build #2 |
| 15:30–16:00 | Příprava dema |
| 16:00–17:00 | **Demo** + Q&A |
| 17:00–17:30 | Vyhodnocení |
| 17:30 → | Večeře |

---

## Slide 5 — Jak se to hodnotí

| Kritérium | Váha |
|---|---|
| **Užitečnost pro BU** | 40 % |
| **Demonstrabilita** (funguje na datech) | 30 % |
| **Reálnost nasazení do měsíce** | 30 % |

Hlasujete navzájem (členové druhého týmu) + BU Lead.

Vítězný tým si bere ownership a dostane rozpočet na dotažení.

---

## Slide 6 — Co máte k dispozici

Každý tým dostane:
- **Starter repo** s Claude Code configem (sub-agent, slash command, hook)
- **Dummy data** v `data/` — žádné přístupy do reálné Jiry, vše lokálně
- **One-pager** se zadáním a definicí úspěchu
- **Claude Code coach** k ruce, když se kdokoli zasekne

Stack: **Claude Code lokálně**, Markdown výstup, Git pro verzování během dne.

---

## Slide 7 — Live demo Claude Code (10 min)

Ukázka, co Claude Code v praxi umí:
1. Otevřít projekt, číst `CLAUDE.md`
2. Vyvolat sub-agenta (per-project analyzer)
3. Pustit slash command (`/health-check`)
4. Hook, který něco loguje
5. Iterativně laděné prompty

**Pointa:** stavění agenta není o programování modelu, je o návrhu kontextu a workflow.

---

## Slide 8 — Tipy pro úspěch

1. **Domain expert je zlato.** Když agent řekne "tohle je riziko", musí to někdo schválit jako reálné.
2. **Najděte killer příklad brzy.** Demo wrangler od ranní hodiny, ne až ve 4 odpoledne.
3. **Scope down.** 1 projekt hluboce > 3 projekty na povrchu.
4. **Korelace > výpisy.** Když seznam ticketů zvládá Jira sama, hodnota je v korelaci.
5. **Iterujte krátké cykly.** Každou hodinu se zeptejte: "kdybychom skončili teď, je to k něčemu?"

---

## Slide 9 — Pravidla soutěžení

- **Žádný cheating s daty** — používejte jen `data/` ve svém repu
- **Žádné napojení na produkci** — žádná reálná Jira, žádný produkční git
- **Otázka koučovi je vždycky OK** — chcete poradit, ne sami trpět
- **Bez vyhraného / poraženého teamu** — chceme dva dobré agenty
- **Co dnes vznikne je BU vlastnictví**, ne osobní hobby projekt

---

## Slide 10 — A teď?

1. Rozdělení do týmů (10 min)
2. Otevřete starter repo, mrkněte na `README.md` a `CLAUDE.md`
3. Pusťte si pro pochopení slash command, který dostanete — i když je to stub
4. Začněte stavět

**Hodně štěstí. V 16:00 se uvidíme na demech.**
