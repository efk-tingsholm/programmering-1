# Villkorsoperatorn

Villkorsoperatorn fungerar som en  if-sats, men på en rad. Användande av denna operator kan alltså spara rader och innebära en mer kompakt kod.

Villkorsoperatorn består av två tecken, ett frågetecken och ett kolon, enligt följande:  ?:

I nedanstående exempel används villkorsoperatorn för att utvärdera om variabeln number är större än noll, och strängen result tilldelas "positivt" eller "negativt".
```csharp
int number = 5;

string result = number > 0 ? "positivt" : "negativt";

Console.WriteLine($"Talet är {result}."); // Ger utskriften positivt.
```

Samma sak kan uppnås med en vanlig if-sats enligt följande.
```csharp
int number = 5;
string result;

if (number > 0)
{
    result = "positivt";
}
else
{
    result = "negativt";
}

Console.WriteLine($"Talet är {result}.");
```

Ett knep för att komma ihåg syntaxen för villkorsoperatorn:
```
Är villkoret sant ? Ja : Nej
```


Jämför detta med det föregående exemplet.
```csharp
//              Villkoret  ?     Ja     :    Nej
string result = number > 0 ? "positivt" : "negativt";
```
