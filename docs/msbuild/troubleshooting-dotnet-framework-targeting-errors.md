---
title: Problembehandlung bei .NET Framework-Zielversionsfehlern | Microsoft-Dokumentation
description: Erfahren Sie mehr über MSBuild-Fehler aufgrund von Verweisproblemen und die Behebung dieser Fehler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 7b4e6f14eb5ba771ff83b0aa5fedc8ae261ca69d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902627"
---
# <a name="troubleshoot-net-framework-targeting-errors"></a>Problembehandlung bei .NET Framework-Zielversionsfehlern

Dieses Thema beschreibt MSBuild-Fehler, die aufgrund von Verweisproblemen auftreten könnten, und wie Sie diese Fehler auflösen können.

## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Sie haben auf ein Projekt oder eine Assembly verwiesen, das bzw. die auf eine andere Version von .NET Framework abzielt

 Sie können Anwendungen erstellen, die auf Projekte oder Assemblys verweisen, die auf andere Versionen von .NET Framework abzielen. Beispielsweise können Sie eine Anwendung erstellen, die auf das Clientprofil für .NET Framework 4 abzielt, aber auf eine Assembly verweist, die auf .NET Framework 2.0 ausgerichtet ist. Wenn Sie jedoch ein Projekt erstellen, das auf eine frühere Version von .NET Framework abzielt, können Sie keinen Verweis in diesem Projekt auf ein Projekt oder eine Assembly festlegen, die auf das Clientprofil für .NET Framework 4 oder .NET Framework 4 selbst abzielt. Um den Fehler aufzulösen, stellen Sie sicher, dass die Anwendung auf ein Profil oder Profile abzielt, die mit dem Profil kompatibel sind, auf die die Projekte oder Assemblys abzielen, auf die Ihre Anwendung verweist.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Sie haben ein Projekt einer anderen Version von .NET Framework neu zugewiesen

 Wenn Sie die Zielversion von .NET Framework für Ihre Anwendung ändern, ändert Visual Studio einige Verweise, aber Sie müssen möglicherweise einige Verweise manuell aktualisieren. Einer der oben erwähnten Fehler könnte z. B. auftreten, wenn Sie eine Anwendung so ändern, dass sie auf .NET Framework 3.5 Service Pack 1 abzielt, und diese Anwendung Ressourcen oder Einstellungen umfasst, die vom Clientprofil für .NET Framework 4 abhängen.

 Um die Anwendungseinstellungen zu umgehen, öffnen Sie den **Projektmappen-Explorer**, wählen Sie **Alle Dateien anzeigen**, und bearbeiten Sie dann die Datei *app.config* im XML-Editor von Visual Studio. Ändern Sie die Version in den Einstellungen auf die entsprechende Version von .NET Framework. Beispielsweise können Sie die Versionseinstellung von 4.0.0.0 in 2.0.0.0 ändern. Öffnen Sie auf ähnliche Weise für eine Anwendung, der Ressourcen hinzugefügt wurden, den **Projektmappen-Explorer**, wählen Sie die Schaltfläche **Alle Dateien anzeigen**, erweitern Sie **Mein Projekt** (Visual Basic) oder **Eigenschaften** (C#), und bearbeiten Sie dann die Datei *Resources.resx* im XML-Editor von Visual Studio. Ändern Sie die Versionseinstellung von 4.0.0.0 in 2.0.0.0.

 Wenn die Anwendung über Ressourcen wie Symbole oder Bitmaps oder Einstellungen wie Datenverbindungs-Zeichenfolgen verfügt, können Sie die Fehler auch auflösen, indem Sie alle Elemente auf der Seite **Einstellungen** auf der **Projekt-Designers** entfernen und dann die erforderlichen Einstellungen erneut hinzufügen.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Sie haben ein Projekt einer anderen Version von .NET Framework neu zugewiesen, und die Verweise werden nicht aufgelöst

 Wenn Sie ein Projekt einer anderen Version von .NET Framework neu zuweisen, werden die Verweise in einigen Fällen vielleicht nicht korrekt aufgelöst. Explizite vollqualifizierte Verweise auf Assemblys führen häufig zu diesem Problem, jedoch können Sie es auflösen, indem Sie die Verweise entfernen, die nicht aufgelöst werden, und dann wieder dem Projekt hinzufügen. Als Alternative können Sie die Projektdatei bearbeiten, um die Verweise zu ersetzen. Zunächst entfernen Sie Verweise in folgender Form:

```xml
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />
```

 Dann ersetzen Sie sie durch die einfache Form:

```xml
<Reference Include="System.ServiceModel" />
```

> [!NOTE]
> Nach Schließen und erneutem Öffnen des Projekts sollten Sie es auch neu erstellen, um sicherzustellen, dass alle Verweise ordnungsgemäß aufgelöst werden.

## <a name="see-also"></a>Weitere Informationen

- [Vorgehensweise: .NET Framework-Version als Ziel](../ide/visual-studio-multi-targeting-overview.md)
- [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile)
- [Übersicht über Frameworkziele](../ide/visual-studio-multi-targeting-overview.md)
- [Festlegen von Zielversionen](../msbuild/msbuild-multitargeting-overview.md)
