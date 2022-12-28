TCP är det transportprotokoll som används när man vill vara säker på datan som man skickar kommer fram. Den har felhantering inbyggt.

# Segmentformat 
Data som kommer från applikationen delas upp i block så kallade segment och överförs sedan till mottagaren. TCP överför datan som en ström av bytes.

## Header format
![IMG_0041.jpeg]({{< ref "IMG_0041.jpeg" >}})
![IMG_0042.jpeg]({{< ref "IMG_0042.jpeg" >}})
![IMG_0043.jpeg]({{< ref "IMG_0043.jpeg" >}})

# TCP- förbindelse
TCP anvnder sig av en [Förbindelse orienterad överföring]({{< ref "Paketförmedlad dataöveföring#förbindelseorienterad-dataöverföring" >}}) överföring. Eftersom IP är [Förbindelse fri]({{< ref "Paketförmedlad dataöveföring#förbindelsefri-dataöverföring" >}}) så sparar TCP alla segment och sorterar dem innan de levereras till applikationen. Innan någon data kan överföras måste [#Uppkoppling av TCP-förbindelse]({{< ref "#uppkoppling-av-tcp-förbindelse" >}}) ske.

## Uppkoppling av TCP-förbindelse
TCP använder sig av en så kallad handskaningsproceduer för att sätta upp en förbindelse. Uppkopplingen går till så här
![IMG_0044.jpg]({{< ref "IMG_0044.jpg" >}})
I bilden så markerar vi ena datorn som "Dator 1" och andra som "Dator 2", detta är bara under uppkopplingen. Efter uppkopplingen så sker överföringen i full duplex och man kan inte skilja på datorerna. 

1. Uppkoppling börjar med dator ett skickar ett paket med SYN flaggan satt till 1 och ett start sekvensnummer x
2. Dator två svarar med ett paket med SYN som har sitt inledande sekvensnummer y och skickar ACK som svar på dator 1 med sekvensnummer x+1
3. Dator 1 tar emot detta och vet nu att sitt SYN meddelande funkade, den svarar nu med ACK till dator 2 SYN meddelande

## Nedkoppling av TCP-förbindelse
Båda parterna i en TCP-förbindelse kan stänga ner för bindelsen. Detta görs via en handskaknings process, se bild.

![IMG_0045.jpeg]({{< ref "IMG_0045.jpeg" >}})

Observera att vi ser detta som två kopplingar. När Dator 2 får FIN så vet den att Dator 1 inte skickar något mer och den uppkopplingen är klar. Dator 2 kan ändå skicka saker till Dator 1. Detta kan vara användbart på webben när klienten inte skickar något mer till servern.

# Dataöverföring
TCP överför data med hjälp av buffrar, se bild. Data lagras i sändbuffern till de kan bli skickade med ett TCP segment. De ligger sedan kvar i buffern till de blivit ackade. Den maximala mängden data TCP skickar i ett segment är **Maximum segment size (MSS)**. 

På mottagar sidan läggs segmenten i en buffer, de levereras sedan till mottagaren vid lämpligt tidpunkt. Inkommande segment sorteras i rätt ordning. Det finns en sänd och mottagar buffer samtidigt

![IMG_0046.jpeg]({{< ref "IMG_0046.jpeg" >}})

### Snabba upp en överföring
I TCP finns det en funktioner för att snabba upp överföring av högprioriterad data. Ett TCP-segment med URG flaggan satt till 1 kommer hos mottagaren inte läggas i buffern, den kommer istället skickas direkt till mottagaren. Om URG är satt till 1 behöver även Urgent Pointer innehålla sekvensnumret till den sista data byten i det segment som är högprioriterat. Detta gör det möjligt att skicka högprioriterat och icke hörprioriterad data samtidigt. 

# Felkorrigering

TCP använder sig av en så kallad [AQR]({{< ref "Felhantering" >}})-algoritm och bygger på [Go-Back-N]({{< ref "Felhantering#go-back-n-arq" >}}). I TCP är sändföntret dynamisk vilket är en del av TCP:s flödeskontroll. Sändförnstrets storlek är minimum av två värden: **rwind** (reciever window) och **cwnd** (congestion window). Värdet på **rwind** bestäms av mottagaren (fältet Fönsterstorlek). Värdet på **cwind** bestäms av sändarens flödeskontroll.

Om inga fel uppstår så fungerar det som nedan
![IMG_0047.jpeg]({{< ref "IMG_0047.jpeg" >}})

## Omsändningar
För att detekera förlorade paket så används två principer, [Felhantering#Timeout]({{< ref "Felhantering#timeout" >}}) som kallas **retransmission time-out (RTO)** i TCP. [Felhantering#Duplicerad ACK]({{< ref "Felhantering#duplicerad-ack" >}}) används också.

Se [Felhantering#Go-Back-N ARQ]({{< ref "Felhantering#go-back-n-arq" >}}) för mer info.

