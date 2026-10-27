# Záverečná správa z testovania (Test Summary Report)

**Projekt:** Saucedemo.com (Swag Labs E-commerce Demo Application)   
 **Verzia aplikácie:** N/A  
 **URL:** https://www.saucedemo.com  
 **Autor / Tester:** Katarína Kyselová  
 **Obdobie testovania:** 18. august 2026 – 27. september 2026  
**Testované prostredie:** Windows 11 | MS Edge v152.0 (64-bit), Google Chrome v152.0 (64-bit) | Rozlíšenie 1920x1080 px  
**Použité nástroje:** Jira (správa úloh a defektov), Canva (vizualizácie), Chrome DevTools (meranie načítania stránky), AI asistent (podpora pri spracovaní dokumentácie a analýze).  

## 1. 🔎 Úvod a prehľad (Executive Summary)
### 1.1 Účel dokumentu
Tento dokument predstavuje záverečnú správu z manuálneho testovania webovej stránky *SauceDemo*.  

Saucedemo.com je simulovaný frontendový e-shop určený začínajúcim testerom na učenie a zdokonaľovanie v QA testingu. Základný profil `standard_user` slúži ako referenčný účet, zatiaľ čo doplnkové profily `visual_user`, `problem_user`, `error_user`,  `performance_glitch_user` a `locked_out_user` obsahujú zámerne zapracované špecifické defekty.  

**Cieľom projektu bolo overiť QA postupy v praxi:**  
* preskúmať aplikáciu
* pripraviť testovaciu dokumentáciu (testovacie scenáre a prípady)
* otestovať aplikáciu a evidovať nájdené chyby
* vypracovať záverečnú správu z testovania  

**Typy a metodika testovania:** manuálne testovanie čiernej skrinky (prieskumné testovanie a testovanie podľa testovacích prípadov; funkcionálne pozitívne a negatívne testy, nefunkcionálne testy zamerané na bezpečnosť, vizuálnu stránku (UI) a rýchlosť načítania stránky (Performance)).

### 1.2 Rozsah testovania (Test Scope)
**In Scope**   
* **Autentifikácia (Prihlásenie/Login) a Správa relácií (Session Management):** Prihlásenie/odhlásenie, správanie tlačidiel prehliadača (*Back/Forward*), ochrana chránených stránok a funkčnosť `Reset App State`.  
* **Katalóg produktov (Products):** Zobrazenie produktov, funkčnosť radenia a perzistencia filtra pri obnovení/navigácii, interaktivita UI prvkov a správnosť obrázkov a popisov.  
* **Nákupný košík a Objednávka (Cart & Order):** Pridávanie/odoberanie položiek, prechod cez checkout, validácia polí doručovacieho formulára až po finálne vygenerovanie potvrdenia objednávky.  
* **Testovanie špecifických používateľských profilov:** Najmä porovnanie správania špecifických doplnkových účtov `visual_user`, `performance_glitch_user`, `problem_user` a `error_user` oproti hlavnému testovanému (referenčnému) profilu `standard_user`. 
* **Cross-browser testovanie:** Microsoft Edge a Google Chrome.  

**Out of Scope**
* **Platobná brána a transakcie:** Aplikácia disponuje iba simulovaným checkoutom bez spracovania reálnych platieb.  
* **Backend & API testovanie:** Testovanie prebiehalo iba na úrovni používateľského rozhrania.  
* **Záťažové a výkonnostné testovanie (Load/Stress Testing):** S výnimkou zhodnotenia profilu performance_glitch_user v prieskumnom testovaní neboli vykonávané záťažové testy.  
* **Prístupnosť (Accessibility):** Testovanie špeciálnych potrieb nebolo súčasťou tohto projektu. 
* **Responzibilita** pre smartfóny a tablety.  

## 2. 🧮 Metrika úspešnosti testov (Test Execution Metrics)
#### 2.1 Súhrn testovania podľa testovacích prípadov
**Počet testovacích scenárov:** 10  
**Počet testovacích prípadov (Test Cases, TC):** 29  
**Vykonaných TC:** 29  
**Úspešné (Passed):** 20 (69 %)  
**Zlyhané (Failed):** 9 (31 %)  
**Zablokované (Blocked):** 0 (0 %)   

<img width="1920" height="1080" alt="Saucedemo com (5)" src="https://github.com/user-attachments/assets/b38a21b9-3d27-4a1c-ad11-e4651d498a81" />

Všetky uvedené metriky vychádzajú z vykonania 29 testovacích prípadov na referenčnom účte standard_user.   
Modul **Prihlásenie (Login)** obsahoval testovacie prípady, ktoré mali pri testovaní 100% úspešnosť.   
Naopak najviac zlyhaní (5) bolo zaznamenaných v module s najväčším počtom testovacích prípadov - **Katalóg produktov**. Boli to vizuálne nedostatky, nekonzistentnosť obsahu a nedostatočná perzistencia filtra.  Najviac defektov (4) sa v Katalógu produktov vzťahovalo **na tlačidlo a správanie filtra**.    
Najväčšiu severitu mali bugy zistené v moduloch **Nákupný košík a Objednávka** (1xMajor) a **Správa relácií** (1xMajor). To naznačuje potrebu venovať týmto modulom zvýšenú pozornosť.    

<img width="1920" height="1080" alt="Saucedemo com (1)" src="https://github.com/user-attachments/assets/8e6a71cd-2167-4dea-8ef2-15fb408ace20" />  

<img width="1920" height="1080" alt="4" src="https://github.com/user-attachments/assets/c9a3992b-7ac9-40af-8840-91d2effcd6f3" />

### 2.2 Súhrn prieskumného testovania (Exploratory Testing)
**Počet vykonaných testovacích relácií (Sessions/Charters):** 2   
**Celkový investovaný čas:** 180 minút (120 minút testovanie / 60 minút dokumentácia výsledkov)  
**Počet evidovaných bugov z prieskumného testovania:** 2 bugy  
  * **BUG_Exploratory_I (KAN-16):** Výkonnostné spomalenie načítania katalógu pri `performance_glitch_user`.
  * **BUG_Exploratory_II (KAN-17):** Vytvorenie neviditeľnej položky v košíku pri `problem_user`.

### 2.3 Celkový súhrn defektov
**Celkový počet evidovaných bugov:** 11 (9 bugov vytvorených na základe testovacích prípadov a 2 bugy identifikované počas prieskumného testovania). 


## 3. 📙 Prehľad nájdených defektov podľa testovacích prípadov
Počas testovania podľa definovaných testovacích prípadov bolo zaznamenaných 9 defektov, z toho 2 defekty s významnou (Major) severitou. Základný testovaný účet pre bug reporty bol referenčný profil `standard_user` (na ktorom bolo spustených všetkých 29 TC). Všetky nájdené defekty mali status *To Do* (*Úloha*). 
Nad rámec týchto defektov boli počas dvoch prieskumných testovaní zaznamenané ďalšie 2 špecifické bugy pre doplnkové účty `performance_glitch_user` a `problem_user` (pozri nasledujúcu kapitolu 4).  

| # | BUG_ID | Modul | Opis defektu | Závažnosť / Severita |
| :--- | :--- | :--- | :--- | :---| 
|1| **BUG_Cart_03 (KAN-13)** | Nákupný košík a Objednávka | Umožnenie dokončenia objednávky s prázdnym nákupným košíkom. | Významná / Major |
|2| **BUG_Session_01 (KAN-11)** | Správa relácií | Pri aktívnej relácii sa po stlačení tlačidla *späť* zobrazí login stránka. | Významná / Major |
|3| **BUG_BikeLight_01 (KAN-12)** | Katalóg produktov | Pri zobrazení produktu *Sauce Labs Bike Light* v katalógu aj v detaile produktu sa zobrazuje nesprávny obrázok. | Stredná / Medium |
|4| **BUG_Order_02 (KAN-9)** | Nákupný košík a Objednávka | Formuláru na stránke `/checkout-step-one.html` chýba validácia formátu vstupných údajov a systém umožní používateľovi pokračovať v objednávke.  | Stredná / Medium |
|5| **BUG_Reset_01 (KAN-10)** | Bočné menu a Odhlásenie | Funkcia `Reset App State` funguje len čiastočne. Predvolený stav nenastane pri tlačidlách `Remove`, nastavení aktívneho filtra a zoradení produktov v Katalógu.  | Stredná / Medium |
|6| **BUG_Filter_02 (KAN-4)** | Katalóg produktov | Po obnovení stránky sa aktívny filter *Price (low to high)* neuloží a produkty nie sú zoradené podľa ceny, ale abecedne podľa predvoleného filtra. | Nízka / Low |
|7| **BUG_Filter_03 (KAN-5)** | Katalóg produktov | Zoradenie produktov podľa zvoleného filtra pretrvá iba na stránke `/inventory.html`. Ak používateľ prejde do detailu akéhokoľvek produktu a následne sa vráti späť tlačidlom `Back to products`, aktívny filter sa obnoví na predvolenú hodnotu. | Nízka / Low |
|8| **BUG_UI_Filter_02 (KAN-7)** | Katalóg produktov | Kliknutie na *caret ikonku* nevyvolá žiadnu akciu. K rozbaleniu menu dôjde iba, ak používateľ klikne na tlačidlo mimo tejto ikonky.  | Nízka / Low |
|9| **BUG_UI_Filter_03 (KAN-8)** | Katalóg produktov | Tlačidlo filtra poskytuje nekonzistentnú indikáciu klikateľnosti. Kurzor pointer sa zobrazuje iba nad *caret ikonkou*. | Nízka / Low |


## 4. 📘 Prínos prieskumného testovania (Exploratory Testing Value)
**Prínosom prieskumného testovania** na začiatku projektu (Prieskumné testovanie I.) bolo definovanie základného toku aplikácie a príprava podkladov pre tvorbu štruktúrovaných testovacích scenárov a prípadov. Pri zvolenom profile `performance_glitch_user` bolo kľúčovým nálezom citeľné spomalenie načítania stránky.  

Prieskumné testovanie na konci projektu (Prieskumné testovanie II.) odhalilo kritický problém v správaní košíka pri špecifickom doplnkovom profile `problem_user`.  

V rámci uvedených sessions boli evidované nasledovné 2 bugy: 

  **BUG_Exploratory_I**  
Úvodná fáza prieskumného testovania odhalila neúmerne dlhú dobu (5,55 sekúnd) načítania stránky `/inventory.html` v dvoch špecifických momentoch – bezprostredne po prihlásení a pri návrate z dokončeného nákupu.   

  **BUG_Exploratory_II**   
Záverečná fáza prieskumného testovania zaznamenala kriticky závažné správanie košíka, pri ktorom vznikla neviditeľná položka. Táto položka sa dala odstrániť `Reset App State` (nie je to štandardný používateľský spôsob).

<img width="1920" height="1080" alt="Saucedemo com (7)" src="https://github.com/user-attachments/assets/1810f874-2063-4851-b570-fc7df9150810" />



## 5. 📝 Záver a odporúčania
### 5.1 Celkové zhodnotenie
**Pre komerčné produkčné nasadenie (Commercial Release):** NO-GO   
Aplikácia nie je pripravená na produkčné nasadenie z dôvodu prítomnosti závažných defektov v nákupnej logike (možnosť dokončiť objednávku s prázdnym košíkom) a v správe relácií (nechránený návrat na login), ktoré boli zistené pri štandardnom používateľskom účte (`standard_user`).   

**Pre vzdelávacie a didaktické účely (Educational Tool):** 100 % GO.  
SauceDemo je vynikajúcou didaktickou pomôckou na výučbu junior QA testerov:  
* poskytuje reálne príklady funkcionálnych, UI aj logických defektov - vhodný materiál pre tvorbu testovacích prípadov a bug reportov   
* umožňuje používať vývojárske nástroje (DevTools) a nástroje na zachytávanie dôkazov (screenshoty a videozáznamy)   
* poskytuje priestor na praktickú aplikáciu techník testovania čiernej skrinky (najmä analýza hraničných hodnôt, negatívne testovanie) a prieskumného testovania  
* najmä nezhody medzi obrázkami a popismi produktov by v reálnom e-shope boli defekty, v aplikácii *SauceDemo* sú z pohľadu výučby jedným z najzaujímavejších aspektov - podnecujú k ďalšiemu skúmaniu aplikácie, hľadaniu súvislostí a prirodzene rozvíjajú zvedavosť, pozornosť k detailom a testerské myslenie  


### 5.2 Identifikované riziká (reálna produkčná aplikácia)

**(1) Riziko finančnej straty a straty zákazníka (Zlá logika košíka):** Možnosť odoslať prázdnu objednávku (*BUG_Cart_03*) vytvára riziko zbytočných nákladov pri spracovaní nulových objednávok. So vznikom neviditeľnej položky, ktorú nie je možné odstrániť štandardným tlačidlom `Remove` (*BUG_Exploratory_II*) sa vytvára kritické riziko, že zákazník košík aj e-shop opustí.  

**(2) Bezpečnostné riziko (Ponechanie aktívnej relácie):** Ponechanie aktívnej relácie pri návrate tlačidlom *späť* v prehliadači (*BUG_Session_01*) vystavuje používateľa riziku neoprávneného prístupu k účtu.   

**(3) Zhoršená používateľská skúsenosť (UX a výkon):** Strata nastaveného filtra pri prechode do detailu produktu alebo pri refreshi (*BUG_Filter_02, BUG_Filter_03*) a zhoršená výkonnostná efektivita načítania katalógu (*BUG_Exploratory_I*) negatívne ovplyvňuje používateľský zážitok.   

**(4) Validácia vstupov:** Chýbajúca validácia formátu údajov v checkoute (*BUG_Order_02*) umožňuje odoslanie neplatných adries/PSČ, čo by viedlo k nedoručiteľným zásielkam.  


### 5.3 Odporúčania pre ďalší vývoj / QA kroky (reálna produkčná aplikácia)

**(1) Oprava biznis logiky & bezpečnosti:** Prioritne zapracovať podmienku na minimálny počet položiek v košíku pre prechod do checkoutu, opraviť fungovanie košíka tak, aby v ňom neostali neviditeľné položky a zabezpečiť, aby sa prihlasovacia stránka nezobrazovala už prihlásenému používateľovi, keď klikne na šípku *späť* v prehliadači.   

**(2) Optimalizácia výkonu a načítavania:** Optimalizovať čas načítania stránky `/inventory.html`. Počas testovania bola ako orientačná referenčná hodnota použitá doba načítania do 3 sekúnd, pričom pri profile `performance_glitch_user` bol zaznamenaný výrazne dlhší čas načítania.  

**(3) Oprava perzistencie filtrov:** Zaistiť ukladanie stavu filtra tak, aby filter pretrval aj po obnovení stránky a návrate z detailu produktu.   

**(4) Doplnenie validácie formulárov:** Zaviesť regex pravidlá na povinné polia (napr. overovanie formátu PSČ, mien a priezvisk).    


<img width="1920" height="1080" alt="1" src="https://github.com/user-attachments/assets/a0b39862-1f8b-4363-b56e-75756c665169" />





