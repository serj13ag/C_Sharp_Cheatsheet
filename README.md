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

## Терминология

**Кодовый файл (.cs csharp code file)** — это один из файлов на языке C#.
**Проект (project)** — это совокупность кодовых файлов, которые могут быть скомпилированы в сборку: программу или библиотеку.
**Сборка (assembly)** — это, соответственно, результат компиляции проекта. Как правило это *.exe или *.dll файл, содержащий инструкции для компьютера.

**Решение (solution)** — это несколько проектов, объединенные общими библиотеками и задачами. Как правило открывать с помощью Visual Studio нужно именно файл решения (.sln), хотя можно открыть и отдельный проект (.csproj файл). Имейте в виду, если открыть отдельный кодовый файл, не открывая проект или решение, то не будет возможности его запустить. Это распространённая ошибка новичков.

**Reference** — ссылка внутри проекта на другие сборки. Только сославшись на другую сборку можно будет использовать код из неё.

**Метод (method)** — это последовательность действий. Аналог функций, процедур и подпрограмм в других языках. В устной речи часто используют все эти слова как синонимы, но в спецификации на язык C# используется термин «метод».

**Класс (class)** — это совокупность данных и методов. Все сборки состоят из скомпилированных классов.

**Пространство имен (namespace)** — это совокупность классов, логически связанных между собой.

Между сборками и пространствами имен нет прямого соответствия: в сборке может хранится несколько пространств имен, а разные классы одного пространства имен могут быть определены в разных сборках.

После успешной компиляции, в директории проекта создается поддиректория bin/Debug, в которой и оказывается сборка — результат компиляции — exe или dll файлы вашей программы.


