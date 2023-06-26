## Nuget
- Must be the same version as (Dependencies > Frameworks > Microsoft.AspNetCore.App version)
	- EntityFrameworkCore
	- EntityFrameworkCore.Tools
	- EntityFrameworkCore.SqlServer

## Route
- {domainame}/{controllername}/{actionname}/{id?}

## appsettings.json
- connection strings
- api key
- secret key

## Temp data
```cs
// in controller
// stay only for 1 request.
// disappeared after reloading the page.
TempData["customertempname"] = "Category create successfully";

// in partial view (add new partial view)
@if(TempData["customertempname"] != null)
{
	<h2>@TempData["customertempname"]</h2>
}

// in view
<partial name="partialviewname" />
```

## Folder Structure
- 📂ProjectName
	- 📂Connected Services
	- 📂Dependencies
		- 📂Analyzers
		- 📂Frameworks
		- 📂Packages
	- 📂Properties
		- 📄launchSettings.json <!-- launch profile contains port -->
	- 🕸wwwroot <!-- store static files in project (ex. css, js, images, lib, !cs) -->
		- 📂css
		- 📂js
		- 📂lib
		- 📄favicon.ico
	- 📂Controllers <!-- interact between model and view -->
		- 📄NameController.cs
			- actionMethod1 <!-- return view as actionMethod1.cshtml in views>controller folder -->
			- actionMethod2 <!-- return view as actionMethod2.cshtml in views>controller folder -->
	- 📂Models <!--  data related, table -->
	- 📂Views <!--  user interface -->
		- 📂ControllerName
			- 📄actionMethod1.cshtml
			- 📄actionMethod2.cshtml
		- 📂Shared <!-- partials view -->
			- 📄\_Layout.cshtml
			- 📄\_ValidationScriptsPartial.cshtml
			- 📄Error.cshtml
		- 📄\_ViewImports.cshtml <!-- global import for all file connection -->
		- 📄\_ViewStart.cshtml <!-- define default master page -->
	- 📄appsettings.json <!-- connection strings, API key, secret key -->
		- 📄appsettings.Development.json
		- 📄appsettings.xxx.json
	- 📄program.cs <!-- running configuration -->

## MVC workflow
1. USER --request--> CONTROLLER
2. CONTROLLER --get data--> MODEL 
3. MODEL --send data--> CONTROLLER 
4. CONTROLLER --get presentation--> VIEW 
5. VIEW --send presentation--> CONTROLLER 
6. CONTROLLER --response--> USER

## ValidateAntiForgeryToken
- Block Cross Site Request Forgery Attack.
- Can't use form action to link the post method on already open web application.
```cs
// add on controller.cs
[ValidateAntiForgeryToken]
[AutoValidateAntiforgeryToken] // apply ValidateAntiForgeyToken for all method except GET method

// add on the program.cs
builder.Services.AddControllersWithViews(option =>{
	option.Filters.Add(new AutoValidateAntiforgeryTokenAttribute());
});
```

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
	// constructor to recieve options argrument and pass it to the base class 
	public dbcontextclassname(DbContextOptions<dbcontextclassname> options) 
	: base(options)
	{}

	// create the database table base on model class
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

// controller overloading
[HttpPost]
// the name will called by form action: actionname
[HttpPost, ActionName("actionname")]
[ValidateAntiForgeryToken]
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

## Use Dependency Injection in controller.cs
```cs
public class controllername : Controller
{
	private readonly dbcontextclassname _db;

	// db parameter will have all the implementation of connectionstring or table to retrieve the data
	public controllername(dbcontextclassname db)
	{
		_db = db;
	}

	// example: retrieve all data in table
	public IActionResult Index()
	{
		// retrieve all data in table and return it to list
		var objlist = _db.tablename.ToList();
		// IEnumerable<tablename> objlist = _db.tablename;_
		return View(objlist);
	}
}
// =====================================================================================
// in view page Index.cshtml
// model from objlist that pass by controller
@model IEnumerable<Category>
@{
	ViewData["Title"] = "index";
}

<h1>Index</h1>

<table class="table table-bordered table-striped" style="width:100%">
	<thead>
		<tr>
			<th>
				column1
			</th>
			<th>
				column2
			</th>
		</tr>
	</thead>
	<tbody>
		@foreach(var obj in Model)
		{
			<tr>
				<td width="50%">
					@obj.column1
				</td>
				<td width="50%">
					@obj.column2
				</td>
			</tr>
		}
	</tbody>
</table>
```

## Tag Helper
```cs
asp-controller="controllername"
asp-action="actionname"
asp-for="attributenameinmodelclass"
// binding the id of the object to the route
asp-rooute-id="@obectname.attributenameinmodelclass"
```

## Data binding
```html
// before binding
@model modelclassname

<label asp-for="attributenameinmodelclass"></label>
<input asp-for="attributenameinmodelclass">
```

## Database Method
```cs
// retrieve data
_db.tablename;

// add data
_db.tablename.Add(object);

// find data by given id
_db.tablename.Find(id);
// Returns a single, specific element of a sequence, or return empty if that element is not found.
_db.tablename.SingleOrDefault();
// throw exception if no elelments are found with given id
_db.tablename.Single();
// return first element of the list
_db.tablename.First();
// find the Id attribute that equal id
_db.tablename.FirstOrDefault(n=>n.Id==id);

// save change
_db.SaveChanges();
```

## Data validation
```cs
// in model
[required]
[range(0, 1)]

// in controller
if(ModelState.IsValid)
{

}

// in view
<input asp-for="attributenameinmodelclass">
<span asp-validation-for="attributenameinmodelclass" class="text-danger"></span>
// to include all validation to display in one place
<div asp-validation-summary="All"></div>
```

## Custom Data Validation
```cs
// in controller
if (condition)
{
	ModelState.AddModelError("customname", "customvalidationmessage")
}
```

## Add Client Side Validation
```cs
// at the end of the view page
...
@section Scripts{
@{
	<partial name="_ValidationScriptsPartial"/>
}
}
```


## Error solution
```cs
// there was an error running the selected code generator: 'package restore failed. rolling back package changes for 'projectname'
- change version of to be compatible with eachother
	- Microsoft.EntityFrameworkCore
	- Microsoft.EntityFrameworkCore.Sqlserver
	- Microsoft.EntityFrameworkCore.Tools
```
