För att slippa skriva IP-adressen till t.ex google så finns DNS som översätter google.com till 216.58.207.238 (du kan checka en sida med `nslookup google.com`. 

DNS bygger på en globalt distruberad databas, och varje organisation som har egna Internetadresser måste ha minst två oberoende DNS-system i drift. 

Vad menar dom med org som har egna internetadresser? #förstår-inte 

# Domäner
Varje domän får sin egen kod sedan kan ha en subdomän till sig. Man kan se detta som ett träd, se bild. 
![[IMG_0039.jpg]]

Det finns två typer av domäner **geografiska (dountry domain)** och **organistatoriska (generic domain)**. Varje land har en egen geogrisk domän, t.ex Sverige har se. 

Registering av nya domäner sker av specilla organisationer, så kallade registrar, som är godkända av [[Internet Corporation for Assigned Names and Adresses (ICANN)]]. För att registrera en ny domän anmäler man domännamnet till en registrar. Om domännamnet är unikt och en avgift betalas registrar namnet i DNS-databasen. 

Man kan också få hjälp med tjänsten DNS-server för sin domän om man inte själv kan tillhandahålla en sån. #förstår-inte 

# Översättning av domän till IP
DNS-servers hanterar själva översättningen från domän till IP-adress och från IP-adress till domän. DNS-servers hanterar även uppgifter om adressen till den mailserver som hanterar e-post för en viss domän.

# DDNS - Dynamic Domian Name System
Usprungligen hanterades uppdatering av vilka adresser som gick var på DNS-server manuellt. Detta går inte idag när vi har så många domäner som registeras. Man har infört DDNS för att dynamiskt uppdatera servern. Det fungerar så att DHCP servern i den aktuella domänen skickar ett meddelande til lsin primära DNS-server. DNS-servern snvarar sedan för att databasen uppdateras och att andra berörda DNS-servers blir meddelade. Detta gör att alla DNS-server uppdateras i realtid.

# Övergång från [[IPv4]] till [[IPv6]]

DNS-servers kan spara både [[IPv4#Adressering]] och [[IPv6#Adressering]]. För att skilja på dem och låta datorer fråga om en spefik så har vi två olika poster i DNS-servers, **A-records** används för IPv4 och **AAAA-records** används för IPv6. Om en dator ber om A-record och den inte finns så hanteras det som att domänen inte är registerad. Om en dator inte specifierar typ av record så får den i förstahand **AAAA-records**, om den inte finns så får den **A-records**. I vanligt tal kallas **AAAA-records** för **quad A**.

