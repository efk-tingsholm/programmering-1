# Konstruktorer

ATT GÖRA: Den här är kaos, ej fixad.

## Vad är en konstruktor?

En **konstruktor** är en speciell metod i en klass som anropas automatiskt när ett objekt skapas. Dess huvudsakliga syfte är att **sätta startvärden** för objektets variabler och säkerställa att objektet är i ett giltigt tillstånd direkt vid skapandet.

Varje klass i C# har alltid en **standardkonstruktor**, även om den inte skrivs ut. Denna konstruktor är tom och gör ingenting, men den gör det möjligt att skapa instanser av klassen utan att behöva ange några parametrar.

```csharp
class Bil
{
    private int hastighet;
    private string färg;

    // Standardkonstruktor - men vi har lagt till tilldelning för färg och hastighet
    public Bil()
    {
        hastighet = 50;
        färg = "Vit";
    }

    // Konstruktor med endast färg
    public Bil(string färg)
    {
        hastighet = 50; // Standardhastighet
        this.färg = färg;
    }

    // Konstruktor med både hastighet och färg
    public Bil(int hastighet, string färg)
    {
        this.hastighet = hastighet;
        this.färg = färg;
    }
}

// Användning av konstruktorerna ute i Main()
class Program
{
    static void Main()
    {
        Bil bil1 = new Bil(); // Standardvärden
        Bil bil2 = new Bil("Blå"); // Standardhastighet, men blå färg
        Bil bil3 = new Bil(120, "Röd"); // Anpassade värden
    }
}
```


I många fall vill vi dock förhindra att objekt skapas utan vissa viktiga värden. Tänk dig en bil utan en färg eller en hastighet – det skulle vara ologiskt! Genom att skapa en egen konstruktor kan vi säkerställa att alla objekt får en korrekt startuppsättning av data direkt vid skapandet.

En **konstruktor** är en speciell metod i en klass som anropas automatiskt när ett objekt skapas. Dess huvudsakliga syfte är att sätta startvärden för objektets variabler och säkerställa att objektet är i ett giltigt tillstånd direkt vid skapandet.

### Utan konstruktor
Utan en konstruktor måste varje objekt initialiseras manuellt:
```csharp
class Bil
{
    private int hastighet;
    private string färg;

    public void SättHastighet(int nyHastighet)
    {
        hastighet = nyHastighet;
    }

    public void SättFärg(string nyFärg)
    {
        färg = nyFärg;
    }
}

class Program
{
    static void Main()
    {
        Bil minBil = new Bil();
        minBil.SättHastighet(100);
        minBil.SättFärg("Röd");
    }
}
```



### Med konstruktor

När en konstruktor har parametrar som har samma namn som klassens fält används **`this`** för att skilja dem åt. `this` refererar till klassens egna variabler och gör att vi kan tilldela fält rätt värden utan att det blir otydligt.

En konstruktor gör att objektet får sina startvärden direkt vid skapandet:
```csharp
class Bil
{
    private int hastighet;
    private string färg;

    // Konstruktor
    public Bil(int hastighet, string färg)
    {
        // `this` används för att referera till klassens egna fält
        this.hastighet = hastighet;
        this.färg = färg;
    }
}

class Program
{
    static void Main()
    {
        Bil minBil = new Bil(100, "Röd");
    }
}
```


> [!tip] **Tips**
> Om parametrarna har andra namn än fälten, t.ex. `hastighetIn` istället för `hastighet`, behövs inte `this`. Men det är en vanlig praxis att använda `this` när parametern har samma namn som fältet, för att hålla koden tydlig och konsekvent.

> [!summary] **Sammanfattning**
> - En konstruktor anropas automatiskt när ett objekt skapas.
> - Den används för att ge objektet **startvärden** direkt vid skapandet.
> - Konstruktorer minskar risken för inkonsekventa objekt.

## Standardvärden och felkontroll
En konstruktor kan också användas för att **förhindra ogiltiga värden** genom att sätta standardvärden.

```csharp
class Bil
{
    private int hastighet;
    private string färg;

    public Bil(int hastighet, string färg)
    {
        // Sätt standardvärden om indata är ogiltig
        if (hastighet > 0)
        {
            this.hastighet = hastighet;
        }
        else
        {
            this.hastighet = 50;
        }
        // Samma koncept för färg
        if (!string.IsNullOrEmpty(färg))
        {
            this.färg = färg;
        }
        else
        {
            this.färg = "Vit";
        }
    }
}
```



---

## Konstruktoröverlagring

C# tillåter **överlagrade konstruktörer**, vilket innebär att en klass kan ha flera olika konstruktörer med olika parametrar. Detta gör det möjligt att skapa objekt på olika sätt beroende på vad som är känt vid skapandet.

```csharp
class Bil
{
    private int hastighet;
    private string färg;

    // Standardkonstruktor
    public Bil()
    {
        hastighet = 50;
        färg = "Vit";
    }

    // Konstruktor med endast färg
    public Bil(string färg)
    {
        hastighet = 50; // Standardhastighet
        this.färg = färg;
    }

    // Konstruktor med både hastighet och färg
    public Bil(int hastighet, string färg)
    {
        this.hastighet = hastighet;
        this.färg = färg;
    }
}

class Program
{
    static void Main()
    {
        Bil bil1 = new Bil(); // Standardvärden
        Bil bil2 = new Bil("Blå"); // Standardhastighet, men blå färg
        Bil bil3 = new Bil(120, "Röd"); // Anpassade värden
    }
}
```




---

## `this` och kedjade konstrukt0rer
Nyckelordet **`this`** används inom en klass för att referera till klassens egna medlemmar. Det används också för att **anropa en annan konstruktor** inom samma klass.

```csharp
class Bil
{
    private int hastighet;
    private string färg;

    // Standardkonstruktor
    public Bil() : this(50, "Vit") 
    {
        // Anropar huvudkonstruktorn med defaultvärden
    }

    // Huvudkonstruktor
    public Bil(int hastighet, string färg)
    {
        this.hastighet = hastighet;
        this.färg = färg;
    }
}
```


> [!summary] **Sammanfattning**
> - `this` används för att referera till klassens egna variabler.
> - `this()` kan anropa en annan konstruktor i samma klass, vilket minskar koddupplikation.

---
<hr>
## Statiska medlemmar i klasser

Ibland vill man att en variabel eller metod inte ska tillhöra ett specifikt objekt, utan **klassen i sig**. Då används nyckelordet `static`. Ett exempel är en räknare som håller koll på hur många objekt som har skapats.

```csharp
class Bil
{
    private static int antalBilar = 0; // Statisk variabel för att räkna antalet bilar
    private string färg;

    public Bil(string färg)
    {
        this.färg = färg;
        antalBilar++; // Ökar varje gång en ny bil skapas
    }

    public static int HämtaAntalBilar()
    {
        return antalBilar;
    }
}

class Program
{
    static void Main()
    {
        Bil bil1 = new Bil("Röd");
        Bil bil2 = new Bil("Blå");

        Console.WriteLine("Antal skapade bilar: " + Bil.HämtaAntalBilar()); 
        // Utskrift: Antal skapade bilar: 2
    }
}
```

Eftersom `antalBilar` är statisk (`static`), delas värdet mellan alla instanser. Man kan hämta antalet skapade bilar utan att behöva skapa ett objekt.

---

### Statiska klasser för globala inställningar
I större projekt används ofta **statiska klasser** för att lagra globala inställningar eller gemensamma funktioner. Exempelvis kan en klass innehålla konstanter eller metoder som används överallt i programmet utan att behöva skapa ett objekt.

En klass behöver **inte** vara statisk för att ha statiska medlemmar. Om en klass är `static`, går det inte att skapa objekt av den, vilket gör den användbar för globala inställningar och hjälpfunktioner.

```csharp
static class Konfiguration
{
    public static readonly int MaxAnvändare = 100;
}

class Program
{
    static void Main()
    {
        Console.WriteLine("Max antal användare: " + Konfiguration.MaxAnvändare);
    }
}
```

Eftersom klassen är `static`, kan dess medlemmar användas globalt utan att skapa en instans.

> [!tip] **Exempel från .NET**
> En av de mest använda statiska klasserna i .NET är `Math`.
> Exempel:
> ```csharp
> double rot = Math.Sqrt(16); // Returnerar 4
> double pi = Math.PI; // Konstanten π
> ```


> [!summary] **Sammanfattning**
> - `static` gör att en variabel eller metod tillhör **klassen istället för enskilda objekt**.
> - Statisk data delas mellan alla instanser.
> - Statiska metoder kan anropas direkt på klassen, utan att skapa ett objekt.

---
