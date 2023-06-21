#### Nuget
- Must be the same version as (Dependencies > Frameworks > Microsoft.AspNetCore.App version)
	- EntityFrameworkCore
	- EntityFrameworkCore.Tools
	- EntityFrameworkCore.SqlServer

#### Route
- {domainame}/{controllername}/{actionname}/{id?}

### appsettings.json
- connection strings
- api key
- secret key

### Folder Structure
- ProjectName
	- Connected Services
	- Dependencies
		- Analyzers
		- Frameworks
		- Packages
	- Properties
		- launchSettings.json <!-- launch profile contains port -->
	- 🕸wwwroot <!-- store static files in project (ex. css, js, images, lib, !cs) -->
		- css
		- js
		- lib
		- favicon.ico
	- 📂Controllers <!-- interact between model and view -->
		- 📄NameController.cs
			- actionMethod1 <!-- return view as actionMethod1.cshtml in views>controller folder -->
			- actionMethod2 <!-- return view as actionMethod2.cshtml in views>controller folder -->
	- 📂Models <!--  data related, table -->
	- 📂Views <!--  user interface -->
		- 📂ControllerName
			- 📄actionMethod1.cshtml
			- 📄actionMethod2.cshtml
	- appsettings.json <!-- connection strings, API key, secret key -->
		- appsettings.Development.json
		- appsettings.xxx.json
	- program.cs <!-- running configuration -->

### MVC workflow
1. USER --request--> CONTROLLER
2. CONTROLLER --get data--> MODEL 
3. MODEL --send data--> CONTROLLER 
4. CONTROLLER --get presentation--> VIEW 
5. VIEW --send presentation--> CONTROLLER 
6. CONTROLLER --response--> USER

## Model Class
```c#
public class ModelClassName
{
	[Key]
	public int Id { get; set; }

	Display(Name = "Full name")]
	[Required(ErrorMessage = "Please enter your name.")]
	[DataType(DataType.Text)]
	public string name { get; set; }

	[Column(TypeName = "nvarchar(100)")]
	public string address { get; set; }

	public DateTime Date { get; set; }
}
```

## DbContext Class
```c#
public class dbcontextclassname: DbContext
{
	public dbcontextclassname(DbContextOptions<dbcontextclassname> options) 
	: base(options)
	{}
	public DbSet<modelclassname> tablename { get; set; } 
}
```


## Connection String in appsettings.js
- <a href="https://learn.microsoft.com/en-us/dotnet/api/system.data.sqlclient.sqlconnection.connectionstring?view=dotnet-plat-ext-6.0" target="_blank">Full ConnectionString Document</a>
```javascript
...
"AllowedHost": "*",
"ConnectionStrings": {
	"connectionname": "Server=servername; Database=databasename; Trusted_Connection=True; MultipleActiveResultSets=True;"
	// if not on local change Trusted_Connection=True to User ID=username; Password=password;
...
}
```
## Add services (Dependencies Injection) in Program.cs
- Older version of asp.net
```c#
...
public IConfiguration Configuration { get; }

// This method gets called by the runtime. Use this ethod to add servies to the container.
public void ConfigureServices(IServiceCollection services)
{
	Services.Configure<CookiePolicyOptions>(options =>
	{
	// This lambda determines whether user consent for non-essential cookies is needed for a given request.
	options.CheckConsentNeeded = context => true;
	options.MinimumSameSitePolicy = SameSiteMode.None;
	});

	services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_2);

	services.AddDbContext<dbcontextclassname>(options =>
	options.UseSqlServer(Configuration.GetConnectionString("connectionname")));
}
...
```
- More recent version
```c#
...
builder.Services.AddControllersWithViews();

builder.Services.AddDbContext<dbcontextclassname>(options => options.UseSqlServer(
builder.Configuration.GetConnectionStrings("connectionname")))
...
```

## Migration in Package Manager Console
```
PM> Add-Migration "migrationname"
...
PM> Update-Database
...
```

## Create Controller
```c#
...
public class HomeController
{

}
public IActionResult methodname1()
{
	return View();
}

public IActionResult methodname2()
{
	return View();
}

public IActionResult methodname3()
{
	return View();
}
...
  
```
```markdown
<!-- Directory Structure -->
Controllers
├──HomeControllers.cs

Views
├── Home
│   ├── methodname1.cshtml
│   ├── methodname2.cshtml
│   ├── methodname3.cshtml
```

