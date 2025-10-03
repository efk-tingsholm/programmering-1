# Switch
En switch-sats jämför värdet på en variabel med flera olika alternativ. Det är användbart om variabeln bara kan anta ett begränsat antal värden, exempelvis veckodagar.

If och switch används båda två för **selektion**. Lite förenklat kan switch sägas vara effektivare när det finns många alternativ. 

Exemplet nedan tar in ett namn från användaren, och sen kan ett av fyra fall (case) att inträffa. Notera hur varje `case` avslutas med nyckelordet `break`.
```csharp
string namn = Console.ReadLine();

switch (namn)
{
    case "Arne":
        Console.WriteLine("Du heter Arne.");
        break;

    case "Bodil":
        Console.WriteLine("Du heter Bodil.");
        break;

    case "Cecilia":
        Console.WriteLine("Du heter Cecilia.");
        break;

    default: // Om inget av de övriga fallen inträffar
        Console.WriteLine("Du heter något som inte känns igen av programmet.");
        break;
}
```

---


## Fall-through
Inte hittat en bra svensk översättning. 

I nedanstående exempel har case 2 inget innehåll och avslutas inte med break. Detta leder till att case 3 utförs. Detta fungerar endast eftersom case 2 varken har kod i sig eller ett avslutande `break`. 

Användbart om flera alternativ ska leda till samma utfall.
```csharp
int a = 2;
switch (a)
{
    case 1:
        Console.WriteLine("Värdet är 1");
        break;

    case 2:
		// Om a är 2 kommer vi att "falla igenom" case 2 och "ramla ner" i case 3.
		
    case 3:
        Console.WriteLine("Värdet kan vara 2 eller 3.");
        break;

    default: 
	    Console.WriteLine("Värdet är något annat!");
        break;
}
```

---



## Intervall
Kan uppnås med [relationsmönster](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/patterns#relational-patterns), kortfattat att man använder jämförelseoperatorer direkt i sitt case.


```csharp
int a = 10;
switch (a)
{
    case <= 5:
        Console.WriteLine("Värdet är mindre än eller lika med 5");
        break;

    case > 50 and < 100:
        Console.WriteLine("Värdet är större än 50 och mindre än 100.");
        break;

    default:
        Console.WriteLine("Värdet är något annat!");
        break;
}
```

---


## Switch-uttryck
Från engelskans [switch expression](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/switch-expression). 


Ett **switch‑uttryck** är en kompakt form av `switch` som tilldelar ett värde. Det passar när flera alternativ ska ge olika resultat (t.ex. namn, färg, text), utan att skriva hela kodblock som i en switch‑sats.

!!! info "Varför switch‑uttryck?"
    Kort och lättläst när målet är *ett värde*. Inga `case`/`break`; i stället används `mönster => uttryck`.


I nedanstående exempel tilldelas variabeln `veckodag` ett värde baserat på värdet i variabeln `tal`. Det första villkoret som stämmer utförs, precis som i en if-sats.
```csharp
int tal = 2;

// Tilldela värdet baserat på ett switch-uttryck för variabeln tal, lättläst.
string veckodag = tal switch
{
    1 => "Mån",
    2 => "Tis",
    3 => "Ons",
    4 => "Tors",
    5 => "Fre",
    6 => "Lör",
    7 => "Sön",
    _ => "Okänd dag"   // Default case, om tal är något annat värde än 1-7
};
```

---


### Intervall med switch-uttryck
Kan göras på motsvarande sätt som för vanliga switch-satser. Nedanstående exempel tilldelar variabeln `känsla` ett värde baserat på värdet i variabeln `celsius`.

```csharp
int celsius = 17;

string känsla = celsius switch
{
    < 0   => "Kallt",
    <= 25 => "Lagom",
    _     => "Varmt"
};
```






