Ett problem med IPv4 är att vi inte har nog med adresser. Det kan delvis lösas med NAT. NAT gör så att alla datorer på ett internt nätverk delar på en extern adress. Idag används NAT även på hela operatörs nätverk med så kallad **Carrier Grade NAT**.

Tre grupper av IP-adreser är reserverade för privata nätverk

| Adressmängd                 | Antal | 
| --------------------------- | ----- |
| 10.0.0.0-10.255.255.255     |       |
| 172.16.0.0-172.31.255.255   |       |
| 192.168.0.0-192.168.255.255 |       |



## Hur fungerar NAT?
Översättningen mellan externa och interna adresser sker i en NAT-router (tillexempel [Default Gateway]({{< ref "Default Gateway" >}})). När en dator skickar ett paket till en extern adress så sparar NAT-routern källadressen och den externa adressen i en tabell. När sedan mottagaren svarar så kan NAT-routern kolla i sin tabell efter vem som skickat till denna externa mottagaren och skicka vidare meddelandet dit.
## Problem med NAT
- Om man kör en egen server på sin dator som behöver en publik IP för kunnas nå så får vi problem
- TCP:s och UDP:s kontrollsummor beräknas på TCP eller UDP-headern. Så när en router ändrar adressen på ett paket till den interna adressen så måste den beräkna om kontrollsummor för IP-headern och TCP/UDP headern
- Två datorer kan inte prata med samma externa adress samtidigt. Vår router kopplar en extern adress till en intern adress men om två interna har samma externa så skrivs de över. Detta kan delvis lösas genom att ha flera externa adresser och med [PAT - Port Adress Translation]({{< ref "PAT - Port Adress Translation" >}})

