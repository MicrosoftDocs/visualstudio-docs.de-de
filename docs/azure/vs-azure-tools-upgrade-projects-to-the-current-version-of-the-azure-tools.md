---
title: Aktualisieren von Projekten auf die aktuelle Version der Azure-Tools
description: Erfahren Sie, wie Sie ein Upgrade von Projekten auf die aktuelle Version von Azure Tools für Visual Studio durchführen.
author: ghogen
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: fce77f6417a14c204df883efd2f64655fa79b432
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901907"
---
# <a name="how-to-upgrade-projects-to-the-current-version-of-the-azure-tools-for-visual-studio"></a>Upgrade von Projekten auf die aktuelle Version von Azure Tools für Visual Studio
## <a name="overview"></a>Übersicht
Nach der Installation der aktuellen Version von Azure Tools (bzw. einer früheren Version ab 1.6) werden alle Projekte, die mit einer Version von Azure Tools vor Version 1.6 (November 2011) erstellt wurden, beim Öffnen automatisch aktualisiert. Wenn Sie Projekte mit Version 1.6 (November 2011) der Tools erstellt haben und diese Version weiterhin installiert ist, können Sie die betreffenden Projekte in der älteren Version öffnen und später entscheiden, ob sie aktualisiert werden sollen.

## <a name="how-your-project-changes-when-you-upgrade-it"></a>Beim Upgrade durchgeführte Projektänderungen
Wenn ein Projekt automatisch aktualisiert oder angegeben wird, dass es aktualisiert werden soll, wird das Projekt so geändert, dass es mit den aktuellen Versionen bestimmter Assemblys fehlerfrei funktioniert. Einige der in diesem Abschnitt beschriebenen Eigenschaften werden ebenfalls geändert. Wenn Ihr Projekt andere Änderungen erfordert, um Kompatibilität mit der neueren Version der Tools zu gewährleisten, müssen Sie diese Änderungen manuell vornehmen.

* Die Datei „web.config“ für Webrollen und die Datei „app.config“ für Workerrollen werden aktualisiert, damit sie auf die neuere Version von „Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener.dll“ verweisen.
* Die Assemblys "Microsoft.WindowsAzure.StorageClient.dll", "Microsoft.WindowsAzure.Diagnostics.dll" und "Microsoft.WindowsAzure.ServiceRuntime.dll" werden auf die neuen Versionen aktualisiert.
* Veröffentlichungsprofile, die in der Azure-Projektdatei (CCPROJ-Format) gespeichert wurden, werden in eine separate Datei mit der AZUREPUBXML-Erweiterung im Unterverzeichnis **Publish** verschoben.
* Einige Eigenschaften im Veröffentlichungsprofil werden aktualisiert, um neue und geänderte Funktionen unterstützen. **AllowUpgrade** wird durch **DeploymentReplacementMethod** ersetzt, da bereitgestellte Cloud-Dienste simultan oder inkrementell aktualisiert werden können.
* Die Eigenschaft **UseIISExpressByDefault** wurde hinzugefügt und auf "False" festgelegt, sodass der Webserver für das Debuggen nicht automatisch von Internetinformationsdienste (IIS) in IIS Express geändert wird. IIS Express ist der Standardwebserver für mit den neueren Versionen der Tools erstellte Projekte.
* Wenn der Azure Cache-Dienst in einer oder mehreren Rollen des Projekts gehostet wird, werden einige Eigenschaften in der Dienstkonfiguration (CSCFG-Datei) und in der Dienstdefinition (CSDEF-Datei) geändert, wenn ein Projekt aktualisiert wird. Wenn vom Projekt das NuGet-Paket für den Azure Cache-Dienst verwendet wird, wird das Projekt auf die aktuelle Version des Pakets aktualisiert. Öffnen Sie die Datei "web.config", und prüfen Sie, ob die Clientkonfiguration während des Upgradevorgangs ordnungsgemäß beibehalten wurde. Wenn Sie die Verweise auf Azure Cache-Clientassemblys ohne das NuGet-Paket hinzugefügt haben, werden diese Assemblys nicht aktualisiert. Diese Verweise müssen manuell auf die neuen Versionen aktualisiert werden.

> [!IMPORTANT]
> Bei F#-Projekten müssen Sie die Verweise auf Assemblys von Azure manuell aktualisieren, sodass diese auf die Assemblys der neueren Versionen verweisen.
>
>

### <a name="how-to-upgrade-an-azure-project-to-the-current-release"></a>So aktualisieren Sie ein Azure-Projekt auf die aktuelle Version
1. Installieren Sie die aktuelle Version von Azure Tools in der Installation von Visual Studio, die Sie für das aktualisierte Projekt verwenden möchten. Öffnen Sie dann das Projekt, das Sie aktualisieren möchten. Wenn das Projekt mit einer Azure Tools-Version vor 1.6 (November 2011) erstellt wurde, wird es automatisch auf die aktuelle Version aktualisiert. Wenn das Projekt mit der November 2011-Version erstellt wurde und diese Version noch installiert ist, wird das Projekt in dieser Version geöffnet.
2. Öffnen Sie im Projektmappen-Explorer das Kontextmenü für den Projektknoten, wählen Sie **Eigenschaften** aus, und wählen Sie dann im angezeigten Dialogfeld die Registerkarte **Anwendung** aus.

    Auf der Registerkarte **Anwendung** wird die Tools-Version angezeigt, die dem Projekt zugeordnet ist. Wenn die aktuelle Version von Azure Tools angezeigt wird, wurde das Projekt bereits aktualisiert. Wenn Sie eine neuere Version der Tools installiert haben, als auf der Registerkarte angezeigt wird, wird die Schaltfläche **Aktualisieren** angezeigt.
3. Klicken Sie auf die Schaltfläche **Aktualisieren**, um ein Projekt auf die aktuelle Version der Tools zu aktualisieren.
4. Erstellen Sie das Projekt, und beheben Sie Fehler, die sich aus Änderungen an der API ergeben können. Informationen dazu, wie Sie den Code zur Anpassung an die neue Version ändern, finden Sie in der Dokumentation zur jeweiligen API.
