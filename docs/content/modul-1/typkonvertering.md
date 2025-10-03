# Typkonvertering

Att omvandla information från en datatyp till en annan kan kallas för att typkonvertera, att byta typ.

## Implicit konvertering
I vissa situationer kan typkonvertering ske utan att en specifik operator används, bara genom att tilldela informationen till en variabel med den önskade datatypen. Detta är generellt genomförbart när ingen information eller precision går förlorad.

Heltalsvärdet 3 kan utan vidare göras om till flyttal. Från en datatyp med mindre information/precision till en med mer.
```csharp
int a = 3;

// Värdet från integer a sparas som flyttal
float b = a;
double c = a;
```

Att implicit konvertera åt andra hållet, från en datatyp med mer information/precision, går inte att göra implicit. Exempelvis kan inte 4,3 utan vidare skrivas som ett heltal.
```csharp
double a = 4.3;

// Båda följande rader ger upphov till kompileringsfel
int b = a; // ERROR
float c = a; // ERROR, notera att float har lägre precision än double
```

---


## Explicit konvertering - Casting
När en typkonvertering innebär förlust av precision, exempelvis från float till int, kan ibland **casting**, eller type casting, användas. Jag har inte hittat ett fint svenskt ord. 

Detta innebär att man i källkoden skriver den datatyp som informationen ska konverteras till inom parenteser innan värdet som ska konverteras
```csharp
float a = 9.8f;

// Konvertera värdet i "a" till int, tilldela till b.
int b = (int)a

// Notera, avrundar INTE. Trunkerar, alltså skär bort decimaler.
Console.WriteLine(b) // Ger utskriften 9.
```

---


## Hjälpmetoder
Det finns lite hjälpmetoder som kan lösa konvertering när inte casting fungerar, ofta handlar det om att konvertera en sträng till ett tal.
### Parse()
Parse är en metod som finns i de flesta numeriska datatyper, såsom int, float, double och så vidare. Denna tar emot en sträng och försöker konvertera till ett tal. Om konverteringen misslyckas ger det upphov till ett exekveringsfel, och programmet "kraschar".

Exempelvis kan strängen "19" konverteras till ett heltal via metoden int.Parse().
```csharp
// Notera att detta är en sträng med 1 och 9, inte ett tal.
string text = "19"; 

// Anropar Parse via datatypen int för att konvertera till int.
int number = int.Parse(text);

// Parse finns även tillgänglig för double.
double number2 = double.Parse("12,34");

// Om man skickar in trams uppstår exekveringsfel.
float number3 = float.Parse("Trams"); //ERROR
```

!!! tip "Tips"
    Ett annat klassiskt sätt att uppnå exekveringsfel med metoden int.Parse() är genom att skriva in "2147483648", alltså dryga två miljarder.

    Detta för att värdet överskrider den maximala storleken för en int.





### TryParse()
För att hantera situationer där trams kan uppstå, se källkoden ovan, kan metoden TryParse() användas. Den är precis som Parse() men ger inga exekveringsfel om den tar emot felaktiga argument, såsom "Trams". 

I Likhet med Parse() finns TryParse() tillgänglig i numeriska datatyper. Däremot är syntaxen lite annorlunda, eftersom TryParse() gör två saker, berättar om det gick att konvertera, och ger oss det konverterade värdet.

Exempelvis så kan strängen "19" konverteras, igen.
```csharp
string text = "19";
int number; // Här ska resultatet av konverteringen sparas
bool isNumber = int.TryParse(text, out number);

Console.WriteLine(number); // Ger utskriften 19.
Console.WriteLine(isNumber); // Ger utskriften True.
```
Notera hur vi får ut resultatet från konverteringen, alltså heltalet 19, via "out number" i exemplet. Metoden i sig returnerar en bool som talar om huruvida konverteringen var framgångsrik, i ovanstående exempel blir den *True*. 

Om konvertering misslyckas returneras istället *False*. Resultatet från konverteringen, som då inte kunde göras, blir värdet 0. Se nedan.
```csharp
string text = "Trams";
int number; // Här ska resultatet av konverteringen sparas
bool isNumber = int.TryParse(text, out number);

Console.WriteLine(number); // Ger utskriften 0.
Console.WriteLine(isNumber); // Ger utskriften False.
```

### ToString()
I vissa situationer har man behov av att konvertera något till en sträng, metoden ToString() kan appliceras på det mesta.

Notera hur den anropas genom att skriva ".ToString()" efter det som ska konverteras.
```csharp
double a = 123.456;
string b = a.ToString(); // b tilldelas strängen "123,456".
```




### Hjälpklassen Convert
Klassen Convert är som en samlingsklass som innehåller flertalet konverteringsmetoder på samma ställe. Dessa anropar egentligen bara Parse utan att vi ser det.

Överlag rekommenderas Parse() eller TryParse(). 

Med hjälp av metoder från klassen Convert kan liknande konverteringar som ovan genomföras.
```csharp
// Går alldels utmärkt.
int a = Convert.ToInt32("19"); 

// Notera att namngivningen för float är lite annorlunda
float b = Convert.ToSingle("1,2"); 
```





