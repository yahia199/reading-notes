# Entity Framework and APIs

## Entity Framework and APIs

Start Visual Studio and select Create a new project.
In the Create a new project dialog, select ASP.NET Core Web Application > Next.
In the Configure your new project dialog, enter ContosoUniversity for Project name. It's important to use this exact name including capitalization, so each namespace matches when code is copied.
Select Create.
In the Create a new ASP.NET Core web application dialog, select:
.NET Core and ASP.NET Core 5.0 in the dropdowns.
ASP.NET Core Web App (Model-View-Controller).
Create

## Create the data model

The preceding entities have the following relationships:

A one-to-many relationship between Student and Enrollment entities. A student can be enrolled in any number of courses.
A one-to-many relationship between Course and Enrollment entities. A course can have any number of students enrolled in it.

## SQL Server Express LocalDB

The connection string specifies SQL Server LocalDB. LocalDB is a lightweight version of the SQL Server Express Database Engine and is intended for app development, not production use. LocalDB starts on demand and runs in user mode, so there's no complex configuration. By default, LocalDB creates .mdf DB files in the C:/Users/<user> directory.

## Create controller and views

Use the scaffolding engine in Visual Studio to add an MVC controller and views that will use EF to query and save data.

The automatic creation of CRUD action methods and views is known as scaffolding.

In Solution Explorer, right-click the Controllers folder and select Add > New Scaffolded Item.
In the Add Scaffold dialog box:
Select MVC controller with views, using Entity Framework.
Click Add. The Add MVC Controller with views, using Entity Framework