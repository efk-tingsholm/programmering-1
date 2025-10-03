# Arrayer

En **array** är en datastruktur som kan lagra flera värden av samma datatyp och är ett effektivt sätt att hantera många relaterade värden samtidigt. 

Varje värde i en array kallas för ett **element** och är **indexerat** med en position, där det första elementet har index 0. Indexeringen fungerar på samma sätt som för tecken i strängar och andra samlingar.

Arrayer är snabba och effektiva, men de har ett **fast antal platser** som bestäms vid skapandet och kan därmed inte växa eller krympa efter behov.

Arrayer kan göras i flera dimensioner, där en **endimensionell array** (1D) är att likna vid en vanlig lista med saker, men med ett bestämt antal platser. En **tvådimensionell array** (2D) är mer att likna vid ett koordinatsystem, där både rad och kolumn spelar roll. Inledningsvis behandlas enbart endimensionella arrayer.

(ATT GÖRA: tips om namnet array? heta annat på svenska?)

## Deklaration
När en array deklareras behövs både datatyp och variabelnamn. Hakparentes används för att specificera att det är en array och inte en vanlig variabel.

För att kunna använda arrayen måste den initieras, det måste reserveras plats i minnet för ett givet antal värden av en viss datatyp, detta uppnås via nyckelordet new. (Som tidigare använts i samband med slumpade tal!)

Precis som med vanliga variabler kan arrayer deklareras och initieras på lite olika sätt.

#### Deklarera utan storlek
```csharp
int[] tal; // En array som kan lagra värden av datatypen int.
```

#### Deklarera och initiera med storlek
Varje element får sitt standardvärde, i fallet med int så är det 0.
```csharp
int[] tal = new int[5]; // En array som kan lagra 5 st heltal
```

#### Deklarera och initiera med storlek och värden
Kan numer också göras utan nyckelordet new, eller ja, kompilatorn sköter det åt oss. Demonstrerar både med string och int. Båda alternativen går bra, det undre är smidigare då man slipper skriva lika mycket.
```csharp
// En int-array med 5 platser
int[] tal = new int[] {1, 2, 3, 4, 5}; 

// En string-array med 3 platser
string[] tal = {"hej", "på", "dig"};
```


!!! tip "Modern deklaration"
    Notera att från och med C# 12.0 (alltså NET 8.0) så kan arrayer (och listor) även initieras med hakparenteser []. Tidigare enbart klammerparenteser {}.

    ```csharp
    int[] tal = [7, 8, 13]; // Bara nu
    int[] tal2 = {7, 8, 13}; // Förr och nu
    ```



---

## Använda och ändra värden
Arrayens värden nås genom dess **index**, där index börjar på 0. Med hjälp av index kan elementen i en array användas eller ändras.

```csharp
// Skapa en array med bokstäverna k a t t
char[] bokstaver = { 'k', 'a', 't', 't' };

// Element kan skrivas ut
Console.WriteLine(bokstaver[1]); // Ger utskriften a.

// Element kan sparas i en egen variabel
char tecken = bokstaver[2]; // Får värdet t.

// Element kan ändras, tilldela positionen i arrayen ett nytt värde
bokstaver[0] = 'H'; // H istället för k, nytt ord. 

// Gå också att använda range-operatorn .. för att få del av array
char[] nyArray = bokstaver[..2]; // Får elementen: H a
```



Notera att det inte går att anropa ett element som inte finns, exempelvis så har en array med 5 platser index från 0 till och med 4, se nedan.
```csharp
// En int-array med 5 platser
int[] tal = new int[] {1, 2, 3, 4, 5}; 

// Trams
Console.WriteLine(bokstaver[9]); // Ger exekveringsfel med meddelande "Index was outside the bounds of the array".
```


!!! tip "Index baklänges"
    Det går också att räkna från slutet i en samling med hjälp av "index from end"-operatorn ^.

    ```csharp
    string[] textArray = ["hej", "på", "dig", "!"];
    Console.WriteLine(textArray[^2]); // Ger utskriften dig
    ```



---

## Iterera över array
Arrayer används ofta tillsammans med loopar för att arbeta med alla element samtidigt. 

Iterera över en array är alltså samma sak som att "loopa genom arrayen", att gå igenom arrayen och utföra samma kodsekvens för varje element.

### For-loop
En for-loop kan användas, fördel här är att man har tillgång till index via räknevariabeln, exempelvis i. Notera att alla arrayer har egenskapen Length, som kan användas för att veta hur många element arrayen har.
```csharp
// En int-array med 4 element
int[] talArray = { 14, 20, 25, 17 };

// Iterera över arrayen och skriv ut värdet för varje element
for (int i = 0; i < talArray.Length; i++)
{
	// Värdet för det aktuella indexet, och mellanslag efteråt
    Console.Write(talArray[i] + " ");
}

// Ger utskriften: 14, 20, 25, 17
```

### Foreach-loop
Ett alternativ är foreach, som automatiskt går igenom alla element utan att behöva använda index. 

```csharp
// En int-array med 4 element
int[] talArray = { 14, 20, 25, 17 };

// Iterera över arrayen och skriv ut respektive värde
foreach (int tal in talArray) 
{
	// Som ovanstående exempel, värdet följt av mellanslag
    Console.Write(tal + " ");
}

// Ger utskriften: 14, 20, 25, 17
```


### Jämförelse for och foreach
En for-loop använder en räknevariabel, ofta `i`, för att ändra index, den kan alltså bara användas på samlingar som är indexerade. Foreach-loopen använder inte index och kan därmed användas på alla samlingar. Foreach-loopen kan också sägas ha lite högre läsbarhet.

Syftet med en foreach-loop är att gå igenom en samling och hämta relevant information, inte att ändra i den. En foreach-loop är därmed read-only, det går alltså inte att ändra värdena. En for-loop däremot kan utan problem ändra i samlingen som itereras över.

Exempel, samma array som tidigare exempel, men med målsättningen att alla tal som är mindre än 20 ska få 5 adderat till sig, en förändring i arrayen.

```csharp
int[] talArray = { 14, 20, 25, 17 };

for (int i = 0; i < talArray.Length; i++)
{
	// Om talet är mindre än 20, så ta talet och lägg till 5.
    if (talArray[i] < 20)
    {
	    // Kan också göras med += operatorn
        talArray[i] = talArray[i] + 5;
    }
}
// Arrayens element efter loopen: 19, 20, 25, 22.
// Notera hur de två element som var lägre än 20 har tagits + 5.
```


!!! tip "Vilken loop ska användas?"
    Ska information hämtas och användas? Använd foreach. 

    Ska information ändras, eller behövs index av någon anledning, exempelvis skriva ut tal? Använd for.



---

## Egenskaper och metoder
Det finns en hel del egenskaper och metoder tillhörande arrayer. Notera hur metoderna anropas på olika sätt. Nedan presenteras ett urval av dessa.

### Egenskaperna Rank och Length
```csharp
// En 2D-array med två rader och tre kolumner
int[,] tdArray3 = { { 1, 2, 3 }, { 4, 5, 6 } };

// Egenskapen Rank anger hur många dimensioner en array har
Console.WriteLine(tdArray3.Rank); // Ger utskriften 2

// Egenskapen Length anger hur många element arrayen har totalt
int elementCount = tdArray3.Length; // Variabeln får värdet 6
```

### Contains()
Metoden Contains() undersöker om något av elementen i arrayen har ett givet värde, returnerar true/false. Anropas via arrayens variabelnamn.
```csharp
string[] tal = {"hej", "på", "dig"};

bool finnsDet = tal.Contains("på"); //Variabeln får värdet true
```

### GetLength()
Metoden GetLength() returnerar hur många element arrayen har i en given dimension. Användbart när arrayen har fler än en dimension.
```csharp
// En 2D-array med två rader och tre kolumner
int[,] tdArray3 = { { 1, 2, 3 }, { 4, 5, 6 } };

// Hur många element i första dimensionen, rad
Console.WriteLine(tdArray3.GetLength(0)); // Ger utskriften 2

// Hur många element i andra dimensionen, kolumn
int numOfColumns = tdArray3.GetLength(1); // Variabeln får värdet 3
```


### Clear()
Metoden Clear() gör precis vad man kan tänka sig, rensar innehållet från en array. Notera att den anropas via klassen Array, till skillnad från de två tidigare metoderna.
```csharp
string[] ord = {"hej", "på", "dig"};

// Anroper metoden Clear(), skickar in vår array som argument
Array.Clear(ord);

// Testar Contains() igen, men får false nu, arrayen är rensad!
bool finnsDet = ord.Contains("på"); //Variabeln får värdet false
```


### IndexOf() och LastIndexOf()
Letar upp ett givet värde och returnerar dess index. Anropas via klassen Array.
```csharp
char[] bokstaver = { 'k', 'a', 't', 't' };

// Hittar index för första t:et
int first = Array.IndexOf(bokstaver, 't'); // Får värdet 2

// Hittar index för andra t:et
int last = Array.LastIndexOf(bokstaver, 't'); // Får värdet 3
```

### Sort() och Reverse()
```csharp
int[] tal = [5, 18, 93, 17];

// Sorterar värdena i arrayen. 
Array.Sort(tal);

// Byter ordning på värdena i arrayen.
Array.Reverse(tal);

// Skriver ut alla värden separerade av mellanslag.
foreach (var item in tal)
{
    Console.Write($"{item} ");
}

// Loopen ger utskriften: 93 18 17 5
// Eftersom arrayen först sorterades, och sen byttes ordning på
```


!!! tip "Tips"
    Höhöhö metoden Resize() höhö.
 



---

## Tvådimensionella Arrayer
Som bekant kan en tvådimensionell array användas för att representera information som ett rutnät/koordinatsystem/liknande. Ett annat perspektiv är att informationen helt enkelt utgörs av ett visst antal rader som alla är lika långa.
```
En 3x3 array, tre rader som alla är tre element långa.
Alt. "Tre rader och tre kolumner"
X X X
X X X
X X X

En 2x4 array skulle kunna representeras enligt följannde.
Alltså två rader och fyra kolumner.
X X X X
X X X X
```

I en 1D-array, string, eller annan endimensionell samling så användas index för att hänvisa till ett specifikt element. Det fungerar på motsvarande sätt för 2D-arrayer, med tillägget att man måste ange index för BÅDE rad och kolumn. Man kan alltså tänka sig ett radindex och ett kolumnindex, båda börjar på 0. Dessa används via hakparentes enligt: \[rad, kolumn].
```
rad	0 1 2 <- kolumn
0	B X X
1	X X X
2	X A X

Värdet A har position [2,1]
Värdet B har position [0,0]
```


### Deklaration
2D-arrayer skapas enligt samma koncept som 1D-arrayer, med skillnaden att ett kommatecken används för att göra arrayen till 2D.
```csharp
// Bara namnet
int[,] tdArray1;

// En tom 3x4 array
int[,] tdArray2 = new int[3,4];

// En 2x3 array med värden
int[,] tdArray3 = { { 1, 2, 3 }, { 4, 5, 6 } };
```

### Användning och ändring av värden
Användning och ändring av värden sker enligt samma princip som för 1D-arrayer, men enligt syntaxen \[rad, kolumn].
```csharp
// En 2x3 array med värden
int[,] tdArray3 = { { 1, 2, 3 }, { 4, 5, 6 } };

Console.WriteLine(tdArray3[1,0]); // Ger utskriften 4
```
### Iterera med nästlade For-loopar eller foreach
Att gå igenom alla värden i en 2D-array sker på motsvarande sätt som för 1D-arrayer.

#### Foreach
Foreach-loopen går helt enkelt igenom alla värden, oavsett hur många rader respektive kolumner som finns.
```csharp
// En 2x3 array med värden
int[,] tdArray3 = { { 1, 2, 3 }, { 4, 5, 6 } };

foreach (int tal in tdArray3)
{
    Console.WriteLine(tal);
}
```


#### Nästlade for-loopar
För att gå igenom alla värden i en 2D-array med hjälp av for-loopar behöver man nästla dem. I nedanstående ändras varje värde i arrayen genom addition med 5. Räknevariablerna `i` och `j` motsvarar index för rad respektive kolumn. Går självklart att byta namn från i och j.
```csharp
// En 2x3 array med värden
int[,] tdArray3 = { { 1, 2, 3 }, { 4, 5, 6 } };

// Använd .GetLength(0) för att hitta antal rader
for (int i = 0; i < tdArray3.GetLength(0); i++)
{
	// Använd .GetLength(1) för antal kolumner
    for (int j = 0; j < tdArray3.GetLength(1); j++)
    {
        // Öka varje värde med 5
        tdArray3[i,j] = tdArray3[i,j] + 5;
    }
}
```


!!! tip "Tips"
    För flerdimensionella arrayer fungerar det enligt samma koncept som tvådimensionella, nästla fler loopar och använd .GetLength() för respektive längd.




Ev. ATT GÖRA: Arrayer och metoder... hmm.. referenstyp? 


