---
title: 'Schritt 3: Arbeiten mit Daten in Ihrer ASP.NET Core-App'
description: Beginnen Sie, mithilfe von Entity Framework Core in Ihrer ASP.NET Core-Web-App mit diesem Videotutorial und schrittweisen Anweisungen mit Daten zu arbeiten.
ms.custom: get-started
ms.date: 03/31/2019
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
ms.openlocfilehash: aa3df844d5fad5dc968a9bab5d02e9a3e8e06719
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879968"
---
# <a name="step-3-work-with-data-using-entity-framework"></a>Schritt 3: Arbeiten mit Daten mithilfe von Entity Framework

Um mithilfe von Entity Framework Core in Ihrer ASP.NET Core-Web-App mit Daten zu arbeiten, gehen Sie wie folgt vor.

_Schauen Sie sich dieses Video an, und fügen Sie wie dort gezeigt Ihrer ersten ASP.NET Core-App Daten hinzu._

> [!VIDEO https://www.youtube.com/embed/dulJCwNrqhM]

## <a name="open-your-project"></a>Öffnen Ihres Projekts

Wenn Sie diesen Videos folgen, öffnen Sie das Projekt „Webanwendung“, das Sie im vorherigen Abschnitt erstellt haben. Wenn Sie hier beginnen, müssen Sie ein neues Projekt erstellen und **ASP.NET-Webanwendung** und dann **Webanwendung** auswählen. Behalten Sie für die restlichen Optionen die Standardwerte bei.

## <a name="add-your-model"></a>Hinzufügen Ihres Modells

Um in Ihrer ASP.NET Core-Anwendung mit Daten zu arbeiten, müssen Sie zunächst beschreiben, wie die Daten aussehen sollten. Dies ist das Erstellen eines *Modells* der Dinge, die an diesem Problem, das wir lösen möchten, beteiligt sind. In Anwendungen in der realen Welt fügen wir diesen Modellen benutzerdefinierte Geschäftslogik hinzu, sodass sie sich auf bestimmte Weise verhalten und Aufgaben für uns automatisieren können. In diesem Beispiel werden wir ein einfaches System für die Verfolgung von Brettspielen erstellen. Wir benötigen eine Klasse, die ein Spiel darstellt und einige Eigenschaften beinhaltet, die wir zu diesem Spiel festhalten möchten, z.B. die Zahl der Spieler, die daran teilnehmen können. Diese Klasse wird sich in einem neuen Ordner namens *Models* befinden, den wir im Stamm des Webprojekts erstellen werden.

```csharp
public class Game
{
    public int Id { get; set; }
    public string Title { get; set; }
    public int PublicationYear { get; set; }
    public int MinimumPlayers { get; set; }
    public int MaximumPlayers { get; set; }
}
```

## <a name="create-the-pages-to-manage-your-game-library"></a>Erstellen der Seiten zum Verwalten Ihrer Spielebibliothek

Wir können nun die Seiten erstellen, mit denen wir unsere Spielebibliothek verwalten werden. Dies hört sich vielleicht schwierig an, ist aber tatsächlich erstaunlich einfach. Zunächst müssen wir entscheiden, wo sich diese Funktionalität in unserer App befinden soll. Öffnen Sie den Ordner „Pages“ im Webprojekt, und fügen Sie dort einen neuen Ordner hinzu. Nennen Sie ihn *Games*.

Klicken Sie jetzt mit der rechten Maustaste auf „Games“, und klicken Sie dann auf **Hinzufügen** > **Neues Gerüstelement**. Wählen Sie die Razor Pages mithilfe der Option **Entity Framework (CRUD)** aus. CRUD steht für „Create, Read, Update, Delete“ (Erstellen, Lesen, Aktualisieren, Löschen), und mit dieser Vorlage werden Seiten für jeden dieser Vorgänge erstellt (einschließlich einer Seite „Alle auflisten“ und einer Seite "Details zu einem Element anzeigen").

![Visual Studio 2019 ASP.NET Core – Seite „Gerüst hinzufügen“](media/vs-2019/vs2019-add-scaffold.png)

Wählen Sie die Modellklasse „Game“ aus, und fügen Sie mit dem Symbol „+“ eine neue Datenkontextklasse hinzu. Nennen Sie es `AppDbContext`. Übernehmen Sie die übrigen Standardeinstellungen, und klicken Sie auf **Hinzufügen**.

Sie sehen, dass die folgenden Razor Pages Ihrem Ordner „Games“ hinzugefügt werden:

- Create.cshtml
- Delete.cshtml
- Details.cshtml
- Edit.cshtml
- Index.cshtml

![Visual Studio 2019 ASP.NET Core – Gerüst-Seiten](media/vs-2019/vs2019-scaffolded-pages.png)

Zusätzlich zum Hinzufügen von Seiten im Ordner *Games* hat der Gerüstbauvorgang der *Startup.cs*-Klasse Code hinzugefügt. Wenn Sie die `ConfigureServices`-Methode in dieser Klasse betrachten, sehen Sie, dass dieser Code hinzugefügt wurde:

```csharp
services.AddDbContext<AppDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("AppDbContext")));
```

Sie sehen auch, dass die `AppDbContext`-Verbindungszeichenfolge der *appsettings.json*-Datei des Projekts hinzugefügt wurde.

Wenn Sie die App nun ausführen, kann ein Fehler auftreten, weil noch keine Datenbank erstellt wurde. Sie können durch [Hinzufügen von ein wenig Code zu Program.cs](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio&preserve-view=true#update-main) konfigurieren, dass die App die Datenbank bei Bedarf automatisch erstellt:

```csharp
public static void Main(string[] args)
{
    var host = CreateWebHostBuilder(args).Build();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        try
        {
            var context = services.GetRequiredService<Data.AppDbContext>();
            context.Database.EnsureCreated();
        }
        catch (Exception ex)
        {
            var logger = services.GetRequiredService<ILogger<Program>>();
            logger.LogError(ex, "An error occurred creating the DB.");
        }
    }

    host.Run();
}
```

Fügen Sie am Ende des vorhandenen Using-Anweisungblocks die folgenden Using-Anweisungen zu *Program.cs* hinzu, um die Typnamen im vorangehenden Code aufzulösen:

```csharp
using Microsoft.Extensions.DependencyInjection;
using WebApplication1.Models;
```

Achten Sie darauf, dass Sie in Ihrem Code anstelle von „WebApplication1“ Ihren Projektnamen verwenden.

Der meiste Code dient nur zur Fehlerbehandlung und um Zugriff auf den EF Core `AppDbContext` zu bieten, bevor die App ausgeführt wird. Die wichtigste Zeile ist `context.Database.EnsureCreated()`, die die Datenbank erstellt, wenn sie noch nicht vorhanden ist. Jetzt kann die App ausgeführt werden.

## <a name="test-it-out"></a>Ausprobieren

Führen Sie die Anwendung aus, und navigieren Sie zu `/Games` in der Adressleiste. Eine leere Listenseite wird angezeigt. Klicken Sie auf **Neu erstellen**, um der Auflistung ein neues `Game` hinzuzufügen. Füllen Sie das Formular aus, und klicken Sie auf **Erstellen**. Es sollte in der Listenansicht angezeigt werden. Klicken Sie auf **Details**, um die Details eines einzelnen Datensatzes anzuzeigen.

Fügen Sie einen weiteren Datensatz hinzu. Klicken Sie auf *Bearbeiten*, um die Details eines Datensatzes zu ändern, oder **Löschen**, um ihn zu entfernen; bevor der Eintrag tatsächlich gelöscht wird, werden Sie aufgefordert, dies zu bestätigen.

![Visual Studio 2019 ASP.NET Core – Gerüst-Seiten im Browser](media/vs-2019/vs2019-game-list.png)

Das sind alle Voraussetzungen, um zu beginnen, in einer ASP.NET Core-App mithilfe von EF Core und Visual Studio 2019 mit Daten zu arbeiten.

## <a name="next-steps"></a>Nächste Schritte

Im nächsten Video erfahren Sie, wie Sie Ihrer App Web-API-Unterstützung hinzufügen.

[Schritt 4: Bereitstellen einer Web-API von Ihrer ASP.NET Core-App aus](tutorial-aspnet-core-ef-step-04.md)

## <a name="see-also"></a>Siehe auch

- [Razor Pages mit Entity Framework Core in ASP.NET Core](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio&preserve-view=true)
- [ASP.NET Core-Razor Pages mit EF Core](/aspnet/core/data/?view=aspnetcore-2.1&preserve-view=true)
