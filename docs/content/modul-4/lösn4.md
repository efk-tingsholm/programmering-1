# Lösningsförslag - Modul 4


## Uppgift 1
```csharp
class Program
{
    // Metod som skriver ut det minsta av två ta
    static void PrintSmallestNumber(int num1, int num2)
    {
        int min;
        if (num1 < num2)
        {
            min = num1;
        }
        else
        {
            min = num2;
        }
        Console.WriteLine($"Det minsta talet är {min}!");
    }

    static void Main(string[] args)
    {
        // Testkörning av metoden med exempelvärden
        PrintSmallestNumber(3, 7);
    }
}
```

## Uppgift 2
```csharp
class Program
{
    // Metod som beräknar medelvärdet av tre tal
    static double CalculateAverage(int num1, int num2, int num3)
    {
        return (num1 + num2 + num3) / 3.0;
    }

    static void Main(string[] args)
    {
        // Testkörning av metoden
        double average = CalculateAverage(4, 5, 6);
        Console.WriteLine($"Medelvärdet är: {average}");
    }
}
```

## Uppgift 3
```csharp
class Program
{
    static double CalculateVolume(double radius, double height)
    {
        return Math.PI * Math.Pow(radius, 2) * height;
    }

    static double CalculateSurfaceArea(double radius, double height)
    {
        return 2 * Math.PI * radius * height;
    }

    static void Main(string[] args)
    {
        Console.Write("Ange cylinderns radie: ");
        double radius = Convert.ToDouble(Console.ReadLine());

        Console.Write("Ange cylinderns höjd: ");
        double height = Convert.ToDouble(Console.ReadLine());

        double volume = CalculateVolume(radius, height);
        double surfaceArea = CalculateSurfaceArea(radius, height);

        Console.WriteLine($"Volymen är {volume:f2} v.e. och mantelarean är {surfaceArea:f2} a.e.");
    }
}
```



## Uppgift 4
```csharp
class Program
{
    static void Main(string[] args)
    {
        string[] words = new string[3];

        for (int i = 0; i < words.Length; i++)
        {
            Console.Write($"Ange ord {i + 1}: ");
            words[i] = Console.ReadLine();
        }

        Console.WriteLine("Du angav följande ord:");
        for (int i = 0; i < words.Length; i++)
        {
            Console.WriteLine($"{i + 1}. {words[i]}");
        }
    }
}
```

## Uppgift 5
```csharp
class Program
{
    static int CountPositiveNumbers(int[] numbers)
    {
        int count = 0;
        foreach (int num in numbers)
        {
            if (num > 0)
                count++;
        }
        return count;
    }

    static void Main(string[] args)
    {
        int[] testArray = { -1, 2, 3, -4, 5 };
        int positiveCount = CountPositiveNumbers(testArray);
        Console.WriteLine($"Antal positiva tal: {positiveCount}");
    }
}
```

## Uppgift 6
```csharp
class Program
{
    static string ToggleCase(string input)
    {
        // Skapar en tom sträng som ska byggas upp med bytta case
        string result = "";  
        for (int i = 0; i < input.Length; i++)
        {
            // Kontrollera om tecknet är gemen/versal
            if (char.IsUpper(input[i]))
            {
                result += char.ToLower(input[i]);
            }
            else if (char.IsLower(input[i]))
            {
                result += char.ToUpper(input[i]);
            }
            else
            {
                // För övriga tecken, t.ex. mellanslag, lägg till dem ändå
                result += input[i]; 
            }
        }
        return result;
    }

    static void Main()
    {
        string toggled = ToggleCase("Hej på dig");
        Console.WriteLine(toggled);
    }
}
```




## Uppgift 7
```csharp
class Program
{
    static bool ContainsNumber(int[] numbers, int target)
    {
        foreach (int num in numbers)
        {
            if (num == target)
            {
	            return true;
            }
        }
        return false;
    }

    static void Main(string[] args)
    {
        int[] array = { 1, 2, 3, 4, 5 };
        bool result = ContainsNumber(array, 3);
        Console.WriteLine($"Finns talet 3 i arrayen? {result}");
    }
}
```


## Uppgift 8
```csharp
class Program
{
    static void Main(string[] args)
    {
	    // Blir rätt kort main, använder eg. bara våra metoder
        int[] randomNumbers = GenerateRandomArray();

        Console.WriteLine($"Minsta tal: {FindMin(randomNumbers)}");
        Console.WriteLine($"Största tal: {FindMax(randomNumbers)}");
        Console.WriteLine($"Medelvärde: {CalculateAverage(randomNumbers)}");
        Console.WriteLine($"Median: {CalculateMedian(randomNumbers)}");
        Console.WriteLine($"Antal jämna tal: {CountEvenNumbers(randomNumbers)}");
        Console.WriteLine($"Antal udda tal: {CountOddNumbers(randomNumbers)}");
    }

    // Metod för att generera en array med 20 slumpmässiga tal mellan 0 och 100
    static int[] GenerateRandomArray()
    {
        Random rand = new Random();
        int[] array = new int[20];
        for (int i = 0; i < array.Length; i++)
        {
            array[i] = rand.Next(0, 101); 
        }
        return array;
    }

    // Metod för att hitta minsta talet i arrayen
    static int FindMin(int[] numbers)
    {
        int min = numbers[0];
        for (int i = 1; i < numbers.Length; i++)
        {
            if (numbers[i] < min)
                min = numbers[i];
        }
        return min;
    }

    // Metod för att hitta största talet i arrayen
    static int FindMax(int[] numbers)
    {
        int max = numbers[0];
        for (int i = 1; i < numbers.Length; i++)
        {
            if (numbers[i] > max)
                max = numbers[i];
        }
        return max;
    }

    // Metod för att beräkna medelvärdet av talen i arrayen
    static double CalculateAverage(int[] numbers)
    {
        int sum = 0;
        for (int i = 0; i < numbers.Length; i++)
        {
            sum += numbers[i];
        }
        return (double)sum / numbers.Length;
    }

    // Metod för att beräkna medianen av talen i arrayen
    static double CalculateMedian(int[] numbers)
    {
        Array.Sort(numbers); // Sortera arrayen först
        int middle = numbers.Length / 2;

        // Om längden är jämn, ta medelvärdet av de två mittersta talen
        if (numbers.Length % 2 == 0)
        {
            return (numbers[middle - 1] + numbers[middle]) / 2.0;
        }
        else
        {
            return numbers[middle];
        }
    }

    // Metod för att räkna antalet jämna tal i arrayen
    static int CountEvenNumbers(int[] numbers)
    {
        int count = 0;
        for (int i = 0; i < numbers.Length; i++)
        {
            if (numbers[i] % 2 == 0)
            {
                count++;
            }
        }
        return count;
    }

    // Metod för att räkna antalet udda tal i arrayen
    static int CountOddNumbers(int[] numbers)
    {
        int count = 0;
        for (int i = 0; i < numbers.Length; i++)
        {
            if (numbers[i] % 2 != 0)
            {
                count++;
            }
        }
        return count;
    }
}
```




## Uppgift 9
```csharp
class Program
{
    static void Main(string[] args)
    {
        Console.Write("Ange en mening: ");
        string userInput = Console.ReadLine();

        int numberOfVowels = CountVowels(userInput);
        Console.WriteLine($"Antal vokaler i meningen: {numberOfVowels}");
    }

    // Metod som räknar antalet vokaler i en sträng
    static int CountVowels(string input)
    {
        // Inkluderar både små och stora vokaler
        string vowels = "aeiouyåäöAEIOUYÅÄÖ"; 
        int vowelCount = 0;

        for (int i = 0; i < input.Length; i++)
        {
            // Kolla om tecknet finns i strängen och då öka räknaren med en
            if (vowels.Contains(input[i]))
            {
                vowelCount++;
            }
        }
        return vowelCount;
    }
    
}
```


## Uppgift 10
```csharp
class Program
{
    static void Main(string[] args)
    {
        int positiveNumber = GetPositiveInteger();
        Console.WriteLine($"Du angav talet: {positiveNumber}");
    }

    static int GetPositiveInteger()
    {
        // Startvärden
        int number = 0;
        bool isValid = false;

        // Kör loopen när isValid är false
        while (!isValid) 
        {
            Console.Write("Ange ett positivt heltal: ");
            string input = Console.ReadLine();

            // Sätt boolen till falsk om det inte går att parsea
            isValid = int.TryParse(input, out number);

            // Sätt boolen till falsk om det inte är ett positivt tal
            if (number < 0)
            {
                isValid = false;
            }

            // Om boolen är falsk skriv ut info
            if (!isValid)
            {
                Console.WriteLine("Ogiltig inmatning. Försök igen med ett positivt heltal.");
            }
        }
        return number;
    }
}
```




## Uppgift 11
```csharp
class Program
{
    static void Main(string[] args)
    {
        int[,] array = GenerateRandomArray();
        bool continueRunning = true;

        while (continueRunning)
        {
            // Skriv ut menyn och arrayen
            Console.Clear();
            Console.WriteLine("\n--- Huvudmeny ---");
            PrintArray(array);
            Console.WriteLine();
            Console.WriteLine("1. Skriv ut summan av alla element");
            Console.WriteLine("2. Skriv ut största elementet");
            Console.WriteLine("3. Skriv ut summan för arrayens rader");
            Console.WriteLine("4. Skriv ut summan för arrayens kolumner");
            Console.WriteLine("5. Generera nya tal till arrayen");
            Console.WriteLine("6. Avsluta");
            Console.Write("Välj ett alternativ (1-6): ");

            string choice = Console.ReadLine();
            switch (choice)
            {
                case "1":
                    Console.WriteLine($"Summan av alla element är: {SumAllElements(array)}");
                    break;
                case "2":
                    Console.WriteLine($"Det största elementet är: {FindMaxElement(array)}");
                    break;
                case "3":
                    PrintRowSums(array);
                    break;
                case "4":
                    PrintColumnSums(array);
                    break;
                case "5":
                    array = GenerateRandomArray();
                    Console.WriteLine("Nya tal har genererats till arrayen.");
                    break;
                case "6":
                    continueRunning = false;
                    Console.WriteLine("Programmet avslutas.");
                    break;
                default:
                    Console.WriteLine("Ogiltigt val, försök igen.");
                    break;
            }
            Console.ReadLine();
        }
    }

    // Metod som returnerar en array med slumpade tal 1-9
    static int[,] GenerateRandomArray()
    {
        Random rand = new Random();
        int[,] array = new int[3, 3];
        for (int row = 0; row < 3; row++)
        {
            for (int col = 0; col < 3; col++)
            {
                array[row, col] = rand.Next(1, 10);
            }
        }
        return array;
    }

    // Returnerar summan av alla element i en 2D int array
    static int SumAllElements(int[,] array)
    {
        int sum = 0;
        for (int row = 0; row < 3; row++)
        {
            for (int col = 0; col < 3; col++)
            {
                sum += array[row, col];
            }
        }
        return sum;
    }

    // Returnerar det största värdet
    static int FindMaxElement(int[,] array)
    {
        // Börja med det första värdet, sen loopa igenom och jämför varje värde
        int max = array[0, 0];
        for (int row = 0; row < 3; row++)
        {
            for (int col = 0; col < 3; col++)
            {
                // Om värdet är större än tidigare max, spara värdet i max, så att det blir nya max
                if (array[row, col] > max)
                {
                    max = array[row, col];
                }
            }
        }
        return max;
    }

    // Skriver ut radsumma för respektive rad
    static void PrintRowSums(int[,] array)
    {
        for (int row = 0; row < 3; row++)
        {
            int rowSum = 0;
            for (int col = 0; col < 3; col++)
            {
                rowSum += array[row, col];
            }
            // Utskrift sker inne i for-loopen
            Console.WriteLine($"Summan av rad {row + 1} är: {rowSum}");
        }
    }

    // Skriver ut kolumnsumma för resp kolumn
    static void PrintColumnSums(int[,] array)
    {
        for (int col = 0; col < 3; col++)
        {
            int colSum = 0;
            for (int row = 0; row < 3; row++)
            {
                colSum += array[row, col];
            }
            Console.WriteLine($"Summan av kolumn {col + 1} är: {colSum}");
        }
    }

    // Metod för att skriva ut arrayen i konsolen
    static void PrintArray(int[,] array)
    {
        Console.WriteLine("Arrayen:");
        for (int row = 0; row < 3; row++)
        {
            for (int col = 0; col < 3; col++)
            {
                Console.Write(array[row, col] + " ");
            }
            Console.WriteLine();
        }
    }
}
```







## Uppgift 12
```csharp
class Program
{
    static void Main(string[] args)
    {
        // Exempel på en giltig 3x3-array
        int[,] sudokuGrid = {
        { 5, 3, 4 },
        { 6, 7, 2 },
        { 1, 9, 8 }
        };

        bool isValid = IsValidSudokuSection(sudokuGrid);
        Console.WriteLine($"Är arrayen en giltig del av en sudokulösning? {isValid}");
    }

    // Metod som kontrollerar om en 3x3-array är en giltig del av en sudokulösning
    static bool IsValidSudokuSection(int[,] grid)
    {
        // Array med bools för att hålla koll på vilka tal som är "hittade" 
        // d.v.s. om vi loopar igenom och börjar med att hitta en 5:a, så markeras 
        // en av bools:en i denna array till true (närmare bestämt den på index 4)
        bool[] seenNumbers = new bool[9]; 

        // Loopa igenom sudoku-arrayen med nästlad loop
        for (int row = 0; row < 3; row++)
        {
            for (int col = 0; col < 3; col++)
            {
                // Spara den aktuella siffran till variabel för läsbarhet i if-satserna
                int number = grid[row, col];

                // Kontrollera om siffran ligger utanför intervallet, 
                // isf så returnera direkt false för hela metoden, då behöver vi inte
                // kolla mer, eftersom vi har redan brutit mot the prime directive 
                if (number < 1 || number > 9)
                {
                    return false;
                }

                // Kontrollera om siffran redan setts, samma visa, avbryt och returnera falskt, vi kan inte ha dubletter
                if (seenNumbers[number - 1])
                {
                    return false; // Ogiltig om siffran redan förekommer
                }

                // Markera siffran som hittad i arrayen med bools
                seenNumbers[number - 1] = true;
            }
        }

        // Om vi ens kommer ut hit i koden så har alltså alla siffror passerat checkarna i for-looparna
        // alltså måste allt vara OK, returnera därmed true
        return true; 
    }
}
```


## Uppgift 13
```csharp
class Program
{
    static void Main(string[] args)
    {
        // Exempel på en 3x3-matris
        int[,] matrix = {
        { 1, 2, 3 },
        { 4, 5, 6 },
        { 7, 8, 9 }
        };

        int mainDiagonalSum = CalculateMainDiagonalSum(matrix);
        int otherDiagonalSum = CalculateOtherDiagonalSum(matrix);

        Console.WriteLine($"Summan av huvuddiagonalen är: {mainDiagonalSum}");
        Console.WriteLine($"Summan av den andra diagonalen är: {otherDiagonalSum}");
    }

    // Metod för att beräkna diagonalsumman från övre vänstra till nedre högra hörnet
    static int CalculateMainDiagonalSum(int[,] array2D)
    {
        int sum = 0;
        // Loopa igenom arrayen antal rader, summera talen som finns på 
        // positionerna 0,0 + 1,1 + 2,2 osv
        for (int i = 0; i < array2D.GetLength(0); i++)
        {
            sum += array2D[i, i];
        }
        return sum;
    }

    // Metod för att beräkna diagonalsumman från övre högra till nedre vänstra hörnet
    static int CalculateOtherDiagonalSum(int[,] array2D)
    {
        // Spara till variabel för läsbarhet sen
        int n = array2D.GetLength(0); 
        int sum = 0;

        // Samma loop som ovan
        for (int i = 0; i < n; i++)
        {
            // Här är villkoret lite bökigare, vi går uppifrån höger ner till vänster

            // Låt säga att arrayen är 3x3, dvs index från 0 - 2, n kommer att bli 3, n = 3
            // Första varvet kommer i = 0, alltså kommer positionen vi tittar på vara [0, 3-0-1] = [0,2]
            // [0,2] stämmer bra överens med det högra hörnet

            // Andra varvet ger [1, 3-1-1] = [1,1], stämmer bra, etc.
            sum += array2D[i, n - i - 1];
        }
        return sum;
    }
}
```


