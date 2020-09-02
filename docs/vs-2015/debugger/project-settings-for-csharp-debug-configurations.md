---
title: Projekteinstellungen für c#-Debugkonfigurationen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- debugging [J#], debugger settings
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
- debug configurations, J#
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f1ec1c18fe92409a72994e4544215da01325d209
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687516"
---
# <a name="project-settings-for--c-debug-configurations"></a>Projekteinstellungen für C#-Debugkonfigurationen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Projekteinstellungen für eine c#-Debugkonfiguration im Fenster **Eigenschaften Seiten** ändern, wie in [Debug-und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md)erläutert. Anhand der folgenden Tabellen erfahren Sie, wo die debuggerspezifischen Einstellungen im Fenster **Eigenschaftenseiten** zu finden sind.  
  
> [!WARNING]
> Dieses Thema gilt nicht für Windows Store-Apps. Siehe [Starten einer Debugsitzung (VB, C#, C++ und XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
## <a name="debug-tab"></a><a name="BKMK_Debug_tab"></a> Debug-Registerkarte  
  
|**Einstellung**|**Beschreibung**|  
|-----------------|---------------------|  
|**Konfiguration**|Legt den Modus für das Kompilieren der Anwendung fest. Sie können **Aktiv (Debuggen)** , **Debuggen**, **Release** oder **Alle Konfigurationen** auswählen.|  
|**Startaktion**|Anhand dieser Gruppe von Steuerungen wird festgelegt, welche Aktion bei Auswahl von Starten im Menü Debuggen erfolgt.<br /><br /> -   **Projekt starten** ist der Standardwert, durch den das Startprojekt zum Debuggen gestartet wird. Weitere Informationen finden Sie unter [auswählen des Start Projekts](https://msdn.microsoft.com/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   **Externes Programm starten** ermöglicht es, ein Programm zu starten, das nicht zu einem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projekt gehört, und eine Verbindung zu diesem Programm herzustellen. Weitere Informationen finden Sie unter [Anhängen an ein laufendes Programm](https://msdn.microsoft.com/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   **Browser mit folgender URL starten** ermöglicht das Debuggen einer Webanwendung.|  
|**Befehlszeilenargumente**|Legt Befehlszeilenargumente für das Programm fest, das gedebuggt werden soll. Der Befehlsname entspricht dem unter Externes Programm starten angegebenen Programmnamen. Wenn für Startaktion die Option Start-URL ausgewählt ist, können keine Befehlszeilenargumente festgelegt werden.|  
|**Arbeitsverzeichnis**|Gibt das Arbeitsverzeichnis des Programms an, das gerade gedebuggt wird. Das Arbeitsverzeichnis in [!INCLUDE[csprcs](../includes/csprcs-md.md)] ist das Verzeichnis, aus dem die Anwendung gestartet wird. Standardmäßig ist dies das Verzeichnis \bin\debug.|  
|**Remotecomputer verwenden**|Der Name eines Remote Computers, auf dem die Anwendung zu Debuggingzwecken ausgeführt wird, oder ein [msvsmon-Servername](https://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c). Der Speicherort der EXE-Datei auf dem Remotecomputer wird durch die Eigenschaft Ausgabepfad festgelegt, die sich im Ordner Konfigurationseigenschaften in der Kategorie Erstellen befindet. Bei diesem Speicherort muss es sich um ein freigegebenes Verzeichnis auf dem Remotecomputer handeln.|  
|**Nicht verwaltetes Codedebuggen aktivieren**|Bietet die Möglichkeit, Aufrufe von systemeigenem (nicht verwaltetem) Win32-Code von einer verwalteten Anwendung aus zu debuggen.|  
|**SQL Server-Debuggen aktivieren**|Ermöglicht das Debuggen von SQL Server-Datenbankobjekten.|  
  
## <a name="build-tab"></a><a name="BKMK_Build_tab"></a> Registerkarte Erstellen  
  
|Einstellung|BESCHREIBUNG|  
|-------------|-----------------|  
|**Symbole für bedingte Kompilierung:**|Hier werden die Konstanten DEBUG und TRACE definiert.<br /><br /> Diese Konstanten ermöglichen das Kompilieren der [Debug-](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx) und [Trace-Klassen](https://msdn.microsoft.com/library/system.diagnostics.trace.aspx). Wenn diese Konstanten definiert sind, generieren die Klassenmethoden „Debug“ und „Trace“ eine Ausgabe im [Ausgabefenster](../ide/reference/output-window.md). Ohne diese Konstanten werden die Klassenmethoden Debug und Trace nicht kompiliert und keine Ausgabe erzeugt.<br /><br /> -Debug wird normalerweise in der Debugversion eines Programms definiert und in der Releaseversion nicht definiert.<br />-Trace wird normalerweise sowohl in Debug-als auch in Releaseversionen definiert.|  
|**Code optimieren**|Sofern Sie keinen Fehler finden, der ausschließlich in optimiertem Code auftritt, sollte diese Einstellung in der Debugversion deaktiviert bleiben. Optimierter Code ist aufwendiger zu debuggen, da die Anweisungen nicht direkt mit den Anweisungen in den Quellcodefenstern übereinstimmen.|  
|**Ausgabepfad:**|Wird zum Debuggen normalerweise auf "bin\Debug" festgelegt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)
