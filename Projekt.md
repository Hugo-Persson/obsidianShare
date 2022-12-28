## Jämförelse med andra standarder

Det finns redan en del andra standarder och protokoll vars syfte är likt Matter, två av dessa konkurrenter är Zigbee och Z-Wave. Nedan jämförs Matter mot dessa.

  

### Zigbee

Zigbee är en kommunikationsstandard som släpptes först 2003 och var uppdaterat 2006. Zigbees nyckelfunktioner är låg strömförbrukning. För att uppnå detta så har Zigbee låg dataöverföring och kort räckvidd. Meshnätverk används för att göra det möjligt för att information att överföras över större avstånd. 

Alla Zigbee nätverk har en Coordinator och Zigbee enheter är antingen en router eller en end device (bok s 291). En coordinator är den nod som startade nätverket och kopplat nätet ut på internet eller till annat Zigbee nät. En router har syftet att föra vidarebefordra signaler från andra noder. Detta gör det möjligt för data att överföras över stora avstånd då datan kan passera flera routrar på nätet för att nå Coordinatorn. En router kan till exempel vara en enhet som har tillång till el. En end device går på battero och vill därför vara så energisnål som möjligt, enheten kan stänga av sig när den inte har data att skicka. Data skickas från end devices till routrar eller coordinators. 

### Jämfört med Matter
Zigbee har liknande användningsområden till Matter (Wiki). Zigbee är bäst jämfört med Thread vilket är ett nätverks protokoll som Matter använder sig av. Båda protokollen är meshnätverk med liknande egenskaper. 


En av de största skillanden mellan Thread och Zigbee är att Thread använder sig av [IPv6]({{< ref "IPv6" >}}) vilket öppnar möjligheter för naturlig kommunikation med andra [IPv6]({{< ref "IPv6" >}}) nätverk så som WiFi. Zigbee däremot använder ett helt nytt protkoll (texas inst). 

Matter har ingen single point av failure tillskillnad från Zigbee, läs mer om detta under teknisk information. 




![Pasted image 20221126142439.png]({{< ref "Pasted image 20221126142439.png" >}})
### Z-Wave
Z-Wave skapades 1999 och har liknande egenskaper och användingsområden till Matted. Z-Wave använder sig av ett meshnätverkt likt Zigbee och Thread.  



Z-Wave använder frekvenser under 1 GHz vilket gör att trafiken inte kolliderar med WiFi trafik medans Thread använder 2.4 GHz band som kolliderar med WiFi (WiFi).

Både Z-Wave och Matter erbjuder en Certifiering process av enheter medans Zigbee inte erbjuder detta (wave alliance). Denna certifieringen kostar pengar vilket gör enheter dyrare för Matter och Z-Wave jämfört med Zigbee men enheterna funkar bättre med varandra jämfört med Zigbee. 

[https://www.the-ambient.com/guides/matter-smart-home-explainer-guide-2676](https://www.the-ambient.com/guides/matter-smart-home-explainer-guide-2676)

[https://www.androidauthority.com/matter-smart-home-protocol-3082804/](https://www.androidauthority.com/matter-smart-home-protocol-3082804/)

[https://en.wikipedia.org/wiki/Zigbee](https://en.wikipedia.org/wiki/Zigbee)
https://e2e.ti.com/blogs_/b/process/posts/thread-vs-zigbee-what-s-the-difference

https://sdomembers.z-wavealliance.org/document/dl/388