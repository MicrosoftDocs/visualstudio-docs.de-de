---
title: Unterstützen mehrerer Dokument Sichten | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mehr als eine Ansicht eines Dokuments bereitstellen, indem Sie separate Dokument Daten und Dokument Ansichts Objekte für Ihren benutzerdefinierten Editor im Visual Studio SDK verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c1d99f4beb000d4b48435b9215a01f31ef8e936
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2020
ms.locfileid: "97716093"
---
# <a name="supporting-multiple-document-views"></a>Unterstützen mehrerer Dokumentansichten
Sie können mehr als eine Ansicht eines Dokuments bereitstellen, indem Sie separate Dokument Daten und Dokument Ansichts Objekte für den Editor erstellen. In einigen Fällen ist eine zusätzliche Dokument Ansicht nützlich:

- Neue Fenster Unterstützung: Sie möchten, dass der Editor zwei oder mehr Ansichten desselben Typs bereitstellt, sodass ein Benutzer, der bereits ein Fenster im Editor geöffnet hat, ein neues Fenster öffnen kann, indem er den Befehl **Neues Fenster** im Menü **Fenster** auswählt.

- Unterstützung für Formular-und Code Ansicht: Sie möchten, dass der Editor Ansichten verschiedener Typen bereitstellt. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]Beispielsweise stellt eine Formularansicht und eine Code Ansicht bereit.

  Weitere Informationen hierzu finden Sie in der Prozedur "| ateeditorinstance" in der Datei "EditorFactory.cs" im benutzerdefinierten Editor-Projekt, das von der Visual Studio-Paket Vorlage erstellt wurde. Weitere Informationen zu diesem Projekt finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines benutzerdefinierten Editors](../extensibility/walkthrough-creating-a-custom-editor.md).

## <a name="synchronizing-views"></a>Synchronisieren von Sichten
 Wenn Sie mehrere Ansichten implementieren, ist das Dokument Datenobjekt dafür verantwortlich, alle Sichten mit den Daten synchronisiert zu halten. Mithilfe der Schnittstellen für die Ereignis Behandlung von können Sie <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> mehrere Ansichten mit den Daten synchronisieren.

 Wenn Sie das-Objekt nicht <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> zum Synchronisieren mehrerer Sichten verwenden, müssen Sie ein eigenes Ereignis System implementieren, um an dem Dokument Datenobjekt vorgenommene Änderungen zu verarbeiten. Sie können verschiedene Granularitätsebene verwenden, um mehrere Sichten auf dem neuesten Stand zu halten. Wenn Sie in einer Ansicht eine Einstellung der maximalen Granularität eingeben, werden die anderen Ansichten sofort aktualisiert. Bei minimaler Granularität werden andere Sichten erst aktualisiert, wenn Sie aktiviert wurden.

## <a name="determining-whether-document-data-is-already-open"></a>Ermitteln, ob Dokument Daten bereits geöffnet sind
 Mit der laufenden dokumententabelle (RDT) in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) können Sie nachverfolgen, ob die Daten für ein Dokument bereits geöffnet sind, wie im folgenden Diagramm dargestellt.

 ![Grafik zu docdataview](../extensibility/media/docdataview.gif "Zu docdataview") Mehrere Ansichten

 Standardmäßig ist jede Ansicht (Dokument Ansichts Objekt) in einem eigenen Fensterrahmen ( <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> ) enthalten. Wie bereits erwähnt, können Dokument Daten jedoch in mehreren Ansichten angezeigt werden. Um dies zu ermöglichen, überprüft Visual Studio den RDT, um zu bestimmen, ob das betreffende Dokument bereits in einem Editor geöffnet ist. Wenn die IDE aufruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> , um den Editor zu erstellen, gibt ein Wert ungleich NULL, der im-Parameter zurückgegeben `punkDocDataExisting` wird, an, dass das Dokument bereits in einem anderen Editor geöffnet ist. Weitere Informationen zur Funktionsweise von RDT finden Sie unter [Ausführen der Dokument Tabelle](../extensibility/internals/running-document-table.md).

 Untersuchen Sie in Ihrer- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Implementierung das in zurückgegebene Dokument Datenobjekt `punkDocDataExisting` , um zu bestimmen, ob die Dokument Daten für Ihren Editor geeignet sind. (Beispielsweise sollten nur HTML-Daten von einem HTML-Editor angezeigt werden.) Wenn dies der Fall ist, sollte die Editorfactory eine zweite Ansicht für die Daten bereitstellen. Wenn der- `punkDocDataExisting` Parameter nicht ist `NULL` , ist es möglich, dass das Dokument Datenobjekt in einem anderen Editor geöffnet ist, oder es ist wahrscheinlicher, dass die Dokument Daten bereits in einer anderen Ansicht mit dem gleichen Editor geöffnet sind. Wenn die Dokument Daten in einem anderen Editor geöffnet sind, den die Editorfactory nicht unterstützt, kann Visual Studio die Editorfactory nicht öffnen. Weitere Informationen finden Sie unter Gewusst [wie: Anfügen von Ansichten an Dokument Daten](../extensibility/how-to-attach-views-to-document-data.md).
