Det vi kallar Ethernet är ethernet 2

![Untitled](Untitled.png)

## Ramstruktur

![Untitled](Untitled%201.png)

- Preamble - 56 bitar synkroniserings fält
- Start Frame Delimiter (SFD) - Säger till mottagaren att data kommer
- Type - Vilket protokoll som överför ramen
- CRC är feldetekterings fält
- 

Most notably, an EtherType value of `0x0800` indicates that the frame contains an [[IPv4]] datagram, `0x0806` indicates an [[ARP-Address Resolution Protocol]] datagram, and `0x86DD` indicates an [[IPv6]] datagram.

Vanligt ethernet använder CDMA/CD som access metod

## Gigabit ethernet 802.3ab

Man har ett stjärnnät med en gigbabit switch i mitten. man kan ha upp till 1 Gbps i överföringshastighet.

CSMA/CD används inte som access protokoll. Den nya tekniken ger full duplex överföring. En ny funktion som heter forward error correction (FEC) används. Denna funktion kan korrigera bitfel genom att några extrabitar läggs till på smart sätt.

## Ethernet med högre hastighet

Det finns idag ethernet som kan ta upp till 100 Gbps, dessa används i stadsnät och kärnnät och använder sig av fiber.