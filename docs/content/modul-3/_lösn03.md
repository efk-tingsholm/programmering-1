# Lösningsförslag - Modul 3


## Uppgift 1
```csharp
// Skriv ut tal från 0 till och med 30 
for (int i = 0; i <= 30; i++)
{
    Console.WriteLine(i);
}

// Vänta på knapptryckning 
Console.WriteLine("Tryck på valfri tangent för att fortsätta...");
Console.ReadKey();

// Räkna ned från 30 till -30
for (int i = 30; i >= -30; i--)
{
    Console.WriteLine(i);
}
```

## Uppgift 2
```csharp
// Input
Console.WriteLine("Ange ett ord eller en mening:");
string input = Console.ReadLine();

// Skriv ut varje tecken
foreach (char c in input)
{
    Console.WriteLine(c);
}

// Skriv ut baklänges
Console.WriteLine("Baklänges:");
for (int i = input.Length - 1; i >= 0; i--)
{
    Console.Write(input[i]);
}
```


## Uppgift 3
```csharp
// Input
Console.WriteLine("Ange ett heltal:");
int number = int.Parse(Console.ReadLine());

// Skriv ut gångertabellen
for (int i = 1; i <= 10; i++)
{
    Console.WriteLine($"{i} x {number} = {i * number}");
}
```

## Uppgift 4
```csharp
// Input
Console.WriteLine("Ange ett startvärde:");
int start = int.Parse(Console.ReadLine());

Console.WriteLine("Ange ett stoppvärde:");
int stop = int.Parse(Console.ReadLine());

// Ev. byt plats på start och stopp
if (start > stop)
{
    int temp = start;
    start = stop;
    stop = temp;
}

// Räkna uppåt och skriv ut talen, lägg till på summan varje gång
int sum = 0;
for (int i = start; i <= stop; i++)
{
    Console.WriteLine(i);
    sum += i;
}

Console.WriteLine($"Summan av talen mellan {start} och {stop} är {sum}");

```


## Uppgift 5
```csharp
// Slump
Random rand = new Random();

// Hur många kast?
Console.WriteLine("Hur många gånger vill du kasta tärningarna?");
int numRolls = int.Parse(Console.ReadLine());

// Slå tärningarna och skriv ut resultatet, lägg till resultat på summan
int sum = 0;
for (int i = 0; i < numRolls; i++)
{
    int result = rand.Next(1, 7);
    Console.Write(result + " ");
    sum += result;
}

// Skriv ut info i slutet
Console.WriteLine();
Console.WriteLine($"Poängsumman för dina kast är: {sum}");
Console.WriteLine($"Medelpoängen för dina kast är: {(float)sum/numRolls:f2}");
```

## Uppgift 6
```csharp
// Input
Console.WriteLine("Ange ett positivt heltal större än 10:");
int number = int.Parse(Console.ReadLine());

// Skriv ut udda tal, räcker att börja på 1 och öka med 2 varje gång
Console.WriteLine("Udda tal:");
for (int i = 1; i <= number; i += 2)
{
    Console.Write(i + " ");
}

Console.WriteLine();

// Skriv ut jämna tal
Console.WriteLine("Jämna tal:");
for (int i = 0; i <= number; i += 2)
{
    Console.Write(i + " ");
}
```

## Uppgift 7
```csharp
bool exit = false;
while (exit == false)
{
    // Rensa så att det ser fint ut
    Console.Clear();

    // Huvudmenyn
    Console.WriteLine("Välj en operation:");
    Console.WriteLine("1. Addition");
    Console.WriteLine("2. Subtraktion");
    Console.WriteLine("3. Multiplikation");
    Console.WriteLine("4. Division");
    Console.WriteLine("5. Avsluta");

    // Input
    int choice = int.Parse(Console.ReadLine());

    // Ta bara in tal om användaren inte avslutar
    double num1 = 0;
    double num2 = 0;
    if (choice != 5)
    {
        Console.WriteLine("Ange första talet:");
        num1 = double.Parse(Console.ReadLine());
        Console.WriteLine("Ange andra talet:");
        num2 = double.Parse(Console.ReadLine());
    }

    // Menyvalet
    switch (choice)
    {
        case 1:
            Console.WriteLine($"Resultat: {num1} + {num2} = {num1 + num2}");
            break;

        case 2:
            Console.WriteLine($"Resultat: {num1} - {num2} = {num1 - num2}");
            break;

        case 3:
            Console.WriteLine($"Resultat: {num1} * {num2} = {num1 * num2}");
            break;

        case 4:
            if (num2 != 0)
            {
                Console.WriteLine($"Resultat: {num1} / {num2} = {num1 / num2}");
            }
            else
            {
                Console.WriteLine("Division med noll är inte tillåtet.");
            }
            break;

        case 5:
            Console.WriteLine("Tack och hej!");
            exit = true;
            break;

        default:
            Console.WriteLine("Ogiltigt val, försök igen.");
            break;
    }

    Console.WriteLine("Tryck på valfri tangent för att fortsätta...");
    Console.ReadKey();
}
```



## Uppgift 8
```csharp
// Input
Console.WriteLine("Ange ditt namn:");
string userText = Console.ReadLine();

// Ange längd
Console.WriteLine($"Strängens längd är: {userText.Length} tecken");

// Kontrollera villkor
if (userText.Contains('a'))
{
    Console.WriteLine("Strängen innehåller bokstaven 'a'");
}
else
{
    Console.WriteLine("Strängen innehåller inte bokstaven 'a'");
}

if (userText.StartsWith('b'))
{
    Console.WriteLine("Strängen inleds med bokstaven 'b'");
}
else
{
    Console.WriteLine("Strängen inleds inte med bokstaven 'b'");
}

// Byta ut 
string newText = userText.Replace('a', 'ä');
Console.WriteLine($"Namnet efter att ha bytt ut 'a' mot 'ä': {replacedName}");

// VERSALER
Console.WriteLine($"Namnet med versaler: {userText.ToUpper()}");
```

## Uppgift 9
```csharp
// Loopen går bara om bool:en är false
bool correctSentence = false;
while (!correctSentence)
{
    // Input
    Console.WriteLine("Skriv en mening:");
    string sentence = Console.ReadLine();

    // Kontrollera om meningen börjar med stor bokstav och slutar med punkt
    if (char.IsUpper(sentence[0]) && sentence.EndsWith('.'))
    {
        Console.WriteLine("Bra jobbat! Du skrev en korrekt mening.");
        correctSentence = true;
    }
    else
    {
        Console.WriteLine("Fel! Meningen måste börja med stor bokstav och sluta med en punkt. Försök igen.");
    }
}
```

## Uppgift 10
```csharp
// Namn på filen för highscore
string filePath = "highscore.txt";

// Kontrollera om en tidigare highscore finns
if (File.Exists(filePath))
{
    string previousHighscore = File.ReadAllText(filePath);
    Console.WriteLine($"Föregående spelare: {previousHighscore}");
}
else
{
    Console.WriteLine("Ingen föregående spelare kunde hittas.");
}

// Input
Console.WriteLine("Vad heter du?");
string playerName = Console.ReadLine();

// Håll koll på poängen med variabel
int score = 0;

// Ställ tre frågor, öka poängen om man svarar rätt
Console.WriteLine("Fråga 1: Vad är 2 + 2?");
if (Console.ReadLine() == "4") 
{ 
    score++; 
}
Console.WriteLine("Fråga 2: Vad är huvudstaden i Sverige?");
if (Console.ReadLine().ToLower() == "stockholm")
{
    score++;
}
Console.WriteLine("Fråga 3: Vilken färg har bananer?");
if (Console.ReadLine().ToLower() == "gul")
{
    score++;
}

// Skriv spelarens namn och poäng till filen
File.WriteAllText(filePath, $"{playerName}, {score}/3 poäng");

Console.WriteLine($"Tack för att du spelade! Du fick {score}/3 poäng.");
```

## Uppgift 11
```csharp
// Input och förklaring
Console.WriteLine("Ange ett uttryck (ex: 2+3, 5-1, 4*2, 8/4):");
string expression = Console.ReadLine();

// Variabler för operator och dess index (position i strängen)
char operation = ' ';
int operatorIndex = -1;

// Kolla vilket räknesätt det är och ta reda på dess index
if (expression.Contains('+'))
{
    operation = '+';
    operatorIndex = expression.IndexOf('+');
}
else if (expression.Contains('-'))
{
    operation = '-';
    operatorIndex = expression.IndexOf('-');
}
else if (expression.Contains('*'))
{
    operation = '*';
    operatorIndex = expression.IndexOf('*');
}
else if (expression.Contains('/'))
{
    operation = '/';
    operatorIndex = expression.IndexOf('/');
}

// Plocka ut talen från uttrycket, trim är smidigt när användare skriver mellanslag
string firstNumberStr = expression.Substring(0, operatorIndex).Trim();
string secondNumberStr = expression.Substring(operatorIndex + 1).Trim();

// Omvandla till heltal
int firstNumber = int.Parse(firstNumberStr);
int secondNumber = int.Parse(secondNumberStr);

// Utför beräkningen, spara i variabel
int result = 0;
switch (operation)
{
    case '+':
        result = firstNumber + secondNumber;
        Console.WriteLine($"{firstNumber} + {secondNumber} = {result}");
        break;
    case '-':
        result = firstNumber - secondNumber;
        Console.WriteLine($"{firstNumber} - {secondNumber} = {result}");
        break;
    case '*':
        result = firstNumber * secondNumber;
        Console.WriteLine($"{firstNumber} * {secondNumber} = {result}");
        break;
    case '/':
        if (secondNumber != 0)
        {
            result = firstNumber / secondNumber;
            Console.WriteLine($"{firstNumber} / {secondNumber} = {result}");
        }
        else
        {
            Console.WriteLine("Division med noll är inte tillåtet.");
        }
        break;
    default:
        Console.WriteLine("Ogiltigt uttryck.");
        break;
}
```

## Uppgift 12
```csharp
// Input
Console.WriteLine("Ange ett tecken:");
string symbol = Console.ReadLine();

Console.WriteLine("Ange bredd:");
int width = int.Parse(Console.ReadLine());

Console.WriteLine("Ange höjd:");
int height = int.Parse(Console.ReadLine());

// Varje rad
for (int i = 0; i < height; i++)
{
    // Skriv ut flera tecken på varje rad
    for (int j = 0; j < width; j++)
    {
        // Skriv bara ut symbolen OM
        // vi är på första raden eller kolumnen, i eller j är 0
        // vi är på sista raden eller kolumnen, dvs height - 1
        if (i == 0 || i == height - 1 || j == 0 || j == width - 1)
        {
            Console.Write(symbol + " ");
        }
        else
        {
            Console.Write("  ");
        }
    }
    Console.WriteLine();
}
```


## Uppgift 13
```csharp
// Input
Console.WriteLine("Ange höjden för triangeln:");
int height = int.Parse(Console.ReadLine());
Console.WriteLine("Ange tecknet för triangeln:");
char symbol = Console.ReadLine()[0];

// Första triangeln
Console.WriteLine();
for (int row = 1; row <= height; row++)
{
    for (int j = 1; j <= row; j++)
    {
        Console.Write(symbol + " ");
    }
    Console.WriteLine();
}

// Triangel åt höger
Console.WriteLine();
for (int i = 1; i <= height; i++)
{
    // Skriva ut mellanslagen, ska minska med rad
    for (int j = height; j > i; j--)
    {
        Console.Write("  ");
    }

    // Skriva ut symbolen, ska öka med rad
    for (int j = 0; j < i; j++)
    {
        Console.Write(symbol + " ");
    }

    //Ny rad
    Console.WriteLine();
}

// Triangel 3, pyramid, samma höjd som de andra
Console.WriteLine();
for (int i = 1; i <= height; i++)
{
    // Skriva ut mellanslagen på vänster, ska minska med rad
    for (int j = height; j > i; j--)
    {
        Console.Write("  ");
    }

    // Skriva ut symbolen, ska öka med rad
    // Använder villkoret när: j < 2i - 1 
    // Ex.
    // när i = 1 -> så går loopen en gång
    // när i = 2 -> då blir villkoret 3, så det blir * * *
    for (int j = 0; j < 2*i - 1; j++)
    {
        Console.Write(symbol + " ");
    }

    // Skriv ut mellanslagen på höger, minska med rad
    for (int j = height; j > i; j--)
    {
        Console.Write("  ");
    }

    // Ny rad
    Console.WriteLine();
}
```
