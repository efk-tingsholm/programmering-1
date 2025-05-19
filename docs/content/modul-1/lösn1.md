# Lösningsförslag - Modul 1

## Uppgift 1
```csharp
static void Main(string[] args)
{
	Console.WriteLine("Hello World!");
}
```

## Uppgift 2
```csharp
static void Main(string[] args)
{
	Console.WriteLine("Det här programmet skriver ut text.");
	Console.WriteLine("Men på flera rader.");
	Console.WriteLine();
	Console.WriteLine("Och ibland med helt tomma rader.");
}
```

## Uppgift 3
```csharp
static void Main(string[] args)
{
    Console.WriteLine("Vissa tecken är \"reserverade\" av programspråket.");
}
```

## Uppgift 4
```csharp
static void Main(string[] args)
{
    Console.WriteLine("  / \\");
    Console.WriteLine(" /   \\");
    Console.WriteLine("/_____\\");
}
```




## Uppgift 5
```csharp
static void Main(string[] args)
{
    Console.ForegroundColor = ConsoleColor.Blue;
    Console.BackgroundColor = ConsoleColor.Yellow;
    Console.Clear();
    Console.WriteLine("Blå text med gul bakgrund.");

    Console.ResetColor();
    Console.WriteLine("Tryck Enter för att ändra färg.");
    Console.ReadLine();

    Console.ForegroundColor = ConsoleColor.Red;
    Console.BackgroundColor = ConsoleColor.White;
    Console.Clear();
    Console.WriteLine("Röd text med vit bakgrund.");
    Console.ResetColor();
}
```

## Uppgift 6
```csharp
static void Main(string[] args)
{
    Console.Beep(440, 500); // A
    Console.Beep(494, 500); // B
    Console.Beep(523, 500); // C
    Console.Beep(587, 500); // D
}
```

## Uppgift 7
```csharp
static void Main(string[] args)
{
    int wait = 600; //Vänta i 0,6 sekunder mellan varje ord
    Console.Write("Hej ");
    Thread.Sleep(wait);
    Console.Write("på ");
    Thread.Sleep(wait);
    Console.Write("dig!");
}
```

## Uppgift 8
```csharp
static void Main(string[] args)
{
	Console.Write("Vad heter du? ");
	string namn = Console.ReadLine();

	Console.Write("Hur gammal är du? ");
	string ålder = Console.ReadLine();

	Console.Write("Vad är din favoritmat? ");
	string favoritmat = Console.ReadLine();

	Console.WriteLine($"Hej vad trevligt att träffas {namn}, du är {ålder} år gammal och gillar {favoritmat}. Hoppas du får en trevlig dag!");
}
```

## Uppgift 9
```csharp
static void Main(string[] args)
{
    Console.Write("Vilket år är det nu? ");
    int nuvarandeÅr = int.Parse(Console.ReadLine());

    int förraÅret = nuvarandeÅr - 1;
    int omTioÅr = nuvarandeÅr + 10;

    Console.WriteLine($"Förra året var det {förraÅret}, och om tio år är det {omTioÅr}.");
}
```



## Uppgift 10
```csharp
static void Main(string[] args)
{
	Console.Write("Skriv in första talet: ");
	double tal1 = double.Parse(Console.ReadLine());

	Console.Write("Skriv in andra talet: ");
	double tal2 = double.Parse(Console.ReadLine());

	double differens = tal1 - tal2;
	double tal1UpphöjtTillTal2 = Math.Pow(tal1, tal2);
	double tal2UpphöjtTillTal1 = Math.Pow(tal2, tal1);

	Console.WriteLine($"Differensen mellan talen är {differens}.");
	Console.WriteLine($"{tal1} upphöjt till {tal2} är {tal1UpphöjtTillTal2}.");
	Console.WriteLine($"{tal2} upphöjt till {tal1} är {tal2UpphöjtTillTal1}.");
}
```

## Uppgift 11
```csharp
static void Main(string[] args)
{
    Console.Write("Skriv in första talet: ");
    double tal1 = double.Parse(Console.ReadLine());

    Console.Write("Skriv in andra talet: ");
    double tal2 = double.Parse(Console.ReadLine());

    Console.Write("Skriv in tredje talet: ");
    double tal3 = double.Parse(Console.ReadLine());

    double summa = tal1 + tal2 + tal3;
    double produkt = tal1 * tal2 * tal3;
    double medelvärde = summa / 3;

    Console.WriteLine($"Summan av talen är {Math.Round(summa,3)}.");
    Console.WriteLine($"Produkten av talen är {Math.Round(produkt, 3)}.");
    Console.WriteLine($"Medelvärdet av talen är {Math.Round(medelvärde, 3)}.");
}
```




## Uppgift 12
```csharp
Console.Write("Skriv in första talet: ");
double tal1 = double.Parse(Console.ReadLine());

Console.Write("Skriv in andra talet: ");
double tal2 = double.Parse(Console.ReadLine());

double addition = tal1 + tal2;
double subtraktion1 = tal1 - tal2;
double subtraktion2 = tal2 - tal1;
double multiplikation = tal1 * tal2;
double division1 = tal1 / tal2;
double division2 = tal2 / tal1;

Console.WriteLine($"Addition: {tal1} + {tal2} = {addition}");
Console.WriteLine($"Subtraktion (tal1 - tal2): {tal1} - {tal2} = {subtraktion1}");
Console.WriteLine($"Subtraktion (tal2 - tal1): {tal2} - {tal1} = {subtraktion2}");
Console.WriteLine($"Multiplikation: {tal1} * {tal2} = {multiplikation}");
Console.WriteLine($"Division (tal1 / tal2): {tal1} / {tal2} = {division1}");
Console.WriteLine($"Division (tal2 / tal1): {tal2} / {tal1} = {division2}");
```

## Uppgift 13
```csharp
static void Main(string[] args)
{
    Console.Write("Ange radien på cirkeln: ");
    bool giltigtTal = false;
    giltigtTal = double.TryParse(Console.ReadLine(), out double radie);

    if (giltigtTal)
    {
        double area = Math.PI * Math.Pow(radie, 2);
        double omkrets = 2 * Math.PI * radie;

        Console.WriteLine($"Arean på cirkeln är {area:F2}.");
        Console.WriteLine($"Omkretsen på cirkeln är {omkrets:F2}.");
    }
    else
    {
        Console.WriteLine("Felaktig inmatning, försök igen.");
    }
}
```

## Uppgift 14
```csharp
static void Main(string[] args)
{
    Console.Write("Hur mycket pengar sätter du in? ");
    double startKapital = double.Parse(Console.ReadLine());

    Console.Write("Vad är räntan (i procent)? ");
    double ränta = double.Parse(Console.ReadLine()) / 100;

    Console.Write("Hur många år ska pengarna stå? ");
    int tid = int.Parse(Console.ReadLine());

    double slutKapital = startKapital * Math.Pow(1 + ränta, tid);

    Console.WriteLine($"Efter {tid} år kommer du att ha {slutKapital} kr på kontot.");
}
```

## Uppgift 15
```csharp
static void Main(string[] args)
{
    Console.Write("Ange värdet på p: ");
    double p = double.Parse(Console.ReadLine());

    Console.Write("Ange värdet på q: ");
    double q = double.Parse(Console.ReadLine());

    double diskriminant = Math.Pow(p / 2, 2) - q;

    if (diskriminant < 0)
    {
        Console.WriteLine("Det finns inga reella rötter.");
    }
    else
    {
        double x1 = -(p / 2) + Math.Sqrt(diskriminant);
        double x2 = -(p / 2) - Math.Sqrt(diskriminant);

        Console.WriteLine($"Lösningarna är x1 = {x1} och x2 = {x2}.");
    }
}
```
