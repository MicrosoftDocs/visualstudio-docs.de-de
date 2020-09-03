---
title: 'Vorgehensweise: Öffnen von projektspezifischen Editoren | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22106ea09f86e3d61fe7aaa6e86e6e99c002f32d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905809"
---
# <a name="how-to-open-project-specific-editors"></a>Gewusst wie: Öffnen von projektspezifischen Editoren
Wenn eine Element Datei, die von einem Projekt geöffnet wird, intrinsisch an den jeweiligen Editor für dieses Projekt gebunden ist, muss das Projekt die Datei mit einem projektspezifischen Editor öffnen. Die Datei kann nicht an den IDE-Mechanismus für die Auswahl eines Editors delegiert werden. Anstatt z. b. einen Standard-Bitmap-Editor zu verwenden, können Sie mit dieser projektspezifischen Editor-Option einen bestimmten Bitmap-Editor angeben, der Informationen in der Datei erkennt, die für Ihr Projekt eindeutig ist.

 Die IDE Ruft die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Methode auf, wenn Sie bestimmt, dass eine Datei von einem bestimmten Projekt geöffnet werden soll. Weitere Informationen finden Sie unter [Anzeigen von Dateien mit dem Befehl "Datei öffnen](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)". Verwenden Sie die folgenden Richtlinien, um die- `OpenItem` Methode zu implementieren, damit das Projekt eine Datei mithilfe eines projektspezifischen Editors öffnet.

## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>So implementieren Sie die OpenItem-Methode mit einem projektspezifischen Editor

1. Wenden Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> Methode ( `RDT_EditLock` ) an, um zu bestimmen, ob die Datei (Dokument Datenobjekt) bereits geöffnet ist.

    > [!NOTE]
    > Weitere Informationen zu Dokument Daten und Dokument Ansichts Objekten finden Sie unter [Dokument Daten und Dokument Ansicht in benutzerdefinierten Editoren](../extensibility/document-data-and-document-view-in-custom-editors.md).

2. Wenn die Datei bereits geöffnet ist, können Sie die Datei durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> -Methode neu anordnen und den Wert IDO_ActivateIfOpen für den- `grfIDO` Parameter angeben.

     Wenn die Datei geöffnet ist und das Dokument im Besitz eines anderen Projekts als dem aufrufenden Projekt ist, wird dem Benutzer eine Warnung angezeigt, dass der zu öffnende Editor von einem anderen Projekt aus angezeigt wird. Das Datei Fenster wird dann angezeigt.

3. Wenn Ihr Text Puffer (Dokument Datenobjekt) bereits geöffnet ist und Sie eine weitere Ansicht an ihn anfügen möchten, sind Sie dafür verantwortlich, diese Sicht zu verknüpfen. Die empfohlene Vorgehensweise zum Instanziieren einer Ansicht (Dokument Ansichts Objekt) aus dem Projekt lautet wie folgt:

    1. Ruft für `QueryService` den <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> Dienst auf, um einen Zeiger auf die- <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> Schnittstelle zu erhalten.

    2. Rufen Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> Methode auf, um eine Instanz der Dokument Ansichts Klasse zu erstellen.

4. Ruft die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> Methode auf und gibt das Dokument Ansichts Objekt an.

     Diese Methode zeigt das Dokument Ansichts Objekt in einem Dokument Fenster an.

5. Führen Sie die entsprechenden Aufrufe entweder für die- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> Methode oder die- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> Methode aus.

     An diesem Punkt sollte die Ansicht vollständig initialisiert und geöffnet werden können.

6. Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> -Methode auf, um die Ansicht anzuzeigen und zu öffnen.

## <a name="see-also"></a>Weitere Informationen
- [Öffnen und Speichern von Projekt Elementen](../extensibility/internals/opening-and-saving-project-items.md)
- [Vorgehensweise: Öffnen von Standard-Editoren](../extensibility/how-to-open-standard-editors.md)
- [Gewusst wie: Öffnen von Editoren für geöffnete Dokumente](../extensibility/how-to-open-editors-for-open-documents.md)
