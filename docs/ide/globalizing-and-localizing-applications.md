---
title: Lokalisierungstools
description: Erfahren Sie mehr über die Lokalisierungstools, die in Visual Studio enthalten sind, und wie Sie sie zum Erstellen lokalisierter Anwendungen in mehreren Sprachen verwenden können.
ms.custom: SEO-VS-2020
ms.date: 02/15/2019
ms.topic: reference
helpviewer_keywords:
- globalization [Visual Studio]
- Visual Basic code, international applications
- C#, international applications
- localization [Visual Studio]
- world-ready applications
- international applications [Visual Studio]
ms.assetid: 4d9815ae-3e80-4b4d-933d-f8309aee18d5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 77402f7503818b310a592a39706ac717ac728852
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847959"
---
# <a name="develop-globalized-and-localized-apps"></a>Entwickeln von globalisierten und lokalisierten Apps

Visual Studio erleichtert mithilfe der in [.NET](/dotnet/standard/globalization-localization/) integrierten Dienste die Entwicklung in einem internationalen Umfeld.

Das Projektsystem für Windows Forms-Apps kann Ressourcendateien sowohl für die Ausweich- als auch für jede weitere Benutzeroberflächenkultur generieren. Wenn Sie ein Projekt in Visual Studio erstellen, werden die Ressourcendateien vom Visual Studio-XML-Format (.resx) in ein binäres Zwischenformat (.resources) kompiliert und anschließend in Satellitenassemblys eingebettet. Weitere Informationen finden Sie unter [Resource files in Visual Studio (Ressourcendateien in Visual Studio)](/dotnet/framework/resources/creating-resource-files-for-desktop-apps#VSResFiles) und [Erstellen von Satellitenassemblys für Desktop-Apps](/dotnet/framework/resources/creating-satellite-assemblies-for-desktop-apps).

## <a name="bidirectional-languages"></a>Bidirektionale Sprachen

Mit Visual Studio können Sie Anwendungen erstellen, die Text mit der Schreibrichtung von rechts nach links, einschließlich Arabisch und Hebräisch, korrekt anzeigen. Für einige Funktionen können Sie ganz einfach Eigenschaften festlegen. In anderen Fällen müssen Features im Code implementiert werden.

> [!NOTE]
> Wenn Sie bidirektionale Sprachen anzeigen und eingeben möchten, müssen Sie mit einer Windows-Version arbeiten, in der die entsprechende Sprache konfiguriert ist. Entweder sollten Sie also eine englischsprachige Windows-Version und das entsprechende Sprachpaket installiert haben, oder Sie verwenden die entsprechende lokalisierte Windows-Version.

### <a name="apps-that-support-bidirectional-languages"></a>Apps, die bidirektionale Sprachen unterstützen

- Windows-Apps

   Sie können vollständig bidirektionale Anwendungen erstellen, die dann bidirektionalen Text, die Rechts-nach-Links-Lesefolge und das Spiegeln (Umkehren des Layouts von Fenstern, Menüs, Dialogfeldern usw.) unterstützen. Diese Features (mit Ausnahme von Spiegeln) sind standardmäßig oder als Eigenschaftseinstellungen verfügbar. Spiegeln wird für einige Features wie Meldungsfelder grundsätzlich unterstützt. In anderen Fällen muss das Spiegeln jedoch im Code implementiert werden. Weitere Informationen finden Sie unter [bidirectional support for Windows Forms applications (Unterstützung von bidirektionalen Sprachen in Windows Forms-Anwendungen)](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications).

- Web-Apps

   Webdienste unterstützen das Senden und Empfangen von mit UTF-8 oder Unicode codiertem Text und sind daher für Anwendungen geeignet, die bidirektionale Sprachen verwenden. Webclientanwendungen verwenden als Benutzeroberfläche den Browser. Wie gut Bidirektionalität bei Webanwendungen unterstützt wird, hängt also davon ab, wie gut der Browser des jeweiligen Benutzers diese bidirektionalen Features unterstützt. Mit Visual Studio können Sie Anwendungen erstellen, die arabischen oder hebräischen Text, Rechts-nach-Links-Lesefolge, Dateicodierung und lokale Kultureinstellungen unterstützen. Weitere Informationen finden Sie unter [Bidirektionale Unterstützung für ASP.NET-Webanwendung](/previous-versions/6eedwbtt(v=vs.140)).

> [!NOTE]
> Konsolen-Apps unterstützen keinen Text für bidirektionale Sprachen. Das liegt an der Art und Weise, wie Windows Konsolenanwendungen einsetzt.

## <a name="see-also"></a>Weitere Informationen

- [Unterstützung für bidirektionale Sprachen in Visual Studio](use-bidirectional-languages.md)
- [Globalisieren und Lokalisieren von .NET-Anwendungen](/dotnet/standard/globalization-localization/)
- [Ressourcen in .NET-Apps](/dotnet/framework/resources/)