# Villkorssatser

Det är oftast önskvärt att ett program kan utvärdera givna villkor och välja vilken eller vilka kodrader som ska utföras och i vilken ordning. Ett sådant val, att välja, kallas **selektion**.

Nedan presenteras både if-satser och switch-case uttryck, dessa båda villkorssatser uppnår samma resultat, men ser lite olika ut. Lite förenklat kan switchuttryck sägas vara effektivare när det finns många alternativ. 

## If-satser
### If
En if-sats är ett villkorat kodblock. Källkoden som står inne i blocket körs bara om villkoret mellan parenteserna är sant. Villkoret mellan parenteserna måste vara ett boolskt uttryck.

```csharp
if (a > 3)
{
    Console.WriteLine("a är större än 3!");
}

// ALLA kodrader inne i blocket utförs om villkoret är sant.
if (namn == "Emil")
{
    Console.WriteLine("Personen heter Emil.");
    Console.WriteLine("I övrigt ett väldigt tjusigt namn.");
}
```

```csharp
string namn = "Emil";
bool lärare = true;

// Villkoret, koden mellan parenteserna, kan vara sammansatt.
if (namn == "Emil" && lärare == true)
{
    Console.WriteLine("Personen heter Emil och arbetar som lärare.");
}

// Notera att det räcker med enbart den boolska variabeln. 
if (namn == "Emil" && lärare) 
{
    Console.WriteLine("Personen heter Emil och arbetar som lärare.");
}
```
### else
Kompletterar en if-sats. Koden i else-blocket körs om if-satsen INTE är sann. Else har inget eget villkor, och kan inte användas fristående från en if-sats.
```csharp
int a = 8;
int b = 0;

if (a >= 10)
{
    b = 100; // Om a är större än eller lika med 10.
}
else
{
    b = -30; // Om a INTE är det.
}

Console.WriteLine(b); // Utskriften ger -30.
```
### else if
Kan användas för att skapa en kedja av villkor, där varje villkor utvärderas om det föregående villkoret är falskt.
```csharp
int a = 1;

if (a > 4) // Falskt.
{
    Console.WriteLine("Högre än fyra!");
}
else if (a < 0) // Falskt.
{
    Console.WriteLine("Lägre än noll!");
}
else // Enda kvarvarande alternativet.
{
    Console.WriteLine("Högre än noll, lägre än fem!");
}
```

---


## Switch
Ett switchuttryck jämför värdet på en variabel med flera olika alternativ. Det är användbart om variabeln bara kan anta ett begränsat antal värden, exempelvis veckordagar.

Exemplet nedan tar in ett namn från användaren, och sen kan ett av fyra cases inträffa. Notera hur varje case avslutas med nyckeordet break, utan detta kommer nästa case också exekveras.
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




I nedanstående exempel har case 2 inget innehåll och avslutas inte med break. Detta leder till att case 3 utförs. Användbart om flera alternativ ska leda till samma utfall.
```csharp
int a = 2;
switch (a)
{
    case 1:
        Console.WriteLine("Värdet är 1");
        break;

    case 2:
		// Om a är 2 kommer vi att "ramla ner" i case 3.
		
    case 3:
        Console.WriteLine("Värdet kan vara 2 eller 3.");
        break;

    default: 
	    Console.WriteLine("Värdet är något annat!");
        break;
}
```

För nyare versioner av C# kan man också specificera intervall för numeriska värden i switchuttryck, se nedanstående exempel.
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

## Nästlade villkorssatser
Det går bra att ha en villkorssats inuti en annan villkorssats, dessa kallas då nästlade (nested). 

Exempel på nästlade if-satser.
```csharp
if (number > 10)
{
    Console.WriteLine("Talet är större än 10.");

    if (number > 20)
    {
        Console.WriteLine("Talet är större än 20.");
    }
    else
    {
        Console.WriteLine("Talet är 20 eller mindre.");
    }
}
else
{
    Console.WriteLine("Talet är 10 eller mindre.");
}
```



Det går också att nästla switchuttryck, det fungerar på samma sätt som för if-satser, men då syntaxen för switchuttrycken är mer omfattande sjunker läsbarheten snabbt.



!!! tip "Tips"
    Det går att nästla många villkorssatser, men ju fler satser som nästlas i varandra desto sämre blir läsbarheten. 

    Var uppmärksam på detta och undvik i möjligaste mån att gröta till det.


