# Förbättringar över IPv4
IPv6 kom som en förbättring på [[IPv4]], följande saker blev förbättrade:
- Fler adresser - IPv6-adresser har 128 bitar istället för 32 bitar som IPv4 har
- Bättre header-format: IPv6-headern har en konstant längd på 40 byte. Eventuella tillval tillhör inte headern utan läggs mellan headern och payload
- Funktioner för realtidsdata: Det finns en flow label i headerns som gör det möjligt för sändaren att begära speciell hantering av datagrammet för att underlätta för realtidsapplikationer
- Säkerhetsfunktioner: IPv6 innehåller tillval för kryptering och autentisering
- Möjlighet till utökning av protokollet: Internet utvecklas alltid och IPv6 har möjligheten att utvecklas när nya tekniker kommer

# Adressering
En IPv6-adress består av 16 bytes (128 bitar), för att man enklare ska kunna läsa detta så skriver man den i hexadecimalt format med 2 bytes sen kolon, vilket blir 4 hexadecimala tal, t.ex xxxx:xxxx:xxxx:xxxx...

## Kortare skrivsätt
Många bitar en IPv6 adress kommer vara satta till noll och vi har därför en bra lösning till detta, man kan skriva adressen kortare på följande sätt
`F043:0043:0000:0000:B0CA:0000:3C30 = F043:43:0:0:0:B0CA:0:3C30 = F053:43::B0CA:0:3c30`

### Adresskatogerier
Det finns olika katogoerier av adresser i IPv6, dessa defineras av de första bgitaran i adressen, typ-prefixet (type prefix). Några av de viktigaste kategorierna är 
- Unicast adresser - En unik mottagare av datagrammet - börjar på 010
- Multicast adresser - En grupp av mottagare, paketet levereras till alla i gruppen - börjar med bitarna 11111111 (8 bitar)
- Lokala adresser - Privata adresser som bara används på ett nät, en router skickar aldrig vidare dem - börjar med bitarna 111111101 (9 bitar)

# Header
40 bytes
Headern har många likheter till [[IPv4#IPv4 Header | IPv4 Headern]] följande saker är intressanta med IPv6
- VER är 0110 för IPv6
- Prioritet (PRI): Finns i IPv6 och definierar vilken prioritet datagrammet ska ha jämfört med andra datagram
- Flow label: I IPv6 kan en sändare skicka en ström av datagram som hör ihop, läs mer under [[#Flödeshantering]]
- Nyttolastenslängd: Längden datagrammet förutom bas-headern, mätt i byte
- Nästa header: Definierar headern som kommer efter bas-headern, detta är antingen en header från protkollet som skickar paketet t.ex TCP eller UDP. Eller så är det en tillvalsheader

![[IMG_0035.jpeg]]

# Flödeshantering
I [[IPv4 | IPv4]] så hanteras alla paket seperat, I IPv6 så finns möjligheten att hantera dessa sammanhörande datagram som ett flöde (flow). Datagram som skickas i ett flöde ha vissa delade egenskaper
- Kanske ska skickas samma väg genom nätet
- Använda vissa säkerhetsfunktioner
- Ha en viss prioritet

**Flow label** tillsammans med sändarens adress idientiferar ett flöde. En router som kan hantera flöden har en [[#Flödes-tabell (flow label table)]]. Anledningen varför IPv6 har flöden är främst för att protokoll som hanterar readltidsapplikationer skall kunna reservera kapacitet i nätet för att kunna garantera kvaliten på dataöverföringen.



### Flödes-tabell (flow label table)
En flödes-tabell sparar hur alla olika flöden ska hanteras. När routern får in ett nytt paket som tillhör ett visst flöde så kollar den i sin tabell för att se hur paketet ska hanteras. Flöden identifieras med **Flow label** tillsammans med sändarens adress.

# Fragmentering
IPv6 tillåter inte routrar på nätet att fragmentera paket, det är bara sändaren som får bestämma hur stora datagrammen får vara. Om en router på vägen får ett paket som har är större än MTU så kastas paketet. För att sändaren ska veta hur stora alla paket får vara så använder den sig av en teknik kallad **Path MTU Discovery Technique**. Anledningen till att att fragmentering inte tillåts i IPv6 är att det är tidskrävande.

# Övergång från IPv4 till IPv6
Det kommer ta lång tid för internet att gå över från IPv4 till IPv6 eftersom alla routrar och datorer måste uppdateras. I slutet av 2018 så använde **cirka 7 %** av de svenska användarna IPv6. Några operatörer har förberett för IPv6 genom att ge ut adresser men inte uppdaterat all hårdvara.

Vi är just nu i en övergångsfas och IETF har definierat tre strategier för övergångsperioden, [[#Dual stack]], [[#Tunnling (tunnelling)]] och [[#Header translation?]]

## Dual stack
Detta innebär att en värddator implementerar både IPv4 och IPv6 under övergånsperioden. Om mottagaren har en [[#Adressering | IPv6 adress]] så används den annars så används [[IPv4#Adressering | IPv4 adressen]]. Det betyder att två nätprotokoll används och routrar måste stödja både [[IPv6]] och [[IPv4]] .



## Tunnling (tunnelling)
Denna tekniken använd då ett IPv6 datagram behöver åka igenom ett nät som bara stödjer IPv4. IPv6-datagrammet kapslas då in i ett [[IPv4]]-datagram med adresser som motsvarar tunnelns ändpunkter i det specifika nätet. På andra sidan nätet packas IPv6-datagrammet upp igen. För att veta det är ett IPv6 datagram som skickas inom ett IPv4 datagram så sätts protokollfältet i [[IPv4#IPv4 Header| IPv4 headern]] till 41.

## Header translation?
#missing

