---
title: Auswahl Kontext Objekte | Microsoft-Dokumentation
description: Erfahren Sie, wie die Visual Studio-IDE ein globales Auswahl Kontext Objekt verwendet, um zu bestimmen, was in der IDE angezeigt werden soll.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf5e54f00ecbac03eaebe68c6fb4de410987b63f
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875569"
---
# <a name="selection-context-objects"></a>Auswahlkontextobjekte
Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) verwendet ein globales Auswahl Kontext Objekt, um zu bestimmen, was in der IDE angezeigt werden soll. Für jedes Fenster in der IDE kann ein eigenes Auswahl Kontext Objekt in den globalen Auswahl Kontext übermittelt werden. Die IDE aktualisiert den globalen Auswahl Kontext mit Werten aus einem Fenster, wenn dieses Fenster den Fokus besitzt. Weitere Informationen finden Sie unter [Feedback an den Benutzer](../../extensibility/internals/feedback-to-the-user.md).

 Jeder Fensterrahmen oder jede Site in der IDE verfügt über einen Dienst mit dem Namen <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . Das von Ihrem VSPackage erstellte Objekt, das im Fensterrahmen positioniert ist, muss die- `QueryService` Methode aufzurufen, um einen Zeiger auf die- <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> Schnittstelle zu erhalten.

 Rahmen Fenster können Teile Ihrer Auswahl Kontextinformationen daran halten, beim Start an den globalen Auswahl Kontext weitergegeben zu werden. Diese Fähigkeit ist nützlich für Tool Fenster, die möglicherweise mit einer leeren Auswahl beginnen müssen.

 Durch das Ändern des globalen Auswahl Kontexts werden Ereignisse ausgelöst, die von VSPackages überwacht werden können. VSPackages können die folgenden Aufgaben durch Implementieren von `IVsTrackSelectionEx` -und- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> Schnittstellen ausführen:

- Aktualisieren Sie die derzeit aktive Datei in einer Hierarchie.

- Überwachen von Änderungen an bestimmten Elementtypen. Wenn für Ihr VSPackage beispielsweise ein spezielles **Eigenschaften** Fenster verwendet wird, können Sie Änderungen im aktiven **Eigenschaften** Fenster Überwachen und bei Bedarf ihren Neustart starten.

  Die folgende Sequenz zeigt den typischen Verlauf der Auswahl Nachverfolgung.

1. Die IDE Ruft den Auswahl Kontext aus dem neu geöffneten Fenster ab und legt ihn im globalen Auswahl Kontext ab. Wenn der Auswahl Kontext HIERARCHY_DONTPROPAGATE oder SELCONTAINER_DONTPROPAGATE verwendet, werden diese Informationen nicht an den globalen Kontext weitergegeben. Weitere Informationen finden Sie unter [Feedback an den Benutzer](../../extensibility/internals/feedback-to-the-user.md).

2. Benachrichtigungs Ereignisse werden an jedes VSPackage gesendet, das Sie angefordert hat.

3. Das VSPackage wirkt sich auf die empfangenen Ereignisse aus, indem er Aktivitäten wie das Aktualisieren einer Hierarchie, das erneute Aktivieren eines Tools oder andere ähnliche Aufgaben ausführt.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Auswahl und Aktualität in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Projekttypen](../../extensibility/internals/project-types.md)
