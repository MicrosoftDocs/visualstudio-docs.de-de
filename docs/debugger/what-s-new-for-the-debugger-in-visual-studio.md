---
title: Neues im Debugger in Visual Studio 2017 | Microsoft-Dokumentation
titleSuffix: ''
description: 'In diesem Artikel werden die neuen Features der Debuggerversion 15.5 beschrieben. Dazu gehören: Momentaufnahmen des ausgewählten Codes von Apps in der Produktionsumgebung und das IntelliTrace-Feature „Schritt zurück“.'
ms.custom: SEO-VS-2020
ms.date: 01/22/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: bac5c7021146a0b9bc66e98e7de334bdbf05a7b7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883947"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2017"></a>Neues im Debugger in Visual Studio 2017

Der Debugger beinhaltet die folgenden neuen Features:

- Neues in Version 15.5: Der **Momentaufnahmedebugger** erstellt eine Momentaufnahme von Ihren in der Produktion befindlichen Apps, wenn Code ausgeführt wird, der für Sie von Interesse ist. Legen Sie Andockpunkte und Protokollpunkte in Ihrem Code fest, um den Debugger anzuweisen, eine Momentaufnahme zu erstellen. Der Debugger zeigt Fehler ohne Auswirkungen auf den Datenverkehr Ihrer Produktionsanwendung an. Der Momentaufnahmedebugger kann Sie dabei unterstützen, die Zeit zum Beheben von Fehlern, die in Produktionsumgebungen auftreten, erheblich zu reduzieren.

    Die Momentaufnahmensammlung ist für folgende Web-Apps verfügbar, die in Azure App Service ausgeführt werden:

  * ASP.NET-Apps, die in .NET Framework 4.6.1 oder höher ausgeführt werden.
  * ASP.NET Core-Apps, die in .NET Core 2.0 oder höher unter Windows ausgeführt werden.

    Weitere Informationen finden Sie unter [Debug live ASP.NET apps using the Snapshot Debugger (Debuggen von ASP.NET-Live-Apps mithilfe des Momentaufnahmedebuggers)](../debugger/debug-live-azure-applications.md).

- Neues in Version 15.5 von Visual Studio Enterprise: Das **IntelliTrace-Feature „Schritt zurück“** nimmt automatisch bei jedem Haltepunkt und Ereignis in einem Debuggerschritt eine Momentaufnahme von Ihrer Anwendung auf. Durch die erfassten Momentaufnahmen können Sie zu vorherigen Haltepunkten oder Schritten zurückkehren und sich den Zustand der Anwendung so anzeigen lassen, wie er zuvor war. Mit dem IntelliTrace-Feature „Step-back“ können Sie Zeit sparen, wenn Sie den vorherigen Zustand der Anwendung anzeigen oder diesen wiederherstellen, aber das Debuggen nicht erneut starten möchten.

    Sie können Momentaufnahmen anzeigen und durch diese navigieren, indem Sie die Schaltflächen **Schritt zurück** und **Schritt vor** in der Debugsymbolleiste verwenden. Mit diesen Schaltflächen können Sie durch die Ereignisse navigieren, die in der Registerkarte **Ereignisse** des Fensters **Diagnosetools** angezeigt werden.

    ![Schaltflächen „Schritt zurück“ und „Schritt vorwärts“](../debugger/media/intellitrace-step-back-icons-description.png  "Schaltflächen „Schritt zurück“ und „Schritt vorwärts“")

    Weitere Informationen finden Sie auf der Seite [Inspect previous app states using IntelliTrace (Untersuchen vorheriger App-Zustände mithilfe von IntelliTrace)](view-historical-application-state.md).

- Der Ausnahmen-Assistent wird durch die **Ausnahmen-Hilfe** ersetzt. Diese wird an der Stelle, an der der Fehler aufgetreten ist, in einem nicht modalen Dialogfeld angezeigt. Die **Ausnahmen-Hilfe** bietet einen schnelleren Zugriff auf alle inneren Ausnahmen, eine zusätzliche Analyse durch den Debugger (sofern vorhanden) und unmittelbaren Zugriff auf die **Ausnahmeeinstellungen** für die entsprechende Ausnahme. Wenn die Ausnahmen-Hilfe etwas verdeckt, das Sie sehen müssen, können Sie auch an dem Dialogfeld ziehen, um es in einer nicht verankerten Ansicht anzuzeigen.

    Bei einer **NullReferenceException** wird jetzt beispielsweise die Variable angezeigt, die den Nullverweis enthält (zusätzliche Informationen).

    ![Ausnahmen-Hilfe im Debugger](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Weitere Informationen finden Sie im Blogbeitrag [Using the New Exception Helper in Visual Studio](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/) (Verwenden der neuen Ausnahmen-Hilfe in Visual Studio).

- Sie können jetzt im Debugger bei angehaltener Ausführung Code bis zu einer bestimmten Zeile ausführen, indem Sie auf den grünen Pfeil für **Ausführung bis hier ausführen** klicken. (Dieses Symbol wird angezeigt, wenn Sie auf eine Codezeile zeigen.) Dadurch müssen keine temporären Haltepunkte mehr festgelegt werden.

    ![„Run to Click“ (Ausführung bis Klick) im Debugger](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- Im Dialogfeld **Ausnahmeeinstellungen** können Sie Bedingungen für Ausnahmen festlegen. (Dies ist entweder über das Symbol für **Bedingung bearbeiten** im Dialogfeld „Ausnahmeeinstellungen“ oder über das Kontextmenü der Ausnahme möglich.) Zu den derzeit unterstützten Bedingungen gehören die Modulnamen, die für die Ausnahme eingeschlossen oder ausgeschlossen werden sollen.

    ![Bedingungen für eine Ausnahme](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- Das Dialogfeld „An Prozess anhängen“ enthält ein neues Suchfeature, mit dem Sie den Prozess zum Anhängen schneller identifizieren können.

    ![Suche in „An Prozess anhängen“](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

Weitere Informationen zu diesen neuen Features finden Sie in den [Versionshinweisen zu [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]](/visualstudio/releasenotes/vs2017-relnotes).

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.yml)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)