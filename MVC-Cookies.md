## Using HTTP cookies
An HTTP cookie (web cookie, browser cookie) is a small piece of data that a server sends to a user's web browser. The browser may store the cookie and send it back to the same server with later requests. Typically, an HTTP cookie is used to tell if two requests come from the same browser—keeping a user logged in, for example. It remembers stateful information for the stateless HTTP protocol.

Cookies are mainly used for three purposes:

Session management
Logins, shopping carts, game scores, or anything else the server should remember

Personalization
User preferences, themes, and other settings

Tracking
Recording and analyzing user behavior

---

## Creating cookies
After receiving an HTTP request, a server can send one or more Set-Cookie headers with the response. The browser usually stores the cookie and sends it with requests made to the same server inside a Cookie HTTP header. You can specify an expiration date or time period after which the cookie shouldn't be sent. You can also set additional restrictions to a specific domain and path to limit where the cookie is sent. For details about the header attributes mentioned below, refer to the Set-Cookie reference article.

---

## Define the lifetime of a cookie
The lifetime of a cookie can be defined in two ways:

Session cookies are deleted when the current session ends. The browser defines when the "current session" ends, and some browsers use session restoring when restarting. This can cause session cookies to last indefinitely.
Permanent cookies are deleted at a date specified by the Expires attribute, or after a period of time specified by the Max-Age attribute.

---

## Define where cookies are sent
The Domain and Path attributes define the scope of a cookie: what URLs the cookies should be sent to.

### Domain attribute
The Domain attribute specifies which hosts can receive a cookie. If unspecified, the attribute defaults to the same host that set the cookie, excluding subdomains. If Domain is specified, then subdomains are always included. Therefore, specifying Domain is less restrictive than omitting it. However, it can be helpful when subdomains need to share information about a user.

For example, if you set Domain=mozilla.org, cookies are available on subdomains like developer.mozilla.org.


### Path attribute
The Path attribute indicates a URL path that must exist in the requested URL in order to send the Cookie header. The %x2F ("/") character is considered a directory separator, and subdirectories match as well.

For example, if you set Path=/docs, these request paths match:

- /docs
- /docs/
- /docs/Web/
- /docs/Web/HTTP

But these request paths don't:

- /
- /docsets
- /fr/docs

## SameSite attribute
The SameSite attribute lets servers specify whether/when cookies are sent with cross-site requests (where Site is defined by the registrable domain and the scheme: http or https). This provides some protection against cross-site request forgery attacks (CSRF). It takes three possible values: Strict, Lax, and None.

With Strict, the cookie is only sent to the site where it originated. Lax is similar, except that cookies are sent when the user navigates to the cookie's origin site. For example, by following a link from an external site. None specifies that cookies are sent on both originating and cross-site requests, but only in secure contexts (i.e., if SameSite=None then the Secure attribute must also be set). If no SameSite attribute is set, the cookie is treated as Lax.
