# C-Sharp-Notes

<br>

# Index<br>

[Hello, World](#Hello-world)<br>

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
		 * static - некое волшебное слово, смысл которого будет ясен позднее.
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

# Переменные

```c#
class Program
{
	static void Main()
	{
		// Переменная — это именованная область памяти.
		//
		// Тип переменной — это формат области памяти, определяющий множество возможных значений
		// переменной и множество допустимых операций над ней.

		int integerNumber;
		// так объявляется переменная: тип (int), затем имя (integerNumber)

		// так осуществляется присваивание
		integerNumber = 10;

		// Можно совмещать объявление и присваивание.
		float floatNumber = 12.34f;
	}
}
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

# Конверсия типов (cast)

```c#
class Program2
{
	static void Main()
	{
		// Конверсия типов (cast) - это преобразование одного типа переменной в другой 

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


