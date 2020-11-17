---
title: Verwalten von Projekt- und Projektmappeneigenschaften
description: In diesem Artikel erfahren Sie, wie Sie die Eigenschaften von Projekten und Projektmappen in Visual Studio für Mac verwalten können.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 0c3277df3be22658acf85a4f0607ed9ad0308b5c
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94492996"
---
# <a name="managing-project-and-solution-properties"></a>Verwalten von Projekt- und Projektmappeneigenschaften

## <a name="project-options"></a>Projektoptionen

Die Projektoptionen sind für jedes Projekt spezifisch und beeinflussen, wie das Projekt geschrieben, erstellt und ausgeführt wird. Im Gegensatz zu den Einstellungen von Visual Studio für Mac, die benutzerspezifisch sind, werden die Projektoptionen in der Projektdatei (.csproj) gespeichert, damit andere Entwickler das Projekt ordnungsgemäß erstellen und ausführen können. Mit spezifischen Projektoptionen können viele Entwickler am gleichen Dokument arbeiten, ohne die Formatierung der Datei zu beeinträchtigen.

Doppelklicken Sie zum Öffnen von Projektoptionen in Visual Studio für Mac auf den Projektnamen, oder machen Sie einen Doppelklick darauf, um das Kontextmenü zu öffnen. Wählen Sie anschließend **Optionen** aus:

![Optionen im Kontextmenü](media/projects-and-solutions-image2.png)

Zu den bearbeitbaren Optionen gehören Optionen zum Erstellen, Ausführen und Festlegen von Quellcode und Optionen zur Versionskontrolle.

Projektoptionen sind in fünf verschiedene Kategorien unterteilt:

* **Allgemein**: Projektinformationen wie zum Beispiel Name, Beschreibung und Standardnamespace werden hier festgelegt, ebenso wie der Speicherort des Projekts.
* **Build:** Diese Einstellung dient zum Festlegen oder Ändern von PCL-Profilen für portierbare Klassenbibliotheken. Es können auch benutzerdefinierte Befehle, Konfigurationen und Compileroptionen festgelegt werden. Der Ausgabepfad und der Assemblyname können hier ebenfalls festgelegt werden.
* **Ausführung:** Mit dieser Option können Sie benutzerdefinierte Ausführungskonfigurationen auf Projektbasis erstellen.
* **Quellcode:** Diese Einstellung steuert die Formatierung von vielen unterschiedlichen Dateitypen und Namenskonventionen. Hier können Sie auch Benennungsrichtlinien und Standard-Headerstile festlegen.
* **Versionskontrolle:** Hier finden Sie Optionen zum Festlegen des Stils von Commitnachrichten, wenn Sie die Versionskontrolle für Ihr Projekt aktiviert haben.

Jedes Projekt kann abhängig von der Plattform bestimmte Projektoptionen enthalten. Beispielsweise verfügt ein Xamarin.Android-Projekt wie das in der folgenden Abbildung dargestellte über Optionen, die sich auf den Android Build beziehen (z.B. Linkeroptionen) und auf die Anwendung (z.B. Berechtigungen):

![Optionen für Android-Projekte](media/projects-and-solutions-image5.png)

Xamarin.iOS enthält Optionen, die sich auf die Bundlesignierung beziehen, zum Beispiel das zur Verwendung erforderliche Bereitstellungsprofil:

![iOS-Projektoptionen](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Projektmappenoptionen

Projektmappenoptionen sind wie Projektoptionen, sie decken jedoch den Bereich ganzer Projektmappen ab. Sie stellen Möglichkeiten zum Festlegen von Autorinformationen, Erstellen von Einstellungen sowie Formatierungsstile für Code und Versionskontrolle bereit. Außerdem ermöglichen Sie das Zuweisen des Startprojekts zur Projektmappe.  Auf das Dialogfeld „Projektmappenoptionen“ kann über das Menüelement **Projekt > Projektmappenoptionen**, über das Kontextmenüelement **Optionen** im Projektmappenfenster der Projektmappe oder durch Doppelklicken auf die Projektmappe im Projektmappenfenster zugegriffen werden:

![Projektmappenoptionen](media/projects-and-solutions-image7.png)

## <a name="see-also"></a>Siehe auch

* [Verwalten von Projekt- und Projektmappeneigenschaften (Visual Studio unter Windows)](/visualstudio/ide/managing-project-and-solution-properties)