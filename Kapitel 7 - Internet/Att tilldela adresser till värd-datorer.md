Det finns tre principer för hur datorer på ett nät ska få sina [ IPv6 adresser]({{< ref "IPv6#adressering-" >}}) och [ IPv4 adresser]({{< ref "IPv4#adressering-" >}})
1. Få en adress manuellt satt 
2. Fråga en databas om den med hjälp av [ DHCP]({{< ref "#dynamic-host-configuration-protocol-(dhcp)" >}}) för IPv4 och [#DHCPv6]({{< ref "#dhcpv6" >}}) för IPv6
4. Datorn själv sätter den

# Dynamic Host Configuration Protocol (DHCP)
DHCP används av en dator för att få en IP-adress, få information om var närmaste router som kopplar ut mot internet är ([Default Gateway]({{< ref "Default Gateway" >}})) samt få veta var närmaste [DNS-server]({{< ref "DNS-server" >}}). När en dator kopplar upp sig så går den igenom [#Bootstrap process]({{< ref "#bootstrap-process" >}})

## Bootstrap process
Processen Fungerar typ så här
1. Host -> DHCP-Server, DHCP-Discovery skickas till alla DHCP-Servrar för att hitta en server
2. En DCHP-Server svarar med DCHP Offer som innehåller en IP adress och annan information
3. Host -> DHCP-Server, DCHP request skickas där datorn ber om tillstånd att använda en adress. 
4. DCHP-Server -> Host, DHCP Acknowledgement skickas som get datorn tillstånd att använda IP-Adressen en viss lease time
5. När halva lease tiden har gått så ber datorn om att förlänga tiden genom en re-lease request

![Note 18 Nov 2022.png]({{< ref "Note 18 Nov 2022.png" >}})
# DHCPv6
I IPv6 används detta protokollet som har delvis samma funktion som DHCP. Det finns två sätt att få en IP-Adress [#Statelss Autoconfiguration]({{< ref "#statelss-autoconfiguration" >}}) och [#Stateful Autoconfiguration]({{< ref "#stateful-autoconfiguration" >}}).

## Statelss Autoconfiguration
Detta är ett sätt för datorn själv att kunna be om en adress. Datorn sätter då själv vilken adress den vill använda men den måste ändå checka så ingen annan använder denna adressen. Den gör detta på följande sätt
1. En förfrågan ICMPv6 Neighbor Solicitation skickas ut på nätet
2. Om någon annan dator på det lokala nätet redan har den förslagna adressen skickar denna ut en ICMPv6 Neighbor Advertisement.

## Stateful Autoconfiguration
Detta fungerar ungefär som i [#Dynamic Host Configuration Protocol (DHCP)]({{< ref "#dynamic-host-configuration-protocol-(dhcp)" >}}) men använder några specifika adresseringstyper och funktioner som är definerade för IPv6.
