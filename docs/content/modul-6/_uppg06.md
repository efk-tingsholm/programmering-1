# Övningsuppgifter - Modul 6

## Uppgift 1: Skapa och använda objekt
Skriv en klass `Person` som har två privata fält: `namn` (string) och `ålder` (int). 

- Skapa metoder `SetNamn()` och `SetÅlder()` för att sätta värdena.
- Skapa metoder `GetNamn()` och `GetÅlder()` för att hämta värdena.
- Skapa ett objekt av klassen i `Main()` och testa att sätta och hämta värdena.

## Uppgift 2: Properties
Skriv en klass `Bil` som har en property `Hastighet` (int). 

- Implementera `get` och `set`, där `set` inte tillåter negativa värden.
- Skapa ett objekt av `Bil` i `Main()` och testa att ändra hastigheten.

## Uppgift 3: Metoder och inkapsling
Skapa en klass `Bankkonto` som har:

- Ett privat fält `saldo` (int).
- En metod `Insättning(int belopp)` som ökar saldot.
- En metod `Uttag(int belopp)` som minskar saldot, men inte tillåter att det blir negativt.
- En metod `GetSaldo()` som returnerar saldot.

Testa klassen genom att skapa ett bankkonto och utföra några insättningar och uttag i `Main()`.

## Uppgift 4: Statisk medlem
Skapa en klass `Bil` där:

- Ett statiskt fält `antalBilar` håller reda på hur många bilar som skapats.
- Konstruktorerna ska öka `antalBilar` varje gång en ny bil skapas.
- En statisk metod `AntalBilar()` returnerar värdet på `antalBilar`.
- Testa genom att skapa flera objekt och anropa `AntalBilar()`.

## Uppgift 5: Konstruktoröverlagring
Skriv en klass `Produkt` med:

- En konstruktor `Produkt()` som sätter standardvärden.
- En konstruktor `Produkt(string namn, int pris)` där användaren kan skicka in värden.
- Skapa olika objekt av klassen i `Main()` och skriv ut deras värden.

## Uppgift 6: Kedjade konstruktorer
Skapa en klass `Lampa` som har:

- En konstruktor `Lampa()` som sätter standardvärden.
- En konstruktor `Lampa(string färg)` som anropar `this()` för att återanvända standardvärden och ändra färg.
- Testa genom att skapa objekt med båda konstruktorerna och skriva ut deras värden.




