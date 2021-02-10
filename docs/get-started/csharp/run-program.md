---
title: Ausführen eines Programms (C#)
description: In diesem Artikel finden Sie eine Anleitung für Einsteiger zum Ausführen eines C#-Programms in Visual Studio.
ms.custom: get-started
ms.date: 10/16/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bbebcec3f5b2de01bcbfa7839f68e6f7a3e2cc64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922839"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>Vorgehensweise: Ausführen eines C#-Programms in Visual Studio

Die Vorgehensweise zum Ausführen eines Programms hängt vom Ausgangspunkt ab, also um welche Art Programm, App oder Dienst es sich handelt, und davon, ob Sie es mit einem Debugger ausführen möchten oder nicht. Die einfachste Möglichkeit,um ein in Visual Studio geöffnetes Projekt zu erstellen und auszuführen, ist das Drücken von **STRG**+**F5** (**Ohne Debuggen starten**) oder von **F5** (**Mit Debugging starten**), oder Sie drücken in der Hauptsymbolleiste in Visual Studio auf den grünen Pfeil (**Schaltfläche „Start“** ).

![Screenshot der Schaltfläche „Start“](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>Projekt als Ausgangspunkt

C#-Projekte (Dateiendung *.csproj*) können ausgeführt werden, wenn es sich um ein ausführbares Programm handelt. Wenn ein Projekt eine C#-Datei mit einer `Main`-Methode enthält und die Ausgabe eine ausführbare Datei (EXE) ist, wird es sehr wahrscheinlich ausgeführt, wenn es erfolgreich erstellt wurde.

Wenn Sie bereits über einen Code für Ihr Programm in einem Projekt in Visual Studio verfügen, öffnen Sie das Projekt. Doppelklicken oder tippen Sie im Datei-Explorer von Windows oder in Visual Studio auf *.csproj*, um das Projekt zu öffnen, klicken Sie dann auf die Option **Projekt öffnen**, suchen Sie nach der Projektdatei ( *.csproj*), und wählen Sie sie aus.

Sobald das Projekt in Visual Studio geladen wurde, drücken Sie **STRG**+**F5** (**Ohne Debuggen starten**), oder verwenden Sie den grünen Pfeil (**Schaltfläche „Start“** ) in der Symbolleiste in Visual Studio, um das Programm auszuführen.  Wenn es mehrere Projekte gibt, muss das Projekt, das die `Main`-Methode enthält, als Startprojekt festgelegt werden. Klicken Sie mit der rechten Maustaste auf den Projektknoten, und klicken Sie dann auf **Als Startprojekt festlegen**, um ein Projekt als Startprojekt festzulegen.

![Festlegen eines Projekts als Startprojekt](media/set-as-startup-project.png)

Visual Studio versucht, Ihr Projekt zu erstellen und auszuführen.  Wenn es zu Buildfehlern kommt, werden die Buildausgabe im Fenster **Ausgabe** und die Fehler im Fenster **Fehlerliste** angezeigt.

Wenn das Projekt erfolgreich erstellt werden konnte, wird die App entsprechend des Projekttyps ausgeführt. Konsolen-Apps werden beispielsweise in einem Terminalfenster ausgeführt, Windows-Desktop-Apps starten in einem neuen Fenster, Web-Apps starten im Browser (gehostet von IIS Express).

## <a name="starting-from-code"></a>Code als Ausgangspunkt

Wenn Ihr Ausgangspunkt eine Codeliste, Codedatei oder eine kleine Anzahl Dateien ist, sollten Sie sich zunächst vergewissern, dass der Code, den Sie ausführen möchten, aus einer vertrauenswürdigen Quelle stammt und dass es sich um ein ausführbares Programm handelt. Wenn der Code eine `Main`-Methode enthält, ist es sehr wahrscheinlich, dass es sich um ein ausführbares Programm handelt. Hierfür können Sie die Vorlage für Konsolen-Apps verwenden, um ein Projekt in Visual Studio zu erstellen, mit dem Sie arbeiten können.

### <a name="code-listing-for-a-single-file"></a>Codelisten für eine einzelne Datei

Starten Sie Visual Studio, öffnen Sie ein leeres C#-Konsolenprojekt, wählen Sie den gesamten Code in der CS-Datei aus, der bereits im Projekt enthalten ist, und löschen Sie ihn. Fügen Sie dann Ihren Code in die CS-Datei ein. Überschreiben oder löschen Sie den vorhandenen Code beim Einfügen Ihres eigenen Codes. Benennen Sie die Datei mit einem für den ursprünglichen Code passenden Namen.

### <a name="code-listings-for-a-few-files"></a>Codelisten für eine kleine Anzahl Dateien

Starten Sie Visual Studio, öffnen Sie ein leeres C#-Konsolenprojekt, wählen Sie den gesamten Code in der CS-Datei aus, der bereits im Projekt enthalten ist, und löschen Sie ihn. Fügen Sie dann die Inhalte der ersten Codedatei in die CS-Datei ein. Benennen Sie die Datei mit einem für den ursprünglichen Code passenden Namen. 

Eine zweite Datei können Sie erstellen, indem Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf den Projektknoten klicken, um das Kontextmenü für das Projekt zu öffnen, dann auf **Hinzufügen > Vorhandenes Element** klicken oder die Tastenkombination **UMSCHALT**+**ALT**+**A** verwenden, und dann die Codedateien auswählen.

### <a name="multiple-files-on-disk"></a>Mehrere Dateien auf einem Datenträger

1. Erstellen Sie ein neues Projekt mit entsprechendem Typ. Wenn Sie sich unsicher sind, verwenden Sie **C#-Konsolen-App**.

2. Klicken Sie mit der rechten Maustaste auf den Projektknoten, und klicken Sie dann auf **Hinzufügen** > **Vorhandenes Element**, um die Dateien auszuwählen und sie in Ihr Projekt zu importieren.  

### <a name="starting-from-a-folder"></a>Ordner als Ausgangspunkt

Wenn Sie mit einem Ordner mit vielen Dateien arbeiten, sollten Sie zuerst überprüfen, ob ein Projekt oder eine Projektmappe vorhanden sind.  Wenn das Programm mit Visual Studio erstellt wurde, sollte eine Projektdatei oder eine Projektmappendatei enthalten sein. Suchen Sie nach Dateien mit der Erweiterung *.csproj* oder der Erweiterung „.sln“, und doppelklicken Sie im Datei-Explorer von Windows auf eine solche Datei, um sie in Visual Studio zu öffnen. Weitere Informationen hierzu finden Sie im Abschnitt [Projekt als Ausgangspunkt](#starting-from-a-project).

Wenn Sie keine Projektdatei finden, z. B. wenn der Code in einer anderen Entwicklungsumgebung erstellt wurde, öffnen Sie mithilfe der **Ordner öffnen**-Methode in Visual Studio den Ordner auf oberster Ebene. Weitere Informationen finden Sie im Artikel [Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="starting-from-a-github-or-azure-devops-repo"></a>GitHub- oder Azure DevOps-Repository als Ausgangspunkt

Wenn sich der Code, den Sie ausführen möchten, in einem GitHub- oder einem Azure DevOps-Repository befindet, können Sie das Projekt mithilfe von Visual Studio direkt im Repository öffnen. Weitere Informationen finden Sie im Artikel [Tutorial: Öffnen eines Projekts von einem Repository aus](../tutorial-open-project-from-repo.md).

## <a name="run-the-program"></a>Ausführen des Programms

Klicken Sie in der Hauptsymbolleiste von Visual Studio auf den grünen Pfeil (**Schaltfläche „Start“** ), oder drücken Sie **F5** oder **STRG**+**F5**, um das Programm zu starten und auszuführen. Wenn Sie auf die **Schaltfläche „Start“** klicken, wird bei der Ausführung der Debugger verwendet.  Visual Studio versucht, Ihr Projekt zu erstellen und den Code auszuführen.  Wenn das möglich ist, verläuft alles ordnungsgemäß. Wenn Probleme auftreten, sollten Sie weiterlesen, um weitere Tipps für die erfolgreiche Erstellung Ihres Projekts zu erhalten.

## <a name="troubleshooting"></a>Problembehandlung

Möglicherweise enthält Ihr Code Fehler. Wenn er jedoch korrekt ist und lediglich Abhängigkeiten von anderen Assemblys oder NuGet-Paketen aufweist oder ursprünglich für eine andere .NET-Version geschrieben wurde, sollte er problemlos angepasst werden können.

### <a name="add-references"></a>Hinzufügen von Verweisen

Damit ein Projekt ordnungsgemäß erstellt werden kann, muss der Code fehlerfrei sein und korrekte Verweise auf Bibliotheken oder andere Abhängigkeiten aufweisen. Rote Wellenlinien unter Code zeigen Fehler an, die Sie sich ansehen können, bevor Sie den Code kompilieren und ausführen. Fehler werden auch in der **Fehlerliste** angezeigt. Wenn Sie Fehler entdecken, die mit nicht aufgelösten Namen zu tun haben, müssen Sie vermutlich einen Verweis und/oder eine Using-Direktive hinzufügen. Wenn der Code auf Assemblys oder NuGet-Pakete verweist, müssen Sie diese Verweise im Projekt hinzufügen.

Visual Studio unterstützt Sie bei der Identifizierung fehlender Verweise. Wenn ein Name nicht aufgelöst ist, wird im Editor ein Glühbirnensymbol angezeigt. Wenn Sie auf das Glühbirnensymbol klicken, werden Vorschläge angezeigt, wie Sie das Problem beheben können. Fehler könnten durch folgende Maßnahmen behoben werden:

- Hinzufügen einer Using-Direktive
- Hinzufügen eines Verweises auf eine Assembly
- Installieren eines NuGet-Pakets

#### <a name="missing-using-directive"></a>Fehlende Using-Direktive

Im folgenden Bildschirm könnten Sie beispielsweise zu Beginn der Codedatei `using System;` hinzufügen, um den nicht aufgelösten Namen `Console` aufzulösen:

![Screenshot des Glühbirnensymbols mit dem Vorschlag, eine Using-Direktive hinzuzufügen](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>Fehlender Assemblyverweis

.NET-Verweise können in Form von Assemblys oder NuGet-Paketen erfolgen. Wenn Quellcode vorhanden ist, stellt der Herausgeber oder Ersteller in der Regel die nötigen Informationen zur Verfügung, welche Assemblys erforderlich sind und für welche Pakete der Code Abhängigkeiten hat. Klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf den Knoten **Verweise**, klicken Sie dann auf **Verweis hinzufügen**, und suchen Sie nach der erforderlichen Assembly, um einem Projekt manuell einen Verweis hinzuzufügen.

![Screenshot des Menüs „Verweis hinzufügen“](media/add-reference.png)

Befolgen Sie die Anleitung in [Vorgehensweise: Hinzufügen und Entfernen von Verweisen mit dem Verweis-Manager](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md), um Assemblys zu finden und Verweise hinzuzufügen.

#### <a name="missing-nuget-package"></a>Fehlendes NuGet-Paket

Wenn Visual Studio erkennt, dass ein NuGet-Paket fehlt, wird ein Glühbirnensymbol angezeigt. Wenn Sie darauf klicken, wird die Option zum Installieren des Pakets angezeigt:

![Screenshot des Glühbirnensymbols mit der Option zum Installieren des Pakets](media/lightbulb-add-package.png)

Wenn das Problem dadurch nicht behoben werden kann und Visual Studio das Paket nicht finden kann, suchen Sie online nach ihm. Weitere Informationen finden Sie im Artikel [Schnellstart: Installieren und Verwenden eines Pakets in Visual Studio (nur Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio).

## <a name="use-the-right-version-of-net"></a>Verwenden der richtigen .NET-Version

Da die verschiedenen Versionen von .NET Framework eine gewisse Abwärtskompatibilität aufweisen, sollte für ein älteres Framework geschriebener Code in einem neuerem Framework dennoch ausgeführt werden können, ohne dass Änderungen vorgenommen werden müssen. Manchmal müssen Sie aber gezielt für ein bestimmtes Framework entwickeln. Möglicherweise müssen Sie eine bestimmte Version von .NET Framework oder .NET Core installieren, wenn die Version noch nicht installiert ist. Weitere Informationen finden Sie im Artikel [Ändern von Visual Studio durch Hinzufügen oder Entfernen von Arbeitsauslastungen und Komponenten](../../install/modify-visual-studio.md).

Weitere Informationen zum Ändern des Zielframeworks erhalten Sie unter [Auswählen einer Zielframeworkversion](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version). Weitere Informationen zum Troubleshooting finden Sie unter [Problembehandlung bei .NET Framework-Zielversionsfehlern](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie die Entwicklungsumgebung von Visual Studio näher kennenlernen möchten, lesen Sie sich den Artikel [Willkommen in der Visual Studio-IDE](../visual-studio-ide.md) durch.

## <a name="see-also"></a>Siehe auch

[Tutorial: Erstellen einer einfachen C#-Konsolen-App in Visual Studio](tutorial-console.md)
