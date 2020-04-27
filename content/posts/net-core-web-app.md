---
title: ".NET Core Web App"
date: 2020-04-27T16:30:23+01:00
tags: [.net core, xunit, moq]
---

_Create a .NET Core C# web application that renders a list of random names [api](http://names.drycodes.com/10?combine=4). Load Names from an API, where the URI for API is set in an appSettings file.  Use the Configuration IOptions pattern and the HttpClientFactory factory class. Create a test using Moq and xUnit, and return Stub from HttpMessageHandler.  Use a different API URI per environment._

**Requirements**:

1. Create an .NET Core web app using the `dotnet` CLI and add to a `src` folder

2. Create an xunit project using the `dotnet` CLI and add to the `src` folder

3. Add the `.NET Core web app` project reference to the `test` project

4. Add the `Moq` nuget package to the `test` project

5. TBC


**Tech**:

- .NET Core 3.1
- xUnit
- Moq

**References**

- [random name generator API](http://names.drycodes.com/10?combine=4)

**Hint 1**

```bash
dotnet new webapp -n foo -o baa/src/foo
dotnet new xunit -n test -o baa/src/test
dotnet add baa/src/test reference baa/src/foo
dotnet add baa/src/test package Moq
```