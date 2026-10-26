# Testovacie scenáre (TS) pre projekt Saucedemo.com

## Modul: Prihlásenie (Login)

### TS_Login - Overenie funkčnosti prihlásenia na stránku

Overte, či systém správne reaguje na rôzne vstupy v prihlasovacom procese, umožní prihlásenie pri zadaní platných údajov a zamedzí prístup a zobrazí chybové hlásenie pri neúplných, nesprávnych alebo zablokovaných údajoch.

**Testovacie prípady (TC):**

- TC_Login_01 - Overenie prihlásenia s platnými prihlasovacími údajmi
- TC_Login_02 - Overenie prihlásenia so zamknutým účtom
- TC_Login_03 - Overenie prihlásenia s neplatným heslom
- TC_Login_04 - Overenie prihlásenia bez zadania mena používateľa (Username is required)

---

## Modul: Katalóg produktov

### TS_Products_01 - Overenie katalógu produktov

Overte správnosť zobrazenia údajov a prvkov produktov v katalógu (názov, obrázok, popis, cena a tlačidlo Add to cart).

**Testovacie prípady:**

- TC_Products_01 - Overenie zobrazenia katalógu produktov
- TC_BikeLight_01 - Overenie zhody popisu a obrázka produktu "Sauce Labs Bike Light"

### TS_Products_02 - Overenie zobrazenia detailu produktu

Overte, že po kliknutí na názov alebo obrázok produktu v katalógu sa otvorí jeho detail so správnymi údajmi a prvkami (názov, obrázok, popis, cena a tlačidlo Add to cart).

**Testovací prípad:**

- TC_Products_02 - Overenie zobrazenia detailu produktu

### TS_Products_03 - Overenie funkcie Add to cart a Remove

Overte, že každý produkt v katalógu a v detaile produktu má funkčné tlačidlo Add to cart / Remove.

**Testovacie prípady:**

- TC_Products_03 - Overenie funkcie Add to cart/Remove v katalógu
- TC_Products_04 - Overenie funkcie Add to cart/Remove v detaile produktu

### TS_Products_04 - Overenie radenia produktov (filter)

Overte, či funkcia radenia (filter) spoľahlivo mení poradie produktov podľa zvolenej možnosti, abecedne alebo podľa ceny, a či sa zvolené nastavenie zachová po obnovení stránky alebo návrate z detailu produktu.

**Testovacie prípady:**

- TC_Filter_01 – Overenie funkčnosti radenia (filtra)
- TC_Filter_02 – Overenie zachovania zoradenia produktov podľa aktívneho filtra po obnovení stránky
- TC_Filter_03 – Overenie zachovania zoradenia produktov podľa aktívneho filtra po návrate z detailu produktu

### TS_UI_Filter - Overenie interaktivity UI prvkov filtra

Overte, že všetky časti filtra, tlačidlo, caret ikonka a rozbaľovacie menu reagujú na kurzor a kliknutie.

**Testovacie prípady:**

- TC_UI_Filter_01 – Overenie interaktivity a funkcionality filtra
- TC_UI_Filter_02 – Overenie interaktivity caret ikonky na tlačidle filtra
- TC_UI_Filter_03 – Overenie vizuálnej indikácie klikateľnosti tlačidla filtra

---

## Modul: Nákupný košík a Objednávka

### TS_Cart - Overenie nákupného košíka

Overte zobrazené produkty v košíku (názov, popis, cena), ovládacie tlačidlá (Remove, Continue shopping, Checkout) a funkčnosť odobratia položiek s prepojením na počítadlo košíka a správanie aplikácie pri prázdnom košíku.

**Testovacie prípady:**

- TC_Cart_01 - Zobrazenie pridaných produktov v košíku
- TC_Cart_02 - Odobratie a aktualizácia počtu položiek
- TC_Cart_03 - Pokus o dokončenie objednávky s prázdnym košíkom

### TS_Order - Overenie procesu objednávky

Overte celý proces dokončenia nákupu vrátane validácie doručovacieho formulára, zobrazenia súhrnu objednávky a vygenerovania PDF dokladu.

**Testovacie prípady:**

- TC_Order_01 – Overenie vyplnenia doručovacieho formulára s platnými údajmi
- TC_Order_02 – Overenie validácie formátu vstupných dát vo formulári Checkout: Your Information
- TC_Order_03 – Overenie odoslania formulára s prázdnym poľom First Name
- TC_Order_04 – Overenie správnosti sumára objednávky
- TC_Order_05 – Overenie dokončenia objednávky

---

## Modul: Správa relácií (Session Management)

### TS_Session - Overenie bezpečnosti relácií

Overte, či aplikácia bezpečne spravuje reláciu (session) prihláseného používateľa, najmä či zabráni neautorizovanému vstupu do chránených častí aplikácie pri použití navigácie v prehliadači.

**Testovací prípad:**

- TC_Session_01 - Overenie bezpečnosti relácie pri navigácii šípkou "späť" na prihlasovaciu stránku

### TS_Reset - Overenie funkčnosti Reset App State pre všetky časti aplikácie

Overte, že funkcia Reset App State obnoví celú aplikáciu SauceDemo do defaultného stavu vrátane filtra, košíka, tlačidiel produktov a zoradenia.

**Testovací prípad:**

- TC_Reset_01 - Overenie funkčnosti Reset App State pre všetky časti aplikácie

### TS_Logout - Overenie odhlásenia

Overte, či sa používateľ dokáže úspešne odhlásiť a po odhlásení nemá prístup k interným sekciám aplikácie.

**Testovacie prípady:**

- TC_Logout_01 - Overenie funkcie odhlásenia sa (Logout)
- TC_Logout_02 - Pokus o návrat do aplikácie tlačidlom "späť" po odhlásení
- TC_Logout_03 - Overenie, či je možný priamy prístup na chránenú URL po odhlásení
- TC_Logout_04 - Overenie odhlásenia po vymazaní prihlasovacích cookies v prehliadači
