Install the latest PowerShell for new features and improvements! https://aka.ms/PSWindows

PS C:\WINDOWS\system32> dotnet new sln -n WebShop
The template "Solution File" was created successfully.

PS C:\WINDOWS\system32> dotnet new classlib -n WebShop.Domain
The template "Class Library" was created successfully.

Processing post-creation actions...
Restoring C:\WINDOWS\system32\WebShop.Domain\WebShop.Domain.csproj:
Restore succeeded.


PS C:\WINDOWS\system32> dotnet new classlib -n WebShop.Application
The template "Class Library" was created successfully.

Processing post-creation actions...
Restoring C:\WINDOWS\system32\WebShop.Application\WebShop.Application.csproj:
Restore succeeded.


PS C:\WINDOWS\system32> dotnet new classlib -n WebShop.Infrastructure
The template "Class Library" was created successfully.

Processing post-creation actions...
Restoring C:\WINDOWS\system32\WebShop.Infrastructure\WebShop.Infrastructure.csproj:
Restore succeeded.


PS C:\WINDOWS\system32> dotnet new webapi -n WebShop.Api
The template "ASP.NET Core Web API" was created successfully.

Processing post-creation actions...
Restoring C:\WINDOWS\system32\WebShop.Api\WebShop.Api.csproj:
Restore succeeded.


PS C:\WINDOWS\system32> dotnet add WebShop.Application/WebShop.Application.csproj reference WebShop.Domain/WebShop.Domain.csproj
Reference `..\WebShop.Domain\WebShop.Domain.csproj` added to the project.
PS C:\WINDOWS\system32> dotnet add WebShop.Infrastructure/WebShop.Infrastructure.csproj reference WebShop.Application/WebShop.Application.csproj
Reference `..\WebShop.Application\WebShop.Application.csproj` added to the project.
PS C:\WINDOWS\system32> dotnet add WebShop.Api/WebShop.Api.csproj reference WebShop.Infrastructure/WebShop.Infrastructure.csproj
Reference `..\WebShop.Infrastructure\WebShop.Infrastructure.csproj` added to the project.
PS C:\WINDOWS\system32> dotnet sln add WebShop.Domain/WebShop.Domain.csproj
Project `WebShop.Domain\WebShop.Domain.csproj` added to the solution.
PS C:\WINDOWS\system32> dotnet sln add WebShop.Application/WebShop.Application.csproj
Project `WebShop.Application\WebShop.Application.csproj` added to the solution.
PS C:\WINDOWS\system32> dotnet sln add WebShop.Infrastructure/WebShop.Infrastructure.csproj
Project `WebShop.Infrastructure\WebShop.Infrastructure.csproj` added to the solution.
PS C:\WINDOWS\system32> dotnet sln add WebShop.Api/WebShop.Api.csproj
Project `WebShop.Api\WebShop.Api.csproj` added to the solution.
PS C:\WINDOWS\system32> dotnet build
Restore complete (0,8s)
  WebShop.Domain net10.0 succeeded (3,3s) → WebShop.Domain\bin\Debug\net10.0\WebShop.Domain.dll
  WebShop.Application net10.0 succeeded (0,3s) → WebShop.Application\bin\Debug\net10.0\WebShop.Application.dll
  WebShop.Infrastructure net10.0 succeeded (0,3s) → WebShop.Infrastructure\bin\Debug\net10.0\WebShop.Infrastructure.dll
  WebShop.Api net10.0 succeeded (3,4s) → WebShop.Api\bin\Debug\net10.0\WebShop.Api.dll

Build succeeded in 8,1s
