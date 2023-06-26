### Structure
```cs
namespace projectname
{
	class classname
	{
		attribute1;
		attribute2;
		...

		method1(){ ... }
		method2(parameter){ ... }
		...
	}
}

// Solution
```

### Top Level Templates
```cs
// program.cs non top level template
using System;

namespace MyApp // Note: actual namespace depends on the project name.
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```
```xml
// disable / enable ImplicitUsings
<ImplicitUsings>disable</ImplicitUsings>
<ImplicisUsings>enable</ImplicitUsings>
```

### Basic
```cs
// single line commend
/*
	multiple line commend
*/

// print
Console.Write
Console.WriteLine("text");;
Console.WriteLine("a + b = {0} + {1} = {2}", a, b, sum);
Console.WriteLine($"a value is {a}, b value is {b}");

// input
Console.ReadLine();

// concatenate
Console.WriteLine("Number: " + num1);
message += " Thank you." // message = "Rus" then result is "Rus Thank you."

// if condition
if (condition) 
{ 
	... 
}
else if (condition) 
{ 
	... 
}
else 
{ 
	... 
}
// conditional operator AKA: ternary condition (right-associative)
condition ? consequent /* true */ : alternative /* false */;
condition ? consequent /* true */ : 
	condition /* else if */ ? consequent : alternative /* else */;
```

### Variable Type
| Type | Value | Initialization |
|-|-|-|
| int | 100 | int num1 = 7; |
| string | "Text" | string firstName = "Rus"; |
| ref | value of num1 | ref int refnum1 = ref num1; |
### Logic Comparison
|