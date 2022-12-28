I internet används 16-bitars portar, definierade som heltal mellan 0 och 65 535. Portar används för att definera vilken applikation ett paket ska till. Det finns tre typer av portar [#Standardportar (well-known ports)]({{< ref "#standardportar-(well-known-ports)" >}}), [#Registerade portar (registered ports)]({{< ref "#registerade-portar-(registered-ports)" >}}) och [[#Dynamiska portar (dynamic 
port)]].
![Pasted image 20221119135818.png]({{< ref "Pasted image 20221119135818.png" >}})
## Standardportar (well-known ports)
Dessa portar kontrolleras av [IANA]({{< ref "IANA" >}}). Det är portar för normala applikationer så som HTTP, SMTPR och så

## Registerade portar (registered ports)
Dessa portar kontrollers **inte** av [IANA]({{< ref "IANA" >}}) men man kan registera sin applikation för en av dessa portar för att undvika att andra applikationer använder dem. Detta är viktigt för att undvika kollisoner av portar.

## Dynamiska portar (dynamic port)
Dessa portar kan användas fritt av vilken applikation som helst

# Sockets
Socketts är en kombination av en IP-adress och en port. Sockets gör det möjligt för en dator att ha flera applikationer samtidigt då inkommande paket syftar på vilken applikation vi ska till. Detta gör det möjligt för oss att ha **multiplexering av processer**