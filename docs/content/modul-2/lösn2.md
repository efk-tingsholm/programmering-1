# Lösningsförslag - Modul 2


## Uppgift 1
```csharp
// Be om två tal från användaren
Console.WriteLine("Ange det första talet:");
int tal1 = int.Parse(Console.ReadLine());

Console.WriteLine("Ange det andra talet:");
int tal2 = int.Parse(Console.ReadLine());

// Jämför de två talen och skriv ut det minsta
if (tal1 < tal2)
{
    Console.WriteLine($"Det minsta talet är: {tal1}");
}
else if (tal2 < tal1)
{
    Console.WriteLine($"Det minsta talet är: {tal2}");
}
else
{
    Console.WriteLine("Talen är lika stora.");
}
```




## Uppgift 2
```csharp
// Be användaren att ange ett heltal
Console.WriteLine("Ange ett heltal:");
string input = Console.ReadLine();

// Spara returvärdet från TryParse i en variabel
bool ärHeltal = int.TryParse(input, out int tal);

// Använd variabeln i if-satsen
if (ärHeltal)
{
    // Kontrollera om talet är jämnt eller udda
    if (tal % 2 == 0)
    {
        Console.WriteLine("Talet är jämnt.");
    }
    else
    {
        Console.WriteLine("Talet är udda.");
    }
}
else
{
    // Felmeddelande om inmatningen inte är ett heltal
    Console.WriteLine("Fel: Det var inte ett giltigt heltal.");
}
```



## Uppgift 3
```csharp
int poäng = 0;

// Fråga 1
Console.WriteLine("Vad är huvudstaden i Sverige?");
string svar1 = Console.ReadLine().ToLower();
if (svar1 == "stockholm")
{
    Console.WriteLine("Rätt svar!");
    poäng++;
}
else
{
    Console.WriteLine("Fel svar.");
}

// Fråga 2
Console.WriteLine("Vad är 2 + 2?");
string svar2 = Console.ReadLine();
if (svar2 == "4")
{
    Console.WriteLine("Rätt svar!");
    poäng++;
}
else
{
    Console.WriteLine("Fel svar.");
}

// Fråga 3
Console.WriteLine("Vilket år började andra världskriget?");
string svar3 = Console.ReadLine();
if (svar3 == "1939")
{
    Console.WriteLine("Rätt svar!");
    poäng++;
}
else
{
    Console.WriteLine("Fel svar.");
}

// Ge återkoppling
Console.WriteLine($"Du fick {poäng} av 3 möjliga rätta svar.");
```

## Uppgift 4
```csharp
// Informera användaren om poänggränserna
Console.WriteLine("Poänggränser: A = 90-100, B = 80-89, C = 70-79, D = 60-69, E = 50-59, F = under 50");

// Fråga användaren om deras poäng
Console.WriteLine("Hur många poäng fick du?");
int poäng = int.Parse(Console.ReadLine());

// Kontrollera om poängen är inom det tillåtna intervallet
if (poäng < 0 || poäng > 100)
{
    Console.WriteLine("Fel: Ange ett giltigt poäng mellan 0 och 100.");
}
else
{
    // Bestäm vilket betyg poängen motsvarar
    if (poäng >= 90)
    {
        Console.WriteLine("Ditt betyg är A.");
    }
    else if (poäng >= 80)
    {
        Console.WriteLine("Ditt betyg är B.");
    }
    else if (poäng >= 70)
    {
        Console.WriteLine("Ditt betyg är C.");
    }
    else if (poäng >= 60)
    {
        Console.WriteLine("Ditt betyg är D.");
    }
    else if (poäng >= 50)
    {
        Console.WriteLine("Ditt betyg är E.");
    }
    else
    {
        Console.WriteLine("Ditt betyg är F.");
    }
}
```




## Uppgift 5
```csharp
// Fråga användaren vilken veckodag det är
Console.WriteLine("Vilken veckodag är det?");
string veckodag = Console.ReadLine().ToLower();

// Använd en switch-sats för att ge förslag på maträtt
switch (veckodag)
{
    case "måndag": // Faller igenom till torsdagens maträtt
    case "torsdag":
        Console.WriteLine("Maträtt: Spaghetti och köttfärssås.");
        break;
    case "tisdag":
        Console.WriteLine("Maträtt: Fiskgratäng.");
        break;
    case "onsdag":
        Console.WriteLine("Maträtt: Kycklingsallad.");
        break;
    case "fredag":
        Console.WriteLine("Maträtt: Tacos.");
        break;
    case "lördag":
        Console.WriteLine("Maträtt: Pizza.");
        break;
    case "söndag":
        Console.WriteLine("Maträtt: Lasagne.");
        break;
    default:
        Console.WriteLine("Fel: Det var inte en giltig veckodag.");
        break;
}
```



## Uppgift 6
```csharp
// Ta in tre tal från användaren
Console.WriteLine("Ange första talet:");
int tal1 = int.Parse(Console.ReadLine());

Console.WriteLine("Ange andra talet:");
int tal2 = int.Parse(Console.ReadLine());

Console.WriteLine("Ange tredje talet:");
int tal3 = int.Parse(Console.ReadLine());

// Sortera och skriv ut talen i storleksordning
if (tal1 <= tal2 && tal1 <= tal3) // Om tal 1 är störst
{
    if (tal2 <= tal3)
    {
        Console.WriteLine($"{tal1}, {tal2}, {tal3}");
    }
    else
    {
        Console.WriteLine($"{tal1}, {tal3}, {tal2}");
    }
}
else if (tal2 <= tal1 && tal2 <= tal3) // Om tal 2 är störst
{
    if (tal1 <= tal3)
    {
        Console.WriteLine($"{tal2}, {tal1}, {tal3}");
    }
    else
    {
        Console.WriteLine($"{tal2}, {tal3}, {tal1}");
    }
}
else // Här är ju automatiskt tal 3 störst
{
    if (tal1 <= tal2)
    {
        Console.WriteLine($"{tal3}, {tal1}, {tal2}");
    }
    else
    {
        Console.WriteLine($"{tal3}, {tal2}, {tal1}");
    }
}
```


## Uppgift 7
```csharp
// Fråga användaren efter första talet
Console.WriteLine("Ange ett tal:");
double tal1 = double.Parse(Console.ReadLine());

// Fråga efter räknesätt
Console.WriteLine("Ange ett räknesätt (+, -, *, /, ^ för upphöjt till, sqrt för roten ur):");
string raknesatt = Console.ReadLine();

// Utför operationer beroende på räknesättet
if (raknesatt == "sqrt")
{
    // Roten ur operation
    Console.WriteLine($"Resultatet är: {Math.Sqrt(tal1)}");
}
else
{
    // Fråga efter andra talet för övriga operationer
    Console.WriteLine("Ange ett tal till:");
    double tal2 = double.Parse(Console.ReadLine());

    switch (raknesatt)
    {
        case "+":
            Console.WriteLine($"Resultatet är: {tal1 + tal2}");
            break;
        case "-":
            Console.WriteLine($"Resultatet är: {tal1 - tal2}");
            break;
        case "*":
            Console.WriteLine($"Resultatet är: {tal1 * tal2}");
            break;
        case "/":
            if (tal2 != 0) // En kontroll så att det inte blir nolldivision!
            {
                Console.WriteLine($"Resultatet är: {tal1 / tal2}");
            }
            else
            {
                Console.WriteLine("Fel: Division med noll är inte tillåten.");
            }
            break;
        case "^":
            Console.WriteLine($"Resultatet är: {Math.Pow(tal1, tal2)}");
            break;
        default:
            Console.WriteLine("Fel: Ogiltigt räknesätt.");
            break;
    }
}
```

## Uppgift 8
```csharp
// Be användaren att ange en vinkel
Console.WriteLine("Ange en vinkel i grader:");
int vinkel = int.Parse(Console.ReadLine());

// Om vinkeln är negativ, konvertera den till en positiv vinkel
if (vinkel < 0)
{
    vinkel = 360 + vinkel;
}

// Bestäm vilken typ av vinkel det är
if (vinkel == 90)
{
    Console.WriteLine("Vinkeln är rät.");
}
else if (vinkel == 180)
{
    Console.WriteLine("Vinkeln är rak.");
}
else if (vinkel == 360)
{
    Console.WriteLine("Vinkeln är en hel vinkel.");
}
else if (vinkel < 90)
{
    Console.WriteLine("Vinkeln är spetsig.");
}
else if (vinkel < 180)
{
    Console.WriteLine("Vinkeln är trubbig.");
}
else
{
	// https://sv.wikipedia.org/wiki/Vinkel
    Console.WriteLine("Vinkeln är reflex.");
}
```




## Uppgift 9
```csharp
// Be användaren att ange ett årtal
Console.WriteLine("Ange ett årtal:");
string input = Console.ReadLine();

// Spara returvärdet från TryParse i en variabel
bool ärHeltal = int.TryParse(input, out int årtal);

// Använd variabeln i if-satsen och kontrollera att årtalet är positivt
if (ärHeltal && årtal >= 0)
{
    // Kontrollera om årtalet är nutid, dåtid eller framtid
    if (årtal < 2023)
    {
        Console.WriteLine("Årtalet är i dåtiden.");
    }
    else if (årtal > 2023)
    {
        Console.WriteLine("Årtalet är i framtiden.");
    }
    else
    {
        Console.WriteLine("Årtalet är i nutiden.");
    }

    // Kontrollera om det är ett skottår
    if ((årtal % 4 == 0 && årtal % 100 != 0) || (årtal % 400 == 0))
    {
        Console.WriteLine("Det är ett skottår.");
    }
    else
    {
        Console.WriteLine("Det är inte ett skottår.");
    }
}
else
{
    // Felmeddelande om inmatningen inte är ett giltigt årtal eller om det är negativt
    Console.WriteLine("Fel: Det var inte ett giltigt positivt årtal.");
}
```




## Uppgift 10
a)
```csharp
// Fråga användaren hur många hg godis de vill köpa
Console.WriteLine("Hur många hekto godis vill du köpa?");
double vikt = double.Parse(Console.ReadLine());

// Bestäm priset beroende på vikten
if (vikt <= 10)
{
    Console.WriteLine($"Priset är {vikt * 9.90} kr.");
}
else if (vikt <= 20)
{
    Console.WriteLine($"Priset är {vikt * 8.90} kr.");
}
else
{
    Console.WriteLine($"Priset är {vikt * 7.90} kr.");
}
```

b)
```csharp
// Fråga användaren hur mycket pengar de har
Console.WriteLine("Hur mycket pengar har du?");
double pengar = double.Parse(Console.ReadLine());

// Bestäm hur många hekto godis användaren kan köpa
// För 89 kr kan man precis köpa 1 kg godis för det billigare priset 8.90
// Alltså är allt under 89 automatiskt priskategori 1, det dyrare
if (pengar <= 89)
{
    Console.WriteLine($"Du kan köpa {Math.Round(pengar / 9.90, 2)} hg godis.");
}
else if (pengar <= 158) // Samma resonemang som ovan, man kan precis köpa 2 kg för billigt pris för 158 kr
{
    Console.WriteLine($"Du kan köpa {Math.Round(pengar / 8.90, 2)} hg godis.");
}
else
{
    Console.WriteLine($"Du kan köpa {Math.Round(pengar / 7.90, 2)} hg godis.");
}
```




## Uppgift 11
```csharp
// Instruktioner
Console.WriteLine("Löser ekvationer på formen ax^2 + bx + c = 0");
Console.WriteLine("a måste vara skiljt från 0.");

// Fråga användaren om koefficienterna för andragradsekvationen
Console.WriteLine("Ange värdet på a:");
double a = double.Parse(Console.ReadLine());
Console.WriteLine("Ange värdet på b:");
double b = double.Parse(Console.ReadLine());
Console.WriteLine("Ange värdet på c:");
double c = double.Parse(Console.ReadLine());

// Beräkna det som står under rottecknet (diskriminanten)
double p = b / a;
double q = c / a;
double diskriminant = (p / 2) * (p / 2) - q;

// Kontrollera lösningar beroende på vad som står under rottecknet (diskriminanten)
if (diskriminant > 0) // Två lösningar
{
    double rot1 = -(p / 2) + Math.Sqrt(diskriminant);
    double rot2 = -(p / 2) - Math.Sqrt(diskriminant);
    Console.WriteLine($"Ekvationen har två reella lösningar: {rot1} och {rot2}");
}
else if (diskriminant == 0) // En lösning
{
    double rot = -(p / 2);
    Console.WriteLine($"Ekvationen har en reell lösning: {rot}");
}
else // Negativ diskriminant, dela upp i två delar, en reell och en imaginär. a.k.a. "Inga reella lösningar"
{
    double reellDel = -(p / 2); // Första delen precis som vanligt i PQ
    // Den andra delen, den som är roten ur negativt tal, kan vi kalla imaginär
    // Byt tecken på den negativa diskriminanten och ta roten ur, lägg sen till "i" i utskriften
    double imagDel = Math.Sqrt(-diskriminant);
    Console.WriteLine($"Ekvationen har två imaginära lösningar: {reellDel} + {imagDel}i och {reellDel} - {imagDel}i");
}
```
