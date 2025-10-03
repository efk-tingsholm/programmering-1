# Slumptal

För att generera slumpade tal i C# kan den färdiga klassen Random med tillhörande metoder användas. Det är värt att notera att det såklart inte är sann slump i strikt mening. 

Enligt Microsoft representerar klassen Random en pseudo-random nummergenerator som ger en följd av nummer som uppfyller vissa statistiska krav för slumpmässighet. Torrt och bra.
## Slumpgenerator
För att komma åt metoderna behöver man starta en "slumpgenerator", i exemplet nedan namnges den till "generator", denna används sen för att generera slumptal.
```csharp
Random generator = new Random();
```

## Heltal

Metoden Next() returnerar heltal.

Metoden kan användas antingen utan argument, med ett argument för övre gräns, eller med två argument som sätter både undre och övre gräns. Notera att den undre gränsen ingår i intervallet, men inte den övre.

```csharp
// Slumpar ett heltal som är mellan 0 och maxvärdet för int.
int a = generator.Next();

// Slumpar ett heltal som är 0, 1, 2 eller 3. 
int b = generator.Next(4);

// Slumpar ett heltal som är 2, 3, eller 4.
int c = generator.Next(2, 5);
```

## Decimaltal

Metoden NextDouble() ger ett decimaltal som är lika med eller större än noll, men mindre än ett. Behöver man ett decimaltal som är större än ett kan man multiplicera.
```csharp
// Slumpar en double mellan 0 och 1.
double d = generator.NextDouble();

// Ex. 0,3456... blir 34,56... 
double e = generator.NextDouble() * 100;
```