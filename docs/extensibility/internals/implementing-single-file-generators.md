---
title: Implementieren von Single-File Generatoren | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein benutzerdefiniertes Tool verwenden, das die IVsSingleFileGenerator-Schnittstelle implementiert, um Visual Basic und Visual c#-Projektsysteme in Visual Studio zu erweitern.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e353101c7932e06042b451360b7ca040adcb303f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839949"
---
# <a name="implementing-single-file-generators"></a>Implementieren von Generatoren einzelner Dateien
Ein benutzerdefiniertes Tool – manchmal auch als ein einzelner Datei Generator bezeichnet – kann verwendet werden, um die [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] -und- [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Projektsysteme in zu erweitern [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Ein benutzerdefiniertes Tool ist eine COM-Komponente, die die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Schnittstelle implementiert. Mithilfe dieser Schnittstelle transformiert ein benutzerdefiniertes Tool eine einzelne Eingabedatei in eine einzelne Ausgabedatei. Das Ergebnis der Transformation kann Quellcode oder eine beliebige andere Ausgabe sein, die nützlich ist. Zwei Beispiele für benutzerdefinierte, Tool generierte Code Dateien sind Code, der als Reaktion auf Änderungen in einem visuellen Designer generiert wird, sowie Dateien, die mit Web Services Description Language (WSDL) generiert werden.

 Wenn ein benutzerdefiniertes Tool geladen wird oder die Eingabedatei gespeichert wird, ruft das Projekt System die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> -Methode auf und übergibt einen Verweis an eine- <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> Rückruf Schnittstelle, bei der das Tool seinen Fortschritt an den Benutzer melden kann.

 Die Ausgabedatei, die das benutzerdefinierte Tool generiert, wird dem Projekt mit einer Abhängigkeit von der Eingabedatei hinzugefügt. Das Projekt System bestimmt den Namen der Ausgabedatei automatisch basierend auf der Zeichenfolge, die von der Implementierung des benutzerdefinierten Tools zurückgegeben wurde <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> .

 Ein benutzerdefiniertes Tool muss die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Schnittstelle implementieren. Optional unterstützen benutzerdefinierte Tools die- <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> Schnittstelle zum Abrufen von Informationen aus anderen Quellen als der Eingabedatei. Bevor Sie ein benutzerdefiniertes Tool verwenden können, müssen Sie es in jedem Fall beim System oder in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lokalen Registrierung registrieren. Weitere Informationen zum Registrieren von benutzerdefinierten Tools finden Sie unter [Registrieren von einzelnen Datei-Generatoren](../../extensibility/internals/registering-single-file-generators.md).

## <a name="see-also"></a>Weitere Informationen
- [Verfügbarmachen von Typen für visuelle Designer](../../extensibility/internals/exposing-types-to-visual-designers.md)
