## Introduction to Razor Pages in ASP.NET Core

Razor Pages can make coding page-focused scenarios easier and more productive than using controllers and views.

---

## Why Razor Pages?
MVC developers want probably ask why we need one more way to build web sites on ASP.NET Core? Isn’t MVC enough? From information I have found from public space I found the following reasoning:

- It’s easier to get to web development for beginners as Razor pages are more lightweight than MVC. Besides beginners there are people who are coming from other scripting languages be it old ASP or PHP or something else.
- Razor Pages fit well to smaller scenarios where building controllers and models as separate classes is overkill.
I don’t fully agree with these points as MVC on ASP.NET Core is lightweight and flexible enough. I cover also smaller scenarios with it and it goes way faster as I’m using things I already know very well. The amount of code that MVC introduces is not so big that it makes a lot of difference for small applications.

But I know – based on my early days – that there are young developers like me who want to jump in and start with something very simple to gain more skills and then move to “real” tools.

---

## Application structure
Application structure is similar to MVC but there are no folders for controllers and views. The folder called Pages contains all Razor views that in this context are called “pages”. These pages are like regular MVC views but they also contain code that for MVC is held in controller classes. I will cover this part of Razor Pages later.

Program and Startup classes are exactly the same as for MVC applications. Not just by name but also by code. As said before, Razor Pages are supported by MVC and they are part of it.

Separating logic from presentation is also possible here. We can create code-behind files for pages and name these as PageName.cshtml.cs. Class that code-behind file contains is called “page model” now. Note the arrows before About, Contacts, Error and Index pages on Solution Explorer screenshot. These views have code-behind files.

As I show later then by architecture Razor Pages are following their own pattern I would call View-ViewModel. It is like mix of MVC and MVVM with some missing genes by both parents.

---

## Exploring Razor page
Back in days Razor pages were closer to old ASP when thinking about coding. Now it’s more object-oriented and it is keeping closer to MVC. This is the code of About page that is part of default Razor Pages application.

```C#
@page
@model AboutModel
@{
    ViewData["Title"] = "About";
}
<h2>@ViewData["Title"].</h2>
<h3>@Model.Message</h3>
 
<p>Use this area to provide additional information.</p>
```
Pages are always marked with @page directive that tells view engine this is Razor page and not a regular MVC view. We can specify model that is acting more like a view model than regular MVC model. Actually model here is more like mix of controller and model. Those who have used XAML should find it familiar by concept. Here is the code-behind or model of About page.


```C#
public class AboutModel : PageModel
{
    public string Message { get; set; }
 
    public void OnGet()
    {
        Message = "Your application description page.";
    }]

 ```

OnGet() is handler method that is called with GET-request. There is also similar handler available for POST-method and both of these methods have also asynchronous counterparts supported (OnGetAsync() and OnPostAsync()). Personally I find these OnGet() and OnPost() methods more cryptic than MVC controller actions that clearly communicate their purpose.


---

## Razor page with no code-behind

Now let’s see how previous page looks without code-behind file. It works exactly like the version with code-behind class.

```C#
@page
@{
    ViewData["Title"] = "About";
}
@functions {
    public string Message { get; set; }
 
    public void OnGet()
    {
        Message = "Your application description page.";
    }
}
<h2>@ViewData["Title"].</h2>
<h3>@Message</h3>
 
<p>Use this area to provide additional information.</p>
```

Methods and properties are defined in @functions section. I just moved the contents of page model to page itself and it works. In practice it’s better idea to have those code-behind files and views clean from code as code in views is not so easy to test using automated tests. Also if views grow more complex over time it’s only good if growing codebase is in code files.