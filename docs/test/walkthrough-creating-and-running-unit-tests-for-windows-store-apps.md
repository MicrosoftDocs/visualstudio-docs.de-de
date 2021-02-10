---
title: Erstellen und Ausführen von Komponententests für UWP-Apps
description: Erfahren Sie, wie Visual Studio Komponententests für UWP-Apps (Universelle Windows-Plattform) unterstützt. Visual Studio stellt Komponententestvorlagen für C#, Visual Basic und C++ bereit.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: mikejo
manager: jmartens
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 52b7712c3e2e283dc92da3b920eccdcb0c312cd4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948035"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für UWP-Apps

Visual Studio unterstützt Komponententests für UWP-Apps (Universelle Windows-Plattform). Visual Studio stellt Komponententest-Projektvorlagen für C#, Visual Basic und C++ bereit.

> [!TIP]
> Weitere Informationen zum Entwickeln von UWP-Apps finden Sie unter [Erste Schritte mit UWP-Apps](/windows/uwp/get-started/).

Die folgenden Verfahren beschreiben die Schritte zum Erstellen, Ausführen und Debuggen von Komponententests für eine UWP-App.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>Erstellen eines Komponententestprojekts für eine UWP-App

::: moniker range=">=vs-2019"

1. Öffnen Sie Visual Studio. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

2. Geben Sie auf der Seite **Neues Projekt erstellen** den Text **Komponententest** in das Suchfeld ein.

   In der Liste der Vorlagenfilter werden diejenigen Vorlagen angezeigt, die sich für Komponententests eignen.

3. Wählen Sie die Vorlage **Komponententest-App (Universelle Windows-App)** für C# oder Visual Basic aus, und klicken Sie dann auf **Weiter**.

   ![Erstellen einer neuen UWP-Komponententest-App in Visual Studio](media/vs-2019/new-uwp-unit-test-app.png)

4. Ändern Sie optional den Namen und den Speicherort für das Projekt oder das Projektmappe, und klicken Sie dann auf **Erstellen**.

5. Ändern Sie optional die Standardwerte für die Ziel- und die Mindestversion der Plattform, und klicken Sie dann auf **OK**.

Wenn Sie diese Schritte ausgeführt haben, wird das Komponententestprojekt erstellt und im Projektmappen-Explorer angezeigt.

![UWP-Komponententestprojekt im Projektmappen-Explorer](media/vs-2019/uwp-unit-test-project-solution-explorer.png)

::: moniker-end

::: moniker range="vs-2017"

1. Wählen Sie im Menü **Datei** die Option **Neues Projekt** aus.

   Daraufhin wird das Dialogfeld **Neues Projekt** angezeigt.

2. Wählen Sie unter „Vorlagen“ die Programmiersprache aus, in der Sie den Komponententest erstellen möchten, und wählen Sie dann die zugeordnete Windows Universal-Komponententestbibliothek aus. Wählen Sie beispielsweise **Visual C#** aus, und wählen Sie dann **Windows Universal** gefolgt von **Komponententestbibliothek (Universal Windows)** aus.

3. (Optional) Geben Sie im Textfeld **Name** den Namen ein, den Sie für das Projekt verwenden möchten.

4. (Optional) Ändern Sie den Pfad, unter dem Sie das Projekt erstellen möchten, indem Sie ihn im Textfeld **Speicherort** eingeben, oder klicken Sie auf die Schaltfläche **Durchsuchen** .

5. (Optional) Geben Sie im Textfeld **Projektmappe** den Namen ein, den Sie für die Projektmappe verwenden möchten.

6. Vergewissern Sie sich, dass die Option **Projektmappenverzeichnis erstellen** ausgewählt ist, und klicken Sie auf **OK** .

   ![Angepasste Komponententestbibliothek](../test/media/unit_test_win8_1.png)

   Der **Projektmappen-Explorer** wird mit dem UWP-Komponententestprojekt ausgefüllt, und der Code-Editor zeigt den Standardkomponententest „UnitTest1“ an.

   ![Neues angepasstes Komponententestprojekt.](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

::: moniker-end

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Bearbeiten der UWP-Anwendungsmanifestdatei für das Komponententestprojekt

1. Klicken Sie im **Projektmappen-Explorer** erst mit der rechten Maustaste auf die Datei *Package.appxmanifest* und anschließend mit der Linken auf **Öffnen**.

2. Wählen Sie im **Manifest-Designer** die Registerkarte **Funktionen** aus.

3. Wählen Sie in der **Funktionen**-Liste die Funktionen, über die die getestete Komponente verfügen soll, und den für diese Tests erforderlichen Code aus. Aktivieren Sie beispielsweise das Kontrollkästchen **Internet** , wenn die Komponente, die getestet werden soll, und der Code Zugriff auf das Internet benötigen.

   > [!NOTE]
   > Die ausgewählten Funktionen sollten nur Funktionen enthalten, die für das ordnungsgemäße Ausführen des Komponententests erforderlich sind.

   ![Komponententestmanifest](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>Schreiben von Code für den Komponententest einer UWP-App

Bearbeiten Sie den Komponententest im Code-Editor, und fügen Sie die Asserts und die Logik für den Test hinzu.

## <a name="run-unit-tests"></a>Komponententests ausführen

So erstellen Sie die Projektmappe und führen den Komponententest mit dem Komponententest-Explorer aus:

1. Wählen Sie im Menü **Test** den Punkt **Windows** und dann **Test-Explorer** aus.

2. Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen** aus.

   Der Komponententest wird jetzt im Test-Explorer angezeigt.

   > [!NOTE]
   > Sie müssen die Projektmappe erstellen, um die Liste der Komponententests im Komponententest-Explorer zu aktualisieren.

3. Wählen Sie im **Test-Explorer** den Komponententest aus, den Sie erstellt haben.

4. Wählen Sie **Alle ausführen** aus.

   ![Komponententest-Explorer &#45; Komponententest ausführen](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

   > [!TIP]
   > Sie können einen oder mehrere der im Komponententest-Explorer aufgeführten Komponententests auswählen und per Rechtsklick **Ausgewählte Tests ausführen** auswählen.
   >
   > Außerdem können Sie die Optionen **Ausgewählte Tests debuggen**, **Test öffnen** und **Eigenschaften** auswählen.
   >
   > ![Komponententest-Explorer – Kontextmenü für Komponententest](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

   Der Komponententest läuft. Nach Abschluss zeigt der Test-Explorer den Teststatus und die verstrichene Zeit an und stellt einen Link zur Quelle bereit.

   ![Komponententest-Explorer &#45; Komponententest abgeschlossen](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Weitere Informationen

- [Testen von UWP-Apps mit Visual Studio](../test/unit-test-your-code.md)
- [Erstellen und Testen einer UWP-App](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)
