# Identity

ASP.NET Core Identity:

Is an API that supports user interface (UI) login functionality.
Manages users, passwords, profile data, roles, claims, tokens, email confirmation, and more.
Users can create an account with the login information stored in Identity or they can use an external login provider. Supported external login providers include Facebook, Google, Microsoft Account, and Twitter.

For information on how to globally require all users to be authenticated, see Require authenticated users.

The Identity source code is available on GitHub. Scaffold Identity and view the generated files to review the template interaction with Identity.

Identity is typically configured using a SQL Server database to store user names, passwords, and profile data. Alternatively, another persistent store can be used, for example, Azure Table Storage.

In this topic, you learn how to use Identity to register, log in, and log out a user. Note: the templates treat username and email as the same for users. For more detailed instructions about creating apps that use Identity, see Next Steps.

Microsoft identity platform is:

An evolution of the Azure Active Directory (Azure AD) developer platform.
Unrelated to ASP.NET Core Identity.
ASP.NET Core Identity adds user interface (UI) login functionality to ASP.NET Core web apps. To secure web APIs and SPAs, use one of the following:

Azure Active Directory
Azure Active Directory B2C (Azure AD B2C)
IdentityServer4
IdentityServer4 is an OpenID Connect and OAuth 2.0 framework for ASP.NET Core. IdentityServer4 enables the following security features:

Authentication as a Service (AaaS)
Single sign-on/off (SSO) over multiple application types
Access control for APIs
Federation Gateway
For more information, see Welcome to IdentityServer4.

View or download the sample code (how to download).

---

## Create a Web app with authentication
Create an ASP.NET Core Web Application project with Individual User Accounts.

Visual Studio
.NET Core CLI
Select the ASP.NET Core Web App template. Name the project WebApp1 to have the same namespace as the project download. Click OK.
In the Authentication type input, select Individual User Accounts.
The generated project provides ASP.NET Core Identity as a Razor Class Library. The Identity Razor Class Library exposes endpoints with the Identity area. For example:

- /Identity/Account/Login
- /Identity/Account/Logout
- /Identity/Account/Manage

---

## Apply migrations
Apply the migrations to initialize the database.

Visual Studio
.NET Core CLI
Run the following command in the Package Manager Console (PMC):

Update-Database

---

## Identity

Key to understanding how authentication works is to first understand what an identity is in ASP.NET Core 2.0. There are three classes which represent the identity of a user: Claim, ClaimsIdentity, and ClaimsPrincipal

## Claims

A Claim represents a single fact about the user. It could be the user's first name, last name, age, employer, birth date, or anything else that is true about the user. A single claim will contain only a single piece of information. A claim representing something about a user John Smith could be his first name: John. A second claim would be his last name: Smith.

Claims are represented by the Claim class in ASP.Net Core. It's most common constructor accepts two strings: type and value. The 'type' parameter is the name of the claim, while the value is the information the claim is representing about the user.

This code will create two new claims. One of type 'FullName' with a value of 'Dark Helmet', and a second of type ClaimTypes.Email and a value of 'dark.helmet@spaceballs.com'. There is a ClaimsType class that contains many string constants that represent industry standard claim types. These are all in URI format, but claim types can be any string.

## ClaimsIdentity

An Identity represents a form of identification or, in other words, a single way of proving who you are. In real life this could be a driver's license. In ASP.Net Core, it is a ClaimsIdentity. This class represents a single form of digital identification.

A single instance of a ClaimsIdentity can be authenticated or not authenticated. According to Andrew Lock's Introduction to Authentication with ASP.NET Core, simply setting the AuthenticationType will automatically ensure the IsAuthenticated property is true. This is because if you have authenticated the identity in any way, then it must, by definition, be authenticated.

An unknown person walking up to you and making various claims about theirself and their life would be equivilent to an unauthenticated ClaimsIdentity. Lock writes that this may be useful to allow guest shopping carts (prior to a sign in, perhaps) and similar use cases.

A driver's license contains many claims about its subject: first and last names, birthdate, hair and eye colors, height, and others. Similarly, a ClaimsIdentity can contain numerous claims about a user.

## ClaimsPrincipal

A Principal represents the actual user. It can contain one or more instances of ClaimsIdentity, just like in life a person may have a driver's license, concealed-carry permit, social security card, and a passport. Each of the identities is used for a different purpose and may contain a unique set of claims, but they all identify the same user in some form or another.

To sum up, a ClaimsPrincipal represents a user and contains one or more instances of ClaimsIdentity, which in turn represent a single form of identification and contain one or more instances of Claim, which represents a single piece of information about a user. The ClaimsPrincipal is what the HttpContext.SignInAsync method accepts and passes to the specified AuthenticationHandler.