# Referenstyp och värdetyp

I C# kan datatyper delas in i två huvudkategorier, **värdetyper** och **referenstyper**. 

## Värdetyp
En **värdetyp** lagrar sitt faktiska värde direkt i minnet där variabeln deklareras. Om en värdetyp kopieras (t.ex. till en annan variabel) skapas en ny, oberoende kopia av värdet. Till värdetyperna räknas de enkla datatyperna t.ex. `int`, `double`, `float`, `bool`, `char` (structs och enums, mer specifikt).

Exempel för värdetyp när en variabel tilldelas värde från en annan variabel.
```csharp
int a = 10;
int b = a; // b får en kopia av värdet i a
b = 20;

Console.WriteLine(a); // Utskrift: 10 (a är oförändrad)
Console.WriteLine(b); // Utskrift: 20
```
Eftersom `b` fick en kopia av `a`, ändras inte `a` om vi ändrar `b`.

---

## Referenstyp
En **referenstyp** lagrar en referens (adressen) till ett objekt i minnet, snarare än själva objektet. Om en referenstyp kopieras skapas en ny referens till samma objekt, inte en oberoende kopia av objektet. Till referenstyperna räknas bland annat alla arrayer och klasser.

```csharp
int[] arr1 = { 1, 2, 3 };
int[] arr2 = arr1; // arr2 pekar på samma objekt som arr1

arr2[0] = 99;

Console.WriteLine(arr1[0]); // Utskrift: 99 (arr1 påverkas)
Console.WriteLine(arr2[0]); // Utskrift: 99
```

Både `arr1` och `arr2` pekar på samma objekt i minnet, så ändringar via en referens återspeglas i den andra.

Notera att `string` är en klass, och därmed av referenstyp. Däremot  fungerar den som en värdetyp eftersom den är **oföränderlig** (immutable). Det betyder att varje ändring av en `string` skapar en ny instans i minnet, vilket skiljer sig från hur andra referenstyper beter sig.

---

## Skillnader mellan värdetyp och referenstyp
En värdetyp lagrar sitt faktiska värde direkt i minnet där variabeln deklareras. När en värdetyp kopieras, skapas en oberoende kopia av värdet. Det innebär att ändringar i en kopia inte påverkar den ursprungliga variabeln. Exempel på värdetyper är `int`, `double`, och `bool`.

En referenstyp lagrar däremot en referens (adressen) till ett objekt i minnet, snarare än själva objektet. När en referenstyp kopieras, skapas en ny referens till samma objekt, inte en oberoende kopia av objektet. Det innebär att ändringar via en referens återspeglas i andra referenser som pekar på samma objekt. Exempel på referenstyper är `string`, `List<>`, och arrayer.

!!! tip "Tips"
    En fördel med referenstyper är att de kan göra det enklare att arbeta med metoder som modifierar data. 

    Om en metod tar emot en referens till en array eller lista, kan metoden ändra innehållet direkt utan att behöva returnera en ny kopia. Detta är effektivt vid arbete med stora datastrukturer.


---

## Skapa en unik kopia av en array

Om du behöver skapa en oberoende kopia av en array kan detta göras på olika sätt. Nedan följer två vanliga metoder.
#### 1. Använda `Clone()`

Metoden `Clone()` skapar en ytlig kopia av arrayen. Detta innebär att elementvärdena kopieras, men om arrayen innehåller referenstyper pekar kopian på samma objekt.

```csharp
int[] original = { 10, 20, 30 };

// Använd Clone(), typecasta till en int-array
int[] shallowCopy = (int[])original.Clone();

// Tilldela första elementet i kopian värdet 99
shallowCopy[0] = 99;

Console.WriteLine(original[0]); // Utskrift: 10
Console.WriteLine(shallowCopy[0]); // Utskrift: 99
```

#### 2. Iterera och kopiera värden manuellt

Genom att iterera över arrayen och kopiera varje element skapas en djup kopia.

```csharp
int[] original = { 10, 20, 30 };
int[] deepCopy = new int[original.Length];

// Gå igenom arrayen och sätt värdet på kopian till respektive värde från första arrayen
for (int i = 0; i < original.Length; i++)
{
    deepCopy[i] = original[i];
}

// Sätt värdet på första elementet i kopian till 99
deepCopy[0] = 99;

Console.WriteLine(original[0]); // Utskrift: 10
Console.WriteLine(deepCopy[0]); // Utskrift: 99
```

## Viktigt att tänka på
Referenstyper kan leda till oförutsedda ändringar i kod om flera referenser pekar på samma objekt. Använd kopieringsmetoder som `Clone()` eller iterera manuellt om du behöver oberoende kopior.

!!! tip "Tips"
    Värdetyper är som att ge någon en kopia av ett papper, medan referenstyper är som att ge personen en livesändning av det ursprungliga pappret, som då alltså ändras i realtid.
    
    *Såhär i efterhand är jag inte imponerad av min egen liknelse...*




