## Benefits of using views
Views help to establish separation of concerns within an MVC app by separating the user interface markup from other parts of the app. Following SoC design makes your app modular, which provides several benefits:

- The app is easier to maintain because it's better organized. Views are generally grouped by app feature. This makes it easier to find related views when working on a feature.
- The parts of the app are loosely coupled. You can build and update the app's views separately from the business logic and data access components. You can modify the views of the app without necessarily having to update other parts of the app.
- It's easier to test the user interface parts of the app because the views are separate units.
- Due to better organization, it's less likely that you'll accidentally repeat sections of the user interface.

---

## Creating a view
Views that are specific to a controller are created in the Views/[ControllerName] folder. Views that are shared among controllers are placed in the Views/Shared folder. To create a view, add a new file and give it the same name as its associated controller action with the .cshtml file extension. To create a view that corresponds with the About action in the Home controller, create an About.cshtml file in the Views/Home folder:

Razor markup starts with the @ symbol. Run C# statements by placing C# code within Razor code blocks set off by curly braces ({ ... }). For example, see the assignment of "About" to ViewData["Title"] shown above. You can display values within HTML by simply referencing the value with the @ symbol. See the contents of the h2 and h3 elements above.

---

## How controllers specify views
Views are typically returned from actions as a ViewResult, which is a type of ActionResult. Your action method can create and return a ViewResult directly, but that isn't commonly done. Since most controllers inherit from Controller, you simply use the View helper method to return the ViewResult:

---

## View discovery
When an action returns a view, a process called view discovery takes place. This process determines which view file is used based on the view name.

The default behavior of the View method (return View();) is to return a view with the same name as the action method from which it's called. For example, the About ActionResult method name of the controller is used to search for a view file named About.cshtml. First, the runtime looks in the Views/[ControllerName] folder for the view. If it doesn't find a matching view there, it searches the Shared folder for the view.

It doesn't matter if you implicitly return the ViewResult with return View(); or explicitly pass the view name to the View method with return View("<ViewName>");. In both cases, view discovery searches for a matching view file in this order:

Views/\[ControllerName]/\[ViewName].cshtml
Views/Shared/\[ViewName].cshtml

---

## Pass data to views
Pass data to views using several approaches:

Strongly typed data: viewmodel
Weakly typed data
ViewData (ViewDataAttribute)
ViewBag

---

## Summary of the differences between ViewData and ViewBag
ViewBag isn't available by default for use in Razor Pages PageModel classes.

- ViewData
Derives from ViewDataDictionary, so it has dictionary properties that can be useful, such as ContainsKey, Add, Remove, and Clear.
Keys in the dictionary are strings, so whitespace is allowed. Example: ViewData["Some Key With Whitespace"]
Any type other than a string must be cast in the view to use ViewData.
- ViewBag
Derives from Microsoft.AspNetCore.Mvc.ViewFeatures.Internal.DynamicViewData, so it allows the creation of dynamic properties using dot notation (@ViewBag.SomeKey = <value or object>), and no casting is required. The syntax of ViewBag makes it quicker to add to controllers and views.
Simpler to check for null values. Example: @ViewBag.Person?.Name

---

## When to use ViewData or ViewBag
Both ViewData and ViewBag are equally valid approaches for passing small amounts of data among controllers and views. The choice of which one to use is based on preference. You can mix and match ViewData and ViewBag objects, however, the code is easier to read and maintain with one approach used consistently. Both approaches are dynamically resolved at runtime and thus prone to causing runtime errors. Some development teams avoid them.