---
title: Anpassen des SharePoint-Lösungs Pakets mithilfe von MSBuild-Zielen
titleSuffix: ''
description: Anpassen, wie Visual Studio SharePoint-projektmappenpaketdateien (. wsp) erstellt, indem MSBuild-Ziele an einer Eingabeaufforderung verwendet werden.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b4d181a6310e1ff924f060e906093d3c28d60ede
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959921"
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>Vorgehensweise: Anpassen eines SharePoint-Lösungs Pakets mithilfe von MSBuild-Zielen
  Mithilfe von MSBuild-Zielen an einer Eingabeaufforderung können Sie anpassen, wie Visual Studio SharePoint-Paketdateien (*. wsp*) erstellt. Beispielsweise können Sie die MSBuild-Eigenschaften anpassen, um das Verpackungs zwischen Verzeichnis und die MSBuild-Elementgruppen zu ändern, die die aufgelisteten Dateien angeben.

## <a name="customize-and-run-msbuild-targets"></a>Anpassen und Ausführen von MSBuild-Zielen
 Wenn Sie die Ziele "beforelayout" und "AfterLayout" anpassen, können Sie Aufgaben vor dem Paket Layout ausführen, z. b. das Hinzufügen, entfernen oder Ändern von Dateien, die verpackt werden.

#### <a name="to-customize-the-beforelayout-target"></a>So passen Sie das Ziel "beforelayout" an

1. Öffnen Sie einen Editor, z. b. Notepad, und fügen Sie dann den folgenden Code hinzu.

   ```xml
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Target Name="BeforeLayout">
       <Message Importance="high" Text="In the BeforeLayout Target"></Message>
     </Target>
   </Project>
   ```

    In diesem Beispiel wird vor dem Verpacken dieses Ziels eine Meldung angezeigt.

2. Benennen Sie die Datei " **CustomLayout. SharePoint. targets**", und speichern Sie Sie im Ordner für das SharePoint-Projekt.

3. Öffnen Sie das Projekt, öffnen Sie das zugehörige Kontextmenü, und wählen Sie dann **Projekt entladen** aus.

4. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt, und wählen Sie dann **Bearbeiten** *\<ProjectName> . vbproj* oder **Bearbeiten** *\<ProjectName> . csproj* aus.

5. `Import`Fügen Sie nach der Zeile am Ende der Projektdatei die folgende Zeile hinzu.

   ```xml
   <Import Project="CustomLayout.SharePoint.targets" />
   ```

6. Speichere und schließe die Projektdatei.

7. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt, und wählen Sie dann **Projekt erneut laden** aus.

   Wenn Sie das Projekt veröffentlichen, wird die Meldung vor dem Beginn der Paket Erstellung in der Ausgabe angezeigt.

#### <a name="to-customize-the-afterlayout-target"></a>So passen Sie das AfterLayout-Ziel an

1. Wählen Sie in der Menüleiste **Datei Datei**  >  **Öffnen** aus  >  .

2. Navigieren Sie im Dialogfeld **Datei öffnen** zum Projektordner, wählen Sie die Datei CustomLayout. Target aus, und klicken Sie dann auf die Schaltfläche **Öffnen** .

3. Fügen Sie direkt vor dem- `</Project>` Tag den folgenden Code hinzu:

   ```xml
   <Target Name="AfterLayout">
     <Message Importance="high" Text="In the AfterLayout Target"></Message>
   </Target>
   ```

    In diesem Beispiel wird eine Meldung angezeigt, nachdem dieses Ziel verpackt wurde.

4. Speichern und schließen Sie die Zieldatei.

5. Starten Sie Visual Studio neu, und öffnen Sie dann das Projekt.

   Wenn Sie das Projekt veröffentlichen, wird die Meldung "beforelayout" vor Beginn der Paket Erstellung angezeigt, und die AfterLayout-Meldung wird nach Abschluss der Paket Erstellung angezeigt.

## <a name="see-also"></a>Weitere Informationen
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
