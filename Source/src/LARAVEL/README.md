# Hotel Site met Laravel 11

## Het Laravel Framework
Laravel is een populair PHP framework waarmee je snel een complete en veilige applicatie voor het web kunt maken. Iedere twee jaar verschijnt er een nieuwe versie van het framework. Laravel kan gecombineerd worden met diverse JavaScript frameworks zoals VUE en React. Met Laravel **Breeze** (Tailwind CSS) of **Laravel UI** (Bootstrap CSS) kan je snel een compleet gebruikerssysteem met authorisatie toevoegen.

## Bronnen
Hieronder staan nog een paar interessante sites met informatie over Laravel

| Site                                                                           | Beschrijving                                                        |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------- |
| <a href="https://sdcheatsheets.nl/laravel/">SD Cheatcheats</a> | Basis tutorial voor Laravel |
| <a href="https://laravel-news.com/category/tutorials">Laravel Tutorials</a> | Links naar betrouwbare Laravel tutorials |
| <a href="https://laracasts.com/">Laracasts</a>|Tutorials en een uitgebreid forum om vragen in te stellen of antwoorden te vinden|
| <a href="https://laravel.com/docs/11.x">Laravel Docs</a>|Officiële documentatie. Let op dat je in de juiste versie van de documentatie kijkt, rechtsbovenin kan je de benodigde versie kiezen.|

## Benodigdheden

### Composer
Composer is de package manager voor PHP. Hiermee kan je PHP packages/libraries eenvoudig installeren.

Download Composer voor je eigen OS en installeer:

https://getcomposer.org/download/

### Node.js
Node.js is een JavaScript runtime environment. Met Node.js kan je JavaScript gebruiken buiten de Browser om. Dit is nodig om JavaScript onderdelen binnen de Laravel applicatie te gebruiken.

Download Node.js voor je eigen OS en installeer:

https://nodejs.org/en/download

### PHP 8.2+
Voor Laravel 11 heb je minimaal PHP 8.2 nodig. Download en installeer PHP voor jouw OS.

### Extra tools
Composer, Node.js en PHP heb je minimaal nodig. Maar voor veel applicaties heb je ook een **Database** nodig. Laravel werkt met diverse databases zoals SQLite, MySQL/MariaDB, PostgresSQL. Een populaire keuze is MySQL/MariaDB.

Als **IDE** werkt Visual Studio Code prima. Een andere veelgebruikte IDE voor Laravel is PHPStorm of IntelliJ.

Een **Database Manager** is handig om je databases mee te beheren. PHPMyAdmin een optie, maar voor een upgrade in gebruikersgemak gebruik je en van onderstaande opties.

Een veelgebruikte tool is DataGrid van Jetbrains. DataGrid is ook geintegreerd aanwezig in PHPStorm en IntelliJ. Voor VS Code zijn er plugins beschikbaar waarmee je de database kan beheren. 

## Een nieuw Laravel project maken

Als je PHP, Composer en Node.js heb geïnstalleerd, open je een nieuwe terminal. Navigeer naar de directory waar je het project wilt bewaren. Bedenk een naam voor je project.

Type in de terminal het volgende commando:

```
composer create-project laravel/laravel hotel
```

Er wordt nu een basis Laravel applicatie gemaakt in de map 'hotel'. Navigeer naar deze nieuwe map:

```
cd hotel
```

> [!TIP]
> #### De root directory
> Vanaf nu voer je alle commando's voor je applicatie uit in de **root** directory van de applicatie. Dit is in de tutorial dus de 'hotel' directory. Zorg ervoor dat alle terminals die je gebruikt altijd in deze directory staan, anders werken de commando's niet.


## Een user systeem toevoegen

De **Laravel-ui** package bevat boilerplate code voor een basis registratie- en login systeem. Je kunt Laravel-ui Bootstrap als CSS laten gebruiken. Die optie bestaat niet voor Breeze 

Ga terug naar de terminal vanwaaruit je de applicatie hebt gestart en run de volgende commando's en beantwoord vragen om bestanden te overschrijven met 'yes':

### Laravel UI (met Bootstrap)
```
composer require laravel/ui
php artisan ui bootstrap --auth
```

De Laravel applicatie moet nu een functionerend registratie- en loginsysteem hebben. Je kan het zelf uitbreiden met bijvoorbeeld een rollensysteem. De gebruikers worden opgeslagen in de tabel 'users'.


## Database instellingen in .env
Start je IDE (VSCode of een andere IDE) en open de map met de applicatie. Ga op zoek naar het bestand '**.env**' en open dit bestand in de IDE. In het bestand .env staan de basisinstellingen voor je applicatie. Een van die instellingen is welke database je wilt gebruiken. Standaard is dit SQLite. Als je bijvoorbeeld MySQL/MariaDB gebruikt dan moet je nu de inloggegevens voor in .env toevoegen.

Pas voor MySQL de volgende regels aan en vervang de waarden met de inloggegevens voor jouw database:

```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=hotel
DB_USERNAME=root
DB_PASSWORD=
```

Hierna voer je het onderstaande commando uit in een terminal in de map 'hotel':

```
php artisan migrate
```
Als de database myapp nog niet bestaat dan zal Laravel vragen of de database aangemaakt moet worden. Kies 'yes'.
Nu worden de standaard tabellen 'users', 'cache' en 'jobs' aangemaakt in je database.

## De applicatie gebruiksklaar maken en starten
Open een nieuwe terminal in de map 'hotel' en voor het volgende commando uit:

```
npm install
```
Hiermee installeer je de benodigde JavaScript packages.

en daarna:

```
npm run dev
```

Hiermee start je de Vite development server. Door dit commando in de achtergrond actief te houden worden wijzigingen in JavaScript en CSS automatisch verwerkt en krijg je  **hot reload** functionaliteit. Daardoor hoef je de Browser niet te verversen om je wijzigingen te zien.

Open een nieuwe terminal en run het volgende commando:

```
php artisan serve
```

Hiermee start je de Laravel development server. Je kunt je nieuwe Laravel app nu bekijken door met de Browser het adres http://localhost:8000 te bezoeken.

De applicatie blijft actief zolang je het commando php artisan serve in de terminal actief laat. Sluit deze terminal dus niet. Je kan de terminal van je OS gebruiken of een terminal in je IDE.

> [!TIP] 
> Er zijn nog andere opties om een Laravel ontwikkelomgeving op te zetten en de applicatie te runnen. Check hiervoor: 
> https://laravel.com/docs/11.x/installation


## Stap 1 - De ontwikkelomgeving
Om snel en goed met Laravel te werken is een **IDE** een must! 

**Visual Studio Code** kan prima overweg met Laravel projecten.  
Je gebruikt deze IDE al, dus een goede keuze. 

> [!TIP] 
> Als alternatief kunnen we ook PHPStorm van JetBrains aanraden. 
>
> Deze IDE wordt veel door bedrijven gebruikt. 
>
> Hij kost geld, maar is gratis voor studenten van het Talland College.
Vraag een gratis studentenversie van PHPStorm aan via:
> 
> https://www.jetbrains.com/shop/eform/students


Open de folder van het project in Visual Studio Code.

Je gebruikt **drie terminals**. Alledrie moeten geopend staan in de root van je applicatie folder. 

De **eerste** terminal gebruik jijzelf om bijvoorbeeld artisan commando's uit te voeren.

De **tweede** terminal draait een ontwikkelomgeving voor de JavaScript onderdelen via het commando 'npm run dev'. Bovendien geeft dit commando je een hot reload, waardoor je wijzigingen direct terugziet in de Browser.

De **derde** terminal draait de Laravel ontwikkelomgeving inclusief een ingebouwde webserver om de applicatie te serveren. Het commando voor deze terminal is 'php artisan serve', en de applicatie is te vinden op url: http://localhost:8000

## Stap 2 - Hotelkamer CRUD
Een CRUD is de software die je bouwt om een tabel te bewerken. Het bestaat uit onderdelen voor **C**REATE, **R**EAD, **U**PDATE en **D**ELETE van records in de tabel.

Hieronder staat hoe je de benodigde bestanden voor een hotelkamer CRUD kunt aanmaken voor Laravel.
Daarna moet je de code van deze bestanden aanpassen om een werkende CRUD te maken.

Voer in de terminal het volgende commando uit:

```
php artisan make:model Room -mcr
```

Met dit commando worden de volgende bestanden gemaakt:

#### - [datum]_create_rooms_table.php
Met dit bestand kan je de databasetabel rooms aanmaken. Het bestand staat in de map **Database**

#### - RoomController.php
In dit bestand komt code om records op te slaan, te wijzigen of te verwijderen. Het staat in de map **App/Http/Controllers**

#### - Room.php
Dit bestand is het model voor de tabel Room. Hier kan je relaties met andere tabellen coderen. Het staat in de map **App/Models**


## Stap 3 - Code schrijven
Je hebt nu alle bestanden om de CRUD voor de kamer af te bouwen. In deze stap geven we je hiervoor de basiscode. 
Je krijgt steeds code voor de kolom 'naam', je moet dit later zelf aanpassen voor de hotekamer.

Voor de boeking tabel gelden dezelfde stappen, ook die moet je later zelf uitvoeren.

### De migratie
Open het bestand [datum]_create_rooms_table.php

Pas de code aan zodat de kolommen van de tabel rooms gedefinieerd worden volgens ons database ontwerp.

##### file: /Database/[datum]_create_rooms_table.php
```
public function up() {
    Schema::create('rooms', function (Blueprint $table) {
        $table->id();
        $table->string('name');
        });
}
```

Dit is alleen nog maar de code, je moet deze code ook **uitvoeren** om de wijzigingen in de database te krijgen. 
Voer de onderstaande code uit in de terminal om de migration uit te voeren:

```
php artisan migrate
```
Als je iets wijzigt aan de migration moet je de migration opnieuw uitvoeren.
Om alle migrations helemaal opnieuw uit te voeren gebruikt je onderstaande commando:

```
php artisan migrate:fresh
```

### Het model
We passen het model Room.php aan zodat de applicatie weet welke kolommen mogen worden gewijzigd door gebruikers. 
Voeg onderstaande code toe aan Room.php

##### file: /App/Models/Room.php
```
protected $fillable = ['name'];
```

### De Views
Views zijn de pagina's met html voor de applicatie. Bijvoorbeeld de pagina met de lijst van kamers, of de pagina om een kamer toe te voegen.

De Views worden opgeslagen in de map **Resources/Views**, elke tabel krijgt zijn eigen folder met views. Dus de views voor de hotelkamer komen in de folder **room**.

Hieronder staat de code voor de minimale views:

#### Lijst met kamers 
##### file: /resources/views/rooms/index.php
```
@extends('layouts.app')

@section('content')
    <h1 class="mb-4">Kamers</h1>
    <a href="{{ route('rooms.create') }}" class="btn btn-primary mb-3">Nieuwe Kamer</a>
    <table class="table table-striped">
        <thead>
            <tr>
                <th>Naam</th>
                <th>Acties</th>
            </tr>
        </thead>
        <tbody>
            @foreach ($rooms as $room)
                <tr>
                    <td>{{ $room->name }}</td>
                    <td>
                        <a href="{{ route('rooms.edit', $room) }}" class="btn btn-sm">Bewerken</a>
                        <form action="{{ route('rooms.destroy', $room) }}" method="POST" class="d-inline">
                            @csrf @method('DELETE')
                            <button type="submit" class="btn btn-danger btn-sm">Verwijderen</button>
                        </form>
                    </td>
                </tr>
            @endforeach
        </tbody>
    </table>
@endsection
```

#### Nieuw kamer toevoegen
##### file: /resources/views/rooms/create.php
```
@extends('layouts.app')

@section('content')
    <h1>Nieuwe Kamer Toevoegen</h1>
    <form action="{{ route('rooms.store') }}" method="POST">
        @csrf
        <div class="mb-3">
            <label class="form-label">Naam</label>
            <input type="text" name="name" class="form-control" required>
        </div>
        <button type="submit" class="btn btn-success">Opslaan</button>
    </form>
@endsection
```
#### Kamer wijzigen
##### file: /resources/views/rooms/edit.php
```
@extends('layouts.app')

@section('content')
<form method="post" action="{{ route('rooms.update', $room->id) }}">
    @csrf
    @method('PATCH')
    <div class="mb-3">
        <label class="form-label">Naam</label>
        <input type="text" class="form-control" name="name" value="{{$room->name}}"/>
    </div>
    <button type="submit" class="btn btn-primary">Wijzigen</button>
</form>
@endsection
```

### De controller
In de RoomController komt code om een lijst van kamers op te vragen, kamers toe te voegen, te wijzigen en kamers te verwijderen

Elke actie (lijst, toevoegen, wijzigen, verwijderen) krijgt zijn eigen functies in de controller.

Voeg onderstaande code toe aan RoomController.php

##### file: /App/Http/Controllers/RoomController.php
```
public function index()
{
    $rooms = Room::all();
    return view('rooms.index', compact('rooms'));
}

public function create()
{
    return view('rooms.create');
}

public function store(Request $request)
{
    $validated = $request->validate([
        'name' => 'required',
    ]);

    Room::create($validated);
    return redirect()->route('rooms.index')->with('success', 'Room successfully created');
}

public function show(Room $room)
{
    return view('rooms.show', compact('room'));
}

public function edit(Room $room)
{
    return view('rooms.edit', compact('room'));
}

public function update(Request $request, Room $room)
{
    $validated = $request->validate([
        'name' => 'required',
    ]);

    $room->update($validated);
    return redirect()->route('rooms.index')->with('success', 'Room successfully updated.');
}

public function destroy(Room $room)
{
    $room->delete();
    return redirect()->route('rooms.index')->with('success', 'Room successfully deleted.');
}
```

We gaan in de les deze code beter uitleggen.


## Stap 5 - Routes
Routes zijn de urls die de applicatie gebruikt om alle acties van de applicatie uit te voeren. Bijvoorbeel om een lijst met beschikbare hotelkamers op te vragen.
Routes staan in het bestand **web.php**. Zonder de juiste route in web php zal je applicatie niet werken.

Voeg de onderstaande code toe aan web.php:
##### file: /web.php

```
use App\Http\Controllers\RoomController;

Route::resource('rooms', RoomController::class);
```

Hiermee krijgt de applicatie de beschikking over verschillende routes voor de tabel room.

## Stap 6 - Menubar
We willen een nette menubalk met daarin linkjes naar de index pagina's van onze CRUDs. 

Deze aanpassing voer je uit in de app.blade.php, de basislayout van elke pagina. Op die manier krijg je op elke pagina dezelfde menubar.

Voeg onderstaande code toe aan app.blade.php, onder de comment **\<!-- Left Side of Navbar -->**:

#### file: /resources/views/layouts/app.blade.php
```
<!-- Left Side Of Navbar -->
<ul class="navbar-nav me-auto">
    <li class="nav-item"><a class="nav-link" href="{{ route('rooms.index') }}">Kamers</a></li>
</ul>
```

## Testen
Als je alle stappen hebt gevolgd kan je nu testen of de applicatie werkt. 

Je hebt als het goed is de volgende terminals openstaan:

terminal met 'npm run dev',
terminal met 'php artisan serve'

Je kan de applicatie in de browser vinden op de url: 'http://localhost:8000'

Om te testen of je een kamer kan toevoegen, wijzigen, verwijderen en een lijst kan krijgen van alle kamers kan je de volgende url's testen:

|Actie|Url|
|---|---|
|toevoegen|http://localhost:8000/rooms/create|
|wijzigen|http://localhost:8000/rooms/id/edit|
verwijderen|http://localhost:8000/rooms/id/delete|
lijst|http://localhost:8000/rooms|

## Verder bouwen
Om de applicatie af te bouwen heb je nog wel het een en ander te doen. Hier is alvast een lijstje met taken die je op kan nemen in je planning:

- Overige velden voor kamer toevoegen aan migratie, model, controller en views zodat een volledige kamer kan worden beheerd.
- Frontend en Backend validaties toevoegen
- CRUD toevoegen voor boekingen (migratie, controller, model, views)
- Zorgen dat er geen dubbele boekingen kunnen ontstaan
- Zorgen dat een kamer niet verwijderd kan worden als er nog boekingen op die kamer bestaan.
- Voorpagina maken
- Pagina maken met extra informatie over het hotel
- Menubalk afmaken


##

# Achtergrond informatie over Laravel

Nu volgt nog extra achtergrond informatie over Laravel

## Artisan
Artisan is de command line tool van Laravel. Met Artisan beheer je je Laravel applicatie. Je kunt er boiler plate code mee genereren, de cache mee beheren, de database beheren en meer. 

Artisan is een PHP applicatie, dus je start artisan met 'php' ervooor, bijvoorbeeld: 'php artisan migrate'.

## Migrations
In Laravel worden tabellen in je database gedefinieerd door migration files. Dit zijn bestanden in de app/database/migrations map.

Migrations worden uitgevoerd met het **artisan migrate** commando.

Het aanmaken van een nieuwe tabel bestaat uit de volgende stappen:

- Maak met artisan een migration bestand voor je tabel
- Definieer de kolommen in de up() function
- Voer de migration uit met artisan

Je kunt eenmaal uitgevoerde migrations ongedaan maken met arstisan **migrate:rollback**. Hieronder staan een paar van de meest gebruikte artisan migrate commando's:

|Commando|Beschrijving|
|---|---|
|php artisan make:migration create_rooms_table|Maak een nieuwe migratie, in dit voorbeeld voor de tabel met de naam 'rooms'. Je vindt het aangemaakte bestand terug in de map database/migrations
|php artisan migrate|Voer alle openstaande migraties uit. Migraties die eerder al een keer zijn uitgevoerd worden niet opnieuw uitgevoerd.|
|php artisan migrate:fresh|Voer alle migraties uit. Ook de migraties die eerder al een keer zijn uitgevoerd worden opnieuw uitgevoerd.
|php artisan migrate:rollback|Maak de laatste migratie ongedaan. Je kunt rollback steeds opnieuw uitvoeren totdat alle migraties zijn teruggedraaid|
|php artisan migrate:reset|Maak alle uitgevoerde migraties ongedaan. De database wordt leeggemaakt.
|php artisan migrate:status|Je krijgt een overzicht van de status van de migraties.

Raadpleeg de <a href="https://laravel.com/docs/11.x/migrations">Laravel database documentatie</a> voor meer database en migrate commando's.


## Models, Views, Controllers
In Laravel werk je met het **MVC design pattern**, Model, View, Controller. Eerst even in het kort waar deze termen voor staan:

### Model
Een model is de 'brug' naar een tabel in de database. Via het model in Laravel kan je veel database acties, zoals het toevoegen, wijzigen of verwijderen van records, eenvoudiger uitvoeren.

### View
Een view is een pagina in je applicatie waar de informatie uit een of meerdere tabellen getoond wordt. Views bestaand uit een mix van HTML code en Blade template code.

### Controller
De controller is de schakel tussen het Model en de View. Een controller bestaat vaak uit standaard functies waarmee je CRUD functionaliteit bouwt.

!!! note "CRUD"
    CRUD staat voor **Create**, **Read**, **Update** en **Delete**. Dit zijn de standaard acties die je nodig hebt om een tabel te bewerken.

Je kan met artisan een Resource Controller laten aanmaken die alle functies bevat die nodig zijn voor je CRUD:

```
php artisan make:controller RoomController --resource
```
Je krijgt nu een bestand met de functies index, create, store, show, edit, update, destroy. Je moet zelf nog de benodigde code in deze functies maken.  

### Artisan commando's voor MVC
Je kan met Artisan boiler plate code voor Models, Views en Controllers laten aanmaken. Hieronder staan een paar veelgebruikte artisan commando's die je hiervoor kan gebruiken.

|Commando|Beschrijving|Aangemaakte bestand(en)
|---|---|---|
|php artisan make:model Room|Maak een Model voor de tabel rooms|app/Models/Room.php
|php artisan make:model Room --seed|Maak een model voor de tabel rooms en een seeder|app/Models/Room.php<br>database/seeders/RoomSeeder.php
|php artisan make:controller RoomController|Maak een controller voor de tabel rooms|app/Http/Controllers/RoomController.php
|php artisan make:controller RoomController --resource|Maak een resource Controller voor de tabel rooms|app/Http/Controllers/RoomController.php
|php artisan make:model Room -mcr|Maak een Model, een Resource Controller en een Migration voor de tabel rooms|app/Models/Room.php<br>database/migrations/(..)_create_rooms_table.php<br>app/Http/Controllers/RoomController.php
|php artisan make:view room|Maak een View voor de tabel rooms|resources/views/room.blade.php
|php artisan make:model Room -mcrsf|Het meest complete commando. Creëert een Model, een Resource Controller, een Migration, een Seeder, en een Factory.<br><br>Voeg zelf nog de benodigde Views toe en je bent compleet.|app/Models/Room.php<br>database/factories/RoomFactory.php<br>database/migrations/(...)_create_rooms_table.php<br>database/seeders/RoomSeeder.php<br>app/Http/Controllers/RoomController.php 

## Laravel Naming Conventions
Laravel volgt de <a href="https://www.php-fig.org/psr/psr-12/">PSR-2/PSR-12 standaard</a>. Een set met coding style standaarden voor PHP.

Hieronder staan alvast enkele belangrijke regels die je kunt volgen.  

Models en Controllers worden met **PascalCase** geschreven, elk woord begint met een hoofdletter. Dus bijvoorbeeld **S**tudent**C**ontroller. 

Models en Controllers worden altijd in **enkelvoud** geschreven. Dus Room.php en **niet** Room**s**.php

Tabellen worden in **snake_case** geschreven en in het **meervoud**. Dus bijvoorbeeld **r**oom_**t**ype**s**. 

Variabelen worden in **camelCase** geschreven. Dus bijvoorbeeld **r**oom**T**type = 'Suite';

## Convention over Configuration
Hoe beter je de Laravel standaarden volgt, hoe beter Laravel je kan helpen met automatische configuratie en acties, dit wordt **convention over configuration** genoemd.

Twee voorbeelden van convention over configuration: 

Als je een Model maak met de naam **Room**, dan hoef je Laravel niet meer te vertellen dat de bijbehorende tabel **rooms** is. Laravel gaat ervan uit dat de tabel die bij een Model hoort geschreven is in de Engelse **meervoudsvorm** van het Model.<br>(*Deze convention werkt trouwens niet lekker als je Nederlandse namen voor tabellen gebruikt*.) 

Als je in een migration een kolom met de naam "**id**" toevoegt, dan gaat Laravel ervan uit dat dit de **primary key** van die tabel is.

## Primary Keys en Foreign Keys in Migrations

### Primary key
Als je de primary key "id" noemt dan zal Laravel in de tabel deze kolom als primary key met een auto-increment aanmaken:

```
Schema::create('rooms', function (Blueprint $table) {
    $table->id();
});
```
 Doordat we de naam 'id' gebruiken wordt er door Laravel automatisch een unsigned bigint met auto-increment aangemaakt

### Foreign Keys
Als je een foreign key aanmaakt met 'id' en de naam van de gerelateerde tabel ervoor, dan weet Laravel hoe deze relatie werkt.

``` 
Schema::create('bookings', function (Blueprint $table) {
    $table->id();
    $table->foreignId('room_id')->constrained(); 
});
```

De **->constrained()** zorgt ervoor dat in de tabel een constrained wordt aangemaakt. Dit zorgt ervoor dat je niet per ongeluk een room kan verwijderen als er nog een booking met die kamer bestaat.

## Routes
Routes zijn url's in je applicatie waarmee de gebruiker naar de diverse beschikbare pagina's kan navigeren. Zonder een route naar een pagina is die pagina niet beschikbaar.

Routes worden gedefinieerd in het bestand **web.php**. Meestal wil je dat een route verwijst naar een functie in een Controller. Die functie gaat dan de benodigde acties uitvoeren om de pagina met de juiste gegevens te laten zien.

Hieronder staat een voorbeeld van een route naar de index functie van de RoomController:

``` title="web.php"
Route::get('/rooms', [App\Http\Controllers\RoomController::class, 'index']);
```

In plaats van voor iedere functie in een controller een aparte route te definieren, kan je ook een resource route gebruiken. Een resource route maakt achter de schermen in één keer routes voor alle functies van een resource controller:

``` title="web.php"
Route::resource('rooms', App\Http\Controllers\RoomController::class);
```

Deze route maakt achter de schermen routes voor de functies in je resource controller: index, create, store, show, edit, update en destroy


## Views
Views zijn de pagina's waarmee je de gebruiker de gegevens van je applicatie kan laten zien en laten bewerken.
Views bestaan uit een **combinatie** van **HTML** code en **Blade** template code.

Een View wordt aangeroepen vanuit een Controller en krijgt van de controller functie de gegevens mee om te laten zien of te laten bewerken.

Views worden opgeslagen in de **resource/views** folder. Het is gebruikelijk om voor elke tabel waarvoor je Views wilt maken een subdirectory te maken. De Views voor de tabel rooms staat dan in de folder resources/views/room

Hieronder staat een voorbeeld van de index function uit RoomController:

``` linenums="1" title="RoomController.php"
public function index()
{
  $rooms = Room::all();
  return view('room.index', ['rooms' => $rooms]);
}
```
Op regel 3 worden alle kamers uit de database opgehaald. Hiervoor wordt het Model Room gebruikt.

Op regel 4 wordt de index View teruggegeven zodat die aan de gebruiker getoond kan worden. De view krijgt de opgehaalde kamers meegestuurd.

De volledige bestandsnaam van de index View is **index.blade.php**, maar je hoeft alleen maar 'index' te schrijven. En omdat de View in de subdirectory 'resources/views/room' staat schrijf je dus '**room.index**'

Je kan in plaats van **['rooms' => $rooms]** ook de handige functie compact() gebruiken. Het resultaat is hetzelfde:

``` linenums="1" title="RoomController.php"
public function index()
{
  $rooms = Room::all();
  return view('room.index', compact('rooms'));
}
```

En hier is dan de voorbeeld code voor de View 'index':

``` linenums="1" title="index.blade.php"
<table>
    <thead>
    <tr>
        <td>Name</td>
        <td>Type</td>
    </tr>
    </thead>
    <tbody>
        @foreach($rooms as $room)
            <tr>
                <td>{{$room->name}}</td>
                <td>{{$room->room_type}}</td>
            </tr>
        @endforeach
    </tbody>
</table>
```

Het is een eenvoudige HTML Table. In de **body** van de table wordt **Blade template code** gebruikt om met een loop alle kamers te laten zien.

De kamers staan in de variabele **$rooms**. Dit is een array met kamers die door de controller functie is opgehaald en aan de view is doorgegeven.

Je kan de Blade template code herkennen aan het '**@**' teken dat altijd voor de instructie staat. In bovenstaand voorbeeld wordt de Blade functie **@foreach()** gebruikt om door de gegevens te lopen. De loop wordt afgesloten met een **@endforeach**. 

Op regel 11 en 12 zie je dat de **name** en **room_type** van de kamers in een **<td\>** wordt gezet. De dubbele krulhaken zijn Blade code om aan te geven dat we de inhoud van de variabelen willen laten zien.
