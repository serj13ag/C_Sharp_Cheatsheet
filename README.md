# C-Sharp-Notes

<br>

# Index<br>

[Hello, World](#Hello-world)<br>
[Переменные (variables)](#Переменные-variables)<br>
[Типы данных](#Типы-данных)<br>
[Конверсия числовых типов данных (cast)](#Конверсия-числовых-типов-данных-cast)<br>
[Строки](#Строки)<br>


# Hello, world!

```c#
// Подключение пространства имен System.
using System;

// Таким образом вы определяете свое пространство имен Lectures.
namespace Lectures
{
	// Таким образом определяется класс Program.
	class Program
	{
		/*
		 * static означает, что данное поле, метод или свойство будет принадлежать не каждому объекту класса, а всем им вместе.
		 * void Main() определяет метод.
		 * Из-за своего названия Main является точкой входа — это метод, 
		 * который будет запущен при выполнении программы.
		 */
		static void Main()
		{
			// Этот код выводит на экран строку
			// Console — это класс, так же как Program, но из пространства имен System.
			Console.WriteLine("Hello, world!");
        	}
	}
}
```

### Терминология

**Кодовый файл (.cs csharp code file)** — это один из файлов на языке C#.

**Проект (project)** — это совокупность кодовых файлов, которые могут быть скомпилированы в сборку: программу или библиотеку.

**Сборка (assembly)** — это, соответственно, результат компиляции проекта. Как правило это .exe или .dll файл, содержащий инструкции для компьютера.

**Решение (solution)** — это несколько проектов, объединенные общими библиотеками и задачами. Как правило открывать с помощью Visual Studio нужно именно файл решения (.sln), хотя можно открыть и отдельный проект (.csproj файл). Имейте в виду, если открыть отдельный кодовый файл, не открывая проект или решение, то не будет возможности его запустить. Это распространённая ошибка новичков.

**Reference** — ссылка внутри проекта на другие сборки. Только сославшись на другую сборку можно будет использовать код из неё.

**Метод (method)** — это последовательность действий. Аналог функций, процедур и подпрограмм в других языках. В устной речи часто используют все эти слова как синонимы, но в спецификации на язык C# используется термин «метод».

**Класс (class)** — это совокупность данных и методов. Все сборки состоят из скомпилированных классов.

**Пространство имен (namespace)** — это совокупность классов, логически связанных между собой.
Между сборками и пространствами имен нет прямого соответствия: в сборке может хранится несколько пространств имен, а разные классы одного пространства имен могут быть определены в разных сборках.
После успешной компиляции, в директории проекта создается поддиректория bin/Debug, в которой и оказывается сборка — результат компиляции — exe или dll файлы вашей программы.

<br>

# Переменные (variables)

**Переменная** — это именованная область памяти.

**Тип переменной** — это формат области памяти, определяющий множество возможных значений переменной и множество допустимых операций над ней.

```c#
class Program
{
	static void Main()
	{
		
		// так объявляется переменная: тип (int), затем имя (integerNumber)
		int integerNumber;

		// так осуществляется присваивание
		integerNumber = 10;

		// Можно совмещать объявление и присваивание.
		float floatNumber = 12.34f;
	}
}
```

### Объявление переменных - Define Variables

```c#
int i, j, k;
char c, ch;
float f, salary;
double d;
```

| Type     | Name          |
| ------------- |:-------------:| 
|```int```|i, j, k;|
|```char```|c, ch;|
|```float```|f, salary;|
|```double```|d;|

### Присваивание переменной - Initialise Varaiable

```c#
variable_name = value;
```

You can also initialize a varaible at the same time you define it.

```c#
int d = 3, f = 5;    // Initializing d and f.
byte z = 22;         // Initializes z.
double pi = 3.14159; // Declares an approximation of pi.
char x = 'x';        // The variable x has the value 'x'.
```

# Типы данных

| Type       | Description          |Examples  |
| ------------- |:-------------:| -----:|
| `int `    | Integer (whole numbers) | 103, 12, 5168|
| `double`    | 64 bit floating-point number | 3.14, 3.4e38|
| `Float`     | Floating-point number     |   3.14, 3.4e38 |
| `Decimal` | Decimal number (higher precision)      |   1037.196543 |
| `Bool`    | Boolean  | true, False|
| `String`  | String | "Hello World" |
| `byte`  | 8-bit unsigned integer | 0 to 255 |
| `char`  | 16-bit Unicode character | "A" |
| `long`  | 64-bit signed integer type | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 |

<br>

# Конверсия числовых типов данных (cast)

**Конверсия типов (cast)** - это преобразование одного типа переменной в другой

```c#
class Program2
{
	static void Main()
	{
		int integerNumber = 45;
		double doubleNumber = 34.56;

		doubleNumber = integerNumber;
		// Это неявная конверсия типов: присвоение переменной одного типа 
		// значения переменной другого типа без дополнительных усилий. 
		// Она возможна, когда не происходит потери информации

		integerNumber = (int)doubleNumber;
		// Это явная конверсия типов. В случае, когда конверсия ведет к потере информации
		// (в данном случае - дробной части), необходимо явно обозначать свои намерения
		// по конверсии.

		integerNumber = (int)Math.Round(34.67);
		// Округление лучше всего делать не конверсией, а функцией Round. 
		// Кстати, Math - "математическая библиотека" C# - имеет множество других
		// полезных методов. 

		long longInteger = 4000000000;
		integerNumber = (int)longInteger;
		// При такой конверсии происходит ошибка переполнения, которая, однако, остается
		// незамеченной для компилятора и среды разработки

		// Таким образом можно отловить эти ошибки явно
		checked
		{
			integerNumber = (int)longInteger;
		}
	}
}
```

# Строки

**Строки** - это последовательности символов

```c#
class Program
{
	public static void Main()
	{
		string myString = "Hello, world!";

		// + — это операция "приписывания" одной строки к другой:
		string s = "Hello" + " " + "world";

		// Можно обращаться к отдельным символам
		char c = myString[1]; //'e' — нумерация символов с нуля.
		char myChar = 'e'; // одинарные кавычки используются для символов. Двойные — для строк.

		//У строк есть собственные методы и переменные (правильно называть это свойствами),
		//которые позволяют узнать информацию о строке 
		Console.WriteLine(myString.Length);

		myString = myString.Substring(0, 5);
		Console.WriteLine(myString);

		string strangeSymbols = "© 2014 Σγμβόλσ";

		//Тип string может иметь особое значение - null.
		//Это не пустая строка, а отсутствие всякой строки.
		myString = null;

		//Интересно, что тип int такого значения иметь не может.
		//int a=null;

		int number = int.Parse("42"); //Из строки в число
		string numString = 42.ToString(); // Из числа в строку
		double number2 = double.Parse("34.42"); // Зависит от настроек операционной системы

		//Следующий вызов не зависит от настроек и всегда ожидает точку в качестве разделителя:
		number2 = double.Parse("34.42", CultureInfo.InvariantCulture);

		//Следующий вызов не зависит от настроек и всегда использует точку в качестве разделителя:
		string invariantNumber2 = number2.ToString(CultureInfo.InvariantCulture);
		Console.WriteLine(invariantNumber2); //34.42
	}
}
```

# Арифметические операции и var

```c#
class Program
{
	static void Main()
	{
		int a = 23;
		int b = 45;
		double angle = 1.4;

		// Математические операции записываются естественным образом
		int c = (a + b) / 2;

		//Класс Math содержит полезные методы и константы
		Console.WriteLine(Math.Sin(angle));

		var d = a - b;
		/* часто понятно, какого типа должна быть переменная. В этом случае можно писать var
		 * Компилятор самостоятельно догадается, что именно вы имели в виду
		 */

		// это целое число
		var e = a / 2;
		// это число с плавающей точкой
		var f = a / 2.0;

		c = b = a;
		/* Как это работает? b=a - оператор присвоения, но он имеет собственное 
		 * возвращаемое значение (равное a)
		 * Поэтому c = b = a выполняется так:
		 * - b присваивается a
		 * - c присваивается результату b=a, который также равен a
		 * В итоге все три переменные будут равны
		 */

		a -= 4;
		// То же самое, что a=a-4, аналогично с другими операциями.

		a++;
		//Оператор инкремента
		//То же самое, что a=a+1

		a--;
		//Оператор декремента
		//То же самое, что a=a-1

		++a;
		//То же самое, что a=a+1, но с одним отличием:

		a = 5;
		Console.WriteLine(a++);
		// выведет 5

		a = 5;
		Console.WriteLine(++a);
		// выведет 6

	}
}
```

# Методы

**Метод** — это блок кода, содержащий ряд инструкций. Программа инициирует выполнение инструкций, вызывая метод и указывая все аргументы, необходимые для этого метода. В C# все инструкции выполняются в контексте метода.

Метод **Main** является точкой входа для каждого приложения C# и вызывается общеязыковой средой выполнения (CLR) при запуске программы. В приложении, использующем инструкции верхнего уровня, метод Main создается компилятором и содержит все инструкции верхнего уровня.

```c#
class Program
{

	// Это метод, возвращающий значение типа int, принимающий два аргумента типа double.
	// Его можно называть функцией, но это название не очень распространено.
	// Сигнатура метода - это совокупность имени метода и последовательности типов аргументов
	static int DivideAndRound(double a, double b)
	{
		// return указывает, какое значение будет возвращено
		return (int)Math.Round(a / b);
	}

	// Это метод, не возвращающий значения. Вместо типа возвращаемого значения стоит void
	static void WriteNumber(int number)
	{
		Console.WriteLine(number);

		// return указывается без значения, и его следует опускать, когда это возможно
		return;
	}

	static void WriteNumber(int number, int anotherNumber)
	{
		Console.WriteLine(number);
		Console.WriteLine(anotherNumber);
	}

	static void Main()
	{
		WriteNumber(DivideAndRound(10.5, 2.1));
	}
}
```
