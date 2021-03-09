---
ms.openlocfilehash: a33871a9a80dfcb6260f57e504c72ae2f72077bd
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101751020"
---
## <a name="prerequisites"></a>Voraussetzungen

::: moniker range=">=vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) mit den passenden Workloads für Ihre bevorzugte Sprache:
  * ASP.NET: **ASP.NET und Webentwicklung**
  * Python: **Python-Entwicklung**
  * Node.js: **Node.js-Entwicklung**
::: moniker-end
::: moniker range="vs-2017"
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) mit den zu der von Ihnen bevorzugten Sprache passenden Workloads:
  * ASP.NET: **ASP.NET und Webentwicklung**
  * Python: **Python-Entwicklung**
  * Node.js: **Node.js-Entwicklung**
::: moniker-end

* Ein ASP.NET-, ASP.NET Core-, Python- oder Node.js-Projekt. Wenn Sie noch nicht über ein Projekt verfügen, wählen Sie eine der nachfolgenden Optionen aus:
  * ASP.NET Core: Arbeiten Sie [Schnellstart: Verwenden von Visual Studio zum Erstellen Ihrer ersten ASP.NET Core-Web-App](../../ide/quickstart-aspnet-core.md) durch, oder führen Sie die folgenden Schritte aus:
    ::: moniker range=">=vs-2019"
    Wählen Sie im Startfenster von Visual Studio 2019 die Option **Neues Projekt erstellen** aus. Wenn das Startfenster nicht geöffnet ist, klicken Sie auf **Datei** > **Startfenster**. Geben Sie im Suchfeld **Web-App** ein, wählen Sie als Sprache **C#** und anschließend **ASP.NET Core-Webanwendung (Model View Controller)** aus, und klicken Sie dann auf **Weiter**. Geben Sie dem Projekt im nächsten Bildschirm den Namen **MyASPApp**, und klicken Sie dann auf **Weiter**.

    Wählen Sie entweder das empfohlene Zielframework (.NET Core 3.1) oder .NET 5 aus, und klicken Sie dann auf **Erstellen**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Wählen Sie in Visual Studio 2017 **Datei** > **Neues Projekt** und anschließend **Visual C#**  >  **.NET Core** aus. Klicken Sie dann auf **ASP.NET Core-Webanwendung**. Wenn Sie dazu aufgefordert werden, klicken Sie auf die Vorlage **Webanwendung (Model View Controller)**, vergewissern Sie sich, dass **No Authentication** (Keine Authentifizierung) ausgewählt ist, und klicken Sie anschließend auf **OK**.
    ::: moniker-end
  * Python: Führen Sie die unter [Schnellstart: Erstellen Ihrer ersten Python-Web-App mithilfe von Visual Studio](../../ide/quickstart-python.md) beschriebenen Schritte aus, oder klicken Sie auf **Datei** > **Neues Projekt**, und wählen Sie **Python** und anschließend **Flask-Webprojekt** aus.
  * Node.js: Führen Sie die unter [Schnellstart: Erstellen Ihrer ersten Node.js-App mithilfe von Visual Studio](../../ide/quickstart-nodejs.md) beschriebenen Schritte aus, oder klicken Sie auf **Datei** > **Neues Projekt**, und wählen Sie **JavaScript** und anschließend **Blank Node.js Web Application** (Leere Node.js Webanwendung) aus.

* Erstellen Sie das Projekt über den Menübefehl **Erstellen > Projektmappe erstellen**, bevor Sie mit der Bereitstellung beginnen.