Building a full-stack app in a week is a "sprint" pace, but it's entirely doable if you leverage the integrated templates provided by **Microsoft Learn**, which remains the industry standard for this stack. 

In 2026, the best way to handle this is using **.NET 10** for the backend and **Vite-powered React or Angular** for the frontend.

---

## 🏗️ The Architecture
Before diving in, understand how these pieces fit together. Your C# backend acts as the "brain" (logic and data), while your TypeScript frontend acts as the "face" (user interaction).

---

## 📅 The 7-Day Roadmap

### Day 1: The Environment & C# Basics
* **Source:** [Microsoft Learn: C# Fundamentals](https://learn.microsoft.com/en-us/training/paths/get-started-c-sharp-part-1/)
* **Task:** Install **Visual Studio 2022/2026** or **VS Code** with the C# Dev Kit. 
* **Goal:** Learn C# syntax, specifically **Classes**, **Async/Await**, and **Dependency Injection** (the backbone of modern .NET).

### Day 2: REST APIs with Minimal APIs
* **Source:** [Create a Minimal API with .NET](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/minimal-apis)
* **Task:** Use the "ASP.NET Core Web API" template.
* **Goal:** Build a simple "Hello World" API and understand **HTTP Methods** (GET, POST, PUT, DELETE).

### Day 3: TypeScript & The SPA Frontend
* **Source:** [TypeScript for Beginners](https://www.typescriptlang.org/docs/handbook/intro.html)
* **Task:** Choose a framework (React is recommended for a 1-week sprint). Use the Visual Studio template: **"React and ASP.NET Core (TypeScript)"**.
* **Goal:** Understand **Interfaces** and **Types** in TypeScript so your frontend knows exactly what data the backend is sending.

### Day 4: Data & Entity Framework Core
* **Source:** [EF Core Getting Started](https://learn.microsoft.com/en-us/ef/core/get-started/)
* **Task:** Connect your API to a database (SQLite is easiest for learning).
* **Goal:** Use **Migrations** to create a database table from a C# class.

### Day 5: Connecting the Dots (Frontend + Backend)
* **Task:** Use the `fetch` API or `Axios` in your TypeScript frontend to call your C# API.
* **Goal:** Display "Live" data from your database on your SPA.
* **Concept:** **CORS (Cross-Origin Resource Sharing)**. You'll likely hit an error here; look up how to enable it in `Program.cs`.

### Day 6: Authentication & Refinement
* **Source:** [Identity in ASP.NET Core](https://learn.microsoft.com/en-us/aspnet/core/security/authentication/identity)
* **Task:** Add a simple login or just refine the UI.
* **Goal:** Ensure your API is secure and your SPA handles errors gracefully.

### Day 7: Cloud Deployment
* **Source:** [Deploy to Azure App Service](https://learn.microsoft.com/en-us/azure/app-service/quickstart-dotnetcore)
* **Task:** Right-click your project in Visual Studio > **Publish** > **Azure**.
* **Alternative:** Use **Docker** to containerize the app and push it to a VPS or DigitalOcean.

---

## 🛠️ Recommended Tools for 2026
| Component       | Technology                              | Why? |

| **Backend**     | **ASP.NET Core 10**                     | High performance and native C# support. |
| **Frontend**    | **React + Vite**                        | The fastest build tool for TypeScript SPAs. |
| **Database**    | **SQLite** (Dev) / **Azure SQL** (Prod) | Zero configuration to start. |
| **Cloud**       | **Azure App Service**                   | "Free tier" available and perfect integration with C#. |

---

### 💡 Pro Tip: The "Proxy" Secret
When you use the Visual Studio **React/Angular and ASP.NET Core** template, it sets up a **Proxy**. This means in development, your frontend (port 5173) automatically talks to your backend (port 7xxx) without you having to hardcode URLs.
