---
title: 'Vorgehensweise: Anfügen von Sichten an Dokument Daten | Microsoft-Dokumentation'
description: Möglicherweise können Sie eine neue Dokument Ansicht an ein vorhandenes Dokument Datenobjekt anfügen. Verwenden Sie dieses Verfahren, um zu bestimmen, ob Sie die Sicht anfügen können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 97926070bd06e4e8a99a4d6b2fe59e4ea57233ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929224"
---
# <a name="how-to-attach-views-to-document-data"></a>Gewusst wie: Anfügen von Sichten an Dokument Daten
Wenn Sie über eine neue Dokument Ansicht verfügen, können Sie Sie möglicherweise an ein vorhandenes Dokument Datenobjekt anfügen.

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>So bestimmen Sie, ob Sie eine Ansicht an ein vorhandenes Dokument Datenobjekt anfügen können

1. Implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.

2. Rufen Sie in ihrer Implementierung von `IVsEditorFactory::CreateEditorInstance` `QueryInterface` für das vorhandene Dokument Datenobjekt auf, wenn die IDE die- `CreateEditorInstance` Implementierung aufruft.

    Durch Aufrufen `QueryInterface` von können Sie das vorhandene Dokument Datenobjekt, das im-Parameter angegeben ist, untersuchen `punkDocDataExisting` .

    Die genauen Schnittstellen, die Sie Abfragen müssen, sind jedoch abhängig vom Editor, der das Dokument öffnet, wie in Schritt 4 beschrieben.

3. Wenn Sie die entsprechenden Schnittstellen für das vorhandene Dokument Datenobjekt nicht finden, geben Sie einen Fehlercode an den Editor zurück, der darauf hinweist, dass das Dokument Datenobjekt mit dem Editor nicht kompatibel ist.

    In der-Implementierung der IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> werden Sie in einem Meldungs Feld benachrichtigt, dass das Dokument in einem anderen Editor geöffnet ist, und Sie werden gefragt, ob Sie es schließen möchten.

4. Wenn Sie dieses Dokument schließen, ruft Visual Studio die Editorfactory ein zweites Mal auf. Bei diesem-Befehl ist der- `DocDataExisting` Parameter gleich NULL. Die Editorfactory-Implementierung kann dann das Dokument Datenobjekt in Ihrem eigenen Editor öffnen.

   > [!NOTE]
   > Um zu ermitteln, ob Sie mit einem vorhandenen Dokument Datenobjekt arbeiten können, können Sie auch private Kenntnisse der Schnittstellen Implementierung verwenden, indem Sie einen Zeiger in die tatsächliche [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] Klasse Ihrer privaten Implementierung umwandeln. Beispielsweise implementieren alle Standard-Editoren `IVsPersistFileFormat` , die von erbt <xref:Microsoft.VisualStudio.OLE.Interop.IPersist> . Daher können Sie für einen aufzurufen `QueryInterface` <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A> , und wenn die Klassen-ID für das vorhandene Dokument Datenobjekt mit der Klassen-ID Ihrer Implementierung übereinstimmt, können Sie mit dem Dokument Datenobjekt arbeiten.

## <a name="robust-programming"></a>Stabile Programmierung
 Wenn Visual Studio Ihre Implementierung der Methode aufruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> , übergibt Sie einen Zeiger auf das vorhandene Dokument Datenobjekt im- `punkDocDataExisting` Parameter, sofern vorhanden. Überprüfen Sie das in zurückgegebene Dokument Datenobjekt `punkDocDataExisting` , um zu bestimmen, ob das Dokument Datenobjekt für Ihren Editor geeignet ist, wie im Hinweis in Schritt 4 des Verfahrens in diesem Thema beschrieben. Wenn dies der Fall ist, sollte die Editorfactory eine zweite Ansicht für die Daten bereitstellen, wie [unter unterstützen mehrerer Dokument Sichten](../extensibility/supporting-multiple-document-views.md)beschrieben. Wenn dies nicht der Fall ist, sollte eine entsprechende Fehlermeldung angezeigt werden.

## <a name="see-also"></a>Weitere Informationen
- [Unterstützung mehrerer Dokument Sichten](../extensibility/supporting-multiple-document-views.md)
- [Dokument Daten und Dokument Ansicht in benutzerdefinierten Editoren](../extensibility/document-data-and-document-view-in-custom-editors.md)
