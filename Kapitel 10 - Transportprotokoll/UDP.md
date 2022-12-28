UDP är ett transportprotkoll som erbjuden **best effort-dataöverföring** vilket betyder att ingen felhantering finns. Saker skickas och så hoppas man på det bästa. Nedan är några standard portar som används av UDP
| Port | Protkoll   | Förklaring                         |
| ---- | ---------- | ---------------------------------- |
| 53   | Nameserver | Används av DNS                     |
| 67   | Bootps     | DHCP, server                       |
| 68   | bootpc     | DHCP klient                        |
| 69   | TFTP       | Trivial File Trasnfer Protocol     |
| 123  | NTP        | Network Time Protocol              |
| 161  | SNMP       | Simple NEtwrok Management Protocol |
|      |            |                                    |

# Datagramformat
UDP är ett meddelande-orienterat protkoll (message-oriented-protocol) vilket betyder att data skickas i form av meddelande. När en applikation lämnar över data till UDP så läggs bara en liten header till på **8 byte** och sen så lämnas datan över till nätprotokollet.

## Headerformat
Headern ser ut som på bilden nedan, förklar för varje del är:
- Sändarens portadress: Port till den applikation som skickat datagrammet
- Mottagarens portadress: Port till den applikation som ska få datagrammet
- Längd: Totala längden på datagrammet, header+data i bytes
- Kontrollsumma: En 16 bitars kontrollsumman som beräknas i UDP. Kontrollsumman beräknas på UDP data och header samt några headers i IP headern. Dessa är sändare och mottagar adresser samt protkollfältet. Anledningen varför UDP använder IP headers är för att detektera om det skickats till fel mottagare eller fel protkoll används.
![IMG_0040.jpeg]({{< ref "IMG_0040.jpeg" >}})