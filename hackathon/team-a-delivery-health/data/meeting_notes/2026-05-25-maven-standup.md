# MAVEN daily — po, 25.5.

PN OFF (dovča), JS, PK, +DR (kvuli release tahu)

## včera
- JS: -103 stripe webhooks dál, dnes ráno mail od Marka že refundy mu funguje líp s
  asynchronnim handlerem, zkusim
- PK: -108 hotovo, PR up. -105 startuju.

## dnes
- JS: -103 dotahnout refund flow, pak review PR od PN (-101) — pingl me dnes do oběda
- PK: -105 (cookie banner) + bude review na PR-91 od PN
- DR: kontaktuju ZAS (Zasilkovna) jejich CTO pres LinkedIn, druha urgence dnes mail

## blockery
- ZAS API porad neodpovida (7 dni). MAVEN-109 je release-blocker, deadline 29.5.
- JS pripustila ze nestihnem -103 v plnem rozsahu. partial refunds presunout do 2.4.1?
- PR-89 (PN checkout step 2) ma red CI — flaky cypress test, ale JS porad neudelala review.
  Petr odjel s tim ze čeká na merge :(

## decisions
- partial refunds → defer to 2.4.1 (PN to schvalil pres mail z dovce)
- DR ozve klientovi ze release 29.5. je at-risk, scenarie:
  A) release bez zasilkovny (fallback DPD only) — klient asi nechce ale tech mozne
  B) posunout release o tyden, vse v
- ZAS eskalace pres DR LinkedIn + Tereza klient

## tomorrow
- standup 9:00 stejne misto
- DR potřebuje update od JS na refunds do oběda

---
zapsal: PK
