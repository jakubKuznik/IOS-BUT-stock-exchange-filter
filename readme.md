TESTY:
    https://github.com/ondrej-mach/iotest/tree/main



Popis

    Skript filtruje záznamy z nástroje pro obchodování na burze. Pokud je skriptu zadán také příkaz, nad filtrovanými záznamy daný příkaz provede.
    Pokud skript nedostane ani filtr ani příkaz, opisuje záznamy na standardní výstup.
    Skript umí zpracovat i záznamy komprimované pomocí nástroje gzip (v případě, že název souboru končí .gz).
    V případě, že skript na příkazové řádce nedostane soubory se záznamy (LOG, LOG2 …), očekává záznamy na standardním vstupu.
    Pokud má skript vypsat seznam, každá položka je vypsána na jeden řádek a pouze jednou. Není-li uvedeno jinak, je pořadí řádků dáno abecedně dle tickerů. Položky se nesmí opakovat.
    Grafy jsou vykresleny pomocí ASCII a jsou otočené doprava. Každý řádek histogramu udává ticker. Kladná hodnota či četnost jsou vyobrazeny posloupností znaku mřížky #, záporná hodnota (u graph-pos) je vyobrazena posloupností znaku vykřičníku !.


JMÉNO

    tradelog - analyzátor logů z obchodování na burze

POUŽITÍ

    tradelog [-h|--help] [FILTR] [PŘÍKAZ] [LOG [LOG2 [...]]

VOLBY

    PŘÍKAZ může být jeden z:
        list-tick – výpis seznamu vyskytujících se burzovních symbolů, tzv. “tickerů”.
        profit – výpis celkového zisku z uzavřených pozic.
        pos – výpis hodnot aktuálně držených pozic seřazených sestupně dle hodnoty.
        last-price – výpis poslední známé ceny pro každý ticker.
        hist-ord – výpis histogramu počtu transakcí dle tickeru.
        graph-pos – výpis grafu hodnot držených pozic dle tickeru.
    FILTR může být kombinace následujících:
        -a DATETIME – after: jsou uvažovány pouze záznamy PO tomto datu (bez tohoto data). DATETIME je formátu YYYY-MM-DD HH:MM:SS.
        -b DATETIME – before: jsou uvažovány pouze záznamy PŘED tímto datem (bez tohoto data).
        -t TICKER – jsou uvažovány pouze záznamy odpovídající danému tickeru. Při více výskytech přepínače se bere množina všech uvedených tickerů.
        -w WIDTH – u výpisu grafů nastavuje jejich šířku, tedy délku nejdelšího řádku na WIDTH. Tedy, WIDTH musí být kladné celé číslo. Více výskytů přepínače je chybné spuštění.
    -h a --help vypíšou nápovědu s krátkým popisem každého příkazu a přepínače.
