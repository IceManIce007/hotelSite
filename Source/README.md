# Hotel Site
De opdracht "HotelSite uitgewerkt in PHP Laravel en dotnet MVC

# Inleiding

In deze portfolio-opdracht maak je een applicatie voor een Hotel. Het doel van de applicatie is om voor een hotel kamers te beheren (invoeren, wijzigen, verwijderen) en kamers in het hotel te kunnen boeken voor gasten.

Bij het boeken van een kamer is het belangrijk dat gecontroleerd wordt dat de kamer vrij is en voldoende bedden heeft.

De eindgebruikers van de applicatie zijn de beheerders van het hotel, **dus niet de gasten**.

Je bepaalt zelf de naam van het hotel en de opmaak van de site.

Hieronder lees je wat de functionele- en technische eisen zijn voor de applicatie. Lees deze eisen goed door en zorg ervoor dat je goed begrijpt wat gevraagd wordt. 

Als je vragen hebt bij een van de eisen, stel die dan aan de opdrachtgever.

Het is de bedoeling dat jij in je eigen woorden de functionele- en technische eisen opschrijft in een ontwerpdocument. Dit mag in de vorm van user stories.

# Functionele eisen
Hieronder staan de functionele eisen voor de applicatie. Bij de eindoplevering moeten deze functionaliteiten beschikbaar zijn en goed werken.

-	Er is een Voorpagina met de naam van de applicatie een logo en een jumbotron
-	Op alle onderdelen/pagina’s van de applicatie is een menu beschikbaar van waaruit alle andere onderdelen/pagina’s bereikt kunnen worden.
-	In het menu is zichtbaar op welke pagina de gebruikt op dat moment staat

-	Er komt een pagina met overzicht een overzicht van alle kamers (geboekte en vrije kamers)
-	Vanuit het kameroverzicht kan je een kamer kiezen en je krijgt dan meer informatie over die kamer (detailoverzicht kamer)
-	Er is functionaliteit aanwezig om nieuwe kamers aan de database toe tevoegen, bestaande kamers te wijzigen en te verwijderen.
-	Als een kamer verwijderd wordt die nog in een huidige of toekomstige boeking gebruikt worden, dan krijgt de gebruiker een waarschuwing te zien waarin staat dat eerst de bestaande boekingen verwijderd moeten worden.

-	Er komt een overzichtspagina met bestaande boekingen (kamernummer, periode)
-	Vanuit het boekingsoverzicht kan je een boeking kiezen en je krijgt dan meer informatie over die boeking te zien.
-	Er is functionaliteit aanwezig om een nieuwe boeking op te voeren, een bestaande boeking te wijzigen of te verwijderen.
-	Er komt een overzicht waarbij je een datum kunt invullen en je de beschikbare (niet geboekte kamers) te zien krijgt.

# Technische specificaties

## Ontwikkelomgeving
De ontwikkelomgeving iis [Visual Studio Code](https://code.visualstudio.com/) voor de Laravel opdracht en [Visual Studio]{https://visualstudio.microsoft.com/} voor de dotnet MVC opdracht. 

# Database
Voor het overzicht van de beschikbare kamers en de boekingen wordt een database gebruikt. Je ontwerpt zelf de tabellen in deze database. In het ontwerp komt een overzicht van de gebruikte tabellen in de vorm van een datamodel en een datadictionary

De volgende gegevens moeten minimaal in de database kunnen worden opgeslagen:

### Kamer

-	Naam van een soort kamer (bijvoorbeeld: familiesuite, economykamer, luxekamer, etc.)
-	Foto van de kamer (optioneel)
-	Nummer of naam van een kamer
-	Oppervlakte van een kamer
-	Beschikbaarheid van minibar
-	Aantal personen
-	Beschikbaarheid van bad
-	Prijs per nacht

### Boeking

-	Datum van een boeking
-	Naam en adresgegevens van een klant
-	Kredietkaartnummer van een klant
-	Aankomstdatum
-	Vertrekdatum
-	Welke kamer geboekt wordt


# Realisatie
1. Maak eerst de applicatie met [Laravel](src/LARAVEL/README.md)
2. Ga daarna aan de slag met de [ASP.NET MVC](src/ASPDOTNETMVC/README.md)
