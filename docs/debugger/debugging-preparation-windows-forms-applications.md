---
title: Vorbereiten des Debuggens von Windows Forms-Apps | Microsoft-Dokumentation
description: Führen Sie vorbereitende Schritte zum Debuggen von Windows Forms-Anwendungen aus. Diese werden mithilfe der Windows Forms-Projektvorlage in Visual Studio erstellt.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ccb195d6c4a35e4ca3b89c5505ab14c45a5d555
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726812"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Vorbereitung des Debugvorgangs: Windows Forms-Anwendungen
Die Windows Forms-Projektvorlage erstellt eine Windows Forms-Anwendung. Das Debuggen dieses Anwendungstyps in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist einfach. Weitere Informationen finden Sie unter [Erstellen eines Windows Anwendungsprojekts](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100)).

 Wenn Sie ein Windows Forms-Projekt mit der Projektvorlage erstellen, werden die erforderlichen Einstellungen für die Debug- und Releasekonfigurationen automatisch durch [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] festgelegt. Diese Einstellungen können ggf. geändert werden. Diese Einstellungen können im Dialogfeld **Eigenschaftenseiten von \<project name>** (in Visual Basic unter **Mein Projekt**) geändert werden.

 Weitere Informationen finden Sie unter [Empfohlene Eigenschafteneinstellungen](../debugger/managed-debugging-recommended-property-settings.md).

 Eine zusätzlich empfohlene Eigenschafteneinstellung wird in der folgenden Tabelle angezeigt.

### <a name="configuration-properties-in-debug-tab"></a>Konfigurationseigenschaften auf der Registerkarte "Debuggen"

|**Eigenschaftenname**|**Einstellung**|
|-----------------------|-----------------|
|**Startaktion**|-   Diese Option ist in den meisten Fällen auf **Projekt starten** festgelegt. Wählen Sie **Externes Programm starten** aus, wenn Sie zu Beginn des Debuggens eine andere ausführbare Datei starten möchten (normalerweise für das Debuggen von DLLs).|

 Sie können Windows Forms-Anwendungen aus [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] heraus debuggen oder durch das Anfügen zu einer bereits laufenden Anwendung. Weitere Informationen zum Anfügen finden Sie unter [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>So debuggen Sie eine C#-, F#- oder Visual Basic-Windows Forms-Anwendung

1. Öffnen Sie das Projekt in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

2. Erstellen Sie Haltepunkte nach Bedarf.

    Da Windows Forms-Anwendungen ereignisgesteuert sind, gehen die Haltepunkte entweder in den Ereignishandlercode oder in Methoden, die vom Ereignishandlercode aufgerufen werden. Typische Ereignisse, in denen Haltepunkte platziert werden sollte, sind z. B. folgende:

   1. Einem Steuerelement zugeordnete Ereignisse, z. B. Klicken, Drücken der Eingabetaste usw.

   2. Ereignisse, die dem Start bzw. Herunterfahren der Anwendung zugeordnet sind, z. B. Laden, Aktivierung usw.

   3. Fokusereignisse und Validierungsereignisse.

      Weitere Informationen finden Sie unter [Erstellen von Ereignishandlern in Windows Forms](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms).

3. Klicken Sie im Menü **Debuggen** auf **Starten**.

4. Debuggen Sie mithilfe der Verfahren, die in [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md) erläutert werden.

## <a name="see-also"></a>Siehe auch
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
- [C#-, F#- und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [How to: Festlegen von Debug- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md)
- [Projekteinstellungen für C#-Debugkonfigurationen](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Projekteinstellungen für eine Visual Basic-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Windows Forms](/dotnet/framework/winforms/index)