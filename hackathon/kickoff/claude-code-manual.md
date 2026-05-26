# Claude Code — manuál pro začátečníky

> Pro team leadery BU Modern Apps před hackathonem. Cíl: za 20 minut čtení mít obrázek, co Claude Code je, čím se liší od Cursoru / Copilota a jak ho rozjet.

---

## 1. Co to vlastně je

**Claude Code je AI agent, kterého spustíš v terminálu uvnitř svého projektu.** Liší se od chatu na claude.ai tím, že:

- **Vidí a čte tvé soubory** (s tvým svolením) — nemusíš mu vše copy-pastovat
- **Píše a edituje soubory přímo** — když řekneš "oprav ten bug", upraví kód
- **Spouští příkazy** (`npm install`, `git commit`, `pytest`) — s tvým souhlasem
- **Pracuje autonomně** delší dobu — postupně, krok za krokem, jako kolega

A liší se od Cursoru / GitHub Copilota tím, že:

- **Funguje v terminálu**, nikoli v IDE — i když existují pluginy do VS Code, JetBrains
- **Je agentický** — nedoplňuje řádek po řádku, dostává úkol a samostatně ho řeší
- **Není závislý na konkrétním IDE** — funguje stejně v jakémkoli editoru

### Když to zjednodušíme

Představ si **juniorního vývojáře**, který:
- Má přístup do tvého repa
- Umí spustit cokoli v terminálu
- Před každou destruktivní akcí se tě zeptá
- Pamatuje si pravidla projektu (z `CLAUDE.md`)
- Nikdy nespí

Claude Code je přibližně tohle, jen rychlejší a levnější.

---

## 2. Instalace a první spuštění

### Předpoklad

- macOS, Linux nebo Windows (WSL)
- Node.js 18+
- Účet u Anthropic / Claude (firma má licence)

### Instalace (1 příkaz)

```bash
npm install -g @anthropic-ai/claude-code
```

### První spuštění

```bash
cd /cesta/k/projektu
claude
```

Při prvním spuštění tě provede přihlášením (otevře browser, autorizuješ účet, vrátí se).

### Co uvidíš

Terminálové UI s promptem na konci. Pošleš mu otázku jako:

```
> co dělá tenhle projekt?
```

Claude se podívá do `README`, prolétne strukturu a odpoví.

---

## 3. Tři režimy práce

### a) Konverzace (chat)

Prostě píšeš a Claude odpovídá. Stejný jako chat na claude.ai, jen vidí tvoje soubory.

```
> kde se v tomhle repu řeší autentizace?
```

### b) Edit / build

Dáš úkol, Claude pracuje — čte, edituje, spouští příkazy.

```
> přidej do checkoutu validaci IČO podle ARES API
```

Před každou edicí / příkazem se zeptá, **co přesně udělá**. Můžeš odsouhlasit (`y`), odmítnout (`n`), nebo dát další instrukce.

### c) Auto mode

Když řekneš "udělej to" a důvěřuješ, můžeš pustit autonomní režim — Claude jede dál bez ptaní (kromě destruktivních akcí). Toggle: `/auto`.

**Pro hackathon doporučuji režim b)** — vidíš co se děje, učíš se.

---

## 4. Klíčové koncepty (pro hackathon nezbytné)

### `CLAUDE.md` — paměť projektu

Markdown soubor v rootu repa, kde popíšeš:
- Co projekt dělá
- Konvence, styl
- Co Claude má a nemá dělat
- Speciální data, formáty, doménová pravidla

Claude ho automaticky načte při startu. **Je to nejdůležitější soubor v projektu, který stavíš.**

Příklad pro Tým A:

```markdown
# Delivery Health Agent

Tenhle agent čte data z `data/` a generuje markdown report
do `out/health-report.md`.

## Pravidla
- Reporty jsou v češtině
- Každé doporučení musí mít konkrétního ownera
- Nehalucinuj data, která nejsou v souborech
```

### Sub-agenti — specializovaní pomocníci

V `.claude/agents/<jméno>.md` definuješ specializovaného agenta s úzkou rolí. Hlavní Claude pak může delegovat:

```
.claude/agents/risk-analyzer.md  ← analyzuje 1 projekt
```

Hlavní agent řekne *"analyzuj projekt MAVEN"* a `risk-analyzer` to zpracuje s vlastním kontextem (nezahltí tím hlavní konverzaci).

**Proč to chcete použít:** velký úkol rozdělíte na menší, paralelizovatelné. Pro Delivery Health Agent: 1 sub-agent per projekt, paralelně, hlavní agent jen aggreguje.

### Slash commandy — předpřipravené akce

V `.claude/commands/<jméno>.md` definuješ "tlačítko", které jde vyvolat napsáním `/jméno`:

```
.claude/commands/health-check.md  ← spustí celý pipeline
```

Pak v Claude Code napíšeš `/health-check` a spustí se to.

**Pro hackathon:** každý tým má jeden hlavní slash command, který agenta spouští. (Tým A: `/health-check`, Tým B: `/make-proposal`.)

### Hooks — automatické reakce

V `.claude/settings.json` můžete nastavit shell příkazy, které se spustí při událostech:

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write",
        "hooks": [
          {
            "type": "command",
            "command": "echo \"$(date) wrote $CLAUDE_TOOL_INPUT_file_path\" >> .claude/audit.log"
          }
        ]
      }
    ]
  }
}
```

Tenhle hook se spustí pokaždé, když Claude něco zapíše do souboru — a do audit logu zapíše čas a soubor.

**Pro hackathon nepovinné**, ale skvělé pro audit / reprodukovatelnost.

### MCP servery — připojení externích nástrojů

MCP (Model Context Protocol) umožní napojit Claude na externí systém — Jiru, Confluence, databázi, GitHub. **Pro náš hackathon je nepoužíváme** (vše lokálně), ale stojí za zmínku jako "to, co je další úroveň".

---

## 5. Jak to celé funguje dohromady (Tým A příklad)

```
1. Otevřu Claude Code v složce team-a-delivery-health/
2. Claude načte CLAUDE.md — ví o čem projekt je
3. Napíšu: /health-check
4. Slash command (z .claude/commands/health-check.md) říká:
   "pro každý projekt zavolej sub-agenta risk-analyzer"
5. Hlavní Claude paralelně spustí 3 sub-agenty (1 per projekt)
6. Každý sub-agent přečte tickety, PR, kalendář, notes pro svůj projekt
7. Vrátí markdown sekci s riziky + blokery + doporučeními
8. Hlavní Claude aggreguje a zapíše out/health-report.md
9. Hook zapíše čas zápisu do audit logu
10. Mně vrátí cestu k reportu, otevřu, čtu
```

Celý pipeline trvá ~1 minutu. Bez agenta bych to dělal ~90 minut.

---

## 6. Praktické tipy pro hackathon

### Začátek dne

1. **Otevři terminál ve své team složce**:
   ```bash
   cd hackathon/team-a-delivery-health   # nebo team-b
   claude
   ```
2. **Nech Claude přečíst README**: napiš *"přečti README a CLAUDE.md a shrň, co máme stavět"*. Ujistíš se, že kontext sedí.
3. **Vyzkoušej slash command**: `/health-check` (Tým A) nebo `/make-proposal` (Tým B). Uvidíš current stub a víš, kde začít rozšiřovat.

### Při práci

- **Krátké iterace.** Než dlouhé "udělej všechno" promptu, dej úkol → ověř → další úkol.
- **Když se Claude ztratí, řekni mu to.** *"Zastav. Dělej jen tohle: ..."* — funguje líp než nechat ho zmateně pokračovat.
- **Když chceš změnit směr, použij Esc.** Přeruší aktuální práci, můžeš dát novou instrukci.
- **`/clear` vyčistí konverzaci**, ale `CLAUDE.md` zůstává — užitečné, když chceš začít čistě.

### Pro debugging

- **Požádej Claude o vysvětlení.** *"Vysvětli mi, proč jsi zvolil tenhle přístup."*
- **Zkontroluj `.claude/audit.log`** (pokud máš hook) — vidíš, co Claude zapsal.
- **Použij `git diff`** mezi iteracemi — vidíš, co se reálně změnilo.

### Kdy je čas vstoupit

- Když Claude opakovaně dělá tu samou chybu — **přidej pravidlo do `CLAUDE.md`**, nebudeš to opakovat.
- Když výstup není "actionable" — **uprav prompt sub-agenta** s konkrétnějším formátem.
- Když je odpověď příliš generická — **dej konkrétní příklad**, jak má výstup vypadat.

---

## 7. Klávesové zkratky a příkazy

| Co chceš | Jak |
|---|---|
| Spustit Claude Code | `claude` v terminálu |
| Pomoct | `/help` |
| Vyčistit konverzaci | `/clear` |
| Přerušit aktuální akci | `Esc` |
| Spustit slash command | `/<jméno>` |
| Vyjít | `Ctrl+D` nebo `/exit` |
| Přepnout auto mode | `/auto` |
| Změnit model | `/model` |
| Skill / dovednost | `/<skill-name>` (např. `/init`) |

---

## 8. Časté otázky

**Q: Pokazí mi Claude kód?**
Před každou editací se ptá. V git repu to navíc jde vrátit pomocí `git restore`. Před hackathonem doporučuji `git init` na začátku, ať máš historii.

**Q: Posílá moje data Anthropicu?**
Ano, prompty (a kontext, který si Claude přečte) jdou do Anthropic API. Pro hackathon používáme jen dummy data, takže nic citlivého neuniká.

**Q: Funguje to offline?**
Ne — potřebuje internet kvůli volání modelu. Modely běží v cloudu.

**Q: Kolik to stojí?**
Firma má licence, pro hackathon se o náklady nestaráš. (Mimochodem typický agent run stojí jednotky korun.)

**Q: Co když nemám zkušenost s terminálem?**
Není problém. Claude ti pomůže i s tím *"jak v tomhle terminálu udělám X"* — zeptej se.

**Q: Naučí se Claude něco z mojí konverzace?**
Ne v rámci sezení mimo aktuální kontext. Pokud chceš, aby si něco zapamatoval napříč sezeními, **zapiš to do `CLAUDE.md`**. To je jeho "dlouhodobá paměť pro projekt".

---

## 9. Co si přinést na hackathon

- Notebook s Node.js 18+
- Claude Code nainstalovaný (`npm install -g @anthropic-ai/claude-code`)
- Ověřit přihlášení (`claude` se zeptá při prvním spuštění)
- Klidně 30 min předem otevřít starter repo a říct *"co tady je?"* — Claude tě seznámí

**Pokud nestihneš ráno:** coach na hackathonu pomůže rozjet.

---

## 10. Co číst dál (po hackathonu)

Pokud tě to chytne:
- Dokumentace: [https://docs.claude.com/claude-code](https://docs.claude.com/claude-code)
- Anthropic blog — případové studie agentů
- Cookbook na GitHubu — příklady agentů pro různé use-case

---

## Souhrn — Claude Code v jedné větě

> Claude Code je AI agent v terminálu, který čte a edituje tvé soubory, spouští příkazy s tvým svolením, řídí se pravidly z `CLAUDE.md` a může delegovat na sub-agenty přes slash commandy a hooks.

Pro hackathon ti stačí: `claude`, `CLAUDE.md`, slash command, sub-agent. Zbytek je bonus.
