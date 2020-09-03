---
title: Versionsnummern für Hauptassemblys und lokalisierte Satellitenassemblys | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aa064d875d5354ac4ae1fc5fdd8493c5efbbee01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663046"
---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>Versionsnummern für Hauptassemblys und lokalisierte Satellitenassemblys
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die <xref:System.Resources.SatelliteContractVersionAttribute>-Klasse bietet Unterstützung bei der Versionsverwaltung für eine Hauptassembly, die lokalisierte Ressourcen mithilfe des Ressourcen-Managers verwendet. Das Anwenden der <xref:System.Resources.SatelliteContractVersionAttribute> auf die Hauptassembly einer Anwendung ermöglicht es Ihnen, die Assembly zu aktualisieren und erneut bereitzustellen, ohne die Satellitenassemblys upzudaten. Beispielsweise können Sie die <xref:System.Resources.SatelliteContractVersionAttribute>-Klasse mit einem Service Pack verwenden, das keine neuen Ressourcen einbringt, ohne die Satellitenassemblys neu zu erstellen und erneut bereitzustellen. Damit Ihre lokalisierten Ressourcen zur Verfügung stehen, muss die Satellitenvertragsversion der Hauptassembly mit der <xref:System.Reflection.AssemblyVersionAttribute>-Klasse der Satellitenassemblys übereinstimmen. Sie müssen eine genaue Versionsnummer in <xref:System.Resources.SatelliteContractVersionAttribute> angeben; Platzhalterzeichen wie „*“ sind ungültig. Weitere Informationen finden Sie unter [Abrufen von Ressourcen in Desktop-Apps](https://msdn.microsoft.com/library/eca16922-1c46-4f68-aefe-e7a12283641f).

## <a name="updating-assemblies"></a>Aktualisieren von Assemblys
 Mit der <xref:System.Resources.SatelliteContractVersionAttribute>-Klasse können Sie eine Hauptassembly aktualisieren, ohne die Satellitenassembly aktualisieren zu müssen oder umgekehrt. Wenn die Hauptassembly aktualisiert wird, wird die Versionsnummer der Assembly geändert. Wenn Sie weiterhin die vorhandenen Satellitenassemblys verwenden möchten, ändern Sie die Versionsnummer der Hauptassembly, aber lassen Sie die Versionsnummer des Satellitenvertrags unverändert. Beispielsweise kann die Hauptassemblyversion im ersten Release 1.0.0.0 sein. Die Satellitenvertragsversion und die Assemblyversion der Satellitenassembly werden ebenfalls 1.0.0.0 sein. Wenn Sie die Hauptassembly für ein Service Pack aktualisieren müssen, können Sie die Assemblyversion zu 1.0.0.1 ändern, während Sie für die Satellitenvertragsversion und die Satellitenassemblyversion 1.0.0.0 beibehalten.

 Wenn Sie eine Satellitenassembly, jedoch nicht die Hauptassembly aktualisieren müssen, ändern Sie die <xref:System.Reflection.AssemblyVersionAttribute> der Satellitenassembly. Zusammen mit der Satellitenassembly müssen Sie eine Richtlinienassembly bereitstellen, die besagt, dass die neue Satellitenassembly mit der alten Satellitenassembly kompatibel ist. Weitere Informationen zu Richtlinien finden Sie unter [So sucht Common Language Runtime nach Assemblys](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).

 Im folgenden Codebeispiel wird veranschaulicht, wie die Satellitenvertragsversion festgelegt wird. Der Code kann in ein Buildskript, die AssemblyInfo.vb-Datei oder die AssemblyInfo.cs-Datei eingefügt werden.

```vb
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>

```

```csharp
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]
```

## <a name="see-also"></a>Weitere Informationen
 [Wie die](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34) Common Language Runtime Assemblys nach Assemblys festlegt, die die Sicherheit von Assemblyattributen [Setting Assembly Attributes](https://msdn.microsoft.com/library/36a98a81-b5b5-4c19-912a-11f91eff7f4e) [und lokalisierte Satellitenassemblys](../ide/security-and-localized-satellite-assemblies.md) [lokalisieren](../ide/localizing-applications.md) [Globalizing and Localizing Applications](../ide/globalizing-and-localizing-applications.md)
