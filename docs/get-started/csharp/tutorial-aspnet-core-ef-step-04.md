---
title: 'Schritt 4: Bereitstellen einer Web-API von Ihrer ASP.NET Core-App aus'
description: Fügen Sie Ihrer ASP.NET Core-Web-App mit diesem Videotutorial und schrittweisen Anweisungen eine Web-API hinzu.
ms.custom: get-started
ms.date: 02/13/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 9625ce43d94158732c2d6af738a1f1abc84f666e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878772"
---
# <a name="step-4-expose-a-web-api-from-your-aspnet-core-app"></a>Schritt 4: Bereitstellen einer Web-API von Ihrer ASP.NET Core-App aus

Um Ihrer vorhandenen ASP.NET Core-App eine Web-API hinzuzufügen, gehen Sie wie folgt vor.

_Schauen Sie sich dieses Video an, und fügen Sie wie dort gezeigt Ihrer ersten ASP.NET Core-App Web-API-Unterstützung hinzu._

> [!VIDEO https://www.youtube.com/embed/o_fYPOsAXts]

## <a name="open-your-project"></a>Öffnen Ihres Projekts

Öffnen Sie Ihre ASP.NET Core-App in Visual Studio 2019. Die App sollte bereits EF Core zum Verwalten Ihrer Modelltypen verwenden, wie in [Schritt 3 dieser Tutorialreihe](tutorial-aspnet-core-ef-step-03.md) konfiguriert.

## <a name="add-an-api-controller"></a>Hinzufügen eines API-Controllers

Klicken Sie mit der rechten Maustaste auf das Projekt, und fügen Sie einen neuen Ordner namens *Api* hinzu. Klicken Sie dann mit der rechten Maustaste auf diesen Ordner, und wählen Sie **Hinzufügen** > **Neues Gerüstelement** aus. Wählen Sie **API-Controller mit Aktionen unter Verwendung von Entity Framework** aus. Wählen Sie nun eine vorhandene Modellklasse aus, und klicken Sie auf **Hinzufügen**.

![Visual Studio 2019 – ASP.NET Core-Gerüst-API-Controller](media/vs-2019/vs2019-add-scaffold-api.png)

## <a name="reviewing-the-generated-controller"></a>Überprüfen des generierten Controllers

Der generierte Code enthält eine neue Controllerklasse. Am oberen Rand der Klassendefinition gibt es zwei Attribute.

```csharp
[Route("api/[controller]")]
[ApiController]
public class GamesController : ControllerBase
```

Das erste gibt die Route für Aktionen in diesem Controller als `api/[controller]` an, d.h. wenn der Controller mit `GamesController` benannt wird, ist die Route `api/Games`.

Das zweite Attribut, `[ApiController]`, fügt der Klasse einige nützliche Überprüfungen hinzu, z.B. um sicherzustellen, dass jede Aktionsmethode ihr eigenes `[Route]`-Attribut enthält.

```csharp
public class GamesController : ControllerBase
{
    private readonly AppDbContext _context;

    public GamesController(AppDbContext context)
    {
        _context = context;
    }
```

Der Controller verwendet den vorhandenen `AppDbContext`, der seinem Konstruktor übergeben wird. Jede Aktion verwendet dieses Feld, um mit den Daten der Anwendung zu arbeiten.

```csharp
// GET: api/Games
[HttpGet]
public IEnumerable<Game> GetGame()
{
    return _context.Game;
}
```

Die erste Methode ist eine einfache GET-Anforderung, wie mit dem `[HttpGet]`-Attribut angegeben. Sie nimmt keine Parameter entgegen und gibt eine Liste aller Spiele in der Datenbank zurück.

```csharp
// GET: api/Games/5
[HttpGet("{id}")]
public async Task<IActionResult> GetGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);

    if (game == null)
    {
        return NotFound();
    }

    return Ok(game);
}
```

Die nächste Methode gibt `{id}` in der Route an, was der Route gefolgt von einem `/` hinzugefügt wird, sodass die vollständige Route etwa `api/Games/5` entspricht, wie im Kommentar oben dargestellt. Die `id`-Eingabe wird dem `id`-Parameter der Methode zugeordnet. Wenn das Modell ungültig ist, wird innerhalb der Methode ein `BadRequest`-Ergebnis zurückgegeben. Andernfalls versucht EF, die Datensätze zu finden, die mit der bereitgestellten `id` übereinstimmen. Wenn dies nicht möglich ist, wird ein `NotFound`-Ergebnis zurückgegeben, andernfalls der entsprechende `Game`-Datensatz.

```csharp
// PUT: api/Games/5
[HttpPut("{id}")]
public async Task<IActionResult> PutGame([FromRoute] int id, [FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    if (id != game.Id)
    {
        return BadRequest();
    }

    _context.Entry(game).State = EntityState.Modified;

    try
    {
        await _context.SaveChangesAsync();
    }
    catch (DbUpdateConcurrencyException)
    {
        if (!GameExists(id))
        {
            return NotFound();
        }
        else
        {
            throw;
        }
    }

    return NoContent();
}
```

Als Nächstes wird eine an die API gerichtete `[HttpPut]`-Anforderung verwendet, um Updates auszuführen. Der neue `Game`-Datensatz wird im Text der Anforderung bereitgestellt. Eine Validierung und Überprüfung auf Fehler wird ausgeführt, und bei erfolgreichem Verlauf wird der Datensatz in der Datenbank mit den Werten im Text der Anforderung aktualisiert. Andernfalls wird eine entsprechende Fehlerantwort zurückgegeben.

```csharp
// POST: api/Games
[HttpPost]
public async Task<IActionResult> PostGame([FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    _context.Game.Add(game);
    await _context.SaveChangesAsync();

    return CreatedAtAction("GetGame", new { id = game.Id }, game);
}
```

Mit einer `[HttpPost]`-Anforderung werden dem System neue Datensätze hinzugefügt. Wie bei `[HttpPut]` wird der Datensatz im Text der Anforderung hinzugefügt. Wenn er gültig ist, fügt EF Core den Datensatz der Datenbank hinzu, und die Aktion gibt den aktualisierten Datensatz (mit in der Datenbank generierter ID) und einen Link zu dem Datensatz in der API zurück.

```csharp
// DELETE: api/Games/5
[HttpDelete("{id}")]
public async Task<IActionResult> DeleteGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);
    if (game == null)
    {
        return NotFound();
    }

    _context.Game.Remove(game);
    await _context.SaveChangesAsync();

    return Ok(game);
}
```

Zum Schluss wird eine `[HttpDelete]`-Route mit einer ID verwendet, um einen Datensatz zu löschen. Wenn die Anforderung gültig ist und ein Datensatz mit der angegebenen ID vorhanden ist, löscht EF Core ihn aus der Datenbank.

## <a name="adding-swagger"></a>Hinzufügen von Swagger

Swagger ist ein API-Dokumentations- und Testtool, das als eine Reihe von Diensten und Middleware einer ASP.NET Core-App hinzugefügt werden kann. Klicken Sie hierzu mit der rechten Maustaste auf das Projekt, und wählen Sie **NuGet-Pakete verwalten** aus. Klicken Sie dann auf **Durchsuchen**, suchen Sie nach `Swashbuckle.AspNetCore`, und installieren Sie die 4.0.1-Version.

![Visual Studio 2019 – Hinzufügen von Swashbuckle aus NuGet](media/vs-2019/vs2019-nuget-swashbuckle.png)

Öffnen Sie nach Abschluss der Installation `Startup.cs`, und fügen Sie Folgendes am Ende der `ConfigureServices`-Methode hinzu:

```csharp
services.AddSwaggerGen(c =>
{
    c.SwaggerDoc("v1", new Info { Title = "My API", Version = "v1" });
});
```

Sie müssen auch `using Swashbuckle.AspNetCore.Swagger;` am Anfang der Datei hinzufügen.

Fügen Sie als Nächstes der `Configure`-Methode direkt vor `UseMvc` Folgendes hinzu:

```csharp
// Enable middleware to serve generated Swagger as a JSON endpoint.
app.UseSwagger();

// Enable middleware to serve swagger-ui (HTML, JS, CSS, etc.),
// specifying the Swagger JSON endpoint.
app.UseSwaggerUI(c =>
{
    c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
});
```

Jetzt sollten Sie Ihre App erstellen und ausführen können. Navigieren Sie im Browser zu `/swagger` in der Adressleiste. Daraufhin sollte eine Liste der API-Endpunkte und Modelle Ihrer App angezeigt werden.

![Visual Studio 2019 – Swagger-Seite im Browser](media/vs-2019/vs2019-swagger-browser.png)

Klicken Sie unter „Games“ auf einen Endpunkt, und dann auf `Try it out` und `Execute`, um zu sehen, wie sich die verschiedenen Endpunkte verhalten.

## <a name="next-steps"></a>Nächste Schritte

Im nächsten Video erfahren Sie, wie Sie Ihre App in Azure bereitstellen.

[Schritt 5: Bereitstellen Ihrer ASP.NET Core-App in Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="see-also"></a>Siehe auch

- [Erste Schritte mit Swashbuckle und ASP.NET Core](/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-2.2&tabs=visual-studio&preserve-view=true)
- [ASP.NET Core-Web-API-Hilfeseiten mit Swagger/OpenAPI](/aspnet/core/tutorials/web-api-help-pages-using-swagger?view=aspnetcore-2.2&preserve-view=true)