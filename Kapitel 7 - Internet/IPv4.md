# Adressering
En IPv4 address består av 32 bitar där varje byte ofta sepereras med en punkt, t.ex 192.168.0.1.
Varje IP-adress består av ett nät-id(net id) och ett värd-id (host id). Net id används av routrar för att skicka paketet till rätt nät. Varje router har en tabell över vilka nät net id som är kopplade till den. För att seperera net id från host id så finns det två tekniker, [Block routing - Klassindelad adressering]({{< ref "Block routing - Klassindelad adressering" >}}) och [CIDR - Klasslös adressering]({{< ref "CIDR - Klasslös adressering" >}}).





### Subnetting
Om vi har ett stort nät som vi vill dela upp i mindre nät så kan vi använda oss av subnets, med subnets så kan ett stort nätverk bli uppdelade i så kallade subnets. Man gör detta genom att ta en del av host id biten och sätta den till net id. ![Pasted image 20221225134319.png]({{< ref "Pasted image 20221225134319.png" >}})
![Pasted image 20221119131342.png]({{< ref "Pasted image 20221119131342.png" >}})
# IPv4 Header
Ett IPv4-paket kallas datagram och består av en header och nyttlast(datan som ska föras över). Förklaring för följande saker är
- Version (VER): Versionsnummer, 0100 för IPv4
- Header length (HLEN): Anger headerns längd
- Type of Service (TOS): Detta fältet innehåller information kring hur datagrammet ska skickas
- Total längd: Anger totalt antal bitar
- Identifikation: Detta innehåller ett sekvensnummer som kan identifiera paketet med source
- Falggor: Detta används när headern fragmanteras
- TTL: Time-to-live anger maximala antal routrar ett paket får skickas igenom.
- Protokoll: Detta anger vilket protkoll som används, tillexempel [TCP - Transmission Control Protocol]({{< ref "TCP - Transmission Control Protocol" >}}), [UDP]({{< ref "UDP" >}}), ICMP och IGMP
- Header checksum: Detta är en kontrollsumma som används på hela headern men inte payload
- Sändar-och-mottagaraddresser: IP-adresserna till sändaren och mottagaren av datagrammet
- Eventuella tillval: IPv4 Tillåter ett antal tillval, t.ex nätövervakning. Detta behöver inte finnas 
![IMG_0032.jpeg]({{< ref "IMG_0032.jpeg" >}})

| Värde | Protokoll |
| ----- | --------- |
| 1     | ICMP      |
| 2     | IGMP      |
| 6     | TCP       |
| 17    | UDP       |
| 89    | OSPF          |

# Fragmentering
TCP/IP modellen definerar inte de första media och länk lagret i OSI modellen. Detta betyder att paket kan röra sig igenom olika typer av nät som har olika protokoll i länklagret. Alla dessa olika protokoll har olika maximum transfer unit (MTU). När ett IP-datagram skall kapslas in i länkprotokollets ram får datagrammet längd inte vara större än länklagrets MTU. Om det är större så måste datan **fragmenteras**.

Hoppsättning (reassembly) av framenten görs endast host mottagaren. Eftersom IP är förbindelsefritt garanteras **inte** att fragmenten tar samma väg genom nätet. Mottagaren måste få alla frament innan den kan pussla ihop dem igen. 

När datagrammet framenteras kopieras alla fält i headern förutom 
- Flaggor
- Frament offset 
- Total längd

### Flaggor
3 bitar
- den första biten är reserverad
- Andra biten är "do not fragment" om 1 så får inte paketet fragmenteras
- Tredje biten "more fragments" betyder att fler fragment kommer

### Fragment offset
Ett fält med 13 bitar som indikerar fragmentets position relativa position i förhållande till resten av datagrammet