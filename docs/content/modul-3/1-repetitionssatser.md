# Repetitionssatser

Det är ofta önskvärt att ett program kan utföra viss kod flera gånger. Detta kan kallas att repetera, loopa eller **iterera**. Genom **iteration** kan ett program utföra samma eller nästan samma kod flera gånger, antingen ett bestämt antal gånger eller så länge som ett givet villkor är sant.

Satser som upprepar kod brukar kallas loopar eller reptitionssatser. 

## While
En while-loop både ser ut och fungerar ungefär som en if-sats, med skillnaden att när koden i kodblocket genomförts så kontrolleras villkoret igen, och om det fortfarande är sant så upprepas kodraderna inuti kodblocket.

```csharp
int a = 1;
while (a < 5) // Upprepa loopen så länge som a är mindre än 5.
{
    // Alla kodrader inuti kodblocket upprepas.
    Console.WriteLine("Vi är i loopen, forever!");
}
```

I det ovanstående exemplet körs loopen ända tills programmet stängs av, ofta är det inte önskvärt, koden kan modifieras så att variabeln a ändras allt eftersom, vilket resulterar i att loopen inte upprepas för evigt.

```csharp
int a = 1;
while (a < 5)
{
    Console.WriteLine("Vi är i loopen!");
    a = a + 1; // Öka värdet på a med 1.
}

// Efter fyra "varv" kommer vi ut ur loopen, då a får värdet 5.
Console.WriteLine("Nu är loopen klar!");
```

Ovanstående kod ger följande utskrift:
```
Vi är i loopen!
Vi är i loopen!
Vi är i loopen!
Vi är i loopen!
Nu är loopen klar!
```

---

## do-while
Ett specialfall av while-loopen, som kan vara användbart om man alltid vill köra koden i loopen minst en gång. 

I följande exempel används en do-while-loop för att ta in ett tal som är större än 10 från användaren.

```csharp
int number;

do
{
    Console.Write("Ange ett tal större än 10: ");
    number = int.Parse(Console.ReadLine());

} while (number <= 10);

Console.WriteLine($"Du angav {number}, vilket är större än 10.");
```

Notera att samma sak kan uppnås med en vanlig while-loop.

```csharp
int number = 0;

while (number <= 10)
{
    Console.Write("Ange ett tal större än 10: ");
    number = int.Parse(Console.ReadLine());
}

Console.WriteLine($"Du angav {number}, vilket är större än 10.");
```

---

## For
En for-loop upprepar koden i kodblocket ett bestämt antal gånger. Fungerar som en vanlig while-loop men har en inbyggd "räknare". 
```csharp
// i är räknevariabeln, börjar här med värdet 0.
// i < 5 är villkoret, så länge det är sant körs loopen.
// i++ körs i slutet av varje iteration, ökar värdet på i med ett.

for (int i = 0; i < 5; i++)
{
    Console.WriteLine("Hej");
}
```

For-loopar är användbara när man vet hur många gånger koden behöver upprepas.

Ofta har man nytta av att använda räknevariabeln inne i loopen. 
```csharp
int num = 5;

// Skriver ut 5:ans gångertabell, då num har värdet 5.
for (int i = 1; i < 11; i++)
{
    Console.WriteLine($"{i} * {num} = {i * num}");
}
```
Ovanstående exempel ger följande utskrift.
```
1 * 5 = 5
2 * 5 = 10
3 * 5 = 15
4 * 5 = 20
5 * 5 = 25
6 * 5 = 30
7 * 5 = 35
8 * 5 = 40
9 * 5 = 45
10 * 5 = 50
```

!! TODO: räknevariabelns räckvidd -> i finns inte utanför loopen

!! TODO: for-reverse snippeten

---

## Foreach
Foreach-loopen är specialdesignad för att gå igenom listor, arrayer och andra samlingstyper. 

En foreach-loop upprepar koden i kodblocket så många gånger som det finns element i samlingen. 

Om man inte känner till arrayer och listor kan foreach-loopen också demonstreras på en sträng, som tekniskt sett är en samling av tecken (char).
```csharp
// Samlingen ifråga, en sträng med 3 element.
string text = "hej";

// Ungefär "För varje grej i samlingen text, gör det här!"
foreach (var item in text) // "item" kan ändras till vad man vill.
{
    // Här anropas "item", som då motsvarar respektive element i samlingen.
    // Först h, sen e och till sist j.
    Console.WriteLine(item);
}
```

Föregående exempel ger utskriften:
```
h
e
j
```

---

## Nästlade repetitionssatser
Det går alldeles utmärkt att skriva loopar inne i andra loopar. Detta kallas nästlade loopar. 

Det här kan vara användbart när man itererar över (går igenom) flerdimensionella datastrukturer, 2D och uppåt. Konkreta exempel kan vara att skriva ut gångertabeller, spelplaner och annat som har både längd och bredd.

Nedanstående exempel skriver ut "Hej!" sex gånger. 
```csharp
// Yttre loop, körs två gånger.
for (int i = 0; i < 2; i++)
{
	// Inre loop, körs 3 gånger FÖR varje varv av den yttre.
	// Notera hur det inte går att använda variabelnamnet i igen.
    for (int j = 0; j < 3; j++)
    {
        Console.WriteLine("Hej!");
    }
}
```

Nästlade loopar kan användas för att skriva ut tvådimensionella strukturer, tänk spelplaner, schackbräden eller sänka skepp. 
```csharp
// Antal gånger yttre loopen går motsvarar antal rader.
for (int i = 0; i < 3; i++)
{
    // Antal gånger inre loopen går motsvarar antal kolumner.
    for (int j = 0; j < 3; j++)
    {
        Console.Write("X ");
    }
    Console.WriteLine(); // Ny rad innan näst rad påbörjas
}
```
Ovanstående exempel ger utskriften:
```
X X X
X X X
X X X
```


---

## break och continue
I repetitionssatser kan nyckelorden break och continue användas.

Nyckelordet **break** avbryter helt repetitionssatsen.
```csharp
for (int i = 1; i <= 10; i++)
{
    if (i == 5)
    {
        break; // Avbryter loopen när i är 5.
    }
    Console.WriteLine(i);
}

Console.WriteLine("Loopen avbröts vid i = 5.");
```

```
1
2
3
4
Loopen avbröts vid i = 5.
```

Nyckelordet **continue** avbryter det aktuella "varvet" i repetitionssatsen och påbörjar nästa varv.
```csharp
for (int i = 1; i <= 10; i++)
{
    if (i == 5)
    {
        continue; // Hoppar över resten av loopen när i är 5.
    }
    Console.WriteLine(i);
}

Console.WriteLine("Talet 5 hoppades över i loopen.");
```

```
1
2
3
4
6
7
8
9
10
Talet 5 hoppades över i loopen.
```