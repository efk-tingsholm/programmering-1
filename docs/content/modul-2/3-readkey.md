# ReadKey

Metoden ReadKey() används för att läsa ett enskilt tecken från användaren via konsolen. Metoden pausar programmet tills användaren trycker på en tangent. Jämför detta med ReadLine(), där programmet pausas tills användaren trycker på enter.

ReadKey() kan alltså användas för att ta inmatning från användaren med bara ETT knapptryck. Det finns också möjlighet att dölja vilken knapp som tryckts ned.

ReadKey() returnerar ett objekt av klassen ConsoleKeyInfo, som innehåller information om vilken tangent som trycktes ned, vilket tecken det motsvarar, samt om några andra modifierare såsom CTRL, ALT eller SHIFT använts. 

```csharp
// Inmatning från användaren. 
Console.WriteLine("Tryck på valfri tangent för att fortsätta...");
ConsoleKeyInfo keyInfo = Console.ReadKey();

// Blankrad.
Console.WriteLine();

// Sparar tecknet för senare användning eller dylikt.
char userinput = keyInfo.KeyChar;

// Skriver ut värdet på keyInfo's egenskaper.
Console.WriteLine($"Key: {keyInfo.Key}");
Console.WriteLine($"KeyChar: {keyInfo.KeyChar}");
Console.WriteLine($"Modifiers: {keyInfo.Modifiers}");
```

Ovanstående exempel med inskrivet procenttecken, alltså shift + 5, ger följande utskrift.
```
Tryck på valfri tangent för att fortsätta...
%
Key: D5
KeyChar: %
Modifiers: Shift
```

För att dölja användarens inmatning kan metoden ReadKey() användas med argumentet true. Detta resulterar i att användarens inmatning inte visas i konsolen.
```csharp
ConsoleKeyInfo keyInfo = Console.ReadKey(true);
```