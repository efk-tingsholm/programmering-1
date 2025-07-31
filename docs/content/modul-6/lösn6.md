# Lösningsförslag - Modul 6

## Uppgift 1: Skapa och använda objekt
```csharp
class Person
{
    private string namn; // Privat fält för att lagra personens namn
    private int ålder; // Privat fält för att lagra personens ålder

    // Metod för att sätta personens namn
    public void SetNamn(string nyttNamn)
    {
        namn = nyttNamn;
    }

    // Metod för att sätta personens ålder (måste vara positivt)
    public void SetÅlder(int nyÅlder)
    {
        if (nyÅlder > 0)
            ålder = nyÅlder;
    }

    // Metod för att hämta personens namn
    public string GetNamn()
    {
        return namn;
    }

    // Metod för att hämta personens ålder
    public int GetÅlder()
    {
        return ålder;
    }
}

class Program
{
    static void Main()
    {
        Person p = new Person();
        p.SetNamn("Anna");
        p.SetÅlder(25);
        Console.WriteLine($"Namn: {p.GetNamn()}, Ålder: {p.GetÅlder()}");
    }
}
```

## Uppgift 2: Properties
```csharp
class Bil
{
    private int hastighet; // Privat fält för att lagra bilens hastighet

    // Property för att läsa och sätta bilens hastighet, med validering
    public int Hastighet
    {
        get { return hastighet; }
        set 
        {
            if (value >= 0)
                hastighet = value;
        }
    }
}

class Program
{
    static void Main()
    {
        Bil b = new Bil();
        b.Hastighet = 120;
        Console.WriteLine("Hastighet: " + b.Hastighet);
    }
}
```


## Uppgift 3: Metoder och inkapsling
```csharp
class Bankkonto
{
    private int saldo = 0;

    // Metod för att sätta in pengar på kontot
    public void Insättning(int belopp)
    {
        if (belopp > 0)
            saldo += belopp;
    }

    // Metod för att ta ut pengar från kontot, men inte mer än saldot
    public void Uttag(int belopp)
    {
        if (belopp > 0 && belopp <= saldo)
            saldo -= belopp;
    }

    // Metod för att hämta aktuellt saldo
    public int GetSaldo()
    {
        return saldo;
    }
}

class Program
{
    static void Main()
    {
        Bankkonto konto = new Bankkonto();
        konto.Insättning(500);
        konto.Uttag(200);
        Console.WriteLine("Saldo: " + konto.GetSaldo());
    }
}
```


## Uppgift 4: Statisk medlem
```csharp
class Bil
{
    private static int antalBilar = 0;
    private string modell;

    public Bil(string modell)
    {
        this.modell = modell;
        antalBilar++;
    }

    public static int AntalBilar()
    {
        return antalBilar;
    }
}

class Program
{
    static void Main()
    {
        Bil b1 = new Bil("Volvo");
        Bil b2 = new Bil("BMW");
        Console.WriteLine("Antal bilar skapade: " + Bil.AntalBilar());
    }
}
```


## Uppgift 5: Konstruktoröverlagring
```csharp
// Klass som representerar en produkt
class Produkt
{
    public string Namn { get; set; } 
    public int Pris { get; set; } 

    // Standardkonstruktor som sätter standardvärden
    public Produkt()
    {
        Namn = "Okänd";
        Pris = 0;
    }

    // Konstruktor som tar emot namn och pris som parametrar
    public Produkt(string namn, int pris)
    {
        Namn = namn;
        Pris = pris;
    }
}

class Program
{
    static void Main()
    {
        Produkt p1 = new Produkt();
        Produkt p2 = new Produkt("Dator", 12000);
        Console.WriteLine($"Produkt: {p1.Namn}, Pris: {p1.Pris}");
        Console.WriteLine($"Produkt: {p2.Namn}, Pris: {p2.Pris}");
    }
}
```


## Uppgift 6: Kedjade konstruktorer
```csharp
class Lampa
{
    public string Färg { get; set; } 
    public int Ljusstyrka { get; set; } 

    // Standardkonstruktor som sätter standardvärden
    public Lampa() : this("Vit", 100) { }

    // Konstruktor som endast tar emot färg och använder standard ljusstyrka
    public Lampa(string färg) : this(färg, 100) { }

    // Konstruktor som tar emot både färg och ljusstyrka, tilldelar via autoproperty
    public Lampa(string färg, int ljusstyrka)
    {
        Färg = färg;
        Ljusstyrka = ljusstyrka;
    }
}

class Program
{
    static void Main()
    {
        Lampa l1 = new Lampa();
        Lampa l2 = new Lampa("Blå");
        Console.WriteLine($"Lampa 1 - Färg: {l1.Färg}, Ljusstyrka: {l1.Ljusstyrka}");
        Console.WriteLine($"Lampa 2 - Färg: {l2.Färg}, Ljusstyrka: {l2.Ljusstyrka}");
    }
}
```

