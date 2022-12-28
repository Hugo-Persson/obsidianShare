ICMPv6 har samma syfte som [[ICMP - Internet Control Message Protocol#ICMP |ICMP]] men skilljer sig till viss del i funktionalitet. ICMPv6 har man även inkluderat funktionalitet av [[ARP-Address Resolution Protocol]] och **IGMP**.

Det finns fortfarande två typer av meddelanden [[#Felmeddelanden]] och [[#Förfrågningar]] 

## Felmeddelanden
Det som skiljer sig från [[ICMP - Internet Control Message Protocol#Felmeddelanden (Error reporting messages)]] är att **Source Quence** har tagit bort eftersom andra funktionaliteter i IPv6 tar hand om detta.

**Packet too big** är ett nytt felmeddelanden och skickas när en router tar emot ett meddelande som är för stort för nästa nät. 
## Förfrågningar
Det som skiljer sig från [[ICMP - Internet Control Message Protocol#Förfrågningar (query messages)]] är att **Timestamp request** och 
**Address-mask request** har tagits bort eftersom andra funktioner i IPv6 tar hand om detta. 

Två förfrågningar har lagts till för att kunna lösa [[ARP-Address Resolution Protocol]] och **IGMP**. [[#Neighbor solictation]] och [[#Neighbor advertisement]]. Båda dessa meddelanden ingår i [[#Neighbor Discovery (ND)]] 

## Neighbor solictation 
En dator kan skicka ut denna requesten för att hitta fysiska adressen till en dator om man vet IP-adressen. Datorn som har IP-adressen svarar med [[#Neighbor advertisement]]

## Neighbor advertisement 
Skickas som svar på [[#Neighbor solictation]].

## Neighbor Discovery (ND)
En grupp av förfrågningar som innehåller
- [[#Neighbor solictation]]
- [[#Neighbor advertisement]]
- Router advertisment 
- Router solicitation