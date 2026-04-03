# AI-workshop-vypracovanie-
## 1. CLI vs GUI

Mnoho AI asistentov funguje ako **CLI** nástroj.

**CLI** znamená Command Line Interface a znamená to, že s nástrojom komunikujeme cez textové príkazy.

**GUI** znamená Graphical User Interface - klasické okná, tlačidlá, myš.

### Výhody CLI pre programátorov

Doplň výhody:
- Rýchlejšie pre skúsených používateľov
- Ľahko sa skriptuje (automatizácia)
- Funguje cez vzdialený prístup / terminál (SSH)
- Menej náročné na systémové prostriedky (výkon, pamäť)

---

### Kedy začať novú session?

Napíš 2 dôvody, prečo by si chcel začať novú session:

1. Keď mením tému (napr. z programovania na inú oblasť) a nechcem, aby starý kontext ovplyvňoval odpovede.

2. Keď je konverzácia príliš dlhá alebo chaotická a chcem začať prehľadne odznova.

---

### Prečo existujú lokálne nastavenia?

Lokálne nastavenia typicky **nie sú** súčasťou Git repozitára.

Je to preto, lebo: obsahujú osobné preferencie alebo citlivé údaje (napr. API kľúče, lokálne cesty, individuálne nastavenia), ktoré by sa nemali zdieľať s ostatnými v repozitári.

---

### Compaction (komprimácia)

Keď konverzácia presiahne limit, AI asistent vykoná **compaction**:

**Compaction** = skrátenie staršej časti konverzácie, aby sa zmestila do context window.

**Výhoda:** AI môže pokračovať v práci

**Nevýhoda:** strata detailov / presnosti (niektoré informácie sa môžu vynechať alebo zjednodušiť).

---

### Prečo ich používať?

Ľahšie sa kontrolujú zmeny pred ich akceptovaním.

---

### Auto-accept módy

**Čo typicky môže AI robiť bez pýtania:**
- Čítať súbory
- Editovať súbory v projekte

**Čo stále vyžaduje povolenie:**
- Git operácie (push, reset)
- spúšťanie shell príkazov
- Operácie mimo projekt

---

## 7. Dangerous Mode

Niektorí asistenti ponúkajú režim, ktorý preskočí všetky povolenia.

**Riziká:**
- AI môže prepísať/poškodiť git históriu
- AI môže vymazať súbory
- AI môže spustiť nebezpečné skripty

---

### Kedy by sa to mohlo hodiť?

Pri použití v kombinácii so sandbox prostredím.

---

Predstav si sandbox ako: uzavretý priestor, kde sa dá experimentovať a robiť „neporiadok“ bez toho, aby to ovplyvnilo okolie.

---

# ČASŤ 4: Version Control a Undo

## 9. Vracanie zmien

### Prečo je Git dôležitý pri práci s AI?

1. umožňuje bezpečné experimentovanie

2. pri nefunkčnom kóde sa vieme dostať k starším verziam repozitára

---

### Dôležité

Pred väčšími zmenami je **VŽDY** dobré urobiť commit alebo zálohu.

---


## ČASŤ 5: Plan Mode

### Kedy použiť Plan Mode?

- Pri zložitejších úlohách
- Keď si nie som istý výsledkom
- Pri úlohách ovplyvňujúcich väčšiu časť projektu

### Výhody

1. Predídeš zbytočným chybám
2. Môžeš ovplyvniť riešenie skôr než je implementované
3. AI lepšie pochopí tvoje požiadavky

---

# ČASŤ 6: Context Engineering a projektové inštrukcie

### Stratégia použitia

V inštrukciách môžeš napísať:
```
Keď implementuješ novú funkcionalitu, pozri sa do @SPEC.md
```

**Prečo je to lepšie?** špecifikácia je oddelená od inštrukcií – môže byť detailná, prehľadná a ľahko aktualizovateľná bez toho, aby si zahltil základné pravidlá pre AI.

---

## 12. Projektové inštrukcie (CLAUDE.md)

### Kedy sa načíta?

Tento súbor sa **automaticky načíta** pri každej session a stáva sa súčasťou systémového promptu.

---

## 13. Context Engineering

**Context Engineering** = umenie poskytnúť AI správny kontext.

### Základné princípy

| Princíp | Vysvetlenie |
|---------|-------------|
| Relevantnosť | Pridávaj len potrebné informácie |
| Stručnosť | Šetri tokeny |
| Štruktúra | Používaj formátovanie pre lepšiu čitateľnosť |

### XML tagy pre štruktúru

```xml
<error>
TypeError: Cannot read property 'map' of undefined
    at UserList.js:15
</error>
```

**Prečo je to lepšie?** Lepšie štrukturovaný a relevantný kontext umožňuje AI rýchlejšie porozumieť problému, presnejšie odpovedať a minimalizovať chyby.

---

### Výhody a nevýhody

| Výhody | Nevýhody |
|--------|----------|
| Vidíš ako AI uvažuje | Spotrebuje viac tokenov |
| Kvalitnejšie odpovede | pomalšia odpoveď |
| Odhalíš chyby v uvažovaní | |

### Kedy ho vypnúť?

Pri jednoduchých úlohách, kde nepotrebujeme detailné uvažovanie.

---

### Tip: Markdown dokumentácia

Väčšina dokumentácií ponúka Markdown verziu. Je lepšia, pretože:
- Menej "šumu"
- Šetrí tokeny
- Lepšie sa vyhodnocuje

---

## 17. MCP - Model Context Protocol

**MCP** = štandard pre pridávanie nových nástrojov a zdrojov pre AI asistentov.

Príklad: MCP server pre dokumentáciu umožňuje AI ľahšie pristupovať k aktuálnym informáciám a zdrojom bez potreby manuálneho vyhľadávania.

---


## ČASŤ 8: Skills a Custom Commands

### Third-party skills

Existujú platformy so zdieľanými skills (napr. skills.sh).

**Výhoda používania hotových skills:** ušetríš čas a prácu, pretože môžeš okamžite využiť overené riešenia a nástroje bez toho, aby si ich musel programovať od začiatku.

---

### Príklad použitia

Po každej úprave súboru automaticky spustiť formátovač kódu.

**Hook sa spustí po:** úspešnom uložení/úprave súboru

**Vykoná:** automatický linting alebo formátovanie kódu

---

### Prečo je to dôležité?

AI môže robiť chyby. Feedback loop jej umožňuje:
1. Vykonať zmenu
2. otestovať výsledok
3. Opraviť chyby
4. Opakovať

### Typy feedback loops

| Typ | Popis |
|-----|-------|
| Unit testy | AI spustí testy a opraví zlyhania |
| Browser testing | AI otvorí prehliadač a skontroluje UI |
| Linting | AI skontroluje kvalitu kódu |

### Príklad: Playwright

Playwright umožňuje AI otvoriť prehliadač a automatizovane interagovať s webstránkou.

**Nevýhoda feedback loops:** Vyššia spotreba tokenov a času

### Pozor na testy písané AI

AI má tendenciu písať testy, ktoré presne zodpovedajú svojmu vlastnému kódu a nemusia odhaliť skutočné chyby.

Preto je dobré testy buď písať pred implementáciou alebo ich nezávisle overiť a upraviť manuálne.

---

## 23. Multi-Agent systémy (Ralph Loops)

**Multi-Agent systém** = viacero AI agentov pracujúcich spoločne alebo AI bežiaca v slučke.

### Ralph Loop - koncept

```
+-----------------------------------------------------------+
|                      RALPH LOOP                           |
|                                                           |
|  while (tasks_remaining && iterations < MAX):             |
|      1. Agent si vyberie task zo zoznamu                  |
|      2. Implementuje riešenie                             |
|      3. Spustí testy                                      |
|      4. Označí task ako hotový                            |
|      5. Pokračuje na ďalší task                           |
|                                                           |
+-----------------------------------------------------------+
```

### Ako to funguje?

1. Vytvoríš zoznam úloh (napr. v PRD súbore)
2. Spustíš agenta v slučke
3. Agent si vyberá a plní úlohy automaticky
4. Ty len kontroluješ výsledky

### Výhody

- Menej manuálnej práce
- Vhodné pre demo verzie

### Nevýhody

- Menšia kontrola nad procesom
- Agent sa môže "zaseknúť"
- Stále potrebuješ dobrý plán a jasné úlohy

### Čo je potrebné pre úspešný Ralph Loop?

1. Dobre definované úlohy
2. Funkčné testy
3. Sandbox prostredie pre kontext projektu
4. Kvalitný project knowledge

---
