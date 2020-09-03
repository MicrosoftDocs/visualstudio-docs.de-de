---
title: Dialogfeld „Assemblyinformationen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06374f70c2552f3e635ada3bc40ef82d890fb46b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661022"
---
# <a name="assembly-information-dialog-box"></a>Assemblyinformationen (Dialogfeld)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im Dialogfeld **Assemblyinformationen** werden die Werte der globalen [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Assemblyattribute festgelegt, die in der AssemblyInfo-Datei gespeichert sind, die mit dem Projekt automatisch erstellt wird. Im **Projektmappen-Explorer** befindet sich die Datei im Knoten **Mein Projekt** in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] (klicken Sie zum Anzeigen auf **Alle Dateien anzeigen**). Sie befindet sich unter **Eigenschaften** in [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Weitere Informationen zu Assemblyattributen finden Sie unter [Attributes (Attribute)](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205).

 Wählen Sie zum Aufrufen des Dialogfelds im **Projektmappen-Explorer** einen Projektknoten aus, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**. Wenn der **Projekt-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Anwendung** . Klicken Sie auf der Seite **Anwendung** auf die Schaltfläche Assemblyinformationen. **Assembly Information**

## <a name="uielement-list"></a>UIElement-Liste
 **Titel:** Gibt einen Titel für das Assemblymanifest an. Entspricht <xref:System.Reflection.AssemblyTitleAttribute>

 **Beschreibung:** Gibt eine optionale Beschreibung für das Assemblymanifest an. Entspricht <xref:System.Reflection.AssemblyDescriptionAttribute>

 **Firma:** Gibt einen Firmennamen für das Assemblymanifest an. Entspricht <xref:System.Reflection.AssemblyCompanyAttribute>

 **Produkt:** Gibt einen Produktnamen für das Assemblymanifest an. Entspricht <xref:System.Reflection.AssemblyProductAttribute>

 **Copyright:** Gibt Copyrightinformationen für das Assemblymanifest an. Entspricht <xref:System.Reflection.AssemblyCopyrightAttribute>

 **Marke:** Gibt eine Marke für das Assemblymanifest an. Entspricht <xref:System.Reflection.AssemblyTrademarkAttribute>

 **Assemblyversion:** Gibt die Version der Assembly an. Entspricht <xref:System.Reflection.AssemblyVersionAttribute>

 **Dateiversion:** Gibt eine Versionsnummer an, die den Compiler anweist, eine bestimmte Version der Versionsressource der Win32-Datei zu verwenden. Entspricht <xref:System.Reflection.AssemblyFileVersionAttribute>

 **GUID:** Eine eindeutige GUID zur Identifizierung der Assembly. Wenn Sie ein Projekt erstellen, generiert Visual Studio eine GUID für die Assembly. Entspricht <xref:System.Guid>

 **Neutrale Sprache:** Gibt an, welche Kultur die Assembly unterstützt. Entspricht <xref:System.Resources.NeutralResourcesLanguageAttribute> Der Standardwert ist **(None)**.

 **Assembly COM-sichtbar machen:** Gibt an, ob Typen in der Assembly für COM verfügbar sind. Entspricht <xref:System.Runtime.InteropServices.ComVisibleAttribute>

## <a name="see-also"></a>Weitere Informationen
 [Anwendungsseite, Projekt-Designer-Attribute (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md) [Attributes](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
