# Övningsuppgifter - Modul 4

## Uppgift 1
Skriv en metod som tar in två tal och skriver ut det minsta av de två talen, i en mening, t.ex. "Det minsta talet är 3!". Din metod ska inte använda den fördefinierade metoden Math.Min().

Testkör din metod genom att anropa den i Main().
## Uppgift 2
Skriv en metod som tar in tre tal och returnerar talens medelvärde. Notera att returnera innebär att metoden ska ha en annan returtyp än void. 

Testkör din metod.

## Uppgift 3 
Skriv ett program som hjälper användaren med sina cylindriska behov, mer precist beräkning av volym och mantelarea.

Programmet fråga användaren om radie och höjd för cylindern.

Programmet beräkna volym och mantelarea med hjälp av en metod för varje. Metoderna ska ha radie och höjd som parametrar, och returnera volym respektive mantelarea.

Programmet ska skriva ut informationen till användaren.


## Uppgift 4
Skriv ett program som frågar användaren efter tre ord, ett ord i taget. 

Programmet ska sedan lägga in informationen i en array av typen string med tre platser på.

Programmet ska sedan skriva ut informationen från arrayen tillbaka till användaren med hjälp av en loop, numrerat i ordningen som orden angavs i, exempelvis
1. Hej
2. på
3. dig




## Uppgift 5
Skriv en metod som tar in en array av heltal som parameter. 

Metoden ska sedan räkna och returnera antalet positiva tal i arrayen som skickades in.

Testa din metod med olika arrayer av heltal för att se att den fungerar.

## Uppgift 6
Skriv en metod som tar emot en sträng och byter "case" på varje bokstav, stora bokstäver ska bli små och små ska bli stora. 

Exempelvis om metoden anropas med texten "Hej på dig" ska metoden returnera "hEJ PÅ DIG".

## Uppgift 7
Skriv en metod som tar emot en array av heltal och ett givet heltal. Metoden ska sedan undersöka om heltalet ifråga finns i arrayen. Metoden ska returnera true om talet finns, och false om talet inte finns.

Använd INTE den fördefinierade metoden Contains(). Du ska uppfinna hjulet själv istället.

## Uppgift 8
Skriv ett program som genererar en array med 20 slumpade tal mellan 0 och 100. 

Programmet ska ha metoder för att:
- beräkna minsta och största talet i arrayen.
- beräkna medelvärdet av talen i arrayen.
- beräkna medianen av talen i arrayen.
- Antal jämna och antal udda tal i arrayen.

Programmet ska sedan skriva ut ovan nämnda data i konsolen till användaren, metoderna ska användas.


## Uppgift 9
Skriv ett program som tar in en mening från användaren. Programmet ska räkna och returnera antalet vokaler i meningen.

Detta ska utföras med hjälp av en metod som tar en sträng som parameter och returnerar antalet vokaler (a, e, i, o, u, y, å, ä, ö) i strängen. 

## Uppgift 10
Skriv en metod som frågar användaren efter ett positivt heltal. 

Metoden ska inte låta användaren skriva in något annat än ett positivt heltal och helt enkelt fråga igen tills användaren gör rätt. Metoden ska sedan returnera heltalet ifråga.

*Tips: Den här metoden kan ju modifieras och klistras in i kommande projekt för att enkelt kontrollera användarinput i framtiden!*


## Uppgift 11
Skriv ett program med huvudmeny. I huvudmenyn ska man se menyalternativ och en utritad 3x3 array av datatypen int. Arrayen ska vara fylld med slumpvalda heltal mellan 0 och 10 från början.

Menyalternativen ska vara:
- Skriv ut summan av alla element.
- Skriv ut största elementet.
- Skriv ut summan för arrayens rader.
- Skriv ut summan för arrayens kolumner.
- Generera nya tal till arrayen.

Menyfunktionerna ska uppfyllas med hjälp av metoder. 

Behöver inte vara begränsat till en metod för varje alternativ, om du anser att det blir vettigt att använda flera metoder så gör det.



## Uppgift 12
Skriv en metod som undersöker om en 3x3 array av heltal kan vara en del av en sudokulösning, alltså om varje siffra förekommer endast en gång och inga siffror under 1 eller över 9.

Metoden ska returnera true om arrayen är en giltig lösning, och false om den inte är det.

Testa din metod för både giltiga och ogiltiga arrayer och kontrollera att den fungerar.

## Uppgift 13
Skriv en metod som beräknar diagonalsumman från övre vänstra hörnet till nedre högra hörnet för en given kvadratisk 2D-array med heltal. 

Metoden ska alltså ta emot en tvådimensionell array och returnera diagonalsumman.

Testa din metod.

Skriv nu en motsvarande metod för den andra diagonalsumman.
