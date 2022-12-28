LTE står för **Long Term Evolution** och tillhör fjärde generationens (4G) 
mobilsystem. LTE är ett all-IP system vilket betyder att all data är [paketförmedlade]({{< ref "Paketförmedlad dataöveföring" >}}) och varje terminal har en [IP-adress]({{< ref "IPv4#adressering" >}}). Tillskillnad från GSM/UMTS är LTE inte i första hand utveckalt för telefoni, utan för Internettrafik. Det går inte att använda LTE för normal kretkopplad telefoni. Man måste istället använda VoIP lösning eller GSM/UMTS-nätet.

# Accessnätet
Accessnätet i LTE kallas för evolved UMTS Terrestial radio access network (e-UTRAN) och har ett helt nytt radiogränssnit jämfört med UMTS. 
![IMG_0050.jpeg]({{< ref "IMG_0050.jpeg" >}})

För att optimera bithastigheterna i olika mijöer finns det olika sorters celler i LTE. Macroceller täcker en större yta, från 1km i diameter som kan användas i städer till 100km i diamter som kan användas på landsbyggden. Det finns piko- och femotceller som är mycket mindre, kanske bara några tiotals meter i diameter och kan användas inom en byggnad för att få hög bithastighet. 

LTE kan använda alla frekvensband som är standardiserade för GSM och UMTS. De lägrre frekvensera är till för användas på landesbygden (tillsammans med större celler), och de högre frekvensera i städer (tillsammans med mindre celler).

# [Kärnnätet]({{< ref "Kärnnät" >}})
[Kärnnätet]({{< ref "Kärnnät" >}}) för LTE kallas för Evolved packet core (EPC) och består huvudsakligen av de noder som visas i [bild](obsidian://open?vault=Obsidian%20Vault&file=Datorkom%2FKapitel%2013%20-%20Telekommunikation%2Fattachments%2FIMG_0050.jpeg) ovan.

- **Mobility Management Entity (MME)** tar hand om styrning och kontrollen av användare och sessioner, tillexempel autitsering och hanteringen av terminalers geografiska placering och mobilitet (så kallade location update). 
- MME kommunicerar med [HSS]({{< ref "Introduktion till cellulära system#home-subscriber-server-(hss)" >}})
- **Serving gateway (SGW)** tar hand om sessionerna om en terminal måste byta från LTE till GSM/UMTS. 
- **Packet data network gateway (PDNGW)** fungerar som gateway mot Internet och andra datanät


# Telefoni över LTE
LTE innehåller inte kretskopplad telefoni som GSM/UMTS gör, utan telefoni måste tillhandahållas på något annat sätt. De finn två metoder för destta

## Circuit Switched Fallback
Detta innebär att telefonsamtal från/till LTE kopplas via GSM/UMTS. 
![IMG_0051.jpeg]({{< ref "IMG_0051.jpeg" >}})

## Voice over LTE (VoLTE)
Detta är ungefär som vilket annat internet baserat röstprotkoll, typ skype. Enda skillnaden är att det är operatören som ger ut det. Tanken är att detta skall möjligöra videosamtal och HD-kvalite på ljudet.

