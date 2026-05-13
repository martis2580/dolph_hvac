# Sistemos veikimo algoritmai ir darbo režimai

## Ventiliatorių paleidimo ir stabdymo seka

1. Ventiliatorių paleidimo seka (Start)
Kai valdiklis gauna komandą „START“ (per HMI pultelį, kalendorių arba išorinį kontaktą), sistema vykdo šiuos veiksmus:

- Sklendžių atidarymas: pirmiausia siunčiamas signalas atidaryti tiekiamo ir ištraukiamo oro sklendes. Maišymo kameros (Mixing chamber) sklendė valdoma lygiagrečiai su tiekimo ir ištraukimo sklendėmis, tačiau priešinga kryptimi: kai tiekimo ir ištraukimo oro sklendės atidarytos 100 %, maišymo kameros sklendė būna visiškai uždaryta. Visos sklendės valdomos 0–10 V signalu.
- Sistemos parengtis: valdiklis laukia patvirtinimo, kad sklendės atsidarė (pagal nustatytą laiko delsą). Įvykdoma programinė delsa, skirta mechaniniams mazgams pasiruošti darbui.
- Ventiliatorių aktyvavimas: Įjungiami tiekimo ir ištraukimo ventiliatoriai. Jų greitis (0–10 V signalas į dažnio keitiklius) kyla palaipsniui iki nustatytos darbinės reikšmės (I, II, III pavara).

2. Ventiliatorių stabdymo seka (Stop)
Stabdymo procesas yra kritinis, nes jame numatytas priverstinis komponentų aušinimo etapas:

- Šilumos/šalčio šaltinių išjungimas: Gavus komandą „STOP“, pirmiausia išjungiami visi aktyvūs energijos šaltiniai: DX sekcijos (freoniniai blokai), sausintuvas.
- Priverstinis aušinimas (cool-down): ventiliatoriai nenustoja suktis iš karto. Jie tęsia darbą nustatytą laiko tarpą (dažniausiai nuo 30 iki 180 sekundžių), kad pašalintų likutinę šilumą ar šaltį nuo kaloriferių DX sekcijoje.
- Ventiliatorių stabdymas: Pasibaigus aušinimo laikui, ventiliatorių sukimosi greitis mažinamas iki nulio.
- Sklendžių uždarymas: Tik visiškai sustojus ventiliatoriams, uždaromos oro sklendės.

3. Avarinis stabdymas
Yra specifinių sąlygų, kai ventiliatorių darbas nutraukiamas nedelsiant arba pagal specialų saugos protokolą:

- Priešgaisrinis signalas (Fire): gavus signalą iš gaisrinės signalizacijos, ventiliatoriai stabdomi nedelsiant, kad būtų užkirstas kelias dūmų plitimui.

Papildoma informacija: OŠP1, OŠP2, OŠP3 naudojami Lenze i510 ir Lenze i550 dažnio keitikliai po 7 kW.

## Temperatūros palaikymo logika (WINTER/SUMMER sezonai)

1. Sezonų nustatymas (WINTER / SUMMER):

Sezono parinkimas atliekamas per valdiklio nustatymus, prisijungus administratoriaus (admin) lygiu: HMI meniu → Settings → Season.

2. Temperatūros reguliavimo kaskada:
Siekdamas išlaikyti užduotą temperatūrą ($T_{set}$), valdiklis nuosekliai jungia turimus mazgus.

Šildymo seka (Žiemos režimas):

- Rekuperatorius: pirmiausia maksimaliai naudojama grąžinama šiluma per freoninį šilumokaitį (sausintuvą).
- DX šildymas (FX): jei vis dar trūksta šilumos, aktyvuojamas DX blokas šildymo režimu.

Vėsinimo seka (Vasaros režimas):

- Rekuperacija: jei lauko oras vėsesnis už grįžtamąjį, naudojamas lauko oras vėsinimui;
- DX vėsinimas: Aktyvuojamos DX sekcijos pakopomis (viena arba abi), kad būtų pasiekta vėsinimo užduotis.

3. Valdymo algoritmas (PI reguliatorius)

- Proporcinis-integralinis (PI) valdymas: valdiklis nuolat lygina tiekiamo ($T_p$) arba grįžtamojo ($T_g$) oro temperatūrą su nustatyta verte ir pagal nuokrypį generuoja 0–10 V valdymo signalą ($Y$).
- Neutrali zona: tarp šildymo ir vėsinimo sekcijų yra nustatoma „negyvoji zona“, kad sistema vienu metu nepradėtų šildyti ir vėsinti, taip taupant energiją.

4. Apsaugos funkcijos
Tiekiamo oro apribojimai: nepriklausomai nuo poreikio, valdiklis neleidžia pūsti per šalto (pvz., < +14 °C) arba per karšto (pvz., > +35 °C) oro į areną, kad būtų išvengta diskomforto. Šie nustatymai koreguojami prisijungus administratoriaus lygiu.

## DX sekcijos valdymas

Šildymo ir vėsinimo pakopų aktyvavimas...

## Energijos grąžinimo ir maišymo kameros sąveika su DX šilumokaičiais

## Papildyti

