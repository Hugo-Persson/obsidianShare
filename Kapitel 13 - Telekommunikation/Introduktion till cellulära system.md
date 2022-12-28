I detta dokument så beskrivs några generall begrepp och principer som rör alla cellulära system (mobilnät)

# Frekvensband och kanalder
För att inte alla mobilasystem ska störa ut varandra så finns det reserverade frekvensband för olika system. I sverige förvaltas frekvensbanden av [[PTS - Post och telestyrelsen]]. De flesta frekvensbanden är licensierade vilket betyder att den som vill använda dem måste ha en licens. Det finns licensfria band t.ex för **bluetooth** och [[Trådlöst LAN (WLAN, IEE 802 11|WLAN]]. 

En mobiloperatör delar upp sitt frekvensband med någon multiplexingeringsmetod. Det måste alltid finnas en broadcast kanal, alla andra kanaler är till för dataöverföring och signalering. När en mobil kopplas upp måste den lyssna på broadcast kanalen först.  


# Celler 
Det mobila accessnätet är geografiskt indelade i celler där en cell är den basytan som täcks av en bassationer (base station BS). BS innehåller utrustning för att skicka och ta emot data. Ofta kan en BS ha tre celler där den har tre antenner som riktas åt olika håll. Flera BS kan styrasfrån en kontrollenhet ( base station controller, BSC).Högre frekvenser dämpas snabbare än lägre, därför beror cellernas storlek på vilket frevensband som används.


![[IMG_0048.jpeg]]

Varje cell får ett visst antal frekvens, celler som ligger nära varandra kan inte ha samma frekvenser. Om cellen ligger i ett tättbebbyggt område där mycket trafik kommer ske så måste cellens yta begränsas. Frekvenser återanvänds i speciellt mönster för att minimera störningar, se bild nedan:
![[IMG_0049.jpeg]]

# Access till nätet
Det finns olika sätta att dela upp frekvensbandet i cellen i kanaler som användare kan utnytja, så kallade [[Access till nät#Access metoder|Access metooder]]. Det gemensamma är att basstationen bestämmer bem som får tillgång till vilken kanla vi vilken tidpunkt, dvs accessmetoder är [[Access till nät#Controlled|Controlled]]. Det brukar också finnas en broadcast kanal som bara basstationen får skicka på. 

# Home Subscriber Server (HSS)
En viktig del av alla mobila nätverk är HSS. HSS lagrar all abonenntdata, varje gång en bonnent sätter på sin mobiltelefon, byter cell, byter nät, ringer elelr skickar data, görs ett anrop till databnasen för att få information om till exempel betalning eller uppdatera informationen om var mobilen är. När någon ringen till en telefon sker ett anrop (paging) till denna abonnenten, HSS används för att lokalisera telefonen för kopplar allt rätt. 
# Hand-over
När en telefon rör sig mellan [[#Celler]] så måste telefonen byta basstation och kanal. Denna procedur kallas **hand-over** eller **handoff**. För att vetan när en **handoff** ska ske så mäter telefonen alltid signalstyrkan, telefonen rapporterar sina signalvärden till mobilnätet som sedan bestämmer när **handoff** ska ske. 

I dagenmobilnät används **sof handover** där mobilen är uppkopplad till gamla och nya basstationen samitidgt. Koppling till gamla bryts när första biten till nyta kommer in.
# Roaming
En operatör har ofta täckning över ett land, t.ex sverige. När vi rör oss utomlands behöver vi använda en annanns operatörs nät. Operatörer har roaming avtal mellan varandra för att detta ska gå. Roamingavtal bestämmer ekonismka förutsättningar för detta. I EU så måste roamingavtalet ha samma vilkor som hemma. 


# SIM-kort
För att en telefon skall fungera behövs en giltig Subscriber Identity Module, ett SIM-kort. Det innehåller information kring vilket abonnemang den är knuten till samt  säkerhetsfunktioner. En avonnent identifieras genom sin så kallade International Mobile SUbscriber Identity (IMSI-nummer). IMSI-numret är unikt för varje SIM-kort. IMSI-numret består av 
- en landskod på 3 siffror
- Operatörskod på 2 siffror
- Samt 10 siffrigt löpnummer

Genom IMSI-numret kan en abonent använda sin telefon överallt i världen där det finns en operatör som har [[#Roaming]] avtal med operatören hemma.

# Talkodning
Idag använder de mobila näten mer avancerade kodnigntekniker än [[PCM]] som gör att bithastigheten kan reduceras kraftigt samtidigt som talkvaliten förbättras. Det människliga talet innehåller massa redundant information. Man kan till exempel använda en matematisk modell av de mänskliga talet när man kodar.



# Telefonnummer
Alla telefonnummer i hela världen är uppbyggda enligtt en internationell standard E.164, som gör det möjligt att ringa till en abonnent oavsett var i värden hen befinnser isg. I Sverige är det [[PTS - Post och telestyrelsen]] som ansvarar för alla telefonnummer. I Sverige har alla mobila telefonnummer något at prefixen 070, 072, 073, 076 eller 079.