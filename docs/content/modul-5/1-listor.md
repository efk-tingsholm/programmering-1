# Listor

## List<>

I C# är en **List<>** en generisk datastruktur som fungerar som en flexibel, dynamiskt stor samling av objekt. "Generisk" innebär att du kan bestämma vilken typ av data listan ska innehålla, till exempel heltal eller strängar. 

Listor erbjuder möjligheter att lägga till, ta bort och manipulera element på ett enkelt sätt.

Listor skiljer sig från arrayer genom att de kan ändra storlek efter att de skapats. Detta sker automatiskt när man lägger till eller tar bort element från listan. Man behöver alltså inte veta hur många element listan kommer innehålla när man deklarerar den.

### Deklarera och initiera en lista

För att skapa en lista måste du ange vilken typ av objekt listan ska innehålla. Detta anges inom olikhetstecken <>.

```csharp
// Skapa en lista av heltal
List<int> numbers = new List<int>();

// Skapa en lista av strängar
List<string> names = new List<string>();
```

Du kan även initiera en lista med värden direkt.

```csharp
List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
```

!!! tip "Tips"
    Använd **List<>** när du behöver en flexibel samling där antalet element kan variera under programmets körtid. Listor erbjuder många praktiska metoder som kan underlätta programmeringen.


### Lägga till och ta bort element

#### Lägga till element

Använd metoden `Add()` för att lägga till ett element.

```csharp
numbers.Add(6); // Lägger till 6 i slutet av listan
```

Det går även att lägga till flera element samtidigt, även dessa hamnar i slutet av listan.

```csharp
numbers.AddRange(new List<int> { 7, 8, 9 });
```

#### Ta bort element

Du kan ta bort element med metoder som `Remove()`, `RemoveAt()` och `RemoveRange()`:

```csharp
numbers.Remove(3);  // Tar bort första förekomsten av talet 3
numbers.RemoveAt(0); // Tar bort elementet på index 0

// Tar bort ett antal element från ett givet index
List<string> letters = new List<string> { "A", "B", "C", "D", "E" };
letters.RemoveRange(1, 2); // Tar bort "B" och "C" från index 1
// Efteråt innehåller listan: ["A", "D", "E"]
```

Metoden `Clear()` tar bort alla element från listan:

```csharp
numbers.Clear();
```


### Iterera över en lista

Du kan använda olika loopar för att gå igenom listans element:

#### For-loop

```csharp
for (int i = 0; i < numbers.Count; i++)
{
    Console.WriteLine(numbers[i]);
}
```

#### Foreach-loop

```csharp
foreach (var number in numbers)
{
    Console.WriteLine(number);
}
```

### Vanliga metoder och egenskaper

#### Count

Returnerar antalet element i listan:

```csharp
int antal = numbers.Count;
```

#### Contains

Kontrollerar om ett visst värde finns i listan:

```csharp
bool finns = numbers.Contains(3); // true om 3 finns i listan
```

#### IndexOf och LastIndexOf

Returnerar index för första respektive sista förekomsten av ett värde:

```csharp
// Hittar index för första 3:an
int index = numbers.IndexOf(3);

// Hittar index för sista 3:an
int lastIndex = numbers.LastIndexOf(3); 
```

#### Insert

Lägger till ett element på en specifik plats:

```csharp
numbers.Insert(2, 99); // Lägger till 99 på index 2
```

#### Sort och Reverse

Sorterar respektive vänder ordningen i listan:

```csharp
numbers.Sort();   // Sorterar listan i stigande ordning
numbers.Reverse(); // Vänder ordningen i listan
```





### Exempelprogram

Följande program demonstrerar flera vanliga operationer med en lista:

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        // Skapa och initiera en lista
        List<string> fruits = new List<string> { "Apple", "Banana", "Cherry" };

        // Lägg till ett element
        fruits.Add("Date");

        // Skriv ut alla element
        foreach (var fruit in fruits)
        {
            Console.WriteLine(fruit);
        }

        // Kontrollera om ett element finns
        if (fruits.Contains("Banana"))
        {
            Console.WriteLine("Banana finns i listan!");
        }

        // Ta bort ett element
        fruits.Remove("Apple");

        // Skriv ut listan efter borttagning
        Console.WriteLine("Efter borttagning:");
        foreach (var fruit in fruits)
        {
            Console.WriteLine(fruit);
        }
    }
}
```

Utskrift:

```
Apple
Banana
Cherry
Date
Banana finns i listan!
Efter borttagning:
Banana
Cherry
Date
```

