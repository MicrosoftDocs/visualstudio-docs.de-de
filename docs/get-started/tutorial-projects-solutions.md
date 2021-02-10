---
title: Einführung in Projekte und Projektmappen
description: Erfahren Sie mehr über den Unterschied zwischen Projekten und Projektmappen und wie sie in Visual Studio verwendet werden können.
ms.date: 11/17/2020
ms.technology: vs-ide-general
ms.custom:
- get-started
- SEO-VS-2020
ms.topic: tutorial
f1_keywords:
- project.addnewitem
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7172ca8c5341dbaee59ae5b2635da9c5585793cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838733"
---
# <a name="introduction-to-projects-and-solutions"></a>Einführung in Projekte und Projektmappen

In diesem einführenden Artikel erfahren Sie mehr über das Erstellen einer *Projektmappe* und eines *Projekts* in Visual Studio. Eine Projektmappe ist ein Container, der zum Organisieren von mindestens einem zugehörigen Codeprojekt verwendet wird, wie z. B. eines Klassenbibliotheksprojekts und dem entsprechenden Testprojekt. Die Eigenschaften eines Projekts und einige der darin enthaltenen Dateien sollen betrachtet werden. Darüber hinaus wird ein Verweis von einem Projekt auf das andere erstellt.

::: moniker range="vs-2017"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) kostenlos herunterladen.

::: moniker-end

::: moniker range="vs-2019"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads) kostenlos herunterladen.

::: moniker-end

Eine Projektmappe und ein Projekt werden von Grund auf neu erstellt, damit Sie das Konzept eines Projekts nachvollziehen können. Wenn Sie Visual Studio normalerweise verwenden, nutzen Sie sehr wahrscheinlich einige der verschiedenen *Projektvorlagen*, die Visual Studio bei der Erstellung eines neuen Projekts zur Verfügung stellt.

> [!NOTE]
> Projektmappen und Projekte werden nicht unbedingt zum Entwickeln von Apps in Visual Studio benötigt. Sie können auch einfach nur einen Ordner öffnen, der Code enthält, und mit dem Codieren, Erstellen und Debuggen beginnen. Wenn Sie beispielsweise ein [GitHub](https://github.com/)-Repository klonen, enthält dieses möglicherweise keine Visual Studio-Projekte und Projektmappen. Weitere Informationen finden Sie unter [Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Projektmappen und Projekte

Trotz der englischen Bezeichnung „Solution“ ist eine Projektmappe keine „Lösung“. Projektmappen sind lediglich Container, die in Visual Studio zum Ordnen von mindestens einem Projekt verwendet werden. Wenn Sie eine Projektmappe in Visual Studio öffnen, werden automatisch alle Projekte geladen, die die Projektmappe enthält.

### <a name="create-a-solution"></a>Erstellen einer Projektmappe

Zunächst soll eine leere Projektmappe erstellt werden. Wenn Sie einmal mit Visual Studio vertraut sind, werden Sie wahrscheinlich eher selten leere Projektmappen erstellen. Wenn Sie in Visual Studio ein neues Projekt erstellen, wird automatisch auch eine Projektmappe für das Projekt erstellt, wenn noch keine geöffnet ist.

::: moniker range="vs-2017"

1. Öffnen Sie Visual Studio.

1. Klicken Sie in der oberen Menüleiste auf **Datei** > **Neu** > **Projekt**.

   Das Dialogfeld **Neues Projekt** wird angezeigt.

1. Erweitern Sie im linken Bereich **Andere Projekttypen**, und klicken Sie dann auf **Visual Studio-Projektmappen**. Wählen Sie im mittleren Bereich die Vorlage **Leere Projektmappe** aus. Geben Sie Ihrer Projektmappe den Namen **QuickSolution**, und klicken Sie anschließend auf **OK**.

   ![Vorlage „Leere Projektmappe“ in Visual Studio 2017](media/tutorial-projects-new-solution.png "Die Vorlage „Leere Projektmappe“ in Visual Studio 2017.")

   Die **Startseite** wird geschlossen, und im **Projektmappen-Explorer** wird auf der rechten Seite im Visual Studio-Fenster eine Projektmappe angezeigt. Sie verwenden den **Projektmappen-Explorer** wahrscheinlich häufig, um die Inhalte Ihrer Projekte zu durchsuchen.

::: moniker-end

::: moniker range=">=vs-2019"

1. Öffnen Sie Visual Studio.

2. Klicken Sie im Startfenster auf **Neues Projekt erstellen**.

3. Geben Sie auf der Seite **Neues Projekt erstellen** im Suchfeld **leere Projektmappe** ein, wählen Sie die Vorlage **Leere Projektmappe** aus, und klicken Sie dann auf **Weiter**.

   ![Vorlage „Leere Projektmappe“ in Visual Studio 2019](media/vs-2019/tutorial-projects-blank-solution-template.png "Die Vorlage „Leere Projektmappe“ in Visual Studio 2019.")

    > [!TIP]
    > Wenn Sie mehrere Workloads installiert haben, wird die Vorlage **Leere Projektmappe** möglicherweise nicht oben in der Liste der Suchergebnisse angezeigt. Scrollen Sie in der Liste zum Abschnitt **Andere Ergebnisse basierend auf Ihrer Suche**. Dort sollte die Vorlage angezeigt werden.

4. Nennen Sie die Lösung **QuickSolution**, und klicken Sie dann auf **Erstellen**.

   Im **Projektmappen-Explorer** wird auf der rechten Seite im Visual Studio-Fenster eine Projektmappe angezeigt. Sie verwenden den **Projektmappen-Explorer** wahrscheinlich häufig, um die Inhalte Ihrer Projekte zu durchsuchen.

::: moniker-end

### <a name="add-a-project"></a>Hinzufügen eines Projekts

Fügen Sie nun der Projektmappe Ihr erstes Projekt hinzu. Beginnen Sie mit einem leeren Projekt, und fügen Sie anschließend die benötigten Elemente hinzu.

::: moniker range="vs-2017"

1. Klicken Sie im Kontextmenü (Rechtsklick) der **Projektmappe „QuickSolution“** im **Projektmappen-Explorer** auf **Hinzufügen** > **Neues Projekt**.

   Das Dialogfeld **Neues Projekt hinzufügen** wird geöffnet.

1. Erweitern Sie im linken Bereich **Visual C#** , und wählen Sie **Windows-Desktop** aus. Wählen Sie anschließend im mittleren Bereich die Vorlage **Leeres Projekt (.NET Framework)** aus. Geben Sie dem Projekt den Namen **QuickDate**, und klicken Sie dann auf **OK**.

   Unter der Projektmappe wird im **Projektmappen-Explorer** ein Projekt mit dem Namen „QuickDate“ angezeigt. Zu diesem Zeitpunkt enthält das Projekt nur eine Datei mit dem Namen *App.config*.

   > [!NOTE]
   > Wenn **Visual C#** nicht im linken Bereich des Dialogfelds angezeigt wird, müssen Sie die Visual Studio-Workload **.NET-Desktopentwicklung** installieren. Visual Studio verwendet die workloadbasierte Installation, damit nur die Komponenten installiert werden, die Sie für Ihre Art von Entwicklung benötigen. Eine einfache Methode zum Installieren einer neuen Workload besteht darin, im Dialogfeld **Neues Projekt hinzufügen** in der unteren linken Ecke auf den Link **Visual Studio-Installer öffnen** zu klicken. Wählen Sie nach dem Starten des Visual Studio-Installers die Workload **.NET-Desktopentwicklung** aus, und klicken Sie anschließend auf **Ändern**.
   >
   > ![Öffnen des Links „Visual Studio-Installer“](media/tutorial-projects-open-installer.png "Der Link „Visual Studio-Installer öffnen“ im Dialogfeld „Neues Projekt hinzufügen“ in Visual Studio 2017.")

::: moniker-end

::: moniker range=">=vs-2019"

1. Klicken Sie im Kontextmenü (Rechtsklick) der **Projektmappe „QuickSolution“** im **Projektmappen-Explorer** auf **Hinzufügen** > **Neues Projekt**.

   Ein Dialogfeld mit dem Titel **Neues Projekt hinzufügen** wird geöffnet.

1. Geben Sie den Text **Leer** oben in das Suchfeld ein, und klicken Sie dann unter **Sprache** auf **C#**.

1. Wählen Sie die Vorlage **Leeres Projekt (.NET Framework)** aus, und klicken Sie dann auf **Weiter**.

1. Geben Sie dem Projekt den Namen **QuickDate**, und klicken Sie dann auf **Erstellen**.

   Unter der Projektmappe wird im **Projektmappen-Explorer** ein Projekt mit dem Namen „QuickDate“ angezeigt. Zu diesem Zeitpunkt enthält das Projekt nur eine Datei mit dem Namen *App.config*.

   > [!NOTE]
   > Wenn die Vorlage **Leeres Projekt (.NET Framework)** nicht angezeigt wird, müssen Sie die Visual Studio-Workload **.NET-Desktopentwicklung** installieren. Visual Studio verwendet die workloadbasierte Installation, damit nur die Komponenten installiert werden, die Sie für Ihre Art von Entwicklung benötigen.
   >
   >Eine einfache Möglichkeit, eine neue Workload beim Erstellen eines neuen Projekts zu installieren, besteht darin, auf den Link **Weitere Tools und Features installieren** unter dem Text **Not finding what you're looking for?** (Sie finden nicht, wonach Sie suchen?) zu klicken. Wählen Sie nach dem Starten des Visual Studio-Installers die Workload **.NET-Desktopentwicklung** aus, und klicken Sie anschließend auf **Ändern**.
   >
   > ![Öffnen des Links „Visual Studio-Installer“](media/vs-2019/tutorial-projects-open-installer.png "Der Link „Visual Studio-Installer öffnen“ im Dialogfeld „Neues Projekt erstellen“ in Visual Studio.")

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Hinzufügen eines Elements zum Projekt

Ihnen liegt ein leeres Projekt vor. Fügen Sie eine Codedatei hinzu.

1. Klicken Sie im Kontextmenü (Rechtsklick) des Projekts **QuickDate** im **Projektmappen-Explorer** auf **Hinzufügen**  >  **Neues Element**.

   Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

1. Erweitern Sie **Visual C#-Elemente**, und wählen Sie anschließend **Code** aus. Wählen Sie im mittleren Bereich die Elementvorlage **Klasse** aus. Geben Sie der Klasse den Namen **Calendar**, und klicken Sie anschließend auf die Schaltfläche **Hinzufügen**.

   Dem Projekt wird eine Datei mit dem Namen *Calendar.cs* hinzugefügt. Die Erweiterung *.cs* wird allen C#-Codedateien am Ende hinzugefügt. Die Datei wird im **Projektmappen-Explorer** in der visuellen Projekthierarchie angezeigt, und ihre Inhalte werden im Editor geöffnet.

1. Ersetzen Sie den Inhalt der Datei *Calendar.cs* durch den folgenden Code:

   ```csharp
   using System;

   namespace QuickDate
   {
       internal class Calendar
       {
           static void Main(string[] args)
           {
               DateTime now = GetCurrentDate();
               Console.WriteLine($"Today's date is {now}");
               Console.ReadLine();
           }

           internal static DateTime GetCurrentDate()
           {
               return DateTime.Now.Date;
           }
       }
   }
   ```

   Sie müssen die Funktionsweise des Codes nicht verstehen, aber falls gewünscht können Sie das Programm ausführen, indem Sie **STRG**+**F5** drücken. Dann sehen Sie, dass das Datum des heutigen Tages im Konsolenfenster (oder in der Standardausgabe) ausgegeben wird.

## <a name="add-a-second-project"></a>Hinzufügen eines zweiten Projekts

Häufig enthalten Projektmappen mehrere Projekte, die aufeinander verweisen. Bei einigen Projekten in der Projektmappe handelt es sich möglicherweise um Klassenbibliotheken oder einige ausführbare Anwendungen, und bei anderen handelt es sich möglicherweise um Komponententestprojekte oder Websites.

Fügen Sie Ihrer Projektmappe einen Komponententest hinzu. Beginnen Sie diesmal mit einer Projektvorlage, damit Sie dem Projekt keine zusätzliche Codedatei hinzufügen müssen.

1. Klicken Sie im Kontextmenü (Rechtsklick) der **Projektmappe „QuickSolution“** im **Projektmappen-Explorer** auf **Hinzufügen**  >  **Neues Projekt**.

::: moniker range="vs-2017"

2. Erweitern Sie im linken Bereich **Visual C#** , und wählen Sie die Kategorie **Test** aus. Wählen Sie im mittleren Bereich die Projektvorlage **MSTest Test Project (.NET Core)** (MSTest-Testprojekt (.NET Core)) aus. Geben Sie dem Projekt den Namen **QuickTest**, und klicken Sie anschließend auf **OK**.

   Daraufhin wird dem **Projektmappen-Explorer** ein zweites Projekt hinzugefügt, und im Editor wird eine Datei mit dem Namen *UnitTest1.cs* geöffnet.

   ![Projektmappen-Explorer von Visual Studio mit zwei Projekten](media/tutorial-projects-solution-explorer.png "Projektmappen-Explorer mit zwei Projekten in Visual Studio 2017.")

::: moniker-end

::: moniker range=">=vs-2019"

2. Geben Sie im Dialogfeld **Neues Projekt hinzufügen** oben in das Suchfeld den Text **Komponententest** ein, und klicken Sie dann unter **Sprache** auf **C#**.

3. Wählen Sie die Projektvorlage **MSTest Test Project (.NET Core)** (MSTest-Testprojekt (.NET Core)), und klicken Sie dann auf **Weiter**.

4. Geben Sie dem Projekt den Namen **QuickTest**, und klicken Sie anschließend auf **Erstellen**.

   Daraufhin wird dem **Projektmappen-Explorer** ein zweites Projekt hinzugefügt, und im Editor wird eine Datei mit dem Namen *UnitTest1.cs* geöffnet.

   ![Projektmappen-Explorer von Visual Studio mit zwei Projekten](media/vs-2019/tutorial-projects-solution-explorer.png "Projektmappen-Explorer mit zwei Projekten in Visual Studio.")

::: moniker-end

## <a name="add-a-project-reference"></a>Hinzufügen eines Projektverweises

Jetzt soll das neue Komponententestprojekt verwendet werden, um die Methode im Projekt **QuickDate** zu testen. Aus diesem Grund müssen Sie einen Verweis auf das Projekt hinzufügen. Dadurch entsteht eine *Buildabhängigkeit* zwischen den beiden Projekten, d.h., **QuickDate** wird beim Erstellen der Projektmappe vor **QuickTest** erstellt.

::: moniker range="vs-2017"

1. Klicken Sie im **QuickTest**-Projekt auf den Knoten **Abhängigkeiten**, und wählen Sie dann im Kontextmenü (Rechtsklick) **Verweis hinzufügen** aus.

   Das Dialogfeld **Verweis-Manager** wird geöffnet.

1. Erweitern Sie im linken Bereich **Projekte**, und wählen Sie **Projektmappe** aus. Aktivieren Sie im mittleren Bereich das Kontrollkästchen neben **QuickDate**, und klicken Sie dann auf **OK**.

   Dem **QuickDate**-Projekt wird ein Verweis hinzugefügt.

   ![Screenshot: Projektmappen-Explorer mit Projektverweis in Visual Studio](media/vs-2019/tutorial-projects-solution-explorer-reference.png "Screenshot: Projektmappen-Explorer mit Projektverweis in Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

1. Klicken Sie im **QuickTest**-Projekt auf den Knoten **Abhängigkeiten**, und wählen Sie dann im Kontextmenü (Rechtsklick) **Projektverweis hinzufügen** aus.

   Das Dialogfeld **Verweis-Manager** wird geöffnet.

1. Erweitern Sie im linken Bereich **Projekte**, und wählen Sie dann **Projektmappe** aus. Aktivieren Sie im mittleren Bereich das Kontrollkästchen neben **QuickDate**, und klicken Sie dann auf **OK**.

   Dem **QuickDate**-Projekt wird ein Verweis hinzugefügt.

   ![Screenshot: Projektmappen-Explorer mit Projektverweis in Visual Studio 2019](media/vs-2019/tutorial-projects-solution-explorer-reference.png)

::: moniker-end

## <a name="add-test-code"></a>Hinzufügen von Testcode

1. Fügen Sie jetzt Testcode zur C#-Testcodedatei hinzu. Ersetzen Sie den Inhalt von *UnitTest1.cs* durch den folgenden Code:

   ```csharp
   using System;
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace QuickTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestGetCurrentDate()
           {
               Assert.AreEqual(DateTime.Now.Date, QuickDate.Calendar.GetCurrentDate());
           }
       }
   }
   ```

   Unter einigen Teilen des Codes werden rote Wellenlinien angezeigt. Sie können diesen Fehler beheben, indem Sie das Testprojekt als [Friend-Assembly](/dotnet/standard/assembly/friend-assemblies) für das **QuickDate**-Projekt festlegen.

1. Öffnen Sie im **QuickDate**-Projekt die Datei *Calendar.cs*, falls diese noch nicht geöffnet ist. Fügen Sie oben in der Datei die folgende [Using-Anweisung](/dotnet/csharp/language-reference/keywords/using-statement) und das <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>-Attribut hinzu, um den Fehler im Testprojekt zu beheben.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   Die Codedatei sollte wie folgt aussehen:

   ![CSharp-Code](media/tutorial-projects-cs-code.png "Der Codeausschnitt aus dem Abschnitt „Hinzufügen von Testcode“ in diesem Artikel.")

## <a name="project-properties"></a>Projekteigenschaften

In der Zeile in der *Calendar.cs*-Datei mit dem Attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> wird auf den Assemblynamen (Dateinamen) des Projekts **QuickTest** verwiesen. Der Assemblyname stimmt nicht immer mit dem Projektnamen überein. Öffnen Sie die Projekteigenschaften, um den Assemblynamen eines Projekts zu suchen.

1. Wählen Sie im **Projektmappen-Explorer** das **QuickTest**-Projekt aus. Wählen Sie im Kontextmenü (Rechtsklick) **Eigenschaften** aus, oder drücken Sie **ALT**+**EINGABETASTE**.

   Die *Eigenschaftenseiten* für das Projekt werden auf der Registerkarte **Anwendung** geöffnet. Die Eigenschaftenseiten enthalten verschiedene Einstellungen für das Projekt. Beachten Sie, dass der Assemblyname des **QuickTest**-Projekts tatsächlich „QuickTest“ lautet. Falls gewünscht können Sie ihn an dieser Stelle ändern. Wenn Sie das Testprojekt erstellen, ändert sich der Name der entstandenen Binärdatei von *QuickTest.dll* in den von Ihnen ausgewählten Namen.

   ![Projekteigenschaften](media/tutorial-projects-netcore-properties.png "Dialogfeld „Projekteigenschaften“ in Visual Studio.")

1. Sehen Sie sich einige der anderen Registerkarten der Eigenschaftenseite des Projekts an, z. B. **Build** und **Debuggen**. Diese Registerkarten sind bei den verschiedenen Projekttypen unterschiedlich.

## <a name="next-steps"></a>Nächste Schritte

::: moniker range="vs-2017"

Wenn Sie testen möchten, ob der Komponententest funktioniert, klicken Sie in der Menüleiste auf **Testen** > **Ausführen** > **Alle Tests**. Ein Fenster mit dem Namen **Test-Explorer** wird geöffnet, und der **TestGetCurrentDate**-Test sollte erfolgreich sein.

::: moniker-end

::: moniker range="vs-2019"

Wenn Sie überprüfen möchten, ob Ihr Komponententest funktioniert, klicken Sie in der Menüleiste auf **Testen** > **Alle Tests ausführen**. Ein Fenster mit dem Namen **Test-Explorer** wird geöffnet, und der **TestGetCurrentDate**-Test sollte erfolgreich sein.

::: moniker-end

![Test-Explorer in Visual Studio, der erfolgreiche Tests anzeigt](media/tutorial-projects-test-explorer.png "Test-Explorer in Visual Studio, der einen erfolgreichen Test anzeigt.")

::: moniker range="vs-2017"

> [!TIP]
> Wenn Sich der **Test-Explorer** nicht automatisch öffnet, können Sie ihn über die Menüleiste öffnen, indem Sie auf **Test** > **Windows** > **Test-Explorer** klicken.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Wenn der **Test-Explorer** nicht automatisch geöffnet wird, können Sie ihn über die Menüleiste öffnen, indem Sie auf **Test** > **Test-Explorer** klicken.

::: moniker-end

## <a name="see-also"></a>Weitere Informationen

- [Arbeiten mit Projekten und Projektmappen](../ide/creating-solutions-and-projects.md)
- [Verwalten von Projekt- und Projektmappeneigenschaften](../ide/managing-project-and-solution-properties.md)
- [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)
- [Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Übersicht über die Visual Studio-IDE](../get-started/visual-studio-ide.md)
