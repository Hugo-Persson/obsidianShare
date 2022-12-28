OSI Modellen är en standard för hur protkollstacken ska se ut för nätverk, den består av 7 nivåer
![Pasted image 20221113172940.png]({{< ref "Pasted image 20221113172940.png" >}})

## Fysiska lagret - nivå 1

Detta lagret är ansvarig för att skicka en bitström över ett transport medium. Detta lagret anger regler såsom hur ettor och nollor ska represnteras när de skickas över länken. Lagret ser också till så att överföringshastigheten blir rätt och att både mottagare och sändare är synkroniserade.



## Länklagret - Nivå 2 

Detta lagret ansvarar för hur data ska överföras mellan två närliggande nodes. Den innehåller regler för hur data skall pakteras i ramar så att mottagaren ska veta betydelsen av datan som kommer. Det kan finnas funktioner för flödeskontroll och felhantering för att göra datan säker.

## Nätlagret - Nivå 3

Detta lagret har ansvar för överföring av data över ett eller flera nät. Det innehåller regler kring addressering så paket kommer fram till rätt mottagare. Det finns också funktioner för att hitta lämplig väg genom nätet

## Transportskitet - OSI 4
Detta lagret ansvarar för att applikationsdata kommer fram korrekt och i rätt ordning. 
### Funktioner
- Flödeskontroll
- Felhantering
- Dela upp applikationsdata i segment
- Addresseringfunktion - portar
[ Läs mer]({{< ref "😀 6.3 Kommunikation över större nät#transportprotokoll-" >}})


## Sessionslagret - Nivå 5
Detta lagret används då två datorer är i en dialog som kräver till exempel synkronisering. Det finns regler kring hur dialogen sätts upp, underhålls, synkronsieras och hur den går till, tillexempel när varje part kan skicka data.

## Presentationsskitet - OSI 6
Detta lager ansvarar för att ta data från applikationen och koda det till binärdata som mottagaren kan förstå. Det finns funktioner **Komprimering** och **Kryptering**

## Applikationslagret - OSI 7
Detta lagret ser till att användaren kan komma åt nätet. Den innehåller gränsnitt och tjänster

[Vägväljare på olika OSI nivåer]({{< ref "Vägväljare på olika OSI nivåer" >}})