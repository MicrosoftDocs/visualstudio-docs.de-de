---
title: Übersicht über das Visio-Objektmodell
description: Erfahren Sie, wie Sie mit dem Visio-Objektmodell interagieren können, um Office-Lösungen für Microsoft Visio zu entwickeln.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Visio
- objects [Office development in Visual Studio], Office object models
- Office object models
- Visio object model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8d7a83b5a900defb63ceffe4f63d57e2b200c47b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921780"
---
# <a name="visio-object-model-overview"></a>Übersicht über das Visio-Objektmodell
  Zur Entwicklung von Office-Projektmappen für Microsoft Office Visio können Sie mit dem Visio-Objektmodell interagieren. Dieses Objektmodell besteht aus Klassen und Schnittstellen, die in der primären Interopassembly für Visio bereitgestellt und im `Microsoft.Office.Interop.Visio`-Namespace definiert werden.

 Dieses Thema enthält eine kurze Übersicht über das Visio-Objektmodell. Informationen zur Verwendung des Visio-Objektmodells für bestimmte Aufgaben in Office-Projekten finden Sie unter den folgenden Themen:

- [Arbeiten mit Visio-Dokumenten](../vsto/working-with-visio-documents.md)

- [Arbeiten mit Visio-Shapes](../vsto/working-with-visio-shapes.md)

## <a name="understand-the-visio-object-model"></a>Grundlegendes zum Visio-Objektmodell
 Visio stellt zahlreiche Objekte bereit, mit denen Sie interagieren können. Diese Objekte werden in einer Hierarchie angeordnet, die eng an die Benutzeroberfläche angelehnt ist. Oben in der Hierarchie befindet sich das [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application) -Objekt. Dieses Objekt stellt die aktuelle Instanz von Visio dar. Das `Microsoft.Office.Interop.Visio.Application` -Objekt enthält die `Microsoft.Office.Interop.Visio.Document` -und- `Microsoft.Office.Interop.Visio.Page` Objekte sowie die `Microsoft.Office.Interop.Visio.Documents` -Auflistung und die-Auflistung `Microsoft.Office.Interop.Visio.Pages` . Jedes dieser Objekte bzw. jede dieser Auflistungen verfügt über zahlreiche Methoden und Eigenschaften, auf die Sie zwecks Bearbeitung und Interaktion zugreifen können.

 Weitere Informationen finden Sie in der VBA-Referenzdokumentation für die Objekte [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application), [Microsoft.Office.Interop.Visio.Document](/office/vba/api/Visio.Document)und [Microsoft.Office.Interop.Visio.Page](/office/vba/api/Visio.Page) sowie für die Auflistungen [Microsoft.Office.Interop.Visio.Documents](/office/vba/api/Visio.Documents) und [Microsoft.Office.Interop.Visio.Pages](/office/vba/api/Visio.Pages) .

 In den folgenden Abschnitten werden die Objekte der obersten Ebene und ihre Interaktion miteinander kurz beschrieben. Dazu gehören die folgenden Objekte:

- Anwendungsobjekt

- Document-Objekt

- Page-Objekt

### <a name="application-object"></a>Anwendungsobjekt
 Das Microsoft. Office. Interop. Visio. Application-Objekt stellt die Visio-Anwendung dar und ist das übergeordnete Element aller anderen Objekte. Seine Elemente gelten normalerweise für Visio als Ganzes. Sie können die Eigenschaften und Methoden der Microsoft. Office. Interop. Visio. Application-und- `Microsoft.Office.Interop.Visio.ApplicationSettings` Objekte verwenden, um die Visio-Umgebung zu steuern.

 In VSTO-Add-in-Projekten können Sie auf das Microsoft. Office. Interop. Visio. Application-Objekt zugreifen, indem Sie das- `Application` Feld der- `ThisAddIn` Klasse verwenden. Weitere Informationen finden Sie unter [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).

### <a name="document-object"></a>Document-Objekt
 Das Microsoft.Office.Interop.Visio.Document-Objekt ist für die Programmierung von Visio von zentraler Bedeutung. Es stellt eine Zeichnungs-, Schablonen- oder Vorlagendatei dar. Wenn Sie ein Visio-Dokument öffnen oder ein neues Dokument erstellen, erstellen Sie ein neues Microsoft.Office.Interop.Visio.Doc-Enumeratorobjekt, das der Microsoft.Office.Interop.Visio.Docum-Auflistung des Microsoft. Office. Interop. Visio. Application-Objekts hinzugefügt wird.

 Das Dokument, das den Fokus besitzt, wird als das aktive Dokument bezeichnet. Sie wird durch die- `Microsoft.Office.Interop.Visio.Application.ActiveDocument` Eigenschaft des Microsoft. Office. Interop. Visio. Application-Objekts dargestellt.

### <a name="page-object"></a>Page-Objekt
 Das Microsoft. Office. Interop. Visio. Page-Objekt stellt den Zeichnungs Bereich einer Vordergrund Seite oder einer Hintergrundseite dar. Mithilfe der `Microsoft.Office.Interop.Visio.Page.Background`-Eigenschaft können Sie feststellen, ob es sich bei der Seite um eine Vorder- oder Hintergrundseite handelt.

 Zum Erstellen von Shapes können Sie Methoden wie die `Microsoft.Office.Interop.Visio.Page.DrawSpline`-Methode und die `Microsoft.Office.Interop.Visio.Page.DrawOval`-Methode verwenden. Darüber hinaus können Sie Masters aus Schablonen abrufen und die Shapes mithilfe der `Microsoft.Office.Interop.Visio.Page.Drop`-Methode oder `Microsoft.Office.Interop.Visio.Page.DropMany`-Methode auf einer Seite platzieren.

## <a name="use-the-visio-object-model-documentation"></a>Verwenden der Dokumentation zum Visio-Objektmodell
 Ausführliche Informationen zum Visio-Objektmodell finden Sie in der VBA-Objektmodellreferenz für Visio. Die VBA-Objektmodellreferenz dokumentiert das Visio-Objektmodell, das für VBA (Visual Basic for Applications) verfügbar gemacht wird. Weitere Informationen finden Sie unter [Visio-Objektmodell Referenz](/office/vba/api/overview/visio/object-model).

 Alle Objekte und Member in der VBA-Objektmodellreferenz entsprechen Typen und Membern in der primären Interopassembly (PIA) für Visio. Das `Document` Objekt in der VBA-Objektmodell Referenz entspricht z. b. dem Microsoft.Office.Interop.Visio.Docenumerentyp in der Visio-Pia. Obwohl die VBA-Objektmodellreferenz Codebeispiele für die meisten Eigenschaften, Methoden und Ereignisse enthält, müssen Sie den VBA-Code in dieser Referenz in Visual Basic oder Visual C# übersetzen, wenn Sie ihn in einem mit Visual Studio erstellten Visio VSTO-Add-In-Projekt verwenden möchten.

> [!NOTE]
> Derzeit ist keine Referenzdokumentation für die primäre Interopassembly für Visio verfügbar.

 Verwandte Codebeispiele und weitere Tools zum Erstellen von Visio-Lösungen finden Sie unter [Visio 2010 Software Development Kit](https://www.microsoft.com/download/details.aspx?id=12365).

### <a name="additional-types-in-primary-interop-assemblies"></a>Zusätzliche Typen in primären Interop-Assemblys
 Primäre Interopassemblys können Typen enthalten, die aufgrund von Unterschieden bei der Implementierung nicht für VBA sichtbar sind. VBA bietet eine Ansicht des Visio-Objektmodells, das nur die Objekte und Member enthält, die Sie direkt verwenden können. Die primären Interopassemblys machen das gleiche Objektmodell verfügbar, enthalten zusätzlich aber weitere Schnittstellen, Klassen und Member, die Objekte im COM-Objektmodell in verwalteten Code übersetzen. Diese zusätzlichen Elemente sollten nicht direkt im Code verwendet werden.

 Weitere Informationen finden Sie unter [Übersicht über Klassen und Schnittstellen in den primären](/previous-versions/office/office-12/ms247299(v=office.12)) Interopassemblys für Office und [primäre Interop](../vsto/office-primary-interop-assemblies.md)-Assemblys in Office.

## <a name="see-also"></a>Weitere Informationen
- [Visio-Lösungen](../vsto/visio-solutions.md)
- [Arbeiten mit Visio-Dokumenten](../vsto/working-with-visio-documents.md)
- [Arbeiten mit Visio-Shapes](../vsto/working-with-visio-shapes.md)
