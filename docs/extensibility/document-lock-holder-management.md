---
title: Dokument Sperr Inhaber-Verwaltung | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Bearbeitungs Sperre für ein Dokument in der laufenden dokumententabelle platzieren, ohne dass der Benutzer ein geöffnetes Dokument in einem Dokument Fenster sehen kann.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5c80c2969676de25575ec75c6976224f1cd0160e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968241"
---
# <a name="document-lock-holder-management"></a>Dokument Sperr Inhaber-Verwaltung

In der laufenden dokumententabelle (RDT) werden die Anzahl der geöffneten Dokumente und ggf. Bearbeitungs Sperren beibehalten. Sie können eine Bearbeitungs Sperre für ein Dokument im RDT platzieren, wenn es im Hintergrundprogramm gesteuert bearbeitet wird, ohne dass der Benutzer ein geöffnetes Dokument in einem Dokument Fenster sehen würde. Diese Funktion wird häufig von Designern verwendet, die mehrere Dateien über eine grafische Benutzeroberfläche ändern.

## <a name="document-lock-holder-scenarios"></a>Szenarien für die Dokument Sperr Inhaber

### <a name="file-a-has-a-dependence-on-file-b"></a>Die Datei "a" hat eine Abhängigkeit von der Datei "b".

Stellen Sie sich eine Situation vor, in der Sie einen Standard Editor "a" für den Dateityp "a" implementieren, und jede Datei des Typs "a" enthält einen Verweis auf eine Datei vom Typ "b" (oder die Abhängigkeit davon). Ein Standard Editor "b" ist für Dateien vom Typ "b" vorhanden. Wenn der Editor "a" die Datei "a" öffnet, wird der Verweis auf die entsprechende Datei "b" abgerufen. Die Datei "b" wird nicht angezeigt, aber der Editor "a" kann Sie ändern. Der Editor "A" Ruft einen Verweis auf die Dokument Daten der Datei "b" aus der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> -Methode ab und verwaltet außerdem eine Bearbeitungs Sperre für die Datei "b". Nachdem der Editor "a" mit dem Ändern der Datei "b" abgeschlossen ist, können Sie die Anzahl der Bearbeitungs Sperren für die Datei "b" verringern, indem Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> Methode aufrufen. Sie können diesen Schritt weglassen, wenn Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> Methode mit dem-Parameter aufgerufen haben `dwRDTLockType` , der auf _VSRDTFLAGS festgelegt ist [. RDT_NoLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_NoLock>).

### <a name="file-b-is-opened-by-a-different-editor"></a>Die Datei "b" wird von einem anderen Editor geöffnet.

Wenn die Datei "b" bereits vom Editor "b" geöffnet wird, wenn der Editor "A" versucht, Sie zu öffnen, gibt es zwei separate Szenarien, die behandelt werden müssen:

- Wenn die Datei "b" in einem kompatiblen Editor geöffnet ist, muss der Editor "a" eine Dokument Bearbeitungs Sperre für die Datei "b" mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> Methode registrieren. Nachdem der Editor "a" das Ändern der Datei "b" abgeschlossen hat, heben Sie die Registrierung der Dokument Bearbeitungs Sperre mithilfe der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> Methode auf.

- Wenn die Datei "b" auf nicht kompatible Weise geöffnet ist, können Sie entweder den Versuch, die Datei "b" durch den Editor "a" zu öffnen, fehlschlagen, oder Sie können die dem Editor zugeordnete Ansicht teilweise öffnen lassen und eine entsprechende Fehlermeldung anzeigen. Die Fehlermeldung sollte den Benutzer anweisen, die Datei "b" im inkompatiblen Editor zu schließen und dann die Datei "a" mit dem Editor "a" erneut zu öffnen. Sie können auch die- [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Methode implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> , um den Benutzer aufzufordern, die Datei "b" zu schließen, die im nicht kompatiblen Editor geöffnet ist. Wenn der Benutzer die Datei "b" schließt, wird das Öffnen der Datei "a" im Editor "a" normal fortgesetzt.

## <a name="additional-document-edit-lock-considerations"></a>Weitere Überlegungen zur Dokument Bearbeitungs Sperre

Sie erhalten ein anderes Verhalten, wenn der Editor "A" der einzige Editor ist, der über eine Dokument Bearbeitungs Sperre für die Datei "b" verfügt, als wenn der Editor "b" auch eine Dokument Bearbeitungs Sperre für die Datei "b" enthält. In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist **Klassen-Designer** ein Beispiel für einen visuellen Designer, der keine Bearbeitungs Sperre für die zugeordnete Codedatei enthält. Das heißt, wenn der Benutzer ein Klassendiagramm in der Entwurfs Ansicht geöffnet hat und die zugehörige Codedatei gleichzeitig geöffnet ist, und wenn der Benutzer die Codedatei ändert, aber die Änderungen nicht speichert, gehen die Änderungen auch in die Klassendiagramm Datei (. CD) über. Wenn das **Klassen-Designer** die einzige Dokument Bearbeitungs Sperre für die Codedatei hat, wird der Benutzer beim Schließen der Codedatei nicht aufgefordert, die Änderungen zu speichern. Die IDE fordert den Benutzer auf, die Änderungen erst zu speichern, wenn der Benutzer die **Klassen-Designer** schließt. Die gespeicherten Änderungen werden in beiden Dateien widergespiegelt. Wenn die **Klassen-Designer** und der Codedatei-Editor Dokument Bearbeitungs Sperren in der Codedatei gespeichert haben, wird der Benutzer zum Speichern aufgefordert, wenn entweder die Codedatei oder das Formular geschlossen wird. An diesem Punkt werden die gespeicherten Änderungen sowohl in Form als auch in der Codedatei widergespiegelt. Weitere Informationen zu Klassendiagrammen finden Sie unter [Arbeiten mit Klassendiagrammen (Klassen-Designer)](../ide/class-designer/designing-and-viewing-classes-and-types.md).

Beachten Sie, dass Sie die-Schnittstelle implementieren müssen, wenn Sie eine Bearbeitungs Sperre für ein Dokument für einen nicht-Editor platzieren müssen <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> .

Oft nimmt ein UI-Designer, der Code Dateien Programm gesteuert ändert, Änderungen an mehr als einer Datei vor. In solchen Fällen verarbeitet die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> Methode das Speichern von einem oder mehreren Dokumenten mithilfe des Dialog Felds möchten **Sie die Änderungen an den folgenden Elementen speichern?** .

## <a name="see-also"></a>Weitere Informationen

- [Ausführen der dokumententabelle](../extensibility/internals/running-document-table.md)
- [Persistenz und die laufende Dokument Tabelle](../extensibility/internals/persistence-and-the-running-document-table.md)
