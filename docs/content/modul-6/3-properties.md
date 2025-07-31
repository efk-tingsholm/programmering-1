# Properties i C#

## Vad är en Property?

<!-- ### Varför använda Properties istället för vanliga Getters och Setters? -->
Tidigare har vi använt metoder för att hämta och sätta värden. Där man måste skriva separata `Get`- och `Set`-metoder, vilket gör koden längre.

En **property** (egenskap) är en mekanism i C# för att hantera åtkomst till en privat variabel i en klass. Properties används för att kontrollera hur data läses och skrivs, vilket är en viktig del av **inkapsling** i objektorienterad programmering.

En property består av en **getter** och en **setter**:
```csharp
class Bil
{
    // Privat fält
    private int hastighet; 

    // Property
    public int Hastighet 
    {
        get { return hastighet; }
        set 
        {
            if (value > 0) // Validering av värdet
                hastighet = value;
        }
    }
}
```
Det finns fördelar med properties, exempelvis: 

- **Kortare och mer läsbar kod** – eliminerar behovet av separata getter- och setter-metoder.
- **Inkapsling och kontroll** – ser till att värden alltid sätts och hämtas enligt de regler vi definierat.
- **Inbyggd validering** – istället för att skapa en separat metod för att validera data, kan det göras direkt i `set`-blocket.

!!! tip "Tips"
    Ja, jag förstår att att det inte är mer läsbart första gången man ser det... 


### Exempel på hur en Property används i `Main()`
När en property har definierats kan den användas direkt i `Main()` för att sätta och läsa värden:
```csharp
class Program
{
    static void Main()
    {
        Bil minBil = new Bil();
        minBil.Hastighet = 100; // Använder propertyn för att sätta värdet
        Console.WriteLine("Bilens hastighet: " + minBil.Hastighet); // Läser värdet
    }
}
```
Man använder propertyn som en vanlig variabel, men med **validering** inbyggd!

!!! tip "Namngivning"
    En property bör alltid ha **stor bokstav i början** och motsvara namnet på det privata fältet.


---

## Auto-Properties
Om ingen validering eller extra logik behövs, kan man använda **auto-properties**, vilket gör koden mer kompakt:
```csharp
class Bil
{
    public int Hastighet { get; set; } // Auto-property
}
```

C# skapar automatiskt ett **privat fält i bakgrunden**, så att vi slipper skriva ut det manuellt.

> [!tip] **När ska auto-properties användas?**
> Om ingen validering behövs, är auto-properties ett bättre alternativ än att skapa ett privat fält + full property.

---

## Anropa Properties i Konstruktorn
För att skydda data med validering bör propertyn alltid användas i konstruktorn istället för att sätta fältet direkt. 

- Det säkerställer att valideringen från `set`-blocket återanvänds.
- Dubbel kod undviks och objektet skapas korrekt från början.

Genom att använda propertyn i konstruktorn säkerställs att valideringen används korrekt.

**Exempel – använder propertyn i konstruktorn**:
```csharp
class Bil
{
	// Privat fält
    private int hastighet;

	// Vanlig property, validering för set
    public int Hastighet
    {
        get { return hastighet; }
        set
        {
            if (value > 0)
                hastighet = value;
        }
    }

	// Konstruktorn, tar inkommande värde och tilldelar till property
    public Bil(int hastighetIn)
    {
        Hastighet = hastighetIn; // Använder propertyn för att säkerställa validering
    }
}
```


> [!summary] **Sammanfattning**
> - Använd alltid propertyn i konstruktorn, inte det privata fältet.
> - Detta säkerställer att eventuell validering används konsekvent.

---

## Properties utan både Get och Set
En property behöver inte alltid ha både `get` och `set`. 

### 1. Read-Only Properties (endast `get`)
Om ett värde **aldrig ska ändras** utanför klassen, kan vi ha en property med **bara `get`**:
```csharp
class Bil
{
    public string Färg { get; } // Auto-property med endast 'get', kan bara sättas i konstruktorn 

    public Bil(string färg)
    {
                Färg = färg; // Propertyn kan endast sättas vid objektets skapande
    }
}
```
**Används för:** ID:n, skapelsedatum, konstanta värden per objekt.

### 2. Write-Only Properties (endast `set`)
Om en property bara ska **kunna ta emot värden men inte läsas ut**, kan vi använda **bara `set`**:
```csharp
class SäkerData
{
    private string lösenord; // Privat fält lagrar värdet internt

        public string Lösenord // Property med endast 'set', kan inte läsas ut
    {
        set { lösenord = value; }
    }
}
```
**Används för:** Lösenord, känslig information där data bara ska kunna sättas.

---

## `private set;` – Skydda Properties från att ändras utanför klassen

En property kan ha en **privat setter**, vilket innebär att värdet kan sättas **inuti klassen**, men är endast **läsbart utanför klassen**. Detta används ofta för data som sätts vid objektets skapande men inte ska kunna ändras efteråt.


```csharp
class Bil
{
    public int Id { get; private set; } // Kan bara sättas inom klassen

    public Bil(int id)
    {
        Id = id;
    }
}
```
Objekt kan **tilldelas ett unikt ID**, men ingen annan kod kan ändra det efter att objektet skapats. Går dock bra att titta på ID via `get`.

> [!tip] **När används `private set;`?**
> Det används ofta för **ID-nummer** och andra värden som ska sättas en gång vid skapande men aldrig ändras efteråt.
Om en property ska kunna **sättas internt i klassen** men bara **läsas externt**, kan vi använda `private set;`:

> [!summary] **Sammanfattning**
> - `get` utan `set` gör en property **read-only**.
> - `set` utan `get` gör en property **write-only**.
> - `private set;` gör att propertyn bara kan sättas inuti klassen.




