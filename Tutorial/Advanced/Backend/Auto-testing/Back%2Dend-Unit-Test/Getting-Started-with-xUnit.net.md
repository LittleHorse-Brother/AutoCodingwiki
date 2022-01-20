In this article, we will demonstrate getting started with xUnit.net, showing you how to write and run your first set of unit tests.

- [Create a unit test project](#Create-a-unit-test-project)
- [Learning to use Test Explorer](#Learning-to-use-Test-Explorer)
- [Write your first test](#Write-your-first-test)
- [Write your fist theory](#Write-your-first-theory)

# Create a unit test project

Start Visual Studio, which will bring you to the start splash screen. Under "Get Started", click "Create a new project". This will bring you to the first step of the new project wizard, where you pick your project type:
![image.png](/.attachments/image-82d7c128-d3bf-40e4-bf1a-bf98fd0eb193.png)

In the drop down boxes, choose your language (C#), your platform (All platforms), and your project type (Test). Scroll through the list if necessary until you find the item titled "xUnit Test Project (.NET Core)". Select it, then click "Next".

This leads you to the second part of the new project wizard:

![image.png](/.attachments/image-93ece377-b88e-4840-889d-76ecc28411a7.png)

Type a name into the "Project name" box (like "MyFirstUnitTests"). Click "Create".

After a moment, Visual Studio will launch with your newly created project.

Find the project in the Solution Explorer (it will be titled "MyFirstUnitTests"), right click it, then click "Edit Project File". This will launch the text editor for your project file. It should look something like this:
```csharp
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>

    <IsPackable>false</IsPackable>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.NET.Test.Sdk" Version="16.5.0" />
    <PackageReference Include="xunit" Version="2.4.0" />
    <PackageReference Include="xunit.runner.visualstudio" Version="2.4.0" />
    <PackageReference Include="coverlet.collector" Version="1.2.0" />
  </ItemGroup>

</Project>
```
Let's quickly review what's in this project file:

- `TargetFramework` specifies the target framework for your test project. By default this will be the latest version of .NET Core that your system supports (in this example, .NET 3.1). 
- `IsPackable` is here, though it is redundant (unit test projects cannot be packed by default). You can safely remove this line if you wish.
- The `xunit` package brings in three child packages which include functionality that most developers want: xunit.core (the testing framework itself), xunit.assert (the library which contains the `Assert` class), and `xunit.analyzers` (which enables Roslyn analyzers to detect common issues with unit tests and xUnit.net extensibility).
- The packages `xunit.runner.visualstudio` and `Microsoft.NET.Test.Sdk` are required for being able to run your test project inside Visual Studio as well as with `dotnet test`.
- The `coverlet.collector` package allows collecting code coverage. If you don't intend to collect code coverage, you should remove this package reference.

A single empty unit test was also generated into UnitTest1.cs:
```csharp
using System;
using Xunit;

namespace MyFirstUnitTests
{
    public class UnitTest1
    {
        [Fact]
        public void Test1()
        {

        }
    }
}
```
Let's make sure everything builds. Choose Build > Build Solution from the main menu. Your project should build without issue, as shown in the output window:

```
1>------ Build started: Project: MyFirstUnitTests, Configuration: Debug Any CPU ------
1>MyFirstUnitTests -> C:\Users\admin\source\repos\MyFirstUnitTests\MyFirstUnitTests\bin\Debug\netcoreapp3.1\MyFirstUnitTests.dll
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

# Learning to use Test Explorer

Test Explorer is the name of the window that lets you browse and run your tests from within Visual Studio. Open it by choosing Test > Test Explorer from the main menu. You should be greeted with a window that contains a hierarchy of the tests in your project, which should look something like this:
![image.png](/.attachments/image-844510c5-0e37-4737-b621-090be3cb4afa.png)

The toolbar of Test Explorer has buttons in several groups:

- The first group contains buttons that are used for running tests, including the ability to run all tests, run selected tests, re-run the last tests, and re-run only the failed tests.
- The second group contains buttons which allow filtering the list of tests based on current state (which includes "passed", "failed", and "not run").
- The third group contains buttons which configure Test Explorer, including advanced options like changing processor architecture (x86, x64, or Auto) and automatically running tests after every successful build.

The main window of Test Explorer is split into two panes:

- The left pane contains a tree view of the tests in your project (grouping criteria can be changed as you see fit). Columns can be configured to show details about the test, including things like the current state, how long the test took to run, metadata (traits) related to the test, and more.
- As you select items in the tree view on the left pane, the right pane will provide information about your current selection, including test counts, outcomes, links to the source of the test, test output, and exception messages and stack traces for failed tests.

Click the left-most button on the Test Explorer toolbar (it looks like a double green arrow, titled "Run All Tests In View". This will run the single empty test, and the result should be success:
![image.png](/.attachments/image-6f7da583-405b-47a1-ae8d-f57063885ef7.png)
Now that we've ensured everything is working, it's time to write our first real tests.

# Write your first test
Edit `UnitTest1.cs` and replace the default file contents with this:
```csharp
using Xunit;

namespace MyFirstUnitTests
{
    public class UnitTest1
    {
        [Fact]
        public void PassingTest()
        {
            Assert.Equal(4, Add(2, 2));
        }

        [Fact]
        public void FailingTest()
        {
            Assert.Equal(5, Add(2, 2));
        }

        int Add(int x, int y)
        {
            return x + y;
        }
    }
}
```
Now let's go run the tests again and see what happens:
![image.png](/.attachments/image-c5d304f4-443f-455d-a28b-7d64f144f08e.png)
We purposefully wrote both a passing and failing test, and we can see that the results reflect that. By clicking on the failed test, we can see a link both to the top of the unit test (at line 14), but also the failure message (we expected 5 but got 4) as well as a link to the exact line where the failure occurred (line 16).

When you edit the source file, also take note of the fact that CodeLens decorations show up which indicate not only test status (passed/failed) on the test themselves, but also on functions that are called by the code, indicating how often the code is called in tests, and a count of which of those tests have passed or failed:
![image.png](/.attachments/image-764ac6ad-e381-4c19-94e0-5fb0a78c464d.png)
Now that we've gotten your first unit tests to run, let's introduce one more way to write tests: using theories.

# Write your first theory

You may have wondered why your first unit tests use an attribute named `[Fact]` rather than one with a more traditional name like Test. xUnit.net includes support for two different major types of unit tests: `facts` and `theories`. When describing the difference between facts and theories, we like to say:

- <b>Facts</b> are tests which are always true. They test invariant conditions.
- <b>Theories</b> are tests which are only true for a particular set of data.

A good example of this is testing numeric algorithms. Let's say you want to test an algorithm which determines whether a number is odd or not. If you're writing the positive-side tests (odd numbers), then feeding even numbers into the test would cause it fail, and not because the test or algorithm is wrong.

Let's add a theory to our existing facts (including a bit of bad data, so we can see it fail):
```csharp
[Theory]
[InlineData(3)]
[InlineData(5)]
[InlineData(6)]
public void MyFirstTheory(int value)
{
    Assert.True(IsOdd(value));
}

bool IsOdd(int value)
{
    return value % 2 == 1;
}
```
This time when we run our tests, we see a second failure, for our theory that was given 6:
![image.png](/.attachments/image-b3040357-52bf-4af8-8896-c12611d197b0.png)

Although we've only written 3 test methods, the test runner actually ran 5 tests; that's because each theory with its data set is a separate test. Note also that the runner tells you exactly which set of data failed, because it includes the parameter values in the name of the test. The Test Explorer UI even shows a new level in the tree, as each row of data becomes a test result underneath its test method.