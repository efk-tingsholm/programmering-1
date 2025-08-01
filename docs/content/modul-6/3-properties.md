# Properties i C#

## Vad är en Property?

<!-- ### Varför använda Properties istället för vanliga Getters och Setters? -->
Tidigare har vi använt metoder för att hämta och sätta värden. Där man måste skriva separata `Get`- och `Set`-metoder, vilket gör koden längre.

En **property** (egenskap) är en mekanism i C# för att hantera åtkomst till en privat variabel i en klass. Properties används för att kontrollera hur data läses och skrivs, vilket är en viktig del av **inkapsling** i objektorienterad programmering.

En property består av en **getter** och en **setter**, motsvaras av kodblocken `get` och `set` i nedanstående exempel, där namnen är beskrivande, och `get` då hanterar om värdet ska hämtas (och sen förmodligen användas till något), medan `set` hanterar om värdet ska ändras.
```csharp
class Bil
{
    // Privat fält
    private int hastighet; 

    // Property
    public int Hastighet 
    {
        // När värdet från fältet "hastighet" ska hämtas och sen användas till något.
        get { return hastighet; }

        // När annan del av programmet försöker ändra värdet i "hastighet".
        set 
        {
            // Validering av det inkommande värdet, ändra bara om det är större ön noll.
            if (value > 0) 
            {
                // Tilldelar det privata fältet "hastighet" det nya inkommande värdet.
                hastighet = value;
            }
        }
    }
}
```

Properties bör namnges enligt den privata variabel som hanteras, men med inledande versal. Exempelvis för ovanstående kod, där det privata fältet `hastighet` hanteras av propertyn `Hastighet`.

Det finns fördelar med properties, exempelvis: 

- **Kortare och mer läsbar kod** – eliminerar behovet av separata getter- och setter-metoder.
- **Inkapsling och kontroll** – ser till att värden alltid sätts och hämtas enligt de regler vi definierat.
- **Inbyggd validering** – istället för att skapa en separat metod för att validera data, kan det göras direkt i `set`-blocket.

!!! tip "Tips"
    Ja, jag förstår att att det inte är mer läsbart första gången man ser det... 


### Användning
När en property har definierats kan den användas direkt i `Main()` för att sätta och läsa värden direkt via objektet.
```csharp
class Program
{
    static void Main()
    {
        Bil minBil = new Bil();

        // Använder propertyn för att sätta värdet
        minBil.Hastighet = 100; 

        // Skriver ut bilens hastighet med hjälp av propertyn
        Console.WriteLine("Bilens hastighet: " + minBil.Hastighet); 
    }
}
```

---

## Auto-Properties
Om ingen validering eller extra logik behövs, kan man använda **auto-properties**, vilket gör koden mer kompakt:
```csharp
class Bil
{
    public int Hastighet { get; set; } // Auto-property
}
```

C# skapar automatiskt ett privat fält i bakgrunden, så att vi slipper skriva ut det manuellt.

!!! warning "Auto-property eller inte?"
    Om ingen validering behövs, är auto-properties ett smidigt alternativ till att skapa ett privat fält + full property.

    Fundera på om det i mitt ovanstående exempel är lämpligt med en auto-property eller inte...


---

## Anropa Properties i Konstruktorn
Man kan skriva in validering i konstruktorn, som demonstrerats i föregående avsnitt. Man kan också skriva in validering i sina properties som demonstrerats här ovan. 

Men om man ändå använder properties med validering behöver man inte göra dubbelt jobb och skriva valideringen i konstruktorn också - man kan använda propertyn inne i konstruktorn istället, för propertyn har redan valideringen. 

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
        // Använder propertyn "Hastighet" för att säkerställa validering, 
        // istället för att tilldela till fältet "hastighet" direkt.
        Hastighet = hastighetIn; 
    }
}
```



---

## Properties utan både Get och Set
En property behöver inte alltid ha både `get` och `set`. 

### 1. Read-Only Properties
Om ett värde **aldrig ska ändras** utanför klassen, kan man ha en property med bara `get`:
```csharp
class Bil
{
    // Auto-property med endast 'get', resten av programmet 
    // kan enbart hämta värdet
    public string Färg { get; } 

    // Konstruktor, 
    public Bil(string färg)
    {
        // Vi låter konstruktorn vara enda tillfället då färgen kan tilldelas
        Färg = färg; 
    }
}
```
Kan vara användbart för exempelvis unika ID:n och datum då objekt skapats.

### 2. Write-Only Properties 
Om en property bara ska **kunna ta emot värden men inte läsas ut**, kan man använda bara `set`:
```csharp
class SäkerData
{
    // Vi gör ett privat fält
    private string lösenord; 

    // Property med endast 'set', kan inte läsas ut, bara ändras
    public string Lösenord 
    {
        set { lösenord = value; }
    }
}
```
Kan vara användbart för exempelvis Lösenord och annan känslig information.

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

!!! tip "När används `private set;`?"
    Det används ofta för **ID-nummer** och andra värden som ska sättas en gång vid skapande men aldrig ändras efteråt.
    Om en property ska kunna **sättas internt i klassen** men bara **läsas externt**, kan vi använda `private set;`:


!!! summary "Sammanfattning"
    - `get` utan `set` gör en property **read-only**.
    - `set` utan `get` gör en property **write-only**.
    - `private set;` gör att propertyn bara kan sättas inuti klassen.





