För att mottagaren ska kunna identifiera vilket paket som har kommit bort så har varje paket ett `sekvensnummer`.

## ACK
En grundläggande del av omsändningsalgoritm är ACK används, ACK betyder att varje paket som har kommit fram bekräftas av mottagaren, detta gör genom att mottagaren skickar ACK X där $X-1$ är sekvensnummret för det paket som har kommit fram. När ACK 5 skickas så säger mottagaren att jag är redo för paket 5, detta kommer efter paket 4 kommit fram. 
### Duplicerad ACK
Ifall vi får ACK 5 två gånger så kan sändaren förstår att ett paket har förlorats då vi ber om samma paket två gånger. Exempelvis om paket 5 har förlorats så svarar mottagaren med ACK 5 när paket 6 kommer in då vi vill ha paket 5.

## NAK
Mottagaren kan också skicka NAK X vilket innebär att ett paket har gått förlorat

## Timeout

Om ACK för ett visst paket inte kommer inom en viss tid så antar sändaren att ett paket gått förlorat, då skickas paketet igen. Timeout tiden sätts som den maximala tiden det kan ta för mottagaren att få ett paket och skicka ACK.


## Olika protocol

### Stop-and-Wait ARQ

Stop and wait går ut på att ett paket skickas först sen väntar bekräftelse på detta paket innan nästa paket skickas. När detta paket tagits emot så skickas en ACK och nästa paket kan skickas. I bilden kan vi se att Paket 0 skickas och mottagaren tar emot det och skickar ACK 1 vilket betyder att paket med sekvens nummer 0 har tagits emot. Då skickar sändaren paket 1, paket 1 går förlorat först så efter time-out så skickas det igen och får då ACK. Vi behöver bara en bits sekvensnummer i detta protocol.
![[Pasted image 20221118145545.png]]
### Go-Back-N ARQ

I detta protokol kan flera paket skickas samtidigt, och sändaren behöver inte vänta på att ett paket ska bli bekräftat innan den skickas nästa. Vi använder istället ett sändfönster (sliding window) för att hålla reda på vilka paket som ska skickas och vilka som är bekräftade. Paket till vänster om sändfönstret är bekräftade, paket inom sändfönstret får skickas och de höger om sändfönstret får inte skickas än.
![[Pasted image 20221118145600.png]]

Vi har en sändfönsterstolek vilket indikerar hur många paket som får finnas i sändfönstret på en gång vilket är hur många obekräftade paket som får skickas på en gång.

Om alla paket kommer fram ser det ut så här
![[Pasted image 20221118145615.png]]
När ett sändaren får bekräftelse för ett paket så kan den öka sändfönstret med 1
![[Pasted image 20221118145631.png]]
### Selective repeat ARQ

Detta protocol är en variant av Go back N AQR

Skillnaden är att mottagaren skickar NAK när den får ett paket som kommer efter ett annat paket, i vårt fall när paket 3 kommer innan 2. Sändaren kan då direkt skicka om detta paket. I detta fall så får vi max har sändfönster som är hälften så stors som största sekvensnumret