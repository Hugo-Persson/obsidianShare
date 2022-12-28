

WLAN definerar två typer av MAC-Protokoll, Distributed Coordination function (DCF) och Point Coordination Function (PCF), PCF använder sig av DCF.

## Distributed Coordination function (DCF)

DCF använder sig av CSMA/CA meden reservationsmetod RTS/CTS. RTS/CTS löser hidden terminal problem.

### Hidden terminal problem

Detta problem uppstår när vi har två terminaler A och B och en basstation, både A och B kan se och nå basstationen men A och B ser inte varandra, detta betyder att de kan skicka data samtidigt utan att märka att en kollision uppstår.

### RTS/CTS

För att lösa Hidden terminal problem så fungerar RTS/CTS så här,

1. En terminal detekterar att mediumet är ledigt
2. Efter detta väntar den en viss tid DIFS (distributed interframe space)
    1. DIFS kan sättas så att terminaler eller data med hög prioritet har lägre DIFS
3. Om mediet fortfarande är ledigt efter DIFS skickar terminalen ut en kontrollram kallad **Request to send** (RTS) till basstationen
4. Basstationen väntar en viss tid SIFS(short interframe space)
5. Basstationen skickar sedan Clear to send (CTS) 
6. Efter sändaren tar emot CTS väntar den tiden SIFS och skickar sedan sin dataramt 
7. När mottagarstationen tagit emot dataramen väntar den tiden SIFT och skickar sedan ACK

För att lösa hidden terminal problem räcker inte detta, Network Allocation Vector (NAV) måste också användas. 

- När terminalen skickar RTS så finns det i ramen hur länge terminalen vill sända
- Basstationen bekräftar detta med CTS
- Alla terminaler som hör RTS/CTS dialogen sätter en NAV-timer, medans denna är igång låter de bli att skicka något.

## Point Coordination Function (PCF)

PCF är en centraliserad accessmetod där bastationen syr accessen till mediet. En polling mekanism används vilket betyder att basstationen frågar (polls) varje station i tur och ordning om de har data att sända. En station som blir tillfrågad skickar de data den har till basstationen.

Man kan använda PCF och DCF samtidigt, genom att de får dela på tiden. Det funkar så här

1. Först startar en PCF period
    1. Basstationen väntar en tid kallad PCF interframe space, (PIFS). PIFS är kortare än DIFS vilket innebär att PCF mekanismen har högre prio än DCF
    2. När bastationen har väntar PIFS skickar den ut en beacon, alla stationer som hör denna beacon sätter sin NAV timer
    3. Efter tiden SIFS pollar bassationen en stations som väntar tiden SIFS och sedan skickar tillbaka data plus ett ACK.
    4. Basstationen kan sedan polla alla stationen som har PCF efter varandra.
    5. Efter detta är PCF slut
2. DCF perioden börjar
    1. Under DCF får de stationer som använder DCF skicka sina data