# Hotel Site met ASP.NET Core MVC

## ASP.NEt Core MVC
ASP.NET MVC is een framework binnen ASP.NET voor het bouwen van webapplicaties, waarbij de focus ligt op het MVC (Model-View-Controller) ontwerppatroon. In tegenstelling tot Razor Pages, die de frontend en backend logica in één pagina combineren, scheidt MVC deze in drie componenten: **Models** (voor data representatie), **Views** (voor UI/HTML output), en **Controllers** (voor het verwerken van gebruikersinput en interactie met models). Deze scheiding maakt het makkelijker om complexe applicaties te beheren, te testen en te onderhouden.

## Bronen
| Site                                                                           | Beschrijving                                                        |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------- |
| [ASP.NET Core MVC](https://docs.microsoft.com/en-us/aspnet/core/mvc/overview) | Officiële documentatie van ASP.NET Core MVC                         |
| [Entity Framework Core](https://docs.microsoft.com/en-us/ef/core/)            | Officiële documentatie van Entity Framework Core                    |
| [MVC Tutorial](https://www.tutorialsteacher.com/mvc/index)                    | Een uitgebreide tutorial over ASP.NET Core MVC                      |

## Benodigdheden
### Visual Studio
Visual Studuio is een uitgebreide IDE van Microsoft waarion je applicaties kunt ontwikkelen voor Windows, Android, iOS, web en cloud. Het is beschikbaar voor Windows en macOS.

# Een Hotel Site maken met Visual Studio

## Afspraken voor dit project:
- Alle namen van classes, variabelen en methods zijn in de Engelse taal
- We gebruiken de [code conventions](CONVENTIONS.md)

## Installeer Visual Studio

1. [Download Visual Studio](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&channel=Release&version=VS2022&source=VSLandingPage&cid=2030&passive=false)
1. Installeer Visual Studio met de volgende Workloads:
   - ASP.NET and web development
   - Data storage and processing

## Een nieuw project starten

1. Maak een nieuw project aan in Visual Studio en kies voor een ASP.NET Core Web Application.
1. Installeer de volgende packages voor Microsoft SQL Server en [Entity Framework Core](https://learn.microsoft.com/en-us/ef/core/):

| Package                           |   Omschrijving                                                                       |   
| --------------------------------  | -----------------------------------------------------------------------------------  |
| Microsoft.EntityFrameworkCore     | Entity Framework Core is een ORM (Object-Relational Mapping) framework voor .NET.    |
| Microsoft.EntityFrameworkCore.SqlServer | Entity Framework Core provider voor SQL Server.                         |
| Microsoft.EntityFrameworkCore.Design | Entity Framework Core tools voor het maken van Migrations. |
| Microsoft.EntityFrameworkCore.Tools | Entity Framework Core tools voor het maken van Controllers en Views. |

## Models maken
1. Maak in de map `Models` een nieuwe `class Room`.
1. Geef `Room` een `int Id` en een `string Name` property.

```csharp
    public class Room
    {
        // Een intteger met de naam Id wordt automatisch de primary key van de tabel
        public int Id { get; set; }
        public string Name { get; set; }
    }
```

## Database Context maken
1. Maak in het project een nieuwe map `Data`.
1. Maak in de map `Data` een nieuwe class `ApplicationDbContext` die een [`DbContext`](https://learn.microsoft.com/en-us/ef/core/dbcontext-configuration/) is.
1. Gebruik de volgende contructor:
```csharp
    public ApplicationDbContext(DbContextOptions<ApplicationDbContext> options) : base(options)
    {
    }
```
4. Voeg voor `Room` een [`DbSet<>`](https://www.learnentityframeworkcore.com/dbset) property toe met de naam `Rooms`.

```csharp
    public DbSet<Room> Rooms { get; set; }
```

## Een database koppelen
Voor deze opdracht gebruiken we SQL Server LocalDb. Deze versie van Sql Server is geïnstalleerd met Visual Studio. LocalDb heeft beperkte databasemogelijkheden, maar is geschikt voor het ontwikkelen van database applicaties.

> [!IMPORTANT] 
> Voeg een entry `ConnectionStrings` toe aan `appsettings.Development.json`.

```json
  "ConnectionStrings": {
    "DefaultConnection": "Server=(localdb)\\mssqllocaldb;Database=Hotel;Trusted_Connection=True;MultipleActiveResultSets=true"
  }
```
- `Server=(localdb)\\mssqllocaldb` geeft aan dat we de LocalDb versie van Sql Server gebruiken.
- `Database=Hotel` geeft aan dat we een database met de naam `Hotel` gebruiken.
- `Trusted_Connection=True` geeft aan dat we Windows Authentication gebruiken.
- `MultipleActiveResultSets=true` geeft aan dat we meerdere actieve resultaten gebruiken.

2. Voeg een Sql Sever database toe aan de services in `Program.cs`.
```csharp
  var connectionString = builder.Configuration.GetConnectionString("DefaultConnection") ?? throw new InvalidOperationException("Connection string 'DefaultConnection' not found.");
  builder.Services.AddDbContext<ApplicationDbContext>(options =>
  options.UseSqlServer(connectionString));
```
> [!TIP]  
> Je hoeft deze database nog niet te maken in Sql Server. Die laten we genereren met Migrations.

## Een Migratie toevoegen
Je gebruikt [Migrations](https://learn.microsoft.com/en-us/ef/core/managing-schemas/migrations/?tabs=vs) om de database te bouwen en te wijzigen.
1. Ga naar **Tools → NuGet Package Manager → Package Manager Console**
1. Toets het commando: `Add-Migration HotelBasicSchema`

Je ziet dat een nieuw bestand is aangemaakt. Met dit bestand wordt de database gemaakt. 

## De database genereren
1. Typ in de Package Manager Console het commando `Update-Database`.
1. Bekijk de database `HotelDb` en de tables in **View → SQL Server Object Explorer**, onder `(localdb)`

## Controllers en Views maken
1. Rechts-Klik in de Solution Explorer op de folder **Controllers**
1. Kies **Add → Controller...**
1. Kies **MVC Controller with views, using Entity Framework**
1. Model Class → `Room (Hotel.Models)`
1. DbContext class → `ApplicationDbContext (Hotel.Data)` 
1. Klik op **Add**

## Routing
Hier is een uitgebreide uitleg over **Routing in ASP.NET Core MVC**:

---

## Routing in ASP.NET Core MVC

### Wat is Routing?
Routing in ASP.NET Core MVC bepaalt hoe HTTP-verzoeken worden afgehandeld door de applicatie. Een route is een patroon dat een URL koppelt aan een specifieke controller en actie in een MVC-applicatie.

ASP.NET Core gebruikt **middleware** voor routing, en er zijn twee belangrijke soorten routing:
1. **Conventionele routing** – Wordt meestal gebruikt in traditionele MVC-applicaties.
2. **Attribuutrouting** – Wordt rechtstreeks op controllers en acties toegepast.

---

## 1. Conventionele Routing
Conventionele routing wordt meestal ingesteld in `Program.cs` binnen de `MapControllerRoute`-methode.

### Voorbeeld van conventionele routing:
``#`csharp
app.UseRouting();

app.MapControllerRoute(
        name: "default",
        pattern: "{controller=Home}/{action=Index}/{id?}")
    .WithStaticAssets();
```
#### Hoe werkt dit?
- `{controller=Home}` → Standaardcontroller is `HomeController`.
- `{action=Index}` → Standaardactie is `Index()`.
- `{id?}` → Een optionele parameter (`id` kan ontbreken).

#### Voorbeeld van URL-matching:
| URL                     | Controller       | Actie       | Parameter |
|-------------------------|-----------------|------------|-----------|
| `/`                     | `HomeController` | `Index`    | n.v.t.    |
| `/Product/Details/5`    | `ProductController` | `Details` | `5`       |
| `/Account/Login`        | `AccountController` | `Login` | n.v.t.  |

---

### 2. Attribuutrouting
Met **attribuutrouting** definieer je routes direct op controllers en methodes. Dit biedt meer controle over hoe routes worden ingesteld.

#### Voorbeeld:
```csharp
[Route("products")]
public class ProductController : Controller
{
    [Route("")]
    public IActionResult Index()
    {
        return View();
    }

    [Route("details/{id}")]
    public IActionResult Details(int id)
    {
        return View();
    }
}
```
#### Hoe werkt dit?
- `/products` → Roept `Index()` aan in `ProductController`.
- `/products/details/5` → Roept `Details(5)` aan.

Attribuutrouting maakt het makkelijker om **RESTful API's** te bouwen, omdat je specifieke routes kunt definiëren.

---

### 3. Routeparameters en Constraints
Je kunt **parameters** in routes gebruiken om waarden door te geven aan controllers.

#### Basisvoorbeeld:
```csharp
[Route("products/details/{id}")]
public IActionResult Details(int id)
{
    return View();
}
```
Deze route verwacht dat `id` een geheel getal is, bijvoorbeeld `/products/details/10`.

#### Constraints (Beperkingen)
Met constraints kun je het type van een parameter afdwingen.

##### Voorbeeld: `id` moet een geheel getal zijn (`int`):
```csharp
[Route("products/details/{id:int}")]
public IActionResult Details(int id)
{
    return View();
}
```
**Andere constraints:**
| Constraint | Voorbeeld | Betekenis |
|------------|----------|-----------|
| `int` | `{id:int}` | Alleen gehele getallen toegestaan |
| `guid` | `{id:guid}` | Moet een GUID zijn |
| `alpha` | `{name:alpha}` | Alleen letters toegestaan |
| `minlength(x)` | `{name:minlength(3)}` | Minimaal 3 tekens |
| `maxlength(x)` | `{name:maxlength(10)}` | Maximaal 10 tekens |

---

### 4. Default Waarden en Optionele Parameters
Soms wil je standaardwaarden instellen of parameters optioneel maken.

#### Standaardwaarde instellen:
```csharp
[Route("products/details/{id=1}")]
public IActionResult Details(int id)
{
    return View();
}
```
Als een gebruiker `/products/details/` bezoekt, wordt `id` automatisch `1`.

#### Optionele parameter:
```csharp
[Route("products/details/{id?}")]
public IActionResult Details(int? id)
{
    return View();
}
```
De `id`-parameter is nu optioneel.

---

### Samenvatting
| Routing Type | Definitie | Gebruik |
|-------------|----------|---------|
| **Conventionele Routing** | Gedefinieerd in `Program.cs` met `MapControllerRoute` | Goed voor standaard MVC-apps |
| **Attribuutrouting** | Routes worden direct op controllers/acties geplaatst | Ideaal voor API’s en flexibele routing |
| **Parameters & Constraints** | Dynamische waardes in routes (`{id:int}`) | Maakt routes specifieker en robuuster |
| **Default & Optionele Waarden** | `{id=1}` of `{id?}` | Maakt routes flexibeler |


## Lower case Routes

> [!TIP]
> Als je wilt dat alle routes in kleine letters (lower case) worden weergegeven, kun je dit instellen in `Program.cs`. Voeg de volgende regel toe aan het blokje ` // Add services to the container.` 
```csharp
    builder.Services.AddRouting(options => options.LowercaseUrls = true);
```
---




## Applicatie gebruiksklaar maken
1. Pas `_Layout.cshtml` aan, zodart **Rooms** ook in het menu staat

## Test de applicatie
1. Ga naar **Debug → Start Debugging**

Je Browser start in de Debug mode en je ziet de applicatie.
Om te testen of je een kamer kan toevoegen, wijzigen, verwijderen en een lijst kan krijgen van alle kamers kan je de volgende url's testen:

|Actie|Url|
|---|---|
|toevoegen|https://localhost:7187/Rooms/Create |
|wijzigen|https://localhost:7187//Rooms/Edit/id |
verwijderen|https://localhost:7187//Rooms/Delete/id|
lijst|https://localhost:7187//Rooms|

* port 7187 kan bij jouw applicatie een andere zijn

## Verder bouwen
Om de applicatie af te bouwen heb je nog wel het een en ander te doen. Hier is alvast een lijstje met taken die je op kan nemen in je planning:

- Overige velden voor kamer toevoegen aan model, controller en views zodat een volledige kamer kan worden beheerd.
- Frontend en Backend validaties toevoegen
- CRUD toevoegen voor boekingen model, migratie, controller, views)
- Zorgen dat er geen dubbele boekingen kunnen ontstaan
- Zorgen dat een kamer niet verwijderd kan worden als er nog boekingen op die kamer bestaan.
- Voorpagina maken
- Pagina maken met extra informatie over het hotel
- Menubalk afmaken

# Handige weetjes voor je verdere werk met ASP.NET Core MVC

## Primary Keys en Foreign Keys

- Als je een integer property `Id` noemt, wordt deze automatisch de primary key van de tabel.

```csharp
    public class Room
    {
        public int Id { get; set; }
        public string Name { get; set; }
    }
```

- Als je een property Room aanmaakt in de Booking class, wordt deze automatisch een foreign key naar de Room tabel.
- Om meer controle te hebben over de foreign key, kun je de RoomId property toevoegen.
- Voeg een annotation toe om de RoomId property als foreign key te markeren.
```csharp
    public class Booking
    {
        public int Id { get; set; }
        public int RoomId { get; set; }

        [ForeuignKey(nameof(RoomId)]]
        public Room Room { get; set; }
    }

