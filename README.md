## Implementačná dokumentácia k 1. úlohe do IPP 2021/2022
Meno a priezvisko: Samuel Sadlek  
Login: xsadle01  
  
### parse.php
Ako prvé sme si skontrolovali, či máme správny počet argumentov, načítali sme si súbor zo vstupu,  
pomocou regexu sme odstránili komentáre na konkrétnom riadku a funkciu trim sme použili na odstránenie bielych znakov
### parse_line.php
Skontrolovali sme či sa prvý riadok nerovná hlavičke pokiaľ áno odstránime bodku a vypíšeme do xml názov hlavičky.  
Funkcia preg_split mi rozdelí slová do poľa podľa bielych znakov.
### set_inst.php
Vytvorili sme si konštanty, do ktorých sme si uložili všetky inštrukcie, koľko argumentov potrebujú a aké.  
Kontrolujeme pomocou regexu či boli inštrukcie správne zapísané vždy v prvom poli riadku.
Tieto inštrukcie sa zapíšu ako Objekt
Následne kontrolujeme typy za inštrukciou zavolaním funkcie get_type. V nej kontrolujeme  
cez cyklus, ktorý spracováva pole riadku, operandy či sú správne zapísané podľa jazyka IPPcode22.  
S týmto sa kontroluje aj, či bol správny počet operandov pre každú konkrétnu inštrukciu.  
Pri znakoch ako sú napríklad "<" sme prepísali špecialnou hodnotou "&lt;"
Následný switch nám prechádza po jednotlivých symbolov predom definovaných konštánt, ak nájde inštrukcie, následne kontroluje, 
či sa typ predefinovaného operandu rovná typu práve spracovaváneho operandu. Pokiaľ nájde, zapíše sa ako objekt.
### Argument.php
Táto trieda vytvára objekty typu operandov má svoj typ,symbol,a hodnotu. Symbol je uložený iba ak sa typ nerovná label.
### Instruction.php
Táto trieda vytvára objekty pre inštrukcie a má svoje meno a počet operandov.
