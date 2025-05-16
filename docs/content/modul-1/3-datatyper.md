# Datatyper

Olika typer av variabler kan lagra olika typer av värden. Det är lite som att man inte bör tömma saft i kakburken, eller försöka lägga kakorna i saftflaskan. Dessa typer kallas **datatyper**. 

Variablers datatyp talar om för kompilatorn vilka operationer som kan utföras för den aktuella variabeln. Olika datatyper tar också olika stor plats i minnet, så genom korrekt användande av datatyper kan man optimera minnesanvändningen. 

## Primitiva datatyper i C\#
Primitiva datatyper är de grundläggande datatyperna som används för att lagra värden i ett program, och utgör grunden för att skapa mer komplexa datatyper. Dessa kan skilja sig åt lite beroende på programmeringsspråk. 

Tabellen nedan tar upp vanligt förekommande primitiva datatyper i C#.

| Datatyp | Beskrivning               | Storlek        | Intervall                                                    |     |
| ------- | ------------------------- | -------------- | ------------------------------------------------------------ | --- |
| int     | Heltal                    | 32 bits        | $-2{^3}{^1}$ till $2{^3}{^1}-1$                              |     |
| long    | Heltal                    | 64 bits        | $-2{^6}{^3}$ till $2{^6}{^3}-1$                              |     |
| float   | Flyttal                   | 32 bits        | $-3,4\cdot10{^3}{^8}$ till $3,4\cdot10{^3}{^8}$              |     |
| double  | Flyttal, dubbel precision | 64 bits        | $\pm5,0\cdot10{^3}{^2}{^4}$ till $\pm1,7\cdot10{^3}{^0}{^8}$ |     |
| decimal | Flyttal, hög precision    | 128 bits       | 28 gällande siffror                                          |     |
| string  | Sekvens av tecken         | 16 bits/tecken | Ej applicerbart                                              |     |
| char    | Enskilt tecken            | 16 bits        | Ett enskilt tecken                                           |     |
| bool    | Boolean                   | 8 bits         | Sant eller falskt                                            |     |

<hr>

### Flyttal
Ett flyttal är en datatyp som används för att representera decimaltal. Till skillnad från heltal är flyttal en approximation av ett decimaltal och kan därför inte representera alla decimaler exakt, utan ger en uppskattning av det verkliga värdet. Detta innebär att flyttal kan ha begränsad precision, vilket kan leda till avrundningsfel i beräkningar. 

Nedan följer ett exempel på sådant avrundningsfel, som i grund och botten är baserat på att datorn inte förstår oändlig decimalutveckling.
```csharp
// Värdet på variablen num borde vara 0,3.
double num = 0.1 + 0.2; 
// Det kommer skrivas ut som 0,30000000000000004.
Console.WriteLine(num);
```

### char
Namnet kommer från engelskans *character*, och datatypen används för att representera enskilda tecken, exempelvis en bokstav. 

Datorn lagrar som bekant bara ettor och nollor, så varje tecken har en egen sifferkod, enligt en given teckentabell. Exempelvis ASCII och Unicode. 

Alltså är varje bokstav egentligen bara ett heltal för datorn. Exempelvis enligt båda ovan nämnda exempel så är sifferkoden för lilla a lika med 97. Notera att för stora A är den 65.
```csharp
// Man kan direkt spara en char som en integer
int myInt = 'A';
Console.WriteLine(myInt); // Ger utskriften "65".

// Sifferkoden kan användas för att "casta" en int till char.
char myChar = (char)97;
Console.WriteLine(myChar); // Ger utskriften "a".
```
### string
En string är en serie tecken, chars, efter varandra. Man kan komma åt enskilda tecken via dess index.
```csharp
string myString = "Hejsan!";
Console.WriteLine(myString[1]); // Ger utskriften "e".
```
