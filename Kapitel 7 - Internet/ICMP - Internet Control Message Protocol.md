ICMPO är ett hjälpprotokoll till IP på [[OSI-Modellen#Nätlagret - Nivå 3 card|Nätlagret (OSI 3)]], IP saknar feldektektering, felkorrigering och hjälpfunktioner. ICMP är gjort för att hjälpa IP med dessa brister.

ICMP-meddelande är specifierat på nät nivå men har inga funktioner för transport, ett ICMP-meddelande kapslas istället in i ett IP paket som sedan ansvarar för transport. 

Det finns två varianter av ICMP, [[#ICMP]] för IPv4 och [[ICMPv6]] för IPv6. 

## ICMP
Ett ICMP-meddelande består av **8 byte** och en datadel som är variabel:
- **Typ**: Detta faält talar om vilken typ meddelandet det är, se [[#Typer av meddelanden]]
- **Kod**: Detta fält talar om varför detta meddelande har skickats
- **Kontrollsumman**: Beräknas på hela headern och datan
- **Resten av headern**: Beror på vilken typ av meddelande som skickas
- **Data**: Innehåller information om original meddealndet så identifiera vilket datagram det blivit något fel med
![[IMG_0037.jpeg]]

## Typer av meddelanden
Det finns två typer av meddelanden [[#Felmeddelanden (Error reporting messages)]] och [[#Förfrågningar (query messages)]]

## Felmeddelanden (Error reporting messages)
Felmeddelanden skickas av routrar eller värddatorer när ett problem uppstår med ett IP-datagram. Felmeddelandet skickas till usprungliga sändaren av IP-datagrammet. ICMP har inga funktioner för felhantering den rapporterar bara att ett fel har uppståt. Det är sedan det överliggande protokollets jobb att hantera felet.

Alla felmeddelanden innehåller original IP headern som sin data del, se bild nedan.
![[IMG_0038 1.jpeg]]

Det finns 4 typer av felmeddelande, värdet i [[#ICMP]] headern sätts till det:
1. Destination Unreachable (Typ = 3) - Skickas när Routern inte kan skicka vidare ett datagram eller om en värddator inte kan hitta applikationen som ska ta emot IP-datagrammet
2. **Source Quench** (Typ = 4) skickas om en router eller värddator måste kasta ett datagram på grund av överbelastning. Detta har två funktioner, det säger till sändaren att ett paket har förlorats och att den måste skicka data långsammare
3. **Time exceeded** (typ = 11) skickas i två fall
	1. När [[IPv4#IPv4 Header |IPv4 Headerns]] TTL når 0
	2. När inte alla fragment som utgör ett paket inte kommer fram i tid
4. **Parameter problem** (Typ = 12) - Ifall ett fel märks i IP-Headern



## Förfrågningar (query messages)
Detta används för att upptäcka nätproblem. Meddelandet skickas i ett IP-datagram från en användare, värddator eller router till en mottagande router eller värddator. Mottagaren svarar sedan med ett **reply**-meddelande. Det finns **fyra** typer av förfrågnignar, värdet i [[#ICMP]] headern sätts till det:
1. **Echo request**: (Typ=8) används för att kontrollera att två enheter kan prata med varandra. Mottagaren svarar med **Echo reply** (Typ = 0)
2. **Timestamp request**: (Typ = 13), används för att bestämma tiden det tar att skicka ett datagram fram och tillbaka mellan två enheter, (round-trip-time RTT). Timestamp request kan också anvädas för synkronisera två enheters klockor. Mottagaren skickar **timestamp reply** (Typ=14)
3. **Address-mask requst** (Typ 17) skciaks av en värddator som inte kan sin [[IPv4#Klasslös adressering (classless addressing)|IP-Mask]]. Om värddatorn vet adressen till sin närmaste router skickar den meddealndet dit, annars skickas meddelandet som broadcast. En router tar emot meddelandet och svarar med **address-mask reply** (typ 18)
4. **Router solicitation** (Typ=10) kan användas av en värddator för att kolla om dess routrar fungerar. Meddelandet kan skickas i broadcast eller multicast. En router som tar emot meddelandet skickar **router advertisement** (Typ=9) i brodcast. En router kan även göra detta med jämna mellanrum utan att en värddator ber om det







































