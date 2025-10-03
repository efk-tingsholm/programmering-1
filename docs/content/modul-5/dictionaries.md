# Dictionaries

## Dictionary<>

I C# är en **Dictionary<>** en samling som lagrar nyckel-värde-par. Det är en generisk datastruktur där varje unikt nyckelobjekt (key) kopplas ihop med ett specifikt värdeobjekt (value). 

Dictionary är mycket effektivt när det gäller att söka efter värden baserat på nycklar. 

En dictionary är inte indexerad, alltså kan man inte arbeta med index för de olika elementen, utan arbetar med deras "nycklar" istället.



### Deklarera och initiera en Dictionary

För att skapa en dictionary anges datatyperna för både nycklar och värden inom olikhetstecken <>.

```csharp
// Skapa en dictionary med strängar som nycklar och heltal som värden
// Den första datatypen i <> anger nyckelns typ, och den andra anger värdets typ
Dictionary<string, int> ages = new Dictionary<string, int>();

// Skapa och initiera en dictionary direkt
Dictionary<int, string> cities = new Dictionary<int, string>
{
    { 1, "Stockholm" },
    { 2, "Göteborg" },
    { 3, "Malmö" }
};
```

!!! tip "Tips"
    Använd **Dictionary<>** när du behöver lagra data som kan sökas upp snabbt med unika nycklar. Dictionary är mycket effektiv för att hantera stora mängder data.


### Lägga till och åtkomst till element

#### Lägga till element

Använd metoden `Add()` för att lägga till nyckel-värde-par.

```csharp
Dictionary<string, int> ages = new Dictionary<string, int>();
ages.Add("Alice", 25); // Lägger till nyckeln "Alice" med värdet 25
```

Du kan även lägga till element, eller uppdatera dess värde via dess nyckel.

```csharp
// Lägger till eller uppdaterar nyckeln "Bob" till värdet 30
ages["Bob"] = 30; 
```

#### Åtkomst till värden

För att komma åt ett värde används nyckeln.

```csharp
// Sparar värdet från nycklen "Alice" i en int
int age = ages["Alice"]; // Ger värdet 25
```

#### Kontrollera om en nyckel finns

Du kan kontrollera om en nyckel finns med metoden `ContainsKey()`:

```csharp
if (ages.ContainsKey("Charlie"))
{
    Console.WriteLine("Nyckeln 'Charlie' finns i dictionary!");
}
```


#### Ta bort element

Använd metoden `Remove()` för att ta bort ett nyckel-värde-par:

```csharp
ages.Remove("Alice"); // Tar bort nyckeln "Alice" och dess värde
```

### Iterera över en Dictionary

Du kan iterera över en dictionary med en `foreach`-loop. Varje element i dictionary är ett KeyValuePair. Notera att det inte går att använda en `for`-loop eftersom dictionary saknar indexering:

```csharp
foreach (var kvp in cities)
{
    Console.WriteLine($"Nyckel: {kvp.Key}, Värde: {kvp.Value}");
}
```

### Vanliga metoder och egenskaper

#### Count

Returnerar antalet element i dictionary:

```csharp
int antal = cities.Count;
```

#### TryGetValue

En säkrare metod för att hämta värden:

```csharp
if (ages.TryGetValue("Bob", out int age))
{
    Console.WriteLine($"Bobs ålder är {age}.");
}
else
{
    Console.WriteLine("Bob finns inte i dictionary.");
}
```


#### Keys och Values
Returnerar alla nycklar respektive värden som en samling, exempelvis en array eller lista.

```csharp
int[] keys = cities.Keys.ToArray(); // Konverterar nycklarna till en array
List<string> values = cities.Values.ToList(); // Konverterar värdena till en lista

foreach (int key in keys)
{
    Console.WriteLine($"Nyckel: {key}");
}

foreach (string value in values)
{
    Console.WriteLine($"Värde: {value}");
}
```

### Exempelprogram

Följande program demonstrerar flera vanliga operationer med en dictionary.

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        // Skapa och initiera en dictionary
        Dictionary<string, int> ages = new Dictionary<string, int>
        {
            { "Alice", 25 },
            { "Bob", 30 },
            { "Charlie", 35 }
        };

        // Lägg till ett element
        ages["Diana"] = 40;

        // Iterera över dictionary
        foreach (var kvp in ages)
        {
            Console.WriteLine($"Namn: {kvp.Key}, Ålder: {kvp.Value}");
        }

        // Kontrollera om en nyckel finns
        if (ages.ContainsKey("Alice"))
        {
            Console.WriteLine("Alice finns i dictionary!");
        }

        // Ta bort ett element
        ages.Remove("Bob");

        // Skriv ut efter borttagning
        Console.WriteLine("Efter borttagning:");
        foreach (var kvp in ages)
        {
            Console.WriteLine($"Namn: {kvp.Key}, Ålder: {kvp.Value}");
        }
    }
}
```

Utskrift:

```
Namn: Alice, Ålder: 25
Namn: Bob, Ålder: 30
Namn: Charlie, Ålder: 35
Namn: Diana, Ålder: 40
Alice finns i dictionary!
Efter borttagning:
Namn: Alice, Ålder: 25
Namn: Charlie, Ålder: 35
Namn: Diana, Ålder: 40
```

