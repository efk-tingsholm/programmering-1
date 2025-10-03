# Filhantering

Filhantering i denna kurs kommer använda klassen File, som finns i System.IO, där IO står för Input/Output, vilket ju är rimligt i sammanhanget. Läggs till överst i källkoden.
~~~csharp
using System;
using System.IO;
~~~
Notera, att skriva till fil och läsa från fil med klassen File är egentligen bara en förenkling av andra metoder från klassen FileStream. Lättsmält förklaring, tack stackoverflow. [^1]

[^1]:https://stackoverflow.com/questions/17380506/filestream-vs-system-io-file-writealltext-when-writing-to-files



## Skriva till fil
För att skriva till en fil, alltså spara information i filen utanför programmet, kan man använda metoden WriteAllText(), som tar två argument, 
- en sökväg för filen som ska skrivas i 
- och texten som ska skrivas

Dessa anges rimligen via variabler.
~~~cs
string path = @"C:\Users\emilw\Desktop\MIN_FIL.txt";
string msg = "Jag skriver saker...";

File.WriteAllText(path, msg);
~~~
Om filen inte finns skapas den. Om filen redan finns skriver metoden över det som står i den. Om man bara anger filnamn istället för hela sökvägen t.ex. "MIN_FIL.txt", så kommer filen skapas i samma mapp som .exe filen, din projektmapp.

För att undvika att skriva över det som redan står, alltså om man bara vill lägga till text, kan metoden AppendAllText() användas. Syntaxen är likadan som med ovanstående WriteAllTExt().
~~~cs
File.AppendAllText(path, msg);
~~~
Den sträng som anges som argument till metoden kommer läggas till sist i filen.


---


## Läsa från fil
För att komma åt informationen från en fil används metoden ReadAllText(), som tar ett argument, nämligen filens sökväg. Metoden returnerar en sträng med all text som finns i filen, denna informationen kan sparas/skrivas ut.
~~~cs
string path = @"C:\Users\emilw\Desktop\MIN_FIL.txt";
string info;

//Läsa in text från filen, spara i variabel
info = File.WriteAllText(path);

//Skriva ut
Console.WriteLine(info);
~~~

---

## Arrayer och listor
Har man en array/lista/dylikt går det utmärkt att istället använda metoderna WriteAllLines(), AppendAllLines() och ReadAllLines().

 De fungerar på samma sätt som motsvarigheterna ovan, förutom att man anger en array av strängar som argument. Samt att ReadAllLines() returnerar en array.

~~~cs
string path = @"C:\Users\emilw\Desktop\MIN_FIL.txt";
string[] myArray = {"Hej", "på", "dig!"};

File.WriteAllText(path, myArray);
~~~
Notera att dessa metoder skriver varje element från arrayen på en ny rad.

---

## Övrigt
Andra metoder och egenskaper som kan vara av intresse när man arbetar med klassen File.
~~~cs
File.Exists(); //Kontrollerar om en fil finns
File.Create(); //Gör en fil, t.ex. om den inte redan finns, men borde finnas

//Om man vill flytta runt och kopiera filer
File.Copy();
File.Delete();
File.Move();
File.Replace();
~~~





