# Logic 

If a hacker finds a bug in your web layer, they might gain direct access to your database. In Clean Architecture, the "Onion" layers act as a series of defensive perimeters.

## Summary  Trust No One logic flow

TypeScript: Validates basic format (UX only).

API Layer: Checks the JWT Token (Is this user an Admin?).

Application Layer: Runs the FluentValidator (Is the data shaped correctly?).

Domain Layer: The Product Constructor runs (Does this follow business rules?).

Infrastructure Layer: EF Core saves the data to the database.

## Extended explanation logic flow

1. The Domain Layer (The Core)

    What it does: Contains your "Entities" (Product, Order, User) and "Business Rules."

    Trust Factor: This layer trusts nobody. It doesn't even know a database exists.

    Example Rule: A Product cannot have a negative price. This rule is enforced here, so even if the UI and API fail to check the price, the Domain will throw an error before the data is saved.

2. The Application Layer (The Use Cases)

    What it does: Orchestrates the flow of data. It defines "Features" like PlaceOrder or GetProductCatalog.

    The "Contract": It uses Interfaces (e.g., IOrderRepository) to say "I need to save an order," but it doesn't care how (SQL, NoSQL, or a flat file).

    Mapping: It converts internal Entities into DTOs (Data Transfer Objects) to send only necessary data to the TypeScript frontend.

3. The Infrastructure Layer (The Tools)

    What it does: Implements the interfaces from the Application layer. This is where Entity Framework Core, Stripe API, or Azure Blob Storage live.

    Trust Factor: This is the "dirty" layer that talks to the outside world. If you want to switch from SQLite to PostgreSQL, you only change code here.

4. The Web API Layer (The Gatekeeper)

    What it does: Handles HTTP requests, JWT authentication, and CORS.

    Logic Level: Zero. It should only receive a request, call an Application Service, and return an HTTP status code (200 OK, 403 Forbidden, etc.).

## Deploying it in the cloud

Since I'm using C#, Azure is the most seamless "reliable source." For a week-long sprint, use Azure App Service.

    Containerize (Optional but Recommended): Use a Dockerfile to package your C# API and your React SPA into a single image.

    GitHub Actions: Set up a "CI/CD" pipeline. When you git push, the cloud automatically builds and redeploys your app.

    Environment Secrets: Use Azure Key Vault. As per your "Trust No One" policy, your production database password should never exist in your code or on your local machine.

## Recommended Setup

WebShop.sln

    WebShop.Domain (Class Library)

    WebShop.Application (Class Library)

    WebShop.Infrastructure (Class Library)

    WebShop.WebAPI (ASP.NET Core Web API)

    webshop-ui (React + TypeScript SPA)
