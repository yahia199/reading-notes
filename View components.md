# View components

View components are similar to partial views, but they're much more powerful. View components don't use model binding, they depend on the data passed when calling the view component. This article was written using controllers and views, but view components work with Razor Pages.

A view component:

- Renders a chunk rather than a whole response.
- Includes the same separation-of-concerns and testability benefits found between a controller and view.
- Can have parameters and business logic.
- Is typically invoked from a layout page.

View components are intended anywhere reusable rendering logic that's too complex for a partial view, such as:

- Dynamic navigation menus
- Tag cloud, where it queries the database
- Sign in panel
- Shopping cart
- Recently published articles
- Sidebar content on a blog
- A sign in panel that would be rendered on every page and show either the links to sign out or sign in, depending on the sign in state of the user

A view component consists of two parts:

- The class, typically derived from ViewComponent
- The result it returns, typically a view.

---

## View component methods
A view component defines its logic in an:

- InvokeAsync method that returns Task<IViewComponentResult>.
- Invoke synchronous method that returns an IViewComponentResult.
Parameters come directly from invocation of the view component, not from model binding. A view component never directly handles a request. Typically, a view component initializes a model and passes it to a view by calling the View method. In summary, view component methods:

- Define an InvokeAsync method that returns a Task<IViewComponentResult> or a synchronous Invoke method that returns an IViewComponentResult.
- Typically initializes a model and passes it to a view by calling the ViewComponent.View method.
- Parameters come from the calling method, not HTTP. There's no model binding.
- Aren't reachable directly as an HTTP endpoint. They're typically invoked in a view. A view component never handles a request.
- Are overloaded on the signature rather than any details from the current HTTP request.

---

## View search path
The runtime searches for the view in the following paths:

- /Views/{Controller Name}/Components/{View Component Name}/{View Name}
- /Views/Shared/Components/{View Component Name}/{View Name}
- /Pages/Shared/Components/{View Component Name}/{View Name}
The search path applies to projects using controllers + views and Razor Pages.

The default view name for a view component is Default, which means view files will typically be named Default.cshtml. A different view name can be specified when creating the view component result or when calling the View method.

We recommend naming the view file Default.cshtml and using the Views/Shared/Components/{View Component Name}/{View Name} path. The PriorityList view component used in this sample uses Views/Shared/Components/PriorityList/Default.cshtml for the view component view.


