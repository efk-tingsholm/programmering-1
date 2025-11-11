# Metoder

En metod är ett block med kod som kan återanvändas, när en metod används kallas det för metodanrop, metoden **anropas**.

Det finns fördefinierade metoder i C#, exempelvis Main(), WriteLine(), Parse() och ReadLine(). 

Utöver fördefinierade metoder finns det möjlighet att skapa egendefinierade metoder i källkoden. Detta har flera fördelar, exempelvis ökad struktur, läsbarhet och återanvändning av kod. Det är också lättare att felsöka och göra förbättringar i ett program som är uppbyggt av metoder som kan ändras var för sig, jämfört med ett program som utgörs av en stor vägg med spaghetti.


!!! tip "Tips"
    DRY (Don't Repeat Yourself) är en princip inom programmering och går ut på just vad det låter som, skriv din källkod en gång, återanvänd med metoder. 

    Notera att detta är ett strävansmål i denna kursen, inte ett totalitärt krav.



Den grundläggande strukturen för en metod i C# ser ut som nedan. Notera att för metoder används PascalCase istället för camelCase som namngivningsstandard. 
```csharp
static void MinMetod()
{
    // Här skrivs all kod som utförs i metoden
}
```
Metoddeklarationen består av tre delar delar, som kan ses ovan:

- static - modifierare som avgör hur metoden kan anropas, används för att kunna använda metoden direkt.
- void - metodens returtyp, void betyder att metoden inte returnerar något.
- MinMetod() - metodens namn, namnge metoden beskrivande, och använd PascalCase.


Det är också värt att notera att av organisatoriska skäl placeras metoder utanför Main()-metoden, ovanför eller under, spelar ingen roll.
```csharp
namespace test
{
    internal class Program
    {
        static void Main(string[] args)
        {
            // Här är den vanliga Main()
            // Programmet startar här!
        }

        static void MinMetod()
        {
            // Här skrivs all kod som utförs i metoden
        }
    }
}
```

!!! info "Info"
    Det går att lägga metoder intui andra metoder, t.ex. Main() eller annan metod du själv definierat. I sådana situationer kallas de istället *lokala funktioner* (local functions) och Microsoft har en [hel artikel](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/local-functions){:target="_blank"} dedikerad till dem.

    

---


## Metodanrop
Metoder anropas genom att skriva deras namn, exempelvis i Main()-metoden. Notera att koden fortfarande exekveras uppifrån och ned, men när raden med metoden nås så körs hela metoden innan programmet fortsätter nedåt.
```csharp
static void Main(string[] args)
{
    Console.WriteLine("Nu ska min egen metod köras!");
    MinMetod();
    Console.WriteLine("Nu HAR min metod körts.");
}

static void MinMetod()
{
    Console.WriteLine("Hej nu körs min metod!");
}
```
Ovanstående exempel ger följande utskrift. 
```
Nu ska min egen metod köras!
Hej nu körs min metod!
Nu HAR min metod körts.
```

---

## Parametrar
Metoder kan designas för att ta emot information och göra något relevant med informationen. Vilken information metoden ska ta emot bestäms i metoddeklarationen och kallas **parametrar**. 
```csharp
// Metoden GladHälsning har parametern namn, av typen string
static void GladHälsning(string namn)
{
    Console.WriteLine($"Trevligt att träffas {namn}!");
}
```

En metod kan ha flera parametrar, så länge de inte är exakt likadana. 
```csharp
static void AdderaTvåTal(int a, int b)
{
    int summa = a + b;
    Console.WriteLine($"Summan är {summa}.");
}
```

När en metod med en eller flera parametrar behöver någon lämplig information anges, annars kan inte metoden anropas. Informationen som skickas in kallas **argument**. Argumenten kan antingen vara variabler eller riktiga värden.
```csharp
static void Main(string[] args)
{
    int tal = 10;
    AdderaTvåTal(tal, 20);
}
// Körning av programmet ger utskriften: Summan är 30.
```


---

## Returvärde
Metoder kan returnera ett värde. Vad en metod ska returnera anges i metoddeklarationen, genom att skriva en datatyp istället för "void". Returvärdet kan sedan antingen sparas till en variabel, eller användas direkt via metodanropet.

Nedanstående exempel vidareutvecklar metoden AdderaTvåTal(), till att returnera svaret istället för att skriva ut det.
```csharp
static int AdderaTvåTal(int a, int b)
{
    int summa = a + b;
    return summa;
}
```
Detta innebär en förändring när metoden anropas.
```csharp
static void Main(string[] args)
{
	// Metodens returvärde kan sparas i en variabel.
	int summa = AdderaTvåTal(10, 20);

	// Metoden kan också användas direkt för sitt returvärde.
	Console.WriteLine(AdderaTvåTal(5, 10)); // Utskrift: 15
}
```

---

## Metodöverlagring
Vissa metoder kan anropas på olika sätt. Exempelvis kan metoden Beep() från klassen Console anropas antingen helt utan argument, eller genom att ange både frekvens och varaktighet.
```csharp
// Beep() anropas utan argument, går bra.
Console.Beep();

// Beep() anropas med argumenten 700 och 2000, 
// för parametrarna frekvens och varaktighet. Går också bra.
Console.Beep(700, 2000);
```

Hemligheten med att göra EN metod som kan anropas på olika sätt är att det helt enkelt inte går.

Istället gör man flera metoder med samma namn, men olika parametrar. Detta kallas **metodöverlagring**, metoden **överlagras** med olika versioner. I Visual Studio kan man ibland se exempelvis "+2 overloads" eller liknande, det hänvisar till överlagringar.

Exempelvis skulle en metod för att addera två tal kunna överlagras med en metod som adderar tre tal, och därmed ge intrycket av att metoden ifråga klarar av både två och tre tal.
```csharp
static int AdderaTal(int a, int b)
{
    return a + b;
}

static int AdderaTal(int a, int b, int c) 
{ 
    return a + b + c;
}
```

Metoden AdderaTal() kan nu anropas antingen med två eller tre argument.
```csharp
static void Main(string[] args)
{
    int summa1 = AdderaTal(5,6);
    int summa2 = AdderaTal(5,6,7);

    Console.WriteLine(summa1); // Utskrift: 11
    Console.WriteLine(summa2); // Utskrift: 18
}
```

---

## Rekursiva metoder
Rekursiva metoder är ett tjusigt sätt att beskriva metoder som anropar sig själva. Sådana metoder måste ha ett basfall, så att de inte anropar sig själva i all evighet, på samma sätt som man inte vill fastna i oändliga loopar.

Följande metod räknar ned från ett givet heltal och skriver ut nedräkningen till användaren.
```csharp
static void Countdown(int number)
{
    // Skriv alltid ut vilket nummer vi är på
    Console.WriteLine(number);

    // Basfall när number är lika med noll
    if (number == 0)
    {
        Console.WriteLine("Klar!");
    }
    else
    {
        // Anropa SIG SJÄLV, men med ett värde som är 1 mindre
        Countdown(number - 1);
    }
}
```
När metoden "Countdown()" från exemplet ovanför anropas med argumentet 4 fås följande utskrift.
```
4
3
2
1
0
Klar!
```


!!! tip "Tips"
    Rekursiva metoder tas upp i den här kursen främst i orienteringssyfte, man förväntas förstå konceptet, men inte nödvändigtvis använda dem på en högre nivå än i exemplet ovan.

