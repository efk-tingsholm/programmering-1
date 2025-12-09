# Operatorer

Operatorer inom programmering fungerar som inom matematiken, ett skrivsätt som symboliserar en viss funktion. Ett exempel på en operator är plustecknet. I exemplet "2 + 3" innebär plustecknet att man ska addera värdet av de två operanderna, alltså två och tre. 

Operatorer inom programmering kan delas in i olika kategorier baserat på deras funktion. 


## Matematiska operatorer
Även känt som aritmetiska operatorer.
### + Addition eller konkatenering
Plustecknet fungerar olika i olika situationer. 
```csharp
// Addition, lägga ihop tal
int a = 3 + 4; // a får värdet 7.

// Konkatenering, om en eller fler av operanderna är string 
string b = "Hej" + "då";  // b får värdet "Hejdå".
string c = "Hej" + 19;    // c får värdet "Hej19".
string d = "3" + 4;       // d får värdet 34.
```
### - Subtraktion
```csharp
int a = 10 - 7; // a får värdet 3.

// Minustecknet kan också användas för att multiplicera med -1.
int b = -a; // b får värdet -3.
```
### * Multiplikation
```csharp
int a = 3 * 2; // a får värdet 6.
```
### / Division
Om man utför heltalsdivision, alltså man delar ett heltal med ett annat heltal blir resultatet alltid ett heltal, decimalerna trunkeras(skärs) bort.
```csharp
int a = 12 / 3;    // a får värdet 4.
double b = 5 / 2;  // b får värdet 2. Även om det sparas i en double.

// Om EN av operanderna är i decimalform blir också svaret med decimaler.
double c = 5.0 / 2; // c får värdet 2.5 
```
### % Modulus
Modulusberäkning ger resten vid division. 
```csharp
int a = 7 % 3; // a får värdet 1. Eftersom 3 går två gånger i 7.
int b = 8 % 4; // b får värdet 0. Då divisionen går jämnt ut.
```

---


## Tilldelande operatorer
### = Tilldelning
Likhetstecknet används som tilldelningsoperator, alltså att sätta ett värde på en variabel.
```csharp
int a = 5;
string b = "Hej";
bool c = True;
```
### += Addera och tilldela
```csharp
int a = 12; // a tilldelas värdet 12 från början.

// Öka värdet på a med 8, vanlig tilldelning.
a = a + 8; // a får värdet 20. 

// Ökar också värdet på variabeln a med 8, förkortat skrivsätt.
a += 8; // a får värdet 28.
```
### -= Subtrahera och tilldela
```csharp
int a = 12; // a tilldelas värdet 12 från början.

a -= 10; // a får värdet 2. a = a - 10.
```

### ++, -- Öka eller minska med ett
Det är vanligt förekommande att man behöver öka eller minska variabelns värde med ett, det finns då en ytterligare förkortad tilldelningsoperator. 
```csharp
int a = 12; // a tilldelas värdet 12 från början.

a++; // a får värdet 13. Förtkortning av a = a + 1;
a--; // a får värdet 12 igen. Förtkortning av a = a - 1;
```
Ökning respektive minskning med ett kan används antingen före eller efter variabeln vars värde ska påverkas, detta avgör vilket värde som returneras.
```csharp
int a = 10;

// Skriver ut värdet på a, SEN öka med 1.
Console.WriteLine(a++); // Ger utskriften 10. 

// Ökar värdet på a med 1 FÖRST, sen skriver ut värdet.
Console.WriteLine(++a); // Ger utskriften 12.
```

### \*= Multiplicera och tilldela
```csharp
int a = 12; // a tilldelas värdet 12 från början.

a *= 2; // a får värdet 24. a = 12 * 2.
```
### /= Dividera och tilldela
```csharp
int a = 12; // a tilldelas värdet 12 från början.

a /= 2; // a får värdet 6. a = 12 / 2.
```

### %= Modulus och tilldela
```csharp
int a = 12; // a tilldelas värdet 12 från början.

a %= 2; // a får värdet 0. Eftersom 12 % 2 = 0.
```

---


## Jämförande/Boolska operatorer
Jämförande operatorer ger upphov till en boolskt värde, sant eller falskt. Dessa används oftast i villkorssatser, exempelvis if-satser, snarare än att tilldelas eller skrivas ut direkt som i vissa exempel nedan.
### <,> Mindre än, större än
```csharp
bool a = 10 > 6; // a får värdet true.

int b = 5;
Console.WriteLine(b < 3); // Ger utskriften False.
```

### <=, >= Mindre än eller lika med, större än eller lika med
```csharp
bool a = 6 >= 6; // a får värdet true.

int b = 5;
Console.WriteLine(b <= 3); // Ger utskriften False.
```
### == Lika med
```csharp
bool a = 3 == 4; // a får värdet False, eftersom 3 inte är 4.
```
### != Skiljt från
```csharp
Console.WriteLine(5 != 20); // Ger utskriften True.
```


---


## Logiska operatorer
### && And (Och)
Och-operatorn ger resultatet *True* om båda operanderna är *True*, alltså om det är *True* på båda sidorna om &&.
```csharp
int a = 12;

// 5 är större än 2 OCH 8 är mindre än a.
Console.WriteLine(5 > 2 && 8 < a); // Ger utskriften True.

Console.WriteLine(a == 12 && a < 10); // ger utskriften False.
```
### || Or (Eller)
Eller-operatorn ger resultatet *True* om minst en av operanderna är *True*.
```csharp
bool a = True; 

// a är True ELLER 5 är lika med 19. Behöver inte skriva a == true.
Console.WriteLine(a || 5 == 19); // Ger utskriften True. a är true.

// Här används det boolska värdet false direkt 
Console.WriteLine(false || 6 > 0 ); // Ger utskriften False. Båda är falska.

//Värdet från en logisk operator kan också sparas i en variabel
bool b = 5 < 10 || a; // b får värdet true, båda är true.
```

---


## Prioriteringsordning
Inom programmering fungerar prioriteringsordning ganska likt matematiken, olika operatorer har olika prioritet, och de med högst prioritet utvärderas först. Utöver detta kan parenteser användas för att styra ordningen.

Lite förenklat kan prioriteringsordningen sägas vara:
#### 1. Räknesätt
Räknesätten har också en inbördes prioriteringsordning precis som i matematiken.

1. Postfix ++ och --
2. Prefix ++ och --, även andra unitära operatorer såsom - och !
3. Multiplikation, Division och Modulus
4. Addition och Subtraktion

```csharp
int a = 3 + 4 * 5; // a får värdet 23. Multiplikation högre prioritet.

int b = 10;
Console.WriteLine(b++ * 2); // Ger utskriften 20. b blir 11 nästa rad och framåt.

Console.WriteLine(++b * 2); // Ger utskriften 24. b blir 12, sen gånger 2.
```

#### 2. Jämförelser
Mindre än, större än, lika med, etc.
#### 3. Logiska operatorer
Innefattar AND och OR. Notera att AND har högre prioritet än OR.
```csharp
// Här utvärderas "false && true" till false, sen "false || true" till true. 
Console.WriteLine(false && true || true); // Ger utskriften True.
```
#### 4. Tilldelningar
Både vanlig tilldelning med =, men också de tilldelande aritmetiska operatornerna exempelvis +=.
