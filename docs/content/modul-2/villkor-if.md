# If-sats

Det är oftast önskvärt att ett program kan utvärdera givna villkor och välja vilken eller vilka kodrader som ska utföras och i vilken ordning. Ett sådant val, att välja, kallas **selektion**.

Ett vanligt alternativ är **if-satsen**, som kan kombineras med `else if` och `else` för att passa olika situationer.

## If
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

---


## else
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


---


## else if
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

!!! tip "Tips"
    Det går att nästla många villkorssatser, men ju fler satser som nästlas i varandra desto sämre blir läsbarheten. 

    Var uppmärksam på detta och undvik i möjligaste mån att gröta till det.