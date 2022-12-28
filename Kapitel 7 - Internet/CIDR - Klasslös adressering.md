## Klasslös adressering (classless addressing)
Class Interdomain Routing (CIDR) är det som används idag på Internet. I denna lösning så används en mask för att definiera hur stor del av en adress som net id och hur stor del som är host id. Masken består av 32 bitar där en etta indikerar att den biten i IP adressen är en del av net id och en nolla indikerar att det är en del av host id.

Det finns två sätt att skriva masken på
- Decimal notation: 255.255.255.240 
	- Om man gör om detta till bits så kan får man masken 
- Slash notation: 16.4.8.26/24.
	- 24 indikerar att net id är 24 bitar stor