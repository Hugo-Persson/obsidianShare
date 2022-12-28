Med VLAN kan en switch konfigureras så att några portar hör till ett VLAN medans andra ett annat VLAN. En dator kopplad till ett VLAN märker inte detta och för den är det som den är ansluten till ett LAN. Broadcast meddelande skickas endast inom ett VLAN. Fördelen med VLAN är att det är enkelt att konfigurera. Om en terminal ska byta VLAN så är det bara att konfigurera om switchen.

![Pasted image 20221116082252.png]({{< ref "Pasted image 20221116082252.png" >}})

### Tagged VLAN

Det finns så kallade taggade VLAN. I taggade VLAN markeras varje ram med vilket VLAN det tillhör. Sedan kan switchen skicka vidare ramen på de utgående portal som associaras med det VLAN:et. Detta gör det möjligt för flera VLAN att dela en länk mellan två switchar.

I IEEE 802.1.q så görs detta med hjälp av TPID (Tag protocol identifier) och tag control information (TCI). TPID är alltid satt till 0x8100 och används för att identifiera att ramen använder sig av 802.1q. TCI innehåller tre fält Priority Code Point (PCP), Drop Eligable Indicator (DEI) och VLAN identifier (VID).

-   PCP är ett tre bitar fält som används för prioritering av trafik.
-   DEI är en bit som indikerar om ramen kan kastas om det är överbelastning på nätet
-   VID är själva identifieringen aav vilket VLAN ramen tillhör, 0x000 används om ingen VLAN används. 0xFFF är reserverat vilket betyder att det kan vara upp till 4094 olika VLANs
![Pasted image 20221116082302.png]({{< ref "Pasted image 20221116082302.png" >}})