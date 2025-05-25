# Code Conventions

## Inleiding
De coding conventions zoals die bij deze opdracht, betreffen naamgeving van variabelen en functies (zoals hooflettergebruik), uitlijning van de broncode. 
De voorbeelden zijn een uittreksel van de volledige [naming conventiins](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/identifier-names) en [coding concentions](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions) voor C#.

## Naamgeving van variabelen en functies
- Gebruik PascalCasing voor de namen van klassen en methoden.

```csharp
public class ClientActivity
{
    public void ClearStatistics()
    {
        //...
    }

    public void CalculateStatistics()
    {
        //...
    }
}
```

- Gebruik CamelCasing voor de parameters van methoden, lokale variabelen en voor de instantie van classes.

```csharp
public class UserLog
{
   public void Add(LogEvent logEvent)
    {
        int itemCount = logEvent.Items.Count;
        // ...
    }
}
```

in variabelen:
```csharp
UserGroup userGroup;
Assignment employeeAssignment;
CustomerId customerId;
XmlDocument xmlDocument;
FtpHelper ftpHelper;
UriPart uriPart;
HtmlHelper htmlHelper;
FtpTransfer ftpTransfer;
UIControl uiControl;
```

- Gebruik géén underscore (onderstreepte spatie) in namen.
Uitzondering: Je mag een onderstreepte spatiestreepje gebruiken als prefix van statische variabelen. 

```csharp
public DateTime clientAppointment;
public TimeSpan timeLeft;
private DateTime _registrationDate;
```

- Gebruik de standaard gedefinieerde typenamen (string, int, bool) in plaats van de system typenamen zoals Int16, Single, UInt64.

```csharp
string firstName;
int lastIndex;
bool isSaved;
```

- Gebruik zelfstandige naamwoorden of zelfstandig naamwoordzinnen voor de naam van een klasse.

```csharp
public class Employee
{
}

public class BusinessLocation
{
}

public class DocumentCollection
{
}
```

- Declareer alle private fields en properties bovenin de klasse. 
```csharp
public class Account
{
    private AccountRepository _accountRepository

    public string Number {get; set;}
    public DateTime DateOpened {get; set;}
    public DateTime DateClosed {get; set;}
    public decimal Balance {get; set;}
 
    // Constructor
    public Account(AccountRepository accountRepository)
    {
        _accountRepository = accountRepositpry
    }
}
```

## Begrippen
- Pascalcase
  Eén woord maken van afzonderlijke woorden die met een hoofdletter beginnen.
  Voorbeeld: Gekookte Eieren Eten wordt in PascalCasing: `GekookteEierenEten`.

- Camelcase
  Is gelijk aan Pascalcase, maar de eerste letter van het eerste woord is altijd een kleine letter.
  Voorbeeld: Gekookte Eieren Eten wordt in CamelCasing: `gekookteEierenEten`.

## Uitlijning
- Lijn alle accolades verticaal uit: zet ze netjes onder elkaar. Spring binnen de accolades in met tabs van 4 spaties.

```csharp
class Program
{
    static void Main(string[] args)
    {
        if(whatever)
        {

        }
    }
}
```