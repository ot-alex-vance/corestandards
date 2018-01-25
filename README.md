# dotnetcore standards
This repo should be used as a guideline and/or template to setting up a dotnetcore repository / solution.

## Solution/Project Structure

The solution file, build files, licenses, readmes, etc. should be located at the root of the repostiory.

The solution name should match the repo name.

The solution need to contain solution folders that match the physical folders (src, test, etc).

All source code should exist in project folders underneath a 'src' solution/physical folder.

All tests should exist in project folders underneath a 'test' solution/physical folder.

## Namespacing

Projects should be namespaced to match this namespacing scheme: OneTechnologies.Product.Project.Area.SubArea

Ex:
- OneTechnologies.CoreStandards.One
- OneTechnologies.CoreStandards.One.Utils
- OneTechnologies.CoreStandards.One.Tests
- OneTechnologies.CoreStandards.One.Tests.Utils
 
## Coding Guidelines

### General Styling

1. Use 4 spaces instead of tabs
2. Use \_camelCase for private fields
3. Avoid using this. where possible
4. Always specify member visibility (private string \_foo; instead of string \_foo;)
5. Open-braces ({) go on a new line
6. Use only complete words or common/standard abbreviations

### Usage of the var keyword

The <code>var</code> keyword is to be used as much as the compiler will allow.For example, these are correct:

```csharp
var fruit = "Lychee";
var fruits = new List<Fruit>();
var flavor = fruit.GetFlavor();
string fruit = null; // can't use "var" because the type isn't known (though you could do (string)null, don't!)
const string expectedName = "name"; // can't use "var" with const
```

The following are incorrect:

```csharp
string fruit = "Lychee";
List<Fruit> fruits = new List<Fruit>();
FruitFlavor flavor = fruit.GetFlavor();
```

### Use C# type keywords in favor of .NET type names

Examples are <code>string</code> over <code>String</code>; <code>object</code> over <code>Object</code>

### Cross-platform considerations

Since dotnetcore is cross-platform supported, we need to keep in mind that other developers may be working on a non-windows system. Here are a few things we can do to ensure we won't have problems working in different environments.

#### Line Breaks

Windows uses \r\n, OS X and Linux uses \n. When it is important, use Environment.NewLine instead of hard-coding the line break.

#### Environment Variables

OS's use different variable names to represent similar settings. Code should consider these differences.

For example, when looking for the user's home directory, on Windows the variable is <code>USERPROFILE</code> but on most Linux systems it is <code>HOME</code>.

#### File path separators (most important)

Windows uses \ and OS X and Linux use / to separate directories. Instead of hard-coding either type of slash, use <code>Path.Combine()</code> or <code>Path.DirectorySeparatorChar</code>.

If this is not possible (such as in scripting), use a forward slash. Windows is more forgiving than Linux in this regard.

#### Exception Handling

1. Use try/catch/finally blocks around code that can potentially generate an exception
    - In catch blocks, always order exceptions from the most specific to the least specific
    - Use a finally block to clean up resources, whether you can recover or not
2. Handle common conditions without throwing exceptions
    - Ex: checking a connections state before attempting to close it if(con.state != closed) { con.close(); }
3. Design classes to avoid exceptions. 
    - Ex: reading a stream without checking if it's null first
4. Use predefined .net exceptions
    - Only implement a custom exception when no predefined exception applies.
    - Always name exceptions with an "Exception" suffix. Ex: FooException

### Unit testing

XUnit should be used as the test framework for building out unit tests.

All unit tests should follow the three staged structure of: Arrange, Act, Assert.

All our code is should be unit tested when possible. There are obviously some circumstances that will not or cannot be tested. These should be notated during pull requests.
