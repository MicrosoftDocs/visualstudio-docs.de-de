---
title: Visual Studio SDK | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2dbe2832d52d17047795d1898f0e0bfd8a275bb9
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414383"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Mit dem Visual Studio SDK können Sie Visual Studio-Features erweitern oder neue Funktionen in Visual Studio integrieren. Sie können Ihre Erweiterungen sowohl an andere Benutzer als auch an den Visual Studio Marketplace verteilen. Im Folgenden werden einige Möglichkeiten für die Erweiterung von Visual Studio vorgestellt:

- Hinzufügen von Befehlen, Schaltflächen, Menüs und anderen Benutzeroberflächen Elementen zur IDE

- Tool Fenster für neue Funktionen hinzufügen

- Erweitern von IntelliSense für eine bestimmte Sprache oder Bereitstellen von IntelliSense für neue Programmiersprachen

- Verwenden Sie Glühbirnen, um Hinweise und Vorschläge bereitzustellen, mit denen Entwickler besseren Code schreiben können.

- Aktivieren der Unterstützung für eine neue Sprache

- Hinzufügen eines benutzerdefinierten Projekt Typs

- Erreichen Sie Millionen von Entwicklern über die Visual Studio Marketplace

  Wenn Sie noch nie eine Visual Studio-Erweiterung geschrieben haben, finden Sie weitere Informationen zu diesen Features und zum [Einstieg in die Entwicklung von Visual Studio-Erweiterungen](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="install-the-visual-studio-sdk"></a>Installieren des Visual Studio SDK
 Das Visual Studio SDK ist ein optionales Feature in Visual Studio-Setup. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="whats-new-in-the-visual-studio-sdk"></a>Neuerungen im Visual Studio SDK
 Das Visual Studio SDK verfügt über einige neue Features, wie z. b. die synchron authentifigene Erweiterungen Warnung und das VSIX v3-Format sowie wichtige Änderungen, die möglicherweise eine Aktualisierung ihrer Erweiterung erforderlich machen. Weitere Informationen finden Sie unter [What es New in the Visual Studio 2019 SDK](../extensibility/whats-new-visual-studio-2019-sdk.md) und [What es New in the Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).

## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio-Richtlinien für Benutzer Funktionen
 Hier erhalten Sie gute Tipps zum Entwerfen der Benutzeroberfläche für Ihre Erweiterung in den [Richtlinien zur Benutzeroberfläche von Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

 Sie können auch erfahren, wie Sie Ihre Erweiterung auf großen dpi-Geräten mit dem Artikel [Adress dpi-Probleme](../extensibility/addressing-dpi-issues2.md) hervorragend gestalten.

 Nutzen Sie den [Image-Dienst und den Katalog](../extensibility/image-service-and-catalog.md) , um eine hervorragend Abbild Verwaltung und Unterstützung für hohe dpi-Leistung und Design zu nutzen

## <a name="find-and-install-existing-visual-studio-extensions"></a>Suchen und installieren vorhandener Visual Studio-Erweiterungen
 Sie finden Visual Studio-Erweiterungen im Dialogfeld **Erweiterungen und Updates** **im Menü Extras** . Weitere Informationen finden Sie untersuchen [und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md). Sie finden Erweiterungen auch im [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK-Referenz
 Die Visual Studio SDK-API-Referenz finden Sie unter [Visual Studio SDK-Referenz](../extensibility/visual-studio-sdk-reference.md).

## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK-Beispiele
 Open-Source-Beispiele für vs SDK-Erweiterungen finden Sie auf GitHub unter [Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples)-Beispiele. Dieses GitHub-Repository enthält Beispiele, die verschiedene erweiterbare Funktionen in Visual Studio veranschaulichen.

## <a name="other-visual-studio-sdk-resources"></a>Weitere Visual Studio SDK-Ressourcen
 Wenn Sie Fragen zum VSSDK haben oder Ihre Erfahrungen mit der Entwicklung von Erweiterungen freigeben möchten, können Sie das [Visual Studio-Erweiterbarkeits Forum](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) oder den [erweiterbaren Gitter-Chatroom](https://gitter.im/Microsoft/extendvs)verwenden.

 Weitere Informationen finden Sie im [Arkana-Blog zu VSX](/archive/blogs/vsx/) und in einer Reihe von Blogs, die von Microsoft MVPs geschrieben werden:

- [Bevorzugte Visual Studio-Erweiterungen](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [Visual Studio-Erweiterbarkeit](http://www.visualstudioextensibility.com/overview/vs/)

- [Erweitern von Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>Weitere Informationen

- [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)
- [Vorgehensweise: Migrieren von Erweiterungs Projekten zu Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [Häufig gestellte Fragen: Umrechnen von Add-Ins in VSPackage-Erweiterungen](/previous-versions/visualstudio/visual-studio-2015/extensibility/faq-converting-add-ins-to-vspackage-extensions?preserve-view=true&view=vs-2015)
- [Verwalten mehrerer Threads in verwaltetem Code](../extensibility/managing-multiple-threads-in-managed-code.md)
- [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)
- [Hinzufügen von Befehlen zu Symbolleisten](../extensibility/adding-commands-to-toolbars.md)
- [Erweitern und Anpassen von Tool Fenstern](../extensibility/extending-and-customizing-tool-windows.md)
- [Editor-und Sprachdienst Erweiterungen](../extensibility/editor-and-language-service-extensions.md)
- [Erweitern von Projekten](../extensibility/extending-projects.md)
- [Erweitern von Benutzereinstellungen und-Optionen](../extensibility/extending-user-settings-and-options.md)
- [Erstellen von benutzerdefinierten Projekt- und Elementvorlagen](../extensibility/creating-custom-project-and-item-templates.md)
- [Erweitern von Eigenschaften und des Eigenschaften Fensters](../extensibility/extending-properties-and-the-property-window.md)
- [Erweitern anderer Teile von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Verwenden und Bereitstellen von Diensten](../extensibility/using-and-providing-services.md)
- [Verwalten von VSPackages](../extensibility/managing-vspackages.md)
- [Isolierte Visual Studio-Shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [Lieferumfang von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)
- [Im Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Unterstützung für das Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)
- [Visual Studio SDK-Referenz](../extensibility/visual-studio-sdk-reference.md)