---
title: Problembehandlung bei .NET Framework-Zielversionsfehlern | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: troubleshooting
f1_keywords:
- vs.FrameworkTargetingErrors
- MSBuild.ResolveAssemblyReference.FailedToResolveReferenceBecausePrimaryAssemblyInExclusionList
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], .NET Framework Client Profile
- multi-targeting
- multitargeting
- .NET Framework Client Profile
ms.assetid: 830e3e45-9a93-4279-a249-75b84599aefb
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ae55e34f929acca6c708dfc39477f3bd6546f53f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703785"
---
# <a name="troubleshooting-net-framework-targeting-errors"></a>Problembehandlung bei .NET Framework-Zielversionsfehlern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieses Thema beschreibt MSBuild-Fehler, die aufgrund von Verweisproblemen auftreten könnten, und wie Sie diese Fehler auflösen können.  
  
## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Sie haben auf ein Projekt oder eine Assembly verwiesen, das bzw. die auf eine andere Version von .NET Framework abzielt  
 Sie können Anwendungen erstellen, die auf Projekte oder Assemblys verweisen, die auf eine andere Version von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] abzielen. Beispielsweise können Sie eine Anwendung erstellen, die auf das Clientprofil für [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] abzielt, aber auf eine Assembly verweist, die auf .NET Framework 2.0 ausgerichtet ist. Wenn Sie jedoch ein Projekt erstellen, das auf eine frühere Version von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] abzielt, können Sie keinen Verweis in diesem Projekt auf ein Projekt oder eine Assembly festlegen, die auf das Clientprofil für [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] oder [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] selbst abzielt. Um den Fehler aufzulösen, stellen Sie sicher, dass die Anwendung auf ein Profil oder Profile abzielt, die mit dem Profil kompatibel sind, auf die die Projekte oder Assemblys abzielen, auf die Ihre Anwendung verweist.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Sie haben ein Projekt einer anderen Version von .NET Framework neu zugewiesen  
 Wenn Sie die Zielversion von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] für Ihre Anwendung ändern, ändert Visual Studio einige Verweise, aber Sie müssen möglicherweise einige Verweise manuell aktualisieren. Einer der oben erwähnten Fehler könnte z.B. auftreten, wenn Sie eine Anwendung so ändern, dass sie auf [!INCLUDE[net_v35SP1_long](../includes/net-v35sp1-long-md.md)] abzielt, und diese Anwendung verfügt über Ressourcen oder Einstellungen, die vom Clientprofil für [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] abhängen.  
  
 Um die Anwendungseinstellungen zu umgehen, öffnen Sie den **Projektmappen-Explorer**, wählen Sie **Alle Dateien anzeigen**, und bearbeiten Sie dann die Datei app.config im XML-Editor von Visual Studio. Ändern Sie die Version in den Einstellungen auf die entsprechende Version von .NET Framework. Beispielsweise können Sie die Versionseinstellung von 4.0.0.0 in 2.0.0.0 ändern. Öffnen Sie auf ähnliche Weise für eine Anwendung, der Ressourcen hinzugefügt wurden, den **Projektmappen-Explorer**, wählen Sie die Schaltfläche **Alle Dateien anzeigen**, erweitern Sie **Mein Projekt** (Visual Basic) oder **Eigenschaften** (C#), und bearbeiten Sie dann die Datei Resources.resx im XML-Editor von Visual Studio. Ändern Sie die Versionseinstellung von 4.0.0.0 in 2.0.0.0.  
  
 Wenn die Anwendung über Ressourcen wie Symbole oder Bitmaps oder Einstellungen wie Datenverbindungs-Zeichenfolgen verfügt, können Sie die Fehler auch auflösen, indem Sie alle Elemente auf der Seite **Einstellungen** auf der **Projekt-Designers** entfernen und dann die erforderlichen Einstellungen erneut hinzufügen.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Sie haben ein Projekt einer anderen Version von .NET Framework neu zugewiesen, und die Verweise werden nicht aufgelöst  
 Wenn Sie ein Projekt einer anderen Version von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] neu zuweisen, werden die Verweise in einigen Fällen vielleicht nicht korrekt aufgelöst. Explizite vollqualifizierte Verweise auf Assemblys führen häufig zu diesem Problem, jedoch können Sie es auflösen, indem Sie die Verweise entfernen, die nicht aufgelöst werden, und dann wieder dem Projekt hinzufügen. Als Alternative können Sie die Projektdatei bearbeiten, um die Verweise zu ersetzen. Zunächst entfernen Sie Verweise in folgender Form:  
  
```  
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />  
```  
  
 Dann ersetzen Sie sie durch die einfache Form:  
  
```  
<Reference Include="System.ServiceModel" />  
```  
  
> [!NOTE]
> Nach Schließen und erneutem Öffnen des Projekts sollten Sie es auch neu erstellen, um sicherzustellen, dass alle Verweise ordnungsgemäß aufgelöst werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gewusst wie: Ziel einer Version des .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [.NET Framework Client Profil](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1)   
 [Ziel einer bestimmten .NET Framework Version](../ide/targeting-a-specific-dotnet-framework-version.md)   
 [Festlegen von Zielversionen](../msbuild/msbuild-multitargeting-overview.md)
