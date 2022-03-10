# Projekt1

Server sa začína vytvorením socketu aby sa mohlo pripojiť na server. Následné nastavenie setsockopt aby nám nepadal server.
Pripajáme sa na server podľa portu, ktorý sme zadali v argumente, a pomocou funkcie bind priradíme meno socketu.
Pomocou funkcie listen sa čaká na pripojenia na soketu, a následne funkcia accept povolí spojenie so socketom.
Pre popis projektu bolo treba naprogramovať v C funkcie, ktoré nám budú vraciať názov PC, názov procesora a následne joho využitia. 
Názov PC sme zistili cez funkciu gethostname. 
Názov procesora sme zistili pomocou súboru /prec/cpuinfo kde sme si podľa model name naŠli tento názov. 
Využitie procesora sme zistili pomocou súboru /proc/stat kde sme pomocou funkcie skip_lines nechali iba prvý riadok ktorý je dôležitý a jeho hodnoty sme si vložili do štruktúry, do jednotlivých premén. toto sa nám spravilo 2 krát kvôli predchadzajúcim štatistikám a terajším aby sme mohli pomocou funkcie calculate_load vypočítať využitie procesora.

## Spustenie 

Vytvoríme si make aby nám preložil c súbor hinfosvc.c na spustiteľný súbor.

Server spustíme zadaním ./hinfosvc (port) a na stránke zadáme adresu:
```
127.0.0.1:port/hostname
127.0.0.1:port/cpu-name
127.0.0.1:port/load
```
server ukončíme CTRL+C

alebo spustíme server pomocou ./hinfosvc (port) & a v prikazovom riadku zadáme curl+adresa napr:
```
curl http://127.0.0.1:12345/hostname
curl http://127.0.0.1:12345/cpu-name
curl http://127.0.0.1:12345/load
```
server ukončíme tzv kill processom


### Príklady
```
curl http://127.0.0.1:12345/hostname
13%
curl http://127.0.0.1:12345/cpu-name
AMD Ryzen 5 3550H with Radeon Vega Mobile Gfx
curl http://127.0.0.1:12345/load
B07-1219A
```
