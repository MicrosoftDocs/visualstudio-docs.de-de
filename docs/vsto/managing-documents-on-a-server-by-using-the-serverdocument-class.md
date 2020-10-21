---
title: Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e91653734b804693584808478e44443563cdb823
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "92298272"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse
  Sie können die- `ServerDocument` Klasse im verwenden [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , um verschiedene Aspekte von Anpassungen auf Dokument Ebene zu verwalten, auch wenn Microsoft Office Word und Microsoft Office Excel nicht installiert sind. Sie können die folgenden Aufgaben ausführen:

- Zugreifen auf und Ändern von Daten im Datencache eines Dokuments oder einer Arbeitsmappe. Weitere Informationen finden Sie unter [Arbeiten mit zwischengespeicherten Daten im Dokument](#CachedData).

- Verwalten der Anpassungsassembly, die einem Dokument zugeordnet ist. Weitere Informationen finden Sie unter [Verwalten der Dokument Anpassung](#CustomizationInfo).

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="understand-the-serverdocument-class"></a>Grundlegendes zur ServerDocument-Klasse
 Die `ServerDocument`-Klasse kann auf Computern verwendet werden, auf denen Office nicht installiert ist. Daher wird diese Klasse üblicherweise in Anwendungen verwendet, die nicht in Office integriert sind, z. B. Konsolenprojekte oder Windows Forms-Projekte, im Gegensatz zu Office-Projekten. Verwenden Sie die- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse in der *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* -Assembly.

 Die `ServerDocument`-Klasse kann für Anpassungen auf Dokumentebene verwendet werden, die mit [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] erstellt wurden.

 Weitere Informationen über die Visual Studio 2010-Tools für Office-Laufzeit und die Office-Erweiterungen für die .NET Framework finden Sie unter [Visual Studio-Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).

> [!NOTE]
> Wenn Sie über eine Legacy Anwendung verfügen, die die- `ServerDocument` Klasse im `Visual Studio Tools for Office` System (Version 3,0 Runtime) verwendet, `Visual Studio Tools for Office` muss das System (Version 3,0 Runtime) auf Computern installiert sein, auf denen die Anwendung ausgeführt wird. `Visual Studio 2010 Tools for Office runtime`Diese Anwendungen können von nicht ausgeführt werden.

## <a name="work-with-cached-data-in-the-document"></a><a name="CachedData"></a> Arbeiten mit zwischengespeicherten Daten im Dokument
 Die `ServerDocument`-Klasse stellt Member bereit, die Sie verwenden können, um mit dem Datencache in angepassten Dokumenten zu arbeiten. Weitere Informationen zu zwischengespeicherten Daten finden Sie unter zwischen [Speichern von Daten](../vsto/caching-data.md) und [zugreifen auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md).

 In der folgenden Tabelle werden die Member aufgeführt, die Sie verwenden können, um mit zwischengespeicherten Daten zu arbeiten.

|Aufgabe|Zu verwendender Member|
|----------|-------------------|
|Bestimmen, ob ein Dokument über einen Datencache verfügt|Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> -Methode.|
|Zugreifen auf die zwischengespeicherten Daten in einem Dokument<br /><br /> Weitere Informationen finden Sie unter [zugreifen auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md).|Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>-Eigenschaft|

## <a name="manage-the-document-customization"></a><a name="CustomizationInfo"></a> Verwalten der Dokument Anpassung
 Sie können Member der `ServerDocument`-Klasse zum Verwalten der Anpassungsassembly verwenden, die einem Dokument zugeordnet ist. Sie können z. B. die Anpassung aus einem Dokument programmgesteuert entfernen, sodass das Dokument nicht mehr Teil einer Anpassung ist.

 In der folgenden Tabelle werden die Member, mit denen Sie die Anpassungsassembly verwalten können, aufgeführt.

|Aufgabe|Zu verwendender Member|
|----------|-------------------|
|Ermitteln, ob ein Dokument Teil einer Anpassung auf Dokumentebene ist|Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> -Methode.|
|Programmgesteuertes Anfügen einer Anpassung an ein Dokument zur Laufzeit<br /><br /> Weitere Informationen finden Sie unter Gewusst [wie: Anfügen von Erweiterungen durch verwalteten Code an Dokumente](../vsto/how-to-attach-managed-code-extensions-to-documents.md) .|Eine der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>-Methoden|
|Programmgesteuertes Entfernen einer Anpassung aus einem Dokument zur Laufzeit<br /><br /> Weitere Informationen finden Sie unter Gewusst [wie: Entfernen von Erweiterungen durch verwalteten Code aus Dokumenten](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> -Methode.|
|Abrufen der URL des Bereitstellungsmanifests, das dem Dokument zugeordnet ist|Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>-Eigenschaft|

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Anfügen von Erweiterungen durch verwalteten Code an Dokumente](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
- [Gewusst wie: Entfernen von Erweiterungen durch verwalteten Code aus Dokumenten](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Übersicht über Visual Studio-Tools für Office-Laufzeit](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Daten zwischenspeichern](../vsto/caching-data.md)
