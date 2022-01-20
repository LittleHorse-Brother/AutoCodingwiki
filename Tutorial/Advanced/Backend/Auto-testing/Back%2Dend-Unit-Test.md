# What is Unit Testing
Unit testing is a type of testing in which individual units or functions of software testing. Its primary purpose is to test each unit or function. A unit is the smallest testable part of an application. It mainly has one or a few inputs and produces a single output. In procedural programming, a unit referred to as an individual program, while object-oriented programming languages include Base/Superclass, abstract class, Derived/Child class takes place. Unit test frameworks, drivers, stubs and mocks /fake objects used in Unit Testing. It works on the basis of a White box technique.

# When to do Unit Testing
- If you want to write a new function
- If you want to write new functions on untested code
- If you want fix a bug
- If you want code that refactor has not tested
- If you find an edge exception value

# How to do Unit Testing
When you don't know how to start unit test cases, we can consider designing unit test cases from the following aspects:
- Check input parameters
- Check out parameters
- Check boundary values
- External dependency status (open / close / file pointer / file properties / permissions)
- Data type, initial value, default value, overflow, underflow
- Abnormal test
- Intelligibility of error messages
- Branch, condition, path

We recommend using `xUnit` as our unit testing framework. If you don't know how to use `xUnit`, you can read [Getting Started with xUnit.net](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/979/Getting-Started-with-xUnit.net).

After you know how to design and write a unit test case, let's take a look at the best practices of unit testing.
1. Arrange, Act, Assert
2. One Assert Per Test Method
3. Avoid Test Interdependence
4. Keep It Short, Sweet, and Visible
5. Recognize Test Setup Pain as a Smell
6. Add Them to the Build

In order to avoid test interdependence and interdependence and make the test brief and pure, we need to introduce mock. Usually, we use `Moq` library to implement [mock](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/998/What-is-Mock). You can read [Getting Started with Moq](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/984/Getting-Started-with-Moq) about the use of `Moq`。

After you complete the unit test, we need to issue a test report, which should contain the test results (total number of cases, number of successes, number of failures) and relevant data of code coverage. In order to measure the test, which code has been tested and which code has not been tested. For the parts not tested, we will write some cases for testing.

Read [How to Generate Test Report](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/987/Getting-Started-with-Code-Coverage) for information on how to generate test reports.
