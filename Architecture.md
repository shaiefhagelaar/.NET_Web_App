When choosing an architecture, you aren't just choosing how to organize files; you are choosing how your system handles **failures**, **security boundaries**, and **scaling**. 

Since you are building a .NET/TypeScript stack, these are the four primary architectures used in the industry today, ranked from "Easiest to Deploy" to "Most Scalable."

---

## Architecture Comparison Table

| Architecture | Complexity | Security Focus | Best For |
| :--- | :--- | :--- | :--- |
| **Monolithic** | Low | Centralized | Small teams, 1-week sprints, MVPs. |
| **Clean / Onion** | Medium | Logic Isolation | Long-term maintainability, "Trust No One" logic. |
| **Microservices** | High | Network Segregation | Global scale, huge teams, independent deployments. |
| **Headless** | Low/Med | API Security | **Your current project** (SPA + API). |

---

## 1. Monolithic Architecture
In a monolith, everything (the UI, the API, and the Database logic) lives in one single project and one single executable.



* **How it works:** All code shares the same memory and resources.
* **Pros:** Extremely fast to develop and deploy (perfect for a 1-week sprint).
* **Cons:** If one part fails (e.g., the "Order" service crashes), the whole shop goes down.
* **Reliable Source:** [Martin Fowler: MonolithFirst](https://martinfowler.com/bliki/MonolithFirst.html)

---

## 2. Clean Architecture (The "Onion")
This is the **Microsoft-recommended** way to structure .NET applications. It focuses on the "Inversion of Dependencies."



* **How it works:** Your core business logic (e.g., "Calculating Tax") sits in the center. It doesn't know about the database or the web. Everything else (API, SQL Server) points *inward* toward the logic.
* **Why it's Secure:** Because the logic is isolated, you can unit-test your "Trust No One" rules without needing a database or a browser.
* **Reliable Source:** [Microsoft Learn: Common Web Architectures](https://learn.microsoft.com/en-us/dotnet/architecture/modern-web-apps-azure/common-web-application-architectures)

---

## 3. Microservices
Instead of one big app, you have 10 tiny apps (Product Service, User Service, Payment Service) that talk to each other over the network.



* **How it works:** Each service has its own database. They communicate via REST or Message Queues (like RabbitMQ).
* **Why it's Secure:** If a hacker breaks into the "Product Images" service, they still don't have access to the "Credit Card" database because they are on different servers.
* **Cons:** Way too much overhead for a 1-week project. You spend more time configuring the network than writing code.
* **Reliable Source:** [Microservices.io: Patterns](https://microservices.io/patterns/microservices.html)

---

## 4. Headless / Decoupled Architecture
This is exactly what you are building with your **C# REST API** and **TypeScript SPA**.



* **How it works:** The "Head" (the UI in React) is totally separated from the "Body" (the C# API). They only communicate via JSON.
* **Why it fits you:** It allows you to swap the frontend (e.g., build a Mobile App later) without ever touching your secure C# code.
* **Security Focus:** You must secure the "bridge" (the API endpoints) because anyone can try to talk to them.

---

## Week 1 Recommendation
For a webshop built in a week, use **Decoupled Architecture** (SPA + API) but organize your C# code using **Clean Architecture** principles.

> **The "Trust No One" Implementation:**
> 1. Create a `Domain` project (Core logic).
> 2. Create an `Infrastructure` project (Database/EF Core).
> 3. Create a `WebAPI` project (The actual API endpoints).

By separating your "Trust No One" logic into a `Domain` project, you ensure that even if you change your database from SQLite to SQL Server on Day 6, your core business rules (like "Prices cannot be negative") never change.

## Considerations

One day has passed and got the basics of C# down. Since this is "Day 2" I might as well consider  Clean / Onion architecture. Why I consider this option to be the best one is because it uses the "Trust no one" logic. The logic is isolated and we won't be needed to call upon databases/browser. It also a good option because the QA team can run unit tests.
