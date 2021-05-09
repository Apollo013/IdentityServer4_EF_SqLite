# Identity Server 4 - ASP.NET Identity & EntityFramework Support

## N.B.
This builds on a previous demo which used an In Memory Store Here: https://github.com/Apollo013/IdentityServer4_InMemory.

<br /> 

### Identity Server Steps (DB Storage for Identity Server)
| Type | Description |
|---|---|
| CLI | cd ids |
| CLI | dotnet add package IdentityServer4.EntityFramework |
| CLI | dotnet add package Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore |
| CLI | dotnet add package Microsoft.EntityFrameworkCore.Tools |
| CLI | dotnet add package Microsoft.EntityFrameworkCore.Sqlite |
| CLI | dotnet add package Serilog.AspNetCore |
| CODE | Update Startup.cs to use Sqlite storeage |
| CLI | dotnet ef migrations add InitialIdentityServerMigration -c PersistedGrantDbContext |
| CLI | dotnet ef migrations add InitialIdentityServerMigration -c ConfigurationDbContext |
| CLI | dotnet ef database update -c PersistedGrantDbContext |
| CLI | dotnet ef database update -c ConfigurationDbContext |
| CODE | Add SeedData.cs -> https://github.com/kevinrjones/SettingUpIdentityServer/blob/master/step-by-step-demo/identity/IdSWithEF/SeedData.cs |
| CODE | Add Program.cs to seed the data and configure Serilog |
| CLI | Seed the data -> dotnet run bin/Debug/netcoreapp3.1/ids /seed |


<br />

### Identity Server Steps (DB Storage for Identity)
| Type | Description |
|---|---|
| CLI | dotnet add package IdentityServer4.AspNetIdentity |
| CLI | dotnet add package Microsoft.AspNetCore.Identity.EntityFrameworkCore |
| CODE | Add Data/ApplicationDbContext class |
| CODE | Update Startup.cs to use Sqlite storage for Identity |
| CODE | Update SeedData to add Users |
| CODE | Update QuickStart/AccountController to replace TestUserStore with IdentityUser |
| CODE | Update QuickStart/ExternalController to replace TestUserStore with IdentityUser |
| CLI | dotnet ef migrations add InitialIdentityServerMigration -c ApplicationDbContext |
| CLI | dotnet ef database update -c ApplicationDbContext |
| CLI | Seed the data -> dotnet run bin/Debug/netcoreapp3.1/ids /seed |


<br />

## Testing
Run all 3 apps using 'dotnet run'
Navigate to http://localhost:5001/Home
Then navigate to http://localhost:5001/Home/Weather
When prompted for login credentials, use those specified in the SeedData.cs file in the IDS app.

### Credits
https://www.youtube.com/watch?v=Sw1rScI20xM&ab_channel=IdentityServer
