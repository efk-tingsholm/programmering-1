Saker som behöver slottas in:
Random
ReadKey
Enum? NY
Kompilering och Exekvering 
Feltyper

Saker som kanske ska in:
Reserverade ord
Vad är .NET?

Funderingar från böckerna:
Taifun kör med ETT projekt och byter .cs fil hela tiden för konsoll, ja/nej?

lägg in osynlig page break med en < hr >

linebreak med br

eller backslash: \ på flera rader
\
\
# Introduktion
## Vad är programmering?
Programmering handlar om att skriva instruktioner som en dator kan förstå och utföra. Instruktionerna skrivs i ett programmeringsspråk, som fungerar som ett verktyg för att översätta mänskliga instruktioner till något som datorn kan förstå.

Programmering är en kreativ och logisk process som kräver tålamod och problemlösningsförmåga. Genom att lära dig programmering kan du skapa allt från enkla textbaserade program till spel och avancerade webbapplikationer. Det är en färdighet som kan öppna dörrar i karriären och ge dig verktygen att förverkliga dina idéer och innovationer. 
## Vad är C\#?
C# (uttalas "C sharp") är ett programmeringsspråk som utvecklats av Microsoft och introducerades år 2000.

C# skapades med målet att vara ett modernt, kraftfullt och lättanvänt språk för att utveckla olika typer av program och applikationer för Microsoft-plattformar som Windows. Men med tiden har språket blivit alltmer plattformsoberoende och numer kan man skriva och köra sina program på olika operativsystem som Windows, Linux och macOS. 

Ett av de mest intressanta dragen med C# är dess nära koppling till Microsofts .NET-plattform. Detta betyder att C#-program kan dra nytta av .NET:s stora ekosystem av bibliotek och verktyg för att snabbt och effektivt bygga robusta och skalbara applikationer.

C# har blivit ett populärt programmeringsspråk tack vare dess användarvänlighet, kraftfulla funktioner och breda användningsområden, vilket inkluderar allt från desktopapplikationer till webbutveckling och spelprogrammering. För nybörjare är C# ett utmärkt val för att lära sig grunderna i programmering samtidigt som det erbjuder tillräckligt med funktionalitet för att hantera mer avancerade projekt.
## Jämfört med C/C++
C# är ett högnivåspråk med moderna funktioner och starkt stöd för objektorienterad programmering, vilket gör det enklare att utveckla och underhålla program jämfört med C och C++. Medan C och C++ är närmare knutna till datorns hårdvara och erbjuder mer direkt kontroll, ger C# en högre abstraktionsnivå och plattformsoberoende genom Microsofts .NET-plattform.
## IDE - Integrated Development Environment
Även känt som *"programmet som man skriver kod i."*

En IDE, eller Integrated Development Environment, är en programvara som erbjuder utvecklare en komplett miljö för att skriva, testa, felsöka och distribuera program. Det kombinerar vanligtvis en textredigerare med funktioner som kodkomplettering, felsökning och bygginstrument i en enhetlig användargränssnitt.

Vi kommer att använda Visual Studio Community Edition  för att skriva och utveckla C#-program. Visual Studio är en kraftfull och populär IDE utvecklad av Microsoft och erbjuder ett brett utbud av funktioner och verktyg som underlättar utvecklingsprocessen. Community Edition är gratis för studenter och enskilda utvecklare.

Förutom Visual Studio finns det också andra populära IDE:er såsom Rider och Visual Studio Code. Utöver detta kan man också hitta webbaserade IDE:er online, exempelvis Replit. 

## Installera Visual Studio
Visual Studio behöver [laddas ner](https://visualstudio.microsoft.com/vs/community/) och installeras. Om länken blivit gammal är det bara att söka på internet efter exempelvis "Visual Studio Community 2022", eller liknande.

I installationsprogrammet kan man välja vilka funktioner man vill ladda ner och använda. Välj ".NET desktop development" och tryck install. 
![[Kursupplägg-20240221171137166.webp|609]]

Vill man vid senare tillfälle ha fler funktioner kan man alltid starta installationsprogrammet igen för att lägga till fler delar.

Antingen skippa att logga in, eller logga in med ditt skolkonto, det brukar fungera. 
![[Kursupplägg-20240221171559498.webp|500]]

Gör sedan det viktigaste valet i hela din programmeringskarriär. Välj Dark.
![[Kursupplägg-20240221171733256.webp|500]]

## Skapa ett nytt projekt
När du startar Visual Studio möts du av följande ruta, välj **Create a new project**. Det går också att starta programmet utan att starta ett projekt, om man väljer **continue without code**.
![[Kursupplägg-20240221172050227.webp|503]]

Visual Studio har många inbyggda mallar för olika typer av projekt, välj **Console App** och klicka dig vidare.
![[Kursupplägg-20240221172406406.webp|502]]

> [!info] 
> **Console App** är en typ av applikation där man får ut information som text via ett konsolfönster, detta är det typ av program som nästan alltid kommer användas i denna kurs.
> 
> Vill man på egen hand testa en typ av applikation som involverar både text och grafik kan **Windows Forms App** rekommenderas.

Namnge ditt projekt till något lämpligt. Notera att man här kan se och ändra var på hårddisken som projektet sparas under **Location**. Alternativet **Place solution and project in the same directory** är valfritt, det är en mapp- och organisationsdetalj.
![[Kursupplägg-20240221172624651.webp|504]]


Välj den senaste, fräsigaste versionen av .NET. Kryssa i rutan **Do not use top-level statements**. Detta är främst av pedagogiska skäl.
![[Kursupplägg-20240221172959045.webp|400]]

Välkommen till resten av ditt liv.
![[Kursupplägg-20240221173132579.webp]]

Kanske relevant
- UI kan ändras väldigt mkt, kanske skriva nåt om det
- hitta filen, den är eg. bara en textfil? filändelse .cs


## Utmatning och konsolen
Köra programmet F5/ctrl+F5 osv osv osv, utmatning är info ut till användaren. Köra = Exekvera.
![[Kursupplägg-20240222105024848.webp]]


Skriv egen källkod mellan klammerparenteserna, även kända som klammrar/måsvingar, förklaring till den för-genererade texten såsom **internal class Program** och **static void Main()** kommer allt eftersom.
![[Kursupplägg-20240222104923535.webp]]



Programmet exekveras (körs) uppifrån och ned i sekvens. Det enda som inte körs är kommentarer, rader som kompilatorn inte översätter. I C# skriver man kommentarer med dubbla snedstreck. 

Det är viktigt att kommentera sin kod med förklaringar och förtydliganden där det behövs, det underlättar förståelse, dels för sin egen del men också om någon annan ska titta på koden. 

Inom programmering betecknas en instruktion med **sats**, jämför engelskans **statement**. I C# avslutas dessa med ett semikolon. Detta innebär att nästan varje rad avslutas med semikolon.

Att skicka ut information till användaren kallas för **utmatning**, och i en **Console App** sker det via text i konsolfönstret. Kan göras via metoderna **WriteLine()** respektive **Write()**.
```csharp
Console.WriteLine("Hello, World!");

//Metoden Write() kan också användas för utmatning
Console.Write("Hej!");
```

I vissa program finns funktion för kodkomplettering, att programmet kommer med förslag på vad du skulle kunna skriva så fort man börjar skriva. I Visual Studio kallas denna för Intellisense. För att acceptera förslaget kan man använda tab, punkt eller mellanslag.




> [!tip] Tips
> Intellisense har vissa s.k. snippets inbyggda från början, testa att skriva "cw" och sen trycka tab. 
> 
> Beroende på vilken version av Visual Studio du har och dess inställningar kan du behöva trycka på tab-tangenten två gånger.

För att göra konsolprogrammet lite roligare kan man testa sig fram med lite olika metoder som tillhör klassen Console, exempelvis textfärg och bakgrundsfärg.
```csharp
Console.ForegroundColor = ConsoleColor.DarkBlue;
Console.BackgroundColor = ConsoleColor.Gray;
Console.Clear(); //För att bakgrundsfärgen ska användas i hela fönstret
```
> [!info]
> Console.Clear() tar också bort all text i konsolfönstret som är skriven före/ovanför.

En annan moralhöjare är metoden Beep() i kombination med Thread.Sleep().
```csharp
Console.Beep(); //Standardvärden är 800 Hz i 200 ms
Thread.Sleep(1000); //Pausar programmet
Console.Beep(1200, 500); //Kan modifiera frekvens och varaktighet
```

Det är möjligt att modifiera själva konsolfönstret också, exempelvis:
```csharp
Console.Title = "Mitt program!";
Console.SetWindowSize(80,20); //Bredd och höjd i "kolumner", slug enhet

Console.CursorVisible = false; //Döljer markören
Console.SetCursorPosition(0,0); //Flyttar upp markören igen
```

> [!help] Hjälp
> Om du stöter på problem för att du skrivit in en för stor WindowSize kan du hitta den maximala storleken för din skärmupplösning via Console.LargestWindowWidth respektive Height.

Man kan få grundläggande information om en metod eller egenskap genom att hovra på den med musen.

Vill man ha mer information kan man sätta markören i den och klicka på F1, då skickas man till Microsofts dokumentation för C#. Detta kan ibland vara överväldigande och då rekommenderas man att söka på internet istället.




# Variabler
## Lektion 1
## Lektion 2
# Operatorer
# Selektion
# Iteration
# Texthantering
Strings och char och index typ
# Kompilering
Och kanske lite övrigt om vad en dator är etc, kanske köra tidigare?
# Fel och felhantering
Olika typer av fel, debuggern, try-catch
# Planering
Pseudokod/aktivitetsdiagram?
# Metoder
# Samlingar
Fokus på Array och Lista, kanske även ta upp Dict/Queue/Stack etc
# Filhantering
# Klasser och objekt
# Enums?
# MonoGame