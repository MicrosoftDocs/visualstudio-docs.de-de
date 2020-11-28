---
title: Verwalten von Anwendungsressourcen (.NET)
description: Erfahren Sie, wie Sie Anwendungsressourcendateien verwalten, die nicht Teil des Kompilierungsvorgangs sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- Resource Designer
- resources [Visual Studio]
- Resources page in Project Designer
- application resources [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4707a3e33279ead458566bc01ed2eed8c67355cf
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596741"
---
# <a name="manage-application-resources-net"></a>Verwalten von Anwendungsressourcen (.NET)

Ressourcendateien sind Dateien, die Teil einer Anwendung sind, jedoch noch nicht kompiliert sind, beispielsweise Symboldateien oder Audiodateien. Da diese Dateien nicht Teil des Kompilierungsprozesses sind, können Sie sie ändern, ohne Ihre Binärdateien neu zu kompilieren. Wenn Sie beabsichtigen, die Anwendung zu lokalisieren, verwenden Sie beim Lokalisieren Ressourcendateien für alle Zeichenfolgen und anderen Ressourcen, die geändert werden müssen.

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Verwalten von Anwendungsressourcen (Visual Studio für Mac)](/visualstudio/mac/managing-app-resources).

Weitere Informationen zu Ressourcen in .NET-Apps finden Sie unter [Ressourcen in .NET-Apps](/dotnet/framework/resources/index).

## <a name="work-with-resources"></a>Arbeiten mit Ressourcen

Öffnen Sie das Projekteigenschaftenfenster in einem Projekt mit verwaltetem Code. Sie können das Eigenschaftenfenster öffnen, indem Sie Folgendes durchführen:

- Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten, und wählen Sie dann **Eigenschaften** aus.
- Geben Sie im Suchfeld, das Sie über **STRG**+**Q** aufrufen, den Begriff **Projekteigenschaften** ein.
- Drücken von **ALT**+**EINGABE** im **Projektmappen-Explorer**

Wählen Sie die Registerkarte **Ressourcen** aus. Sie können eine *RESX-Datei* hinzufügen, wenn das Projekt noch keine enthält, sowie verschiedene Arten von Ressourcen hinzufügen und löschen und vorhandene Ressourcen ändern.

## <a name="resources-in-other-project-types"></a>Ressourcen in anderen Projekttypen

Ressourcen werden in .NET-Projekten anders verwaltet als in anderen Projekttypen. Weitere Informationen zu folgenden Themen finden Sie unter:

- zu Universelle Windows-Plattform-Apps (UWP): [App-Ressourcen und das Ressourcenverwaltungssystem](/windows/uwp/app-resources/)
- Weitere Informationen zu C++-Projekten finden Sie unter [Arbeiten mit Ressourcendateien](/cpp/windows/working-with-resource-files) und [Vorgehensweise: Erstellen einer Ressource](/cpp/windows/how-to-create-a-resource).

## <a name="see-also"></a>Siehe auch

- [Resources in .NET-Apps (.NET Framework)](/dotnet/framework/resources/index)
- [Verwalten von Anwendungsressourcen (Visual Studio für Mac)](/visualstudio/mac/managing-app-resources)
