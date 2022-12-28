## CRC

Först vill vi göra om våra bitar till ett polynom $d(x)$

![[Pasted image 20221118145503.png]]

Vi har ett generator polynom $g(x)$ som både sändare och mottagare har kommit fram till. Vi har också en grad k som både sändare och mottagare har kommit fram till. k är graden på g

Vi gör sedan polynom division med $\frac{d(x)*x^k}{g(x)}$sen får vi en rest av denna uträkningen. Denna rest ska vara samma som våra paritetsbitar
## Kontrollsumma

Är ett alterntivt sätt att detektera bitfel, det går till så här

1.  VI bestämmer en längd på vår kontrollsumma, t.ex 8 bitar
2.  vi delar upp vår data i chunks av denna storleken
3.  Vi adderar våra chunks
4.  Om vi får en carrybit så adderar vi den som least significant bit
5.  Vi tar komplementet till våra chunks och skickar denna som vår kontrollsumma
6.  Det vi skickar är alla våra chunks och vår kontrollsumma chunk sist
7.  Mottagaren adderar alla chunks och tar komplement till detta
8.  Om vi får overflow adderas den till vårt resultat som least significant bit
9.  Om komplement är 0 så har vi inget bitfel