# Felhantering

Felhantering är en viktig del av programmering eftersom det hjälper till att skapa robusta och användarvänliga applikationer. 

Genom att förebygga fel redan i planeringsstadiet minskar risken att de inträffar, och höjer användarvänligheten. 

Det är dock också viktigt att kunna hantera fel när de uppstår för att säkerställa att programmet inte kraschar och kan ge användbar feedback till användaren.


## Feltyper
Det finns tre huvudsakliga typer av fel inom programmering, baserat på vad de har för effekt.
### Kompileringsfel
Kompileringsfel uppstår när koden bryter mot språkets syntaxregler och kan inte kompileras. 

Dessa fel upptäcks av kompilatorn innan programmet körs, vilket leder till att programmet inte startar.

Visual Studio hjälper till att hitta dessa genom att markera dem med rött.
```csharp
// Kompileringsfel, kan inte konvertera string till int rakt av
int myInt = "Hej";
```

### Exekveringsfel
Exekveringsfel (runtime errors) uppstår under programmets körning, och leder till att programmet "slutar exekvera", alltså krascha. 

I C# kallas dessa för undantag (exceptions), och om ett undantag inte hanteras så kraschar programmet.

```csharp
// Ger upphov till ett exekveringsfel för det blir nolldivision
int num = 10;
int temp = num / 0;
```

Ovanstående exempel ger upphov till ett felmeddelande som kommunicerar "Exception unhandled" följt av namnet på undantaget med tillhörande förklaring vad som orsakade det, i det här fallet: "System.DivideByZeroException: 'Attempted to divide by zero."
### Logiska fel
Logiska fel är ofta den största fienden. Programmet kompilerar och startar upp, det kraschar inte, men om man frågar vilken färg himlen har så svarar programmet "bacon". Inte helt önskvärt.

Följande kod är ett exempel på ett program som ska summera a och b.
```csharp
int a = 5;
int b = 10;
int sum = a - b; // Logiskt fel, fel operator, - istället för +
Console.WriteLine($"Summan av {a} och {b} är {sum}");
```

Logiska fel kan vara svåra att upptäcka, dels för att man själv får tunnelseende, men också när programmet blir större och större.

Följande kod är ett exempel på ett program som räknar antalet vokaler i en sträng som användaren skriver in.
```csharp
string input = Console.ReadLine();
int count = 0;

foreach (char c in input)
{
    if (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u' || c == 'å' || c == 'ä' || c == 'ö')
    {
        count++;
    }
}

Console.WriteLine($"Antalet vokaler i strängen '{input}' är: {count}");
```
Skriver man in "Äntligen får jag programmera!" i ovanstående exempel får man utskriften:
```
Antalet vokaler i strängen "Äntligen får jag programmera!" är: 8
```

Programmet missar alltså en vokal. Mer specifikt så räknar programmet inte versala vokaler (stora bokstäver), i det här fallet "Ä".

Det här hade varit svårare att se eller komma på om man inte testat programmet och belyser vikten av att testköra sina program.


---


## Undantag med try-catch
Exekveringsfel i C# ger upphov till så kallade undantag. Dessa hanteras såklart bäst genom att helt undvika dem via förebyggande arbete, exempelvis kanske använda TryParse() istället för Parse().

Ett annat sätt att hantera undantag och undvika att programmet kraschar är att använda en lite mer allmän lösning, try-catch. 

Följande exempel ger upphov till ett exekveringsfel, System.FormatException, eftersom det inte går att konvertera text till heltal.
```csharp
int myInt = int.Parse("Hej");
```

Användande av try-catch låter programmet "försöka" utföra koden, och sen agera om något undantag dyker upp. Ett try-block måste matchas ihop med minst ett catch-block.
```csharp
try
{
    // Försöker köra koden inne i try-blocket
    int myInt = int.Parse("Hej");
}
catch
{
    // Om något går fel utförs koden i catch-blocket.
    Console.WriteLine("Nåt gick fel!");
}
```

Ovanstående exempel ger dock ingen information till användaren, ett sätt att åstadkomma det är att använda det faktiska undantaget som ett argument i catch-blocket, i nedanstående exempel namnges undantaget till error.
```csharp
try
{
    int myInt = int.Parse("Hej");
}
catch (Exception error) // Undantaget namnges till error
{
    Console.WriteLine("Nåt gick fel!");
    Console.WriteLine(error.Message); // Skriv ut det inbyggda meddelandet
}
```
Ovanstående kod ger en utskrift innehållande undantagets eget felmeddelande:
```
Nåt gick fel!
Input string was not in a correct format.
```

Det går också att "fånga" specifika fel med catch-block, då specificerar man vilken typ av undantag som ska fångas. På så vis kan man låta programmet hantera olika undantag på olika sätt.
```csharp
try
{
    // Försöker omvandla en sträng till integer.
    // Talet ifråga är dock för stort för en int32.
    int myInt = int.Parse("99999999999999999999999");
}
catch (FormatException) //Det här blocket händer ENBART vid fel format.
{
    Console.WriteLine("Fel format!");
}
catch //Alla andra fel.
{
    Console.WriteLine("Något annat oklart hände!");
}
```


---


## Felsökning med debugger
Att felsöka logiska fel kan vara jobbigt, man vet kanske inte vad som är problemet eller var i källkoden sagda problem befinner sig.

Ett sätt att underlätta felsökningsprocessen är att använda sig av Visual Studios debugger och gå igenom koden steg för steg, eller pausa exekveringen vid en viss rad där man misstänker att problemet finns,

### Steg för steg
För att gå igenom koden steg för steg används knappen "Step into" (F11). Ser du inte knappen, högerklicka och visa verktygsfältet "Debug".

Programmet startar och första i källkoden markeras, härifrån kan man gå framåt i programmet genom att trycka på "Step Into" (F11) igen, ett tryck innebär en rad framåt. 

Det finns också möjlighet att se värdet på alla variabler via fliken "Locals", nere till vänster från början.

### Breakpoints
Lek med tanken att ditt program är 300 rader kod. Du misstänker att problemet finns någonstans runt rad 250. Du skulle kunna klicka på "Step Into" (F11) 250 gånger för att komma dit, men det vill du inte.

En breakpoint kan sättas på en specifik rad i källkoden och fungerar precis som namnet antyder, när programmet kommer till raden ifråga så kommer programmet att pausa och gå in i debug läge.

För att sätta ut en breakpoint kan man vänsterklicka längst ut till vänster om radnumret. Alternativt kan man använda F9 när markören är på raden ifråga. Funktionaliteten kan också kommas åt från dropdownen "Debug" högst upp.

Det går utmärkt att sätta ut fler breakpoints.

### Run to cursor
Fungerar som en breakpoint, men bara en gång. Högerklicka på raden du vill köra till, välj "Run To Cursor", programmet kör som vanligt till raden ifråga och går sen in i debug så att du kan undersöka. 



