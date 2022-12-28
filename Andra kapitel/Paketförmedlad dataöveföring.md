
Det finns två sätt paketförmedlad dataöverföring kan se, nedan förklaras båda

## Förbindelseorienterad dataöverföring

I denna typ måste sändare och mottagare sätta upp en förbindelse mellan sig, se bild nedan. En virtuell krets skapas mellan sändare och mottagare och all data som skickas kommer skickas via denna virtuella krets.

![Untitled](Paketfo%CC%88rmedlad%20datao%CC%88vefo%CC%88ring%20a5aca19d7bd048fcb64742d8962c787c/Untitled.png)

## Fördlear

- Det blir lättare att kontrollera dataöverföringen, under uppkopplingskedet kan sändare och mottagare komma överens om saker som har med överföringen att göra.
- Mottagaren kan också spärra upptkopplingen om den inte har tid att ta emot information
- Det är möjligt att reservera kapacitet genom näter och sätta olika prioriteter

## Nackdelar

- Det tar tid att koppla upp en förbindelse

## Förbindelsefri dataöverföring

I denna typ så behövs ingen förbindelse skapas. Istället så skickar sändaren direkt sin information till mottagaren utan att meddela den. Detta passar bra när bara lite data ska skickas då uppkopplingsfasen blir stor overhead.

## Fördelar

- Det krävs ingen uppkopplingsfas vilket kan bli en overhead

## Nackdelar

- Själva dataöverföringen blir mer komplicerad eftersom vägväljaren måste göra ett vägval för varje paket.