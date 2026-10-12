# Developer Notes

Personal references and snippets for Git, .NET, web APIs, authentication, and WordPress.

[← Back to profile](README.md)

## Contents

- [Git](#git)
- [.NET & ASP.NET Core](#net--aspnet-core)
- [HTTP & APIs](#http--apis)
- [Authentication](#authentication)
- [WordPress](#wordpress)

## Git

### Remove tracked files covered by `.gitignore`

Saved command:

```bash
git ls-files --ignored --exclude-standard | xargs git rm --cached
```

## .NET & ASP.NET Core

### Documentation

| Topic | Reference |
| :--- | :--- |
| ASP.NET Core 5.0 | [Getting started — Microsoft Docs](https://docs.microsoft.com/en-us/aspnet/core/getting-started/?view=aspnetcore-5.0&tabs=windows) |
| Dependency injection | [Dependency injection in ASP.NET Core — TEDU](https://tedu.com.vn/lap-trinh-aspnet-core/co-che-dependency-injection-trong-aspnet-core-256.html) |

### SQL snippet

- [Convert to SQL — .NET Fiddle](https://dotnetfiddle.net/CH6kmF)

## HTTP & APIs

- [Choosing an HTTP status code — Code Tinkerer](http://www.codetinkerer.com/2015/12/04/choosing-an-http-status-code.html)

## Authentication

### IdentityServer 4 — saved flow references

The following table preserves the flow-selection notes from the original IdentityServer 4 section.

| Client scenario | Saved flow reference |
| :--- | :--- |
| Is the client a traditional web application executing on the server? | [Authorization Code Flow](https://auth0.com/docs/flows#authorization-code-flow) |
| Is the client a Single-Page Application (SPA)? | [Authorization Code Flow with Proof Key for Code Exchange (PKCE)](https://auth0.com/docs/flows#authorization-code-flow-with-proof-key-for-code-exchange-pkce-) |
| Is the client a Single-Page Application (SPA) that doesn't need an access token? | [Implicit Flow with Form Post](https://auth0.com/docs/flows#implicit-flow-with-form-post) |
| Is the client the resource owner? | [Client Credentials Flow](https://auth0.com/docs/flows#client-credentials-flow) |
| Is the client absolutely trusted with user credentials? | [Resource Owner Password Flow](https://auth0.com/docs/flows#resource-owner-password-flow) |

## WordPress

- [Zigcy Lite — free theme demo](https://accesspressthemes.com/theme-demos/?theme=zigcy-lite)
