# Data Transfer Objects

A Data Transfer Object (commonly known as a DTO) is usually an instance of a POCO (plain old CLR object) class used as a container to encapsulate data and pass it from one layer of the application to another. You would typically find DTOs being used in the service layer to return data back to the presentation layer. The biggest advantage of using DTOs is decoupling clients from your internal data structures.

---

## Create an ASP.NET Core 3.1 API project

First off, let’s create an ASP.NET Core project in Visual Studio. Assuming Visual Studio 2019 is installed in your system, follow the steps outlined below to create a new ASP.NET Core API project in Visual Studio.

- Launch the Visual Studio IDE.
- Click on “Create new project.”
- In the “Create new project” window, select “ASP.NET Core Web Application” from the list of the templates displayed.
- Click Next. 
- In the “Configure your new project” window, specify the name and location for the new project.
- Click Create. 
- In the “Create New ASP.NET Core Web Application” window shown next, select .NET Core as the runtime and ASP.NET Core 3.1 (or later) from the drop-down list at the top.
- Select “API” as the project template to create a new ASP.NET Core API application. 
- Ensure that the check boxes “Enable Docker Support” and “Configure for HTTPS” are unchecked as we won’t be using those features here.
- Ensure that Authentication is set as “No Authentication” as we won’t be using authentication either.
- Click Create. 
 
---

## Why use Data Transfer Objects (DTOs)?

When designing and developing an application, if you’re using models to pass data between the layers and sending data back to the presentation layer, then you’re exposing the internal data structures of your application. That’s a major design flaw in your application.

By decoupling your layers DTOs make life easier when you’re implementing APIs, MVC applications, and also messaging patterns such as Message Broker. A DTO is a great choice when you would like to pass a lightweight object across the wire — especially when you’re passing your object via a medium that is bandwidth-constrained.

---

## Use DTOs for abstraction
You can take advantage of DTOs to abstract the domain objects of your application from the user interface or the presentation layer. In doing so, the presentation layer of your application is decoupled from the service layer. So if you would like to change the presentation layer, you can do that easily while the application will continue to work with the existing domain layer. Similarly, you can change the domain layer of your application without having to change the presentation layer of the application.

---

## Immutability of DTOs

A DTO is meant to transport data from one layer of an application to another layer. The consumer of a DTO might be built in .NET/C#/Java or even JavaScript/TypeScript. A DTO is often serialized so that it can be independent of the technology used in the receiver. In most cases, the receiver of the data does not need to modify that data after receipt — ideally it shouldn’t!

This is a classic example of the importance of immutability. And it’s exactly why a DTO should be immutable!

There are several ways in which you can implement immutable DTOs in C#. You could use a ReadOnlyCollection or the thread-safe immutable collection types present in the System.Collections.Immutable namespace. You can take advantage of record types in C# 9 to implement immutable DTOs as well.

