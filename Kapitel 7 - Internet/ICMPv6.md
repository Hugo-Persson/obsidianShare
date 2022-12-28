ICMPv6 har samma syfte som [ICMP]({{< ref "ICMP - Internet Control Message Protocol#icmp-" >}}) men skilljer sig till viss del i funktionalitet. ICMPv6 har man även inkluderat funktionalitet av [ARP-Address Resolution Protocol]({{< ref "ARP-Address Resolution Protocol" >}}) och **IGMP**.

Det finns fortfarande två typer av meddelanden [#Felmeddelanden]({{< ref "#felmeddelanden" >}}) och [#Förfrågningar]({{< ref "#förfrågningar" >}}) 

## Felmeddelanden
Det som skiljer sig från [ICMP - Internet Control Message Protocol#Felmeddelanden (Error reporting messages)]({{< ref "ICMP - Internet Control Message Protocol#felmeddelanden-(error-reporting-messages)" >}}) är att **Source Quence** har tagit bort eftersom andra funktionaliteter i IPv6 tar hand om detta.

**Packet too big** är ett nytt felmeddelanden och skickas när en router tar emot ett meddelande som är för stort för nästa nät. 
## Förfrågningar
Det som skiljer sig från [ICMP - Internet Control Message Protocol#Förfrågningar (query messages)]({{< ref "ICMP - Internet Control Message Protocol#förfrågningar-(query-messages)" >}}) är att **Timestamp request** och 
**Address-mask request** har tagits bort eftersom andra funktioner i IPv6 tar hand om detta. 

Två förfrågningar har lagts till för att kunna lösa [ARP-Address Resolution Protocol]({{< ref "ARP-Address Resolution Protocol" >}}) och **IGMP**. [#Neighbor solictation]({{< ref "#neighbor-solictation" >}}) och [#Neighbor advertisement]({{< ref "#neighbor-advertisement" >}}). Båda dessa meddelanden ingår i [#Neighbor Discovery (ND)]({{< ref "#neighbor-discovery-(nd)" >}}) 

## Neighbor solictation 
En dator kan skicka ut denna requesten för att hitta fysiska adressen till en dator om man vet IP-adressen. Datorn som har IP-adressen svarar med [#Neighbor advertisement]({{< ref "#neighbor-advertisement" >}})

## Neighbor advertisement 
Skickas som svar på [#Neighbor solictation]({{< ref "#neighbor-solictation" >}}).

## Neighbor Discovery (ND)
En grupp av förfrågningar som innehåller
- [#Neighbor solictation]({{< ref "#neighbor-solictation" >}})
- [#Neighbor advertisement]({{< ref "#neighbor-advertisement" >}})
- Router advertisment 
- Router solicitation