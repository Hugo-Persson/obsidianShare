## Nättopologi

Hur olika nät kan vara uppbyggda, det finns buss, ring, stjärna och trådlöst nät. I ett bussnät så är alla terminaler kopplade til len lång kabel. I ett ringnät skickas signalerna från terminal till terminal i en slutden loop. i ett stjärnnät är alla terminaler kopplade till ett så kallat nätnav(hub) Nätavet ser till att alla data som skickas på nätet når samtliga terminaler. I ett trådlöst nät skickar terminalerna sin data på en förväg överenskommen radioknal, blir som en buss typ 

## Access till länken

För att terminaler ska kunna dela en länk så krävs regler för hur och när data får skickas på länken. Dessa regler kallas för accessmetod (medium access control, MAC) alla terminaler på länken måste använda samma MAC.

I trådlöst nät sker dataöverföring på ett visst frekvesnband, banden regleras av Post & telestryelsen (PTS) i Sverige. Det finns licencierade och icke licensierade band i Sverige. För att skicka data på licenserat band så måste man få licens från PTS. För icke licensierade kan vem som skicka data vilket skapar mycket störning

## Addressing

För att data som skickas över ett nät ska komma rätt så har varje terminal en unik address som data skickas till. Det finns också en ************broadcast************ address som används när alla terminaler ska få data. Det finns också en **********multicast********** address som används när flera enheter ska få data, man kan enheterna som ska få datan lyssnar då på multicast addressen

# Access metoder

<aside>
💡 En access metod beskriver hur terminaler får skicka data på en länk

</aside>

![Untitled](Grundprinciper%20%E2%80%94%20Access%20till%20na%CC%88t%209f9a815d8a5c4c7dbc5a773676ba11aa/Untitled.png)

### Controlled

I denna typ så finns det regler som bestämmer en turordning som alla terminaler måste följa för att få skicka. Denna turordning kan regleras av varje terminal själv eller av en central enhet så som server eller basstation. Detta har fördelen att inga kollisioner sker

### Contention based

I denna typ finns det ingen turordning och inga terminaler bestämmer över någon annan. Istället så gör varje terminal själv ett beslut om den ska skicka. Detta gör att det kan uppstår kollisioner och detta måste kunna hanteras. 

## Polling (master/slave)

I denna typ finns det två datorer, en primary och flera secondary. Primary datorn skickar ut ett så kallat POLL meddelande till Sekundärdator 1, om den har data så får den skicka datan om den inte har data svarar den med NO POLL. Sen så görs samma sak med näst sekundärdator

![Untitled](Grundprinciper%20%E2%80%94%20Access%20till%20na%CC%88t%209f9a815d8a5c4c7dbc5a773676ba11aa/Untitled%201.png)

Fördelen med detta är att inga kollisioner sker och den fungerar i alla topologier. Nackdelen är att det måste finnas en terminal som är primär dator vilket gör det med komplicerat samt att primär datorn kan faila vilket breakar hela nätet. 

## Token ring / Round robin

I denna typ så används en token som en staffettpinne. Om en terminal har staffettpinnen så har den tillåtelse att skicka data. Vi har fyra terminaler A,B,C,D, det fungerar så att om A har token så kan den skicka, den skickar då ett paket till C på länken. B och D kommer ta emot paketet men skiter i det och skickar vidare det på länken. När C tar emot paketet så skickar den det till sin applikation sen skickar på länken igen för att A ska se att den har tagit emot det. När A får paketet igen så vet den att C har fått paketet, den skickar då vidare token till B som sen gör samma sak.

Token kan vara ett paket med bestämt innehåll som alla terminaler vet hur det ser ut.

### Fördelar

- Alla terminaler får lika mycket tillgång

### Nackdelar

- Om bara en terminal vill skicka data så slösas tid då det tar tid att skicka runt token
- Det kan också bli problem om token förloras
- Det är också lite komplicerat att koppla in och ut enheter

## Reservation

I denna typ så fungerar det så att varje terminal kan reserva tillgång till kanalen i en viss tid. Om en basenhet finns så skickar terminalen en ********Request-To-Send******** (RTS) till basstationen, om det är fritt att skicka så svarar bassatationen med ***********Clear-To-Send*********** (CTS). Detta används i WiFi. Om ingen basstation finns så kan man dela upp tillgången till kanalen i tidsluckor, varje terminal har då möjlighet att reserva åtgång till kanalen en viss tid och under den tid kunna skicka.

## TDMA/FDMA

Veckar inte vara så viktigt

TDAM (Time Division Multiple Access) är en teknik är där terminaler turas om att skicka i tidsluckar.

FDMA (Frequence Divsion Multiple Access) är en teknik där det tillgängliga frekvensbandet delas upp till olika kanaler.

Code Division Multiple Access (CDMA) som gör det möjligt för många kanaler att skicka på en och samma frekvens med hjälp Direct Sequence Spread Spectrum (DSSS)

## CSMA/CD

I detta protokoll så är alla terminaler kopplade till en buss, alla terminaler lyssnar på alla paket som skickas men ignorerar paket som inte skickas till den. Alla paket skickas i båda riktningarna och i kanterna finns dämpare som stoppar paket från att speglas. Detta gör att alla terminaler vet när länken är ledig och kan då skicka paket. Det finns ingen turordningen istället kan alla enheter skicka paket när de vill om länken är ledig.

Kollisioner kan uppstår om två terminaler vill skicka data exakt samtidigt. För att en terminal ska veta om kollision uppstår så lyssnar terminalen på länken medans den skickar, om en kollision uppstår så kommer amplituden vara hög när paketen krockar. Om en sändare märker en kollision så slutar den genast att skicka data. Efter en kollision väntar sändaren en viss tid och försöker sedan skicka igen, blir det kollision igen dubbleras tiden som den väntar och så vidare, detta kallas ********************exponential back off********************. Tiden som en terminal väntar väljs slumpmässigt med visst medelvärde. Detta gör att terminaler som var med i en kollision inte kommer vara det igen med stor sannolikhet.

### Fördelar

- Om bara en terminal vill skicka data så kan den få hela länkens kapicitet
- Man kan lätt koppla på och av en terminal

### Nackdelar

- Om flera terminaler börjar sända samtidigt finns det ingen turordning vilket skapar många kollisioner

## CSMA/CA

Detta protokoll fungerar ungefär som [CSMA/CD](https://www.notion.so/CSMA-CD-0ccf796eaa584640b93417859d1cc682) skillnaden är att detta är anpassat för trådlös överföring.

När kollisioner sker vid trådlös överföring så ökar inte amplituden utan dämpas istället.

Man kan införa olika prioriteringar med detta protokoll, läs mer här om det behövs

[https://en.wikipedia.org/wiki/Carrier-sense_multiple_access_with_collision_avoidance](https://en.wikipedia.org/wiki/Carrier-sense_multiple_access_with_collision_avoidance)