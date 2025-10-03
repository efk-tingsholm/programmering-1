# Stränghantering och formatering

## Strängar
I C# är en sträng en sekvens av tecken (char). Dessa kan manipuleras på olika sätt, exempelvis komma åt enskilda tecken, plocka isär och sätta ihop strängar och formatera dem på olika sätt.

Enskilda tecken i strängar kan kommas åt via tecknets **index**. Index är ett sätt att hålla koll på element i samlingar, och kommer användas i andra sammanhang än strängar också. Index börjar alltid på 0, så en sträng med 6 tecken kommer ha index från och med 0 till och med 5.
```csharp
// Index:      012345 
string text = "Hejsan";
char tecken = text[2]; // Tilldela värdet från index 2 till variabeln tecken

Console.WriteLine(tecken); // Ger utskriften j.
```

Man kan också specificera intervall för vilka tecken som ska kommas åt med följande syntax. Notera att den första indexangivelsen ingår i intervallet, men inte den andra, exempelvis från och med 2 till 4.
```csharp
// Index:      012345 
string text = "Hejsan";

// Från och med 2, till 4, dvs index 2 och 3
Console.WriteLine(text[2..4]); // Ger utskriften: js

// Från start till 2, dvs index 0 och 1.
Console.WriteLine(text[..2]); // Ger utskriften: He

// Från och med 3 till slutet, dvs index 3, 4 och 5
Console.WriteLine(text[3..]); // Ger utskriften: san

```

---

## Specialtecken i strängar
### Escape sequences
Teckenkombinationer bestående av backslash `\` följt av något annat tecken kallas "escape sequences", i brist på bra översättning. 

Kan användas för att skriva ut specialtecken såsom citattecken och backslash, som annars inte kan skrivas ut i text eftersom de har en egen funktion i strängar.
```csharp
Console.WriteLine("Backslash: \\"); // Ger utskrift: Backslash: \
Console.WriteLine("Citattecken: \""); // Ger utskrift: Citattecken: "
```

Det finns en del olika escape sequences, några exempel är:
`\n` för ny rad, `\t` för tab och `\b` för backspace.

### Interpolated strings
Stränginterpolering, aningen oklar gällande svenskt begrepp här. En interpolerad sträng är en sträng som kan innehålla variabeluttryck. Tidigare kunde detta genomföras via "string composite formatting", som har markant lägre läsbarhet.

För att göra en interpolerad sträng sätts `$` framför strängen. Variabler kan sedan användas inne i strängen inkapslade i klammerparenteser {}.
```csharp
string name = "Arne";
int age = 99;

Console.WriteLine($"Hej {name}, du är {age} år gammal!");
```

### Verbatim strings
Verbatim översätts till ordagrant. Det här är en metod för att få kompilatorn att tolka strängen ordagrant, precis som det står. För att uppnå detta sätts @ framför strängen. Notera att det här motverkar eventuella escape sequences såsom `\n` som redan finns i strängen.
```csharp
Console.WriteLine("Hej \n på dig."); // Ger en utskrift på två rader.

Console.WriteLine(@"Hej \npå dig."); // Ger utskriften: Hej \npå dig.
```


---

## Hantering av strängar
### Iterera över sträng
För att hantera strängar och deras innehåll kan man ha nytta av att gå igenom strängen och leta efter specifika tecken, exempelvis ett program som ska räkna hur många bokstäver av samma typ det finns i en sträng.
```csharp
string name = "Arne Bengtsson";
int count = 0;

// Iterera över strängen, A, r, n osv
for (int i = 0; i < name.Length; i++)
{
    if (name[i] == 'e')
    {
        count++;
    }
}
```

### Metoder
Det finns en uppsjö av metoder som kan vara behjälpliga vid hantering av strängar, ett urval av dessa presenteras nedan:

<!-- Replace() Alt ToArray() och sen ändra -->

- Replace()
- Contains()
- EndsWith()
- StartsWith()
- Equals()
- IndexOf()
- ToUpper()
- ToLower()
- Insert()
- Remove()
- SubString()
- length <-- en property (egenskap), så ingen parentes

Exempelvis kan Contains() användas för att undersöka om ett visst tecken finns i en sträng.
```csharp
string text = "Det här är min text!";
Console.WriteLine(text.Contains("n")); // Ger utskriften True
```



### Separera information
Ibland kan det föreligga behov av att dela upp information som användaren har skrivit, exempelvis om användaren skrivit både för och efternamn i en sträng, och denna information ska sparas i programmet i två separata variabler. 

Ett sätt att åstadkomma det med hjälp av metoderna IndexOf() och SubString() presenteras nedan.
```csharp
string name = "Arne Bengtsson";
int indexSpace;

// Hitta index för mellanslaget
indexSpace = name.IndexOf(' ');

// Gör nya strängar 
string firstName = name.Substring(0, indexSpace);
string lastName = name.Substring(indexSpace + 1);
```


---

## Formatering
### Tal
I interpolerade strängar kan man formatera värdena, genom att skriva ett kolon och sen en formatkod enligt följande: 
```
{variabel:formatkod}
```

Det finns flertalet olika formatkoder, några relevanta exempel är: 

- F (fixed-point), heltal/decimaltal med givet antal decimaler
- N (Number), tusentalsavgränsare och givet antal decimaler
- E (Exponential), grundpotensform med givet antal decimaler
- P (Procent), procentandel med givet antal decimaler
- C (Valuta), valuta med givet antal decimaler

Saker som vilken enhet valutan har och vilken tusentalsavgränsare som används är beroende på operativsystemets inställningar. Det givna antalet decimaler innebär en avrundning.

Exempelvis kan man avrunda tal med många decimaler, eller skriva stora tal tydligare. Notera att formatkoden inte är skiftlägeskänslig, och kan skrivas antingen med stor eller liten bokstav.
```csharp
double pi = 3.1415926535;
double num = 123456789;

Console.WriteLine($"Formatet f3 ger: {pi:f3}"); // 3,142
Console.WriteLine($"Formatet n0 ger: {num:n0}"); // 123 456 789
```




### Höger -och vänsterjustering
Det går att ange vilken bredd man vill att en interpolerad sträng ska ta upp, och ange om texten ska vara justerad åt något håll. Det här kan vara användbart om man vill skriva ut information i tabeller. Notera att -10 innebär att strängen totalt ska ta upp 10 tecken, och vara justerad åt vänster. 
```csharp
int num1 = 23;
int num2 = 19;

Console.WriteLine($"|{num1,-10}|");
Console.WriteLine($"|{num2, 10}|");
/* Ger utskriften:
|23        |
|        19|
*/
```

Positionsjustering kan kombineras med formateringen. Exemplet nedan avrundar värdet till 2 decimaler, samt högerjusterar över 6 teckens bredd.
```csharp
double temperatur = 12.345;
Console.WriteLine($"Högerjusterat: {temperatur,6:f2}");
```


https://learn.microsoft.com/en-us/dotnet/standard/base-types/standard-numeric-format-strings

