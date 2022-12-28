Internet of Things (IOT) är ett brett område som innefattar många applikationer och tillämpningar. IOT brukar vara system med många uppkopplade enheter med låg energiförbrukning.

Två typer av standarder brukar användas för IOT

# Low Power Wide Area Network (LPWAN)
Störa utmaningen för enheter i IOT är att kunna skicka data över stora avstånd medans de inte konsumera mycket energi. WPAN är en typ av standard som riktar sig mot IOT enheter som kräver låg energikonusumtion. LPWAN ger nät med låg energifröbrukning, låga kostnader och relativt stora avstånd (några kilometer). 

För att ge låg kostnad och hög räckvidd så har näten låg [[Bandbredd]], runt 0.3-50 kbps per kanal jämfört med fast telefoni som har 64kbps.

En generell systemarkitekt tur för LPAN kan ses nedan. Det finns ett antal enheter som är kopplade mot en gateway. Data lagras och behandlas i applikationen vilket gör enheterna väldigt applikationsberoende. 
![[IMG_0052.jpeg]]

## Long Range WAN (LoRaWAN, LoRa)
LoRaWAN är en standard för LPWAN som ger dataöverföring med låg energiförbrukning och lång räckvidd och låg [[BER - Bitfelsfrekvens]]. Nackdelen är att LoRaWAN inte har hög [[Bandbredd]] eller låg fördröjning. 

LoRaWAN använder en modulationsteknik som kallas Long Range (LoRa) som använder sig av licensfria frekvensband på UHF och VHF banden (under 1 GHz).

LoRa använder sig av en teknik som kallas [[Chirp Spread Spectrum (CSS)]]. Denna tekniken användes även inom sonar och radar och ger en väldigt bra mottagarkänslighet vilket innebär att data kan uppfattas även vid mycket svaga signaler.

LoRa innehåller nät och MAC protokoll för kommunkation mellan enheter och dataservrar. #todo skriv kanske lite mer här

# Narrowband IoT ( NB-IoT)
NB-IoT kan sägas vara mobiloperatörerna lösning för [[#Low Power Wide Area Network (LPWAN)]]. NB-IoT standardaliseras av [[3GPP]] och körs i de cullulära näten. NB-Iot har även föreslagits i 5G för användasrscenariot [[5G]] i användarscenartio **Massive Machine Type Communcation**

NB-IoT använder sig av kanaler på 200 kHz som antingen kan ligga på oanvända [[GSM]]-frekvensband eller finnas inom [[LTE (4G)]]-banden. Upp till 50 000 enheter kan vara uppkopplade i samma [[Introduktion till cellulära system#Celler|cell]]. I NB-Iot är det alltid [[Basstation|basstationen]] som styr kommunikationen. För att en enhet ska kunna skicka data behöver den först koppla upp sig till [[Basstation|basstationen]]. Vid uppkoppling får enheten en tilldelad kanal som den sedan kan skicka data över. 

# Personal Area Network (PAN)
PAN är ett datanät som kopplar ihop enheter på korta geografiska avstånd (som ett [[LAN]]), både trådbundet och trådlöst. Det finns ett flertal standarder för trådlösa PAN som är tänkta för IoT-system, två stycken beskrivs här [[Bluetooth]] och [[Zigbee]]

