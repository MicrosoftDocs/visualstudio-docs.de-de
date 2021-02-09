---
title: Bereitstellen von Rückgängigmachen für Designer | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die Rückgängig-Unterstützung in Designern bereitstellen, entweder automatisch oder mithilfe von Features im Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9e8b7ea0dc29e4f8df9113963a95c363998c758d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850467"
---
# <a name="supply-undo-support-to-designers"></a>Unterstützung für die Bereitstellung für Designer

Designer, wie Editoren, müssen üblicherweise rückgängig-Vorgänge unterstützen, damit Benutzer ihre aktuellen Änderungen beim Ändern eines Code Elements umkehren können.

Die meisten Designer, die in Visual Studio implementiert werden, verfügen über eine automatische Rückgängig-Unterstützung durch die Umgebung.

Designer Implementierungen, die Unterstützung für die Rückgängig-Funktion bereitstellen müssen:

- Bereitstellen der rückgängig-Verwaltung durch Implementieren der abstrakten Basisklasse <xref:System.ComponentModel.Design.UndoEngine>

- Unterstützung für Persistenz und CodeDom durch Implementieren der <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> -Klasse und der-  <xref:System.ComponentModel.Design.IComponentChangeService> Klasse.

Weitere Informationen zum Schreiben von Designern mithilfe von .NET Framework finden Sie [unter Erweitern der Design-Time Unterstützung](/previous-versions/37899azc(v=vs.140)).

[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]Bietet eine standardmäßige rückgängig-Infrastruktur durch:

- Bereitstellen von rückgängig-Verwaltungs Implementierungen durch die <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> Klassen und.

- Bereitstellen von Persistenz und CodeDom-Unterstützung durch die Standard <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> -und- <xref:System.ComponentModel.Design.IComponentChangeService> Implementierungen

## <a name="obtain-undo-support-automatically"></a>Rückgängig-Unterstützung automatisch abrufen

Jeder in Visual Studio erstellte Designer verfügt über eine automatische und vollständige Rückgängig-Unterstützung, wenn, der Designer:

- Verwendet eine- <xref:System.Windows.Forms.Control> basierte-Klasse für die Benutzeroberfläche.

- Verwendet die CodeDom-basierte CodeDom-basierte Codegenerierung und das-Modell für die Codegenerierung und-Persistenz.

   Weitere Informationen zum Arbeiten mit der Unterstützung von Visual Studio-CodeDom finden Sie unter generieren [und Kompilieren von dynamischem Quellcode](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation).

## <a name="when-to-use-explicit-designer-undo-support"></a>Verwendungszwecke des expliziten Designer Rückgängigmachen
 Designer müssen eine eigene rückgängig-Verwaltung bereitstellen, wenn Sie eine grafische Benutzeroberfläche verwenden, die als Ansichts Adapter bezeichnet wird, und nicht die von bereitgestellte <xref:System.Windows.Forms.Control> .

 Ein Beispiel hierfür ist das Erstellen eines Produkts mit einer webbasierten grafischen Entwurfs Schnittstelle anstelle einer .NET Framework basierten grafischen Oberfläche.

 In solchen Fällen muss dieser Ansichts Adapter mit Visual Studio registriert <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute> werden, und es muss eine explizite rückgängig-Verwaltung bereitgestellt werden.

 Designer müssen CodeDom-und persistenzunterstützung bereitstellen, wenn Sie das im Namespace bereitgestellte Visual Studio Code-Generierungs Modell nicht verwenden <xref:System.CodeDom> .

## <a name="undo-support-features-of-the-designer"></a>Rückgängig-Unterstützungsfunktionen des Designers
 Das Environment SDK stellt Standard Implementierungen von Schnittstellen bereit, die zum Bereitstellen der Rückgängig-Unterstützung erforderlich sind, die von Designern verwendet werden kann, die keine- <xref:System.Windows.Forms.Control> basierten Klassen für Ihre Benutzeroberflächen oder das standardmäßige CodeDom und

 Die- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Klasse wird von der .NET Framework- <xref:System.ComponentModel.Design.UndoEngine> Klasse mithilfe einer Implementierung der- <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> Klasse zum Verwalten von rückgängig-Vorgängen abgeleitet.

 Visual Studio stellt dem Designer die folgende Funktion zum Rückgängigmachen bereit:

- Verknüpfte Rückgängig-Funktionalität über mehrere Designer hinweg.

- Untergeordnete Einheiten innerhalb eines Designers können durch Implementieren von und in mit ihren übergeordneten Elementen interagieren <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> .

Das Environment SDK bietet CodeDom-und persistenzunterstützung durch Folgendes:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> als Implementierung des <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- Ein, <xref:System.ComponentModel.Design.IComponentChangeService> der vom Visual Studio-Entwurfs Host bereitgestellt wird.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Verwenden der Umgebungs-SDK-Features zum Bereitstellen von rückgängig

Um die Rückgängig-Unterstützung zu erhalten, muss ein Objekt, das einen Designer implementiert, eine Instanz der- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Klasse mit einer gültigen Implementierung instanziieren und initialisieren <xref:System.IServiceProvider> . Diese <xref:System.IServiceProvider> Klasse muss die folgenden Dienste bereitstellen:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Designer, die die CodeDom-Serialisierung von Visual Studio verwenden, wählen möglicherweise die Verwendung <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> von mit der [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] als-Implementierung von <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .

   In diesem Fall sollte die <xref:System.IServiceProvider> Klasse, die für den Konstruktor bereitgestellt wird, <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> dieses Objekt als Implementierung der-Klasse zurückgeben <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Designer, die den <xref:System.ComponentModel.Design.DesignSurface> vom Visual Studio-Entwurfs Host bereitgestellten Standardwert verwenden, verfügen über eine Standard Implementierung der- <xref:System.ComponentModel.Design.IComponentChangeService> Klasse.

Designer, die einen basierten rückgängigmechanismus implementieren, verfolgen <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Änderungen automatisch nach.

- Eigenschafts Änderungen werden über das- <xref:System.ComponentModel.TypeDescriptor> Objekt vorgenommen.

- <xref:System.ComponentModel.Design.IComponentChangeService> Ereignisse werden manuell generiert, wenn ein Commit für eine nicht behebbare Änderung ausgeführt wird.

- Die Änderung des Designers wurde im Kontext eines erstellt <xref:System.ComponentModel.Design.DesignerTransaction> .

- Der Designer wählt das explizite Erstellen von rückgängig-Einheiten mithilfe der standardmäßigen Rückgängig-Komponente aus, die von einer Implementierung von <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> oder der Visual Studio-spezifischen Implementierung bereitgestellt <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> wird. diese wird von abgeleitet <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> und stellt außerdem eine Implementierung von <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> und bereit <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> .

## <a name="see-also"></a>Weitere Informationen

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Erweitern der Design-Time Unterstützung](/previous-versions/37899azc(v=vs.140))
