# Zadanie #1: Blúdny holanďan

Nadaný počítačový vedec z Holandska menom [Edsger](https://en.wikipedia.org/wiki/Edsger_W._Dijkstra) si každý deň o 4:20pm dopraje pochutinu z miestnej predajne. Ako to už býva, dostane potom chuť na ďalšiu pochutinu - ***[Stroopwafel](https://en.wikipedia.org/wiki/Stroopwafel).*** 

Edsger však začal byť ospalý a preto sa rozhodol, že si vyrobí autonómny bicykel, ktorý mu ich sám prinesie. Aby sa pri hľadaní najbližšieho stánku so Stroopwafel bicykel nestratil, vymyslel pre neho [algoritmus](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm), ktorý mu pomôže nájsť najkratšiu cestu.

Návrh algoritmu Edsgera vyčerpal natoľko, že zaspal a preto potrebuje vašu pomoc s dokončením jeho vynálezu.

# 1. Úloha : Mapa

Amsterdam je rozľahlý a autonómny bicykel by sa ľahko stratil, preto mu musíme dať mapu. Edsgerov nápad bol rozdeliť mapu na rovnaké štvorčeky. Potom už len zostáva zistiť, či sa v niektorom štvorčeku nachádza budova, alebo či ním môže bicykel bez problému prejsť.

![Untitled](Zadanie%20#1%20Blu%CC%81dny%20holand%CC%8Can%203c915fbdb1944647bfc5f8f4573c1d7c/Untitled.png)

Vašou úlohou je do triedy pripravenej v súbore ************[map.py](http://map.py)** z objektov triedy v súbore node.py ************************vytvoriť reprezentáciu mapy, ktorú bude bicykel pri hľadaní používať.

Trieda Node má nasledujúce parametre:

- pos_x (int): Riadok, v ktorom sa bunka nachádza,
- pos_y(int): Stĺpec, v ktorom sa bunka nachádza,
- is_occupied(bool): Nadobúda hodnotu 0 ak je bunka priechodná, 1 ak je bunka nepriechodná,
- neighbors(list): Tento parameter je pri incializácii nastavený na **None.** Po zaplnení bude obsahovať zoznam všetkých prilahlých buniek.

V rovnakej triede sa nachádzajú nasledovné metódy:

- set_occupancy(self, is_occupied): Parameter is_occupied je typu boolean a mení stav bunky z obsadenej na neobsadenú a naopak.
- set_neighbors(self, neighbors): List priľahlých buniek nahradí listom buniek v parametri neigbors
- add_neighbor(self, neighbor): Pridá do zoznamu susedných buniek objekt v parametri neighbor
- remove_neighbor(self, neighbor): Odoberie zo zoznamu susedných buniek objekt v parametri neighbor
- get_distance(self, node): Vráti euklidovskú vzdialenosť ku podľa koordinátov objektu node

Trieda Map má nasledujúce parametre:

- size: Veľkosť ************strany************ mapy, ktorú je potrebné vytvoriť

V rovnakej triede sa nachádzajú nasledovné metódy:

- find_neighbors(self): Pre každú bunku v mape vráti zoznam buniek s ňou susediacich vo všetkých ôsmych smeroch
- get_nodes(self): Vráti všetky objekty node ktoré boli vygenerované pre mapu

## 2. Úloha: Nájdenie cesty

Pre vaše pohodlie sa v triede Dijkstra nachádza hotová implementácie Dijkstrovho algoritmu, preto do tejto triedy nezasahujte vôbec.

Pre nájdenie najkratšej cesty je potrebné z tejto triedy vždy vytroviť nový objekt s nasledujúcimi parametrami:

- map: Objekt vygenerovanej mapy
- origin: Objekt Node, ktorý si zvolíte ako začiatok vašej cesty
- destination: Objekt Node, ktorý si zvolíte ako cieľ vašej cesty

Pri používaní tejto implementácie je potrebné zavolať obe metódy, ktoré sa v triede nachádzajú v poradí find_path() → get_path(). Bližší popis činoosti týchto metód nájdete v docstringoch.

## 3. Úloha: ROS

V tejto úlohe je potrebné navrhnúť ROS Service tak, aby klientom bol váš bicykel a na serveri hotová implementácia prehľadávania cesty.

Za bonusové body: Pre mapu vytvorte ros node tak, aby mohol bicykel aktualizovať stav obsadenosti buniek a zároveň aby táto ros node posielala aktuálnu mapu serveru.