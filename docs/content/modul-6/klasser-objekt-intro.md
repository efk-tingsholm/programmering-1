# Klasser och objekt - introduktion


## Vad är en klass och ett objekt?
En **klass** är en mall för att skapa objekt. Den definierar vilka egenskaper (data) och beteenden (metoder) ett objekt ska ha.

En klass kan liknas vid en ritning för något – exempelvis en bil. Ritningen beskriver att en bil har en färg, en motor och kan köra. Men själva bilarna existerar inte förrän de skapas baserat på ritningen.

Ett **objekt** är en faktisk instans av en klass.

- En klass definierar hur något ska fungera, medan objekten är de konkreta exemplaren av den klassen.
- Om klassen är en ritning för en bil, så är varje objekt en faktisk bil med sina egna egenskaper, t.ex. en röd bil och en blå bil.

### Fördelar med klasser och objekt
- **Struktur och organisering** – Klasser hjälper till att hålla koden mer organiserad och återanvändbar.
- **Modularitet** – Separata klasser för olika delar av ett program gör utveckling och underhåll enklare.
- **Återanvändbarhet** – När en klass är definierad kan flera objekt skapas från den, vilket gör koden mer flexibel.
- **Inkapsling** – Klasser möjliggör att interna detaljer döljs och endast relevant information exponeras.


### Filstruktur och namngivning
Det är praxis att skapa en ny fil för varje ny klass för att hålla koden strukturerad och lätt att hantera.

Varje klass ska ha samma namn som filen, med **inledande versal**. Exempel: filen `Bil.cs` innehåller klassen `Bil`.

Metoder i klassen ska också börja med stor bokstav, enligt **PascalCase**-konventionen.
  ```csharp
  public void SättHastighet(int nyHastighet) 
  { 
    // Metodens kod här inne...
  }
  ```

!!! summary "Sammanfattning"
    - En **klass** är en mall för att skapa objekt.
    - Ett **objekt** är en instans av en klass och har sina egna egenskaper.
    - Klasser bidrar till en mer organiserad, modulariserad och återanvändbar kod.
    - Det är praxis att skapa en ny fil per klass, och PascalCase används för namngivning.


---

## Klassmedlemmar

En klass kan innehålla både **variabler (fält)** och **metoder**, som tillsammans kallas **klassmedlemmar**. Variabler används för att lagra information om objektet, medan metoder definierar dess beteenden.

För att skydda data och förhindra oavsiktliga ändringar sätts fält som **private**. Metoder kan däremot vara **public** om de behöver användas utanför klassen, vilket möjliggör en kontrollerad åtkomst till objektets data.

Detta leder till en viktig princip inom objektorienterad programmering: **inkapsling**.

Inkapsling innebär att vissa delar av en klass är dolda från resten av programmet. Genom att använda **private** för variabler kan obehörig åtkomst förhindras, vilket skyddar data och minskar risken för oavsiktliga förändringar.

Att begränsa åtkomsten till variabler gör koden mer robust och lättare att underhålla. Istället för att direkt ändra värden används metoder för att styra hur data manipuleras, vilket gör det möjligt att lägga till logik, som exempelvis validering, innan en ändring tillåts.

```csharp
class Bil
{
    private int hastighet; // Kan bara ändras inuti klassen

    public void SättHastighet(int nyHastighet)
    {
        if (nyHastighet > 0)
            hastighet = nyHastighet;
    }

    public int HämtaHastighet()
    {
        return hastighet;
    }
}
```

---

Om `hastighet` försöker nås direkt utanför klassen, uppstår ett fel:
```csharp
Bil minBil = new Bil();
// minBil.hastighet = 120;  // FEL: hastighet är privat!
```


Normalt sett lagras variabler individuellt för varje objekt. Men ibland vill man att en variabel eller metod ska delas av alla instanser – då används `static`.


!!! summary "Sammanfattning"
    - En klass kan ha **variabler (fält)** för att lagra information och **metoder** för att definiera beteenden.
    - `private` skyddar variabler från direkt åtkomst utanför klassen.
    - `public` gör att metoder eller variabler kan anropas externt.
    - Inkapsling bidrar till att kontrollera hur objekt hanteras och ändras.



## Skapa och Använda en Instans i `Main()`
Efter att en klass är definierad kan en instans/ett objekt skapas och användas i `Main()`. Notera att nyckelordet `new` används för detta.

```csharp
class Program
{
    static void Main()
    {
        // Gör ett nytt objekt, en instans, av klassen Bil
        Bil minBil = new Bil(); 

        // Anropar metoden via objektet
        minBil.SättHastighet(120);

        Console.WriteLine("Bilens hastighet: " +  minBil.HämtaHastighet()); // Ger utskriften "Bilens hastighet: 120"
    }
}
```






