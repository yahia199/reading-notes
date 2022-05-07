#  Roles, Claims, Tokens

## Adding claims checks
Claim based authorization checks:

- Are declarative.
- Are applied to Razor Pages, controllers, or actions within a controller.
- Can not be applied at the Razor Page handler level, they must be applied to the Page.

Claims in code specify claims which the current user must possess, and optionally the value the claim must hold to access the requested resource. Claims requirements are policy based, the developer must build and register a policy expressing the claims requirements.

---

## The difference between Authentication and Authorisation

First of all, we should clarify the difference between these two dependent facets of security. The simple answer is that Authentication is the process of determining who you are, while Authorisation revolves around what you are allowed to do, i.e. permissions. Obviously before you can determine what a user is allowed to do, you need to know who they are, so when authorisation is required, you must also first authenticate the user in some way.

---

## Authentication in ASP.NET Core
The fundamental properties associated with identity have not really changed in ASP.NET Core - although they are different, they should be familiar to ASP.NET developers in general. For example, in ASP.NET 4.x, there is a property called User on HttpContext, which is of type IPrincipal, which represents the current user for a request. In ASP.NET Core there is a similar property named User, the difference being that this property is of type ClaimsPrincipal, which implements IPrincipal.

The move to use ClaimsPrincipal highlights a fundamental shift in the way authentication works in ASP.NET Core compared to ASP.NET 4.x. Previously, authorisation was typically Role-based, so a user may belong to one or more roles, and different sections of your app may require a user to have a particular role in order to access it. In ASP.NET Core this kind of role-based authorisation can still be used, but that is primarily for backward compatibility reasons. The route they really want you to take is claims-based authentication.

## What is JWT? (Recap)
As per openid

JSON Web Token (JWT) is a means of representing claims to be transferred between two parties. The claims in a JWT are encoded as a JSON object that is digitally signed using JSON Web Signature (JWS) and/or encrypted using JSON Web Encryption (JWE).

In simple terms, it is just another way of encoding JSON object and use that encoded object as access tokens for authentication from the server.

This is the second part of the series of two shorts post regarding the practical application of JWT.

- JWT for downloading the files at the client.
- JWT for the server to server authentication (current blog post).

This blog post includes the below topics in detail:

- Parts of JWT token.
- How to authenticate servers API’s (producer and consumer concept).