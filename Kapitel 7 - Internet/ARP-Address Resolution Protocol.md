**ARP** används för att hitta MAC-adressen för en dator om man vet IP-adressen för denna dator. **ARP** anses vara hjälp protokoll för IP och ligger mellan [OSI lager 2]({{< ref "OSI-Modellen#länklagret---nivå-2" >}}) och [OSI lager 3]({{< ref "OSI-Modellen#nätlagret---nivå-3-card" >}}). 
> Det finns ingen IP header när ARP används

Det finns två scenarion som kan uppstå när en dator ska skicka ett IP paket till någon annan, om en dator ska skicka till en annan dator så kan den direkt se på IP adressen om den är på samma nät.


**Vi kallar sändaren A och mottagare B nedan**
## Datorn finns på samma nät
Först så checkar A om B's ip finns i sin cache. Om den finns i sin cache så kan den skicka direkt till B då den redan vet MAC adressen. Annars så måste den ta reda på MAC adressen. Den gör det med hjälp av ARP på följande sätt
1. A skickar ut ARP-förfrågan (ARP request message)
2. B ser förfrågan och känner igen sin IP och svarar med ARP reply message, meddelandet har B's MAC
3. A får nu B's MAC och kan spara den i sin cache och skicka ett paket till B
## Datorn finns på annat nät
Om B finns på annat nät så vill A skicka ramen till sin [Default Gateway]({{< ref "Default Gateway" >}}). För att göra detta så måste den veta MAC till default gateway, den gör det på samma sätt som i [#Datorn finns på samma nät]({{< ref "#datorn-finns-på-samma-nät" >}}) fast B är nu default gateway. Sen skickar A sin ram. **OBS**: ramen som skickas har destination default gateway med själva IP paketet i har mottagare B.

## Skillnad mellan IPv4 och IPv6
I IPv4 så är ARP ett eget protkoll men i IPv6 är det en del av [ ICMPv6 -> Neighbor Discovery]({{< ref "ICMPv6#neighbor-discovery-(nd)" >}}). Principen är typ samma fast istället för att skicka broadcast som man gör i ARP så skickas Neighbor Solictation meddelande som ett multicast till mottagarens solicited-node adress. Den adressen kan sägas vara en multicast variant av mottagarens unicast-adress. 
