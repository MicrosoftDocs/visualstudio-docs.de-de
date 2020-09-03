---
title: 'Gewusst wie: Öffnen von Editoren für geöffnete Dokumente | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f67a7fad5944e82087f520508ef9f4a66b7109d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905812"
---
# <a name="how-to-open-editors-for-open-documents"></a>Gewusst wie: Öffnen von Editoren für geöffnete Dokumente
Bevor ein Projekt ein Dokument Fenster öffnet, muss das Projekt zuerst bestimmen, ob die Datei bereits im Dokument Fenster für einen anderen Editor geöffnet ist. Die Datei kann entweder in einem projektspezifischen Editor oder einem der Standard-Editoren, die bei registriert sind, geöffnet sein [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="open-a-project-specific-editor"></a>Öffnen eines projektspezifischen Editors
 Verwenden Sie das folgende Verfahren, um einen projektspezifischen Editor für eine Datei zu öffnen, die bereits geöffnet ist.

### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>So öffnen Sie einen projektspezifischen Editor für eine geöffnete Datei

1. Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> -Methode auf.

    Dieser Rückruf gibt ggf. Zeiger auf die Hierarchie, das Hierarchie Element und den Fensterrahmen des Dokuments zurück.

2. Wenn das Dokument geöffnet ist, muss das Projekt überprüfen, ob nur ein Dokument Datenobjekt vorhanden ist oder ob ein Dokument Ansichts Objekt vorhanden ist.

   - Wenn ein Dokument Ansichts Objekt vorhanden ist und diese Ansicht für eine andere Hierarchie oder ein anderes Hierarchie Element gilt, verwendet das Projekt den Zeiger auf den Fensterrahmen der Ansicht, um das vorhandene Fenster neu zu verwenden.

   - Wenn ein Dokument Ansichts Objekt vorhanden ist und diese Sicht für dieselbe Hierarchie und dasselbe Hierarchie Element gilt, kann das Projekt eine zweite Ansicht öffnen, wenn es an das zugrunde liegende Dokument Datenobjekt angehängt werden kann. Andernfalls sollte das Projekt den Zeiger auf den Fensterrahmen der Sicht verwenden, um das vorhandene Fenster neu anzuzeigen.

   - Wenn nur das Dokument Datenobjekt vorhanden ist, sollte das Projekt ermitteln, ob das Dokument Datenobjekt für seine Ansicht verwendet werden kann. Wenn das Dokument Datenobjekt kompatibel ist, führen Sie die Schritte aus, die unter [Öffnen eines projektspezifischen Editors](../extensibility/how-to-open-project-specific-editors.md)erläutert werden.

     Wenn das Dokument Datenobjekt nicht kompatibel ist, sollte dem Benutzer ein Fehler angezeigt werden, der angibt, dass die Datei zurzeit verwendet wird. Dieser Fehler sollte nur in vorübergehenden Fällen angezeigt werden, z. b. Wenn eine Datei kompiliert wird, während der Benutzer versucht, die Datei zu öffnen, indem er einen anderen Editor als den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Core-Text-Editor verwendet. Der Kerntext-Editor kann das Dokument Datenobjekt für den Compiler freigeben.

3. Wenn das Dokument nicht geöffnet ist, weil kein Dokument Datenobjekt oder Dokument Ansichts Objekt vorhanden ist, führen Sie die Schritte in [Öffnen eines projektspezifischen Editors](../extensibility/how-to-open-project-specific-editors.md)aus.

## <a name="open-a-standard-editor"></a>Öffnen eines Standard-Editors
 Verwenden Sie das folgende Verfahren, um einen Standard Editor für eine Datei zu öffnen, die bereits geöffnet ist.

### <a name="to-open-a-standard-editor-for-an-open-file"></a>So öffnen Sie einen Standard Editor für eine geöffnete Datei

1. Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> auf.

     Diese Methode überprüft zunächst, ob das Dokument nicht bereits geöffnet ist, indem aufgerufen wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> . Wenn das Dokument bereits geöffnet ist, wird das Editor Fenster wieder geöffnet.

2. Wenn das Dokument nicht geöffnet ist, führen Sie die Schritte unter Gewusst [wie: Öffnen von Standard-Editoren](../extensibility/how-to-open-standard-editors.md)aus.

## <a name="see-also"></a>Weitere Informationen
- [Öffnen und Speichern von Projekt Elementen](../extensibility/internals/opening-and-saving-project-items.md)
- [Gewusst wie: Öffnen von projektspezifischen Editoren](../extensibility/how-to-open-project-specific-editors.md)
- [Vorgehensweise: Öffnen von Standard-Editoren](../extensibility/how-to-open-standard-editors.md)
