# Nabídka — <CUSTOMER>: <PROJECT NAME>

**Datum:** <YYYY-MM-DD>
**Připravil:** BU Modern Apps
**Verze:** 0.1 (draft)

---

## 1. Executive Summary

<3-5 řádků: o čem projekt je, hlavní hodnota pro zákazníka, hrubý časový a finanční rozsah, klíčový předpoklad.>

## 2. Scope

### 2.1 In scope
- <Funkční oblast 1>
- <Funkční oblast 2>
- ...

### 2.2 Out of scope
- <Co výslovně nedodáváme — co zákazník očekává, ale není v ceně>
- ...

## 3. Předpoklady a rizika

### 3.1 Předpoklady (co očekáváme od zákazníka)
- <Předpoklad 1>
- <Předpoklad 2>
- ...

### 3.2 Rizika
| # | Riziko | Dopad | Pravděpodobnost | Mitigace |
|---|---|---|---|---|
| 1 | ... | H/M/L | H/M/L | ... |

### 3.3 Otevřené otázky (potřebujeme upřesnit s klientem)
- <Otázka 1>
- <Otázka 2>
- ...

## 4. High-level architektura

<2-4 odstavce + případně bullety. Co je frontend, backend, persistence, integrace, auth, hosting. Vždy konkrétní stack z `capabilities.md`.>

```
[Klient]
   |
[Web / Mobile front-end]  ← React / Next.js / React Native
   |
[BFF / API gateway]  ← NestJS / .NET Core
   |
[Domain services]  ← business logika
   |
[Persistence + integrace]  ← PostgreSQL, RabbitMQ, ext. API
```

## 5. Backlog

### Epic E1: <Název>
- US 1.1 ...
- US 1.2 ...

### Epic E2: <Název>
- US 2.1 ...
- US 2.2 ...

<... dalších 5-10 epiků>

## 6. Odhad pracnosti

### 6.1 Sumarizace per role

| Role | Low (MD) | Likely (MD) | High (MD) |
|---|---|---|---|
| Frontend | ... | ... | ... |
| Backend | ... | ... | ... |
| Mobile | ... | ... | ... |
| DevOps | ... | ... | ... |
| QA | ... | ... | ... |
| UX/UI | ... | ... | ... |
| PM/Lead | ... | ... | ... |
| **Total MD** | ... | ... | ... |
| **Total kalendářních týdnů** | ... | ... | ... |

### 6.2 Per-epic odhad

| Epic | Likely MD | Reference projekt | Poznámka |
|---|---|---|---|
| E1: ... | ... | PROJ-YYYY-XX | ... |
| E2: ... | ... | PROJ-YYYY-XX | ... |
| ... | | | |

## 7. Doporučený postup

<Postup po fázích: Discovery → Design → MVP → Iterace → Go-live → Hypercare. Co je v které fázi a hrubá délka.>

## 8. Reference

<Odkazy na 2-3 nejrelevantnější case studies z `data/case_studies/`.>

---

*Tento dokument je draft připravený AI agentem. Před odesláním klientovi vyžaduje kontrolu seniora.*
