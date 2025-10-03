# Begrepp - Modul 6

## Allmänt

**Klass:** En mall som definierar vilka egenskaper och metoder ett objekt ska ha.

**Objekt:** En instans av en klass som har egna unika egenskaper och kan utföra handlingar definierade i klassen.

**Instans:** En konkret representation av en klass som skapats med `new`.

## Konstruktorer

**Konstruktor:** En metod i en klass som anropas automatiskt vid skapandet av ett objekt och används för att sätta startvärden.

**Standardkonstruktor:** En konstruktor utan parametrar som skapas automatiskt om ingen definieras.

**Konstruktoröverlagring:** Att en klass kan ha flera konstruktorer med olika parametrar för att möjliggöra olika sätt att skapa objekt.

**Inkapsling:** Principen att skydda data genom att begränsa direkt åtkomst och istället exponera kontrollerade metoder.

**Klassmedlemmar:** De variabler (fält) och metoder som ingår i en klass.

**Fält (Field):** En variabel som lagrar data inom en klass.

**`private`:** Begränsar åtkomst till endast inom den egna klassen.

**`public`:** Tillåter att variabler och metoder kan nås utanför klassen.

**`static`:** Betyder att en variabel eller metod tillhör klassen snarare än enskilda objekt.

**`this`:** Refererar till det aktuella objektet och används för att skilja på klassens fält och parametrar med samma namn.

**`private set;`:** Gör att en property endast kan sättas inuti klassen.

## Properties

**Property:** En metodliknande mekanism som används för att kontrollera åtkomst till privata fält.

**`get`:** Används för att läsa värdet av en property.

**`set`:** Används för att ändra värdet av en property, ofta med validering.

**Auto-Property:** En kortare syntax där C# automatiskt skapar ett privat fält i bakgrunden.

**Read-Only Property:** En property med endast `get`, vilket gör att värdet kan sättas en gång men inte ändras.

**Write-Only Property:** En property med endast `set`, vilket gör att värdet kan sättas men inte läsas.

**Statiska klasser:** Klasser som inte kan instansieras och endast innehåller statiska medlemmar.

**Statiska medlemmar:** Variabler eller metoder som delas mellan alla instanser av en klass istället för att vara unika för varje objekt.






