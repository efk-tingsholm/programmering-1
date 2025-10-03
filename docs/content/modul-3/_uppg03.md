# Övningar - Modul 3

## Uppgift 1
Skriv ett program som skriver ut talen 0 till och med 30 med hjälp av en loop. 

Utöka programmet så att det inväntar knapptryck från användaren och sen räknar nedåt igen från 30, till -30, också med hjälp av en loop. Notera att programmet även nu ska skriva ut talen. 

## Uppgift 2
Skriv ett program som tar in ett ord eller en mening från användaren. Programmet ska sedan skriva ut ordet eller meningen vertikalt, alltså en bokstav på varje rad!

Utöka programmet så att det också skriver ut ordet baklänges, t.ex. "Hej" -> "jeH".

## Uppgift 3
Skriv ett program som låter användaren ange ett heltal, programmet ska sedan tjusigt skriva ut gångertabell för det angivna talet. T.ex. om användaren anger 4:
1 x 4 = 4
2 x 4 = 8
osv...

## Uppgift 4
Skriv ett program som låter användaren ange två heltal, ett startvärde och ett stoppvärde. Programmet ska sedan räkna uppåt, och skriva ut, från start till stopp.

Programmet ska klara av att man skriver ett lägre stopp än startvärde, genom att helt enkelt byta plats på dem. Exempelvis om man anger 20 och 5, så ska programmet vända på dem och räkna från 5 till 20.

Utöka programmet så att det även beräknar summan av de uppräknade talen, och ska presenteras i slutet av körningen.


## Uppgift 5
Skriv ett menyprogram som låter användaren slå en tärning 3 gånger, skriv ut resultatet av varje kast
  
Utöka programmet genom att låta användaren välja hur många gånger den vill kasta tärningen, skriv ut resultatet för varje kast på en rad.

Programmet ska även skriva ut den totala poängsumman och medelpoängen av kasten.

## Uppgift 6
Skriv ett program som låter användaren ange ett positivt heltal över 10. 

Programmet ska sedan skriva ut alla udda tal i intervallet, t.ex: 
Udda tal: 1, 3, 5, 7 ,9

Sedan ska programmet även skriva ut alla jämna tal i intervallet:
Jämna tal: 2, 4, 6, 8

## Uppgift 7
Miniräknare, igen. Utveckla något av dina tidigare miniräknarprogram så att det nu har en huvudmeny som man kommer tillbaka till efter en utförd operation. 

Om du inte har något tidigare miniräknarprogram kan du helt enkelt skriva ett miniräknarprogram med huvudmeny.

## Uppgift 8
Skriv ett program som tar in en sträng, exempelvis användarens namn, programmet ska sedan:

- Ange strängens längd, alltså hur många tecken som ingår.
- Kontrollera om bokstaven ”a” finns i strängen.
- Kontrollera om strängen inleds med bokstaven ”b”.
- Byta ut alla ”a” (eller fler vokaler om du vill), mot någon annan lämplig vokal, ex. ”Hej” -> ”Häj”.
- Byta alla bokstäver till VERSALER.



## Uppgift 9 
Svenskläraren. Skriv ett program som låter användaren skriva in en mening. Programmet ska ge användaren beröm om denne kommit ihåg punkt och stor bokstav. (I slutet respektive början av meningen)

Om användaren misslyckats med att skriva en korrekt mening ska denne behöva göra om.

Tips. Precis som att det finns ToUpper() för string så finns det för char.

## Uppgift 10
Frågesport med highscore. Skriv ett program som frågar användaren vad den heter, och sen har frågesport med användaren, t.ex. 3 frågor. Programmet ska hålla koll på hur många rätt användaren får. 

Programmet ska sedan spara användarens namn och poäng i en textfil. När programmet startar nästa gång ska namnet och poängen visas, t.ex. "Föregående spelare: Emil, 3/3 poäng".

Du kan själv välja om du vill att programmet ska skriva över föregående spelare, eller om du vill spara flera föregående spelare.

## Uppgift 11
Miniräknare igen. Skriv ett miniräknarprogram, eller utöka ett befintligt miniräknarprogram. 

Den här gången ska miniräknaren acceptera inmatning på en rad. Det ska gå att skriva t.ex. "2+3". Programmet ska ta in informationen, tolka den, och skriva ut något i stil med "2 + 3 = 6"

Börja med att försöka få räknesättet addition att fungera, går sen att utöka till övriga räknesätt.



## Uppgift 12
Geometrisk figur. Skriv ett program som skriver ut en kvadrat med sidan 5 av stjärnor ( * ). Två nästlade for-loopar kan vara en bra utgångspunkt.

```
* * * * *
* * * * *
* * * * *
* * * * *
* * * * *
```
  
- Utveckla programmet så att användaren kan välja tecken själv. 
- Utveckla programmet så att användaren kan välja bredd och höjd på formen som skrivs ut, så det kan bli olika bredd och höjd.  
- Utveckla programmet genom att låta rektangeln som skrivs ut vara ”ihålig”, så programmet ska bara skriva ut en ”tavelram”, med den angivna höjden och bredden.  
- Utöka programmet genom att göra en huvudmeny, med alternativen t.ex. ”rita ut”, ”alternativ” och ”avsluta”, under alternativ kan du lägga inställningarna för tecken, bredd och höjd från tidigare del-uppgifter.



## Uppgift 13
Mer geometriska figurer. Denna uppgift kan med fördel göras som en utveckling av den förra uppgiften.

Utveckla ditt geometriprogram så att det kan rita ut lite olika typer av trianglar. Användaren ska kunna ange höjd och tecken för trianglarna. 

```
*  
* * 
* * * 
* * * * 
```

```
      a  
    a a 
  a a a 
a a a a 
```

```  
      * 
    * * * 
  * * * * *
* * * * * * *
```

Tips: Ändra villkoret i den inre for-loopen så att antalet symboler som skrivs ut för respektive rad ändras. Man kan också ha flera inre for-loopar i den yttre loopen.

