# Classes & Objects

are the basic concepts of Object-Oriented Programming which revolve around the real-life entities. A class is a user-defined blueprint or prototype from which objects are created. Basically, a class combines the fields and methods(member function which defines actions) into a single unit. In C#, classes support polymorphism, inheritance and also provide the concept of derived classes and base classes.

---

## Declaration of class

Generally, a class declaration contains only a keyword class, followed by an identifier(name) of the class. But there are some optional attributes that can be used with class declaration according to the application requirement. In general, class declarations can include these components, in order:

- Modifiers: A class can be public or internal etc. By default modifier of the class is internal.
- Keyword class: A class keyword is used to declare the type class.
- Class Identifier: The variable of type class is provided. The identifier(or name of the class) should begin with an initial letter which should be capitalized by convention.
- Base class or Super class: The name of the class’s parent (superclass), if any, preceded by the : (colon). This is optional.
- Interfaces: A comma-separated list of interfaces implemented by the class, if any, preceded by the : (colon). A class can implement more than one interface. This is optional.
- Body: The class body is surrounded by { } (curly braces).
---

## Creating objects

Although they are sometimes used interchangeably, a class and an object are different things. A class defines a type of object, but it is not an object itself. An object is a concrete entity based on a class, and is sometimes referred to as an instance of a class.

Objects can be created by using the new keyword followed by the name of the class that the object will be based on

---

## Constructors

Whenever a class or struct is created, its constructor is called. A class or struct may have multiple constructors that take different arguments. Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.

---

## Properties

- Properties enable a class to expose a public way of getting and setting values, while hiding implementation or verification code.

- A get property accessor is used to return the property value, and a set property accessor is used to assign a new value. In C# 9 and later, an init property accessor is used to assign a new value only during object construction. These accessors can have different access levels.

- The value keyword is used to define the value being assigned by the set or init accessor.

- Properties can be read-write (they have both a get and a set accessor), read-only (they have a get accessor but no set accessor), or write-only (they have a set accessor, but no get accessor). Write-only properties are rare and are most commonly used to restrict access to sensitive data.

- Simple properties that require no custom accessor code can be implemented either as expression body definitions or as auto-implemented properties.

---

## garbage collection

***Fundamentals of garbage collection***

In the common language runtime (CLR), the garbage collector (GC) serves as an automatic memory manager. The garbage collector manages the allocation and release of memory for an application. For developers working with managed code, this means that you don't have to write code to perform memory management tasks. Automatic memory management can eliminate common problems, such as forgetting to free an object and causing a memory leak or attempting to access memory for an object that's already been freed.

***Benefits***

- Frees developers from having to manually release memory.

- Allocates objects on the managed heap efficiently.

- Reclaims objects that are no longer being used, clears their memory, and keeps the memory available for future allocations. Managed objects automatically get clean content to start with, so their constructors don't have to initialize every data field.

- Provides memory safety by making sure that an object cannot use for itself the memory allocated for another object.
