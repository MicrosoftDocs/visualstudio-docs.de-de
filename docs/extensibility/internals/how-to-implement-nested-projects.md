---
title: 'Vorgehensweise: Implementieren von in einem Projekt unter fallenen Projekten | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie in Visual Studio durch das Durchführen von Ereignissen aus den Projektmappen-und übergeordneten Projekten eine Projekt Hierarchie erstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a1b02fca5d37d7e75cd7c32527bb09358425e626
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932539"
---
# <a name="how-to-implement-nested-projects"></a>Gewusst wie: Implementieren von in einem Projekt unter fallenen Projekten

Wenn Sie einen Typ für einen in einem Projekt erstellten Typ erstellen, müssen mehrere zusätzliche Schritte implementiert werden. Ein übergeordnetes Projekt übernimmt einige der gleichen Zuständigkeiten wie die Projekt Mappe für die zugehörigen (untergeordneten) Projekte. Das übergeordnete Projekt ist ein Container mit Projekten, die einer Projekt Mappe ähneln. Insbesondere gibt es mehrere Ereignisse, die von der Projekt Mappe und von den übergeordneten Projekten ausgelöst werden müssen, um die Hierarchie der geschposteten Projekte zu erstellen. Diese Ereignisse werden im folgenden Verfahren zum Erstellen von geschposteten Projekten beschrieben.

## <a name="create-nested-projects"></a>Erstellen von in einem Projekt erstellten Projekten

1. Die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) lädt die Projektdatei und die Startinformationen des übergeordneten Projekts durch Aufrufen der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> Schnittstelle. Das übergeordnete Projekt wird erstellt und der Projekt Mappe hinzugefügt.

    > [!NOTE]
    > An diesem Punkt ist es zu früh im Prozess, bis das übergeordnete Projekt das untergeordnete Projekt erstellt hat, da das übergeordnete Projekt erstellt werden muss, bevor die untergeordneten Projekte erstellt werden können. Nach dieser Sequenz kann das übergeordnete Projekteinstellungen auf die untergeordneten Projekte anwenden, und die untergeordneten Projekte können bei Bedarf Informationen aus den übergeordneten Projekten abrufen. Diese Sequenz ist, wenn Sie von Clients wie der Quell Code Verwaltung (Quell Code Verwaltung, SCC) und **Projektmappen-Explorer** benötigt wird.

     Das übergeordnete Projekt muss warten, bis die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> Methode von der IDE aufgerufen wird, bevor das zugehörige (untergeordnete) Projekt oder die zugehörigen Projekte erstellt werden können.

2. Die IDE ruft `QueryInterface` für das übergeordnete Projekt für auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject> . Wenn dieser Aufruf erfolgreich ist, ruft die IDE die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> Methode des übergeordneten-Elements auf, um alle für das übergeordnete Projekt zu öffnen.

3. Das übergeordnete Projekt Ruft die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> Methode auf, um Listener darüber zu benachrichtigen, dass die Erstellung von Projekten im Begriff ist. Beispielsweise überwacht SCC diese Ereignisse, um zu ermitteln, ob die Schritte im Projektmappen-und Projekt Erstellungs Prozess in der richtigen Reihenfolge ausgeführt werden. Wenn die Schritte nicht in der richtigen Reihenfolge ausgeführt werden, ist die Lösung möglicherweise nicht ordnungsgemäß mit der Quell Code Verwaltung registriert.

4. Das übergeordnete Projekt Ruft die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> Methode oder die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> Methode für jedes seiner untergeordneten Projekte auf.

     Sie übergeben <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> an die- `AddVirtualProject` Methode, um anzugeben, dass das virtuelle (gestreamte) Projekt dem Projektfenster hinzugefügt werden soll, von der Erstellung ausgeschlossen, der Quell Code Verwaltung hinzugefügt usw. `VSADDVPFLAGS` ermöglicht es Ihnen, die Sichtbarkeit des eingefügten Projekts zu steuern und anzugeben, welche Funktionalität damit verknüpft ist.

     Wenn Sie ein bereits vorhandenes untergeordnetes Projekt erneut laden, das eine Projekt-GUID enthält, die in der Projektdatei des übergeordneten Projekts gespeichert ist, ruft das übergeordnete Projekt auf `AddVirtualProjectEx` Der einzige Unterschied zwischen `AddVirtualProject` und `AddVirtualProjectEX` besteht darin, dass `AddVirtualProjectEX` über einen-Parameter verfügt, damit das übergeordnete Projekt eine pro-Instanz angeben kann, damit `guidProjectID` das untergeordnete Projekt aktiviert <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> und ordnungsgemäß <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> funktioniert.

     Wenn keine GUID verfügbar ist, z. b. Wenn Sie ein neues, neu eingefügtes Projekt hinzufügen, erstellt die Projekt Mappe eine für das Projekt, wenn Sie dem übergeordneten Element hinzugefügt wird. Es liegt in der Verantwortung des übergeordneten Projekts, die Projekt-GUID in der Projektdatei beizubehalten. Wenn Sie ein geduschtes Projekt löschen, kann auch die GUID für das Projekt gelöscht werden.

5. Die IDE Ruft die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> Methode für jedes untergeordnete Projekt des übergeordneten Projekts auf.

     Das übergeordnete Projekt muss implementieren `IVsParentProject` , wenn Sie Projekte Schachteln möchten. Das übergeordnete Projekt ruft jedoch nie `QueryInterface` auf, `IVsParentProject` auch wenn es über übergeordnete Projekte darunter verfügt. Die Lösung verarbeitet den Aufruf von `IVsParentProject` und, wenn Sie implementiert ist, ruft `OpenChildren` auf, um die zu erstellenden Projekte zu erstellen. `AddVirtualProjectEX` wird immer von aufgerufen `OpenChildren` . Sie sollte nie vom übergeordneten Projekt aufgerufen werden, um die Hierarchie Erstellungs Ereignisse in der richtigen Reihenfolge beizubehalten.

6. Die IDE Ruft die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> Methode für das untergeordnete Projekt auf.

7. Das übergeordnete Projekt Ruft die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> Methode auf, um Listener zu benachrichtigen, dass die untergeordneten Projekte für das übergeordnete Projekt erstellt wurden.

8. Die IDE Ruft die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> Methode für das übergeordnete Projekt auf, nachdem alle untergeordneten Projekte geöffnet wurden.

     Wenn Sie nicht bereits vorhanden ist, erstellt das übergeordnete Projekt eine GUID für jedes geschachtelte Project durch Aufrufen von `CoCreateGuid` .

    > [!NOTE]
    > `CoCreateGuid` ist eine com-API, die aufgerufen wird, wenn eine GUID erstellt werden soll. Weitere Informationen finden Sie unter `CoCreateGuid` und GUIDs in der MSDN Library.

     Das übergeordnete Projekt speichert diese GUID in der Projektdatei, um beim nächsten Öffnen in der IDE abgerufen zu werden. Weitere Informationen zum Aufrufen von `AddVirtualProjectEX` , um den für das untergeordnete Projekt abzurufen, finden Sie in Schritt 4 `guidProjectID` .

9. Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Methode wird dann für die übergeordnete Itemid aufgerufen, die gemäß der Konvention, die Sie an das untergeordnete Projekt delegiert haben. Der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Ruft die Eigenschaften des Knotens ab, der ein Projekt geschachtelt, das Sie in delegieren möchten, wenn es für das übergeordnete Element aufgerufen wird.

     Da das übergeordnete und das untergeordnete Projekt Programm gesteuert instanziiert werden, können Sie an dieser Stelle Eigenschaften für die untergeordneten Projekte festlegen.

    > [!NOTE]
    > Sie erhalten nicht nur die Kontextinformationen aus dem eingefügten Projekt, sondern Sie können auch Fragen, ob das übergeordnete Projekt über einen Kontext für dieses Element verfügt, indem Sie __VSHPROPID überprüfen [. VSHPROPID_UserContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>). Auf diese Weise können Sie zusätzliche dynamische Hilfe Attribute und Menü Optionen hinzufügen, die für einzelne, in der Projekt masted Projekte spezifisch sind.

10. Die-Hierarchie wird erstellt, um in **Projektmappen-Explorer** mit einem Aufrufen der-Methode angezeigt zu werden <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> .

     Sie übergeben die Hierarchie an die Umgebung, `GetNestedHierarchy` um die Hierarchie für die Anzeige in Projektmappen-Explorer zu erstellen. Auf diese Weise weiß die Lösung, dass das Projekt vorhanden ist und für die Erstellung durch den Build-Manager verwaltet werden kann oder ob Dateien im Projekt in der Quell Code Verwaltung abgelegt werden können.

11. Wenn alle für Projekt1 erstellten Projekte erstellt wurden, wird die Steuerung an die Projekt Mappe zurückgegeben, und der Prozess wird für "Projekt2" wiederholt.

     Der gleiche Vorgang zum Erstellen von untergeordneten Projekten erfolgt bei einem untergeordneten Projekt, das über ein untergeordnetes Projekt verfügt. Wenn BuildProject1, bei dem es sich um ein untergeordnetes Element von Projekt1 handelt, über untergeordnete Projekte verfügte, werden Sie in diesem Fall nach BuildProject1 und vor "Projekt2" erstellt. Der Prozess ist rekursiv, und die Hierarchie wird von oben nach unten erstellt.

     Wenn ein gesperrtes Projekt geschlossen wird, weil der Benutzer die Projekt Mappe oder das spezifische Projekt geschlossen hat, wird die andere Methode in `IVsParentProject` , <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A> , aufgerufen. Das übergeordnete Projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> umschließt Aufrufe der-Methode mit dem <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> und den- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> Methoden, um Listener an Lösungs Ereignisse zu benachrichtigen, dass die geachtelten Projekte geschlossen werden.

In den folgenden Themen werden verschiedene weitere Konzepte behandelt, die bei der Implementierung von in-Projekten zu beachten sind:

- [Überlegungen zum Entladen und erneuten Laden von in einem Projekt Vorgängen](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Unterstützung des Assistenten für die Unterstützung von Projekten](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Implementieren der Befehls Behandlung für in der Liste eingefügte Projekte](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Dialogfeld "AddItem" für die Liste der Projekte filtern](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>Weitere Informationen

- [Hinzufügen von Elementen zum Dialogfeld "Neues Element hinzufügen"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrieren von Projekt-und Element Vorlagen](../../extensibility/internals/registering-project-and-item-templates.md)
- [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Kontextparameter](../../extensibility/internals/context-parameters.md)
- [Assistenten Datei (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
