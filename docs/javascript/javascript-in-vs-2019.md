---
title: JavaScript und TypeScript in Visual Studio 2019
description: Hier erfahren Sie, wie Visual Studio 2019 umfassende Unterstützung für die JavaScript-Entwicklung bereitstellt, wobei sowohl JavaScript direkt als auch die TypeScript-Programmiersprache verwendet werden.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 03/16/2020
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2019'
ms.openlocfilehash: 0fe13030478f62f759b3eabc8e897c09a4295bad
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936755"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>JavaScript und TypeScript in Visual Studio 2019

## <a name="overview"></a>Übersicht

Visual Studio 2019 bietet umfangreiche Unterstützung für die JavaScript-Entwicklung, sowohl mit JavaScript direkt, als auch mit der Programmiersprache [TypeScript](http://www.typescriptlang.org/), die entwickelt wurde, um eine produktivere und angenehmere JavaScript-Entwicklung zu ermöglichen, insbesondere bei der Entwicklung von Projekten im großen Stil. Sie können JavaScript- oder TypeScript-Code in Visual Studio für viele Arten von Anwendungen und Dienste schreiben.

## <a name="javascript-language-service"></a>JavaScript-Sprachdienst

JavaScript in Visual Studio 2019 wird von der gleichen Engine unterstützt, die auch TypeScript unterstützt. Dadurch erhalten Sie sofort bessere Unterstützung, Vielfalt und Integration von Funktionen.

Die Option der Wiederherstellung in den veralteten JavaScript-Sprachdienst ist nicht mehr verfügbar. Benutzer verfügen jetzt von Anfang an über den neuen JavaScript-Sprachdienst. Der neue Sprachdienst basiert ausschließlich auf dem TypeScript-Sprachdienst, der auf statischer Analyse basiert. Dies ermöglicht eine bessere Verwendung von Tools, sodass Ihr JavaScript-Code vom umfangreicheren IntelliSense, basierend auf Typdefinitionen, profitieren kann. Der neue Dienst ist schlank und verbraucht weniger Speicher als der Legacydienst, bietet Ihnen aber gleichzeitig bessere Leistung, wenn Sie Code skalieren. Wir haben auch die Leistung des Sprachdienstes verbessert, um größere Projekte zu bearbeiten.

## <a name="typescript-support"></a>TypeScript-Unterstützung

Visual Studio 2019 bietet mehrere Optionen zur Integration der TypeScript-Kompilierung in Ihr Projekt:

* Das [TypeScript-NuGet-Paket](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild). Wenn das NuGet-Paket für TypeScript 3.2 oder höher in Ihrem Projekt installiert ist, wird die entsprechende Version des TypeScript-Sprachdienstes in den Editor geladen.
* [Das TypeScript-npm-Paket](https://www.npmjs.com/package/typescript). Wenn das npm-Paket für TypeScript 2.1 oder höher in Ihrem Projekt installiert ist, wird die entsprechende Version des TypeScript-Sprachdienstes in den Editor geladen.
* Das TypeScript SDK, das standardmäßig im Visual Studio-Installer verfügbar ist, sowie ein eigenständiger SDK-Download vom [VS Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-395).

> [!TIP]
> Für Projekte, die in Visual Studio 2019 entwickelt wurden, empfehlen wir Ihnen, das TypeScript-NuGet- oder das TypeScript-npm-Paket für eine bessere Portabilität über verschiedene Plattformen und Umgebungen hinweg zu verwenden. Weitere Informationen finden Sie unter [Kompilieren von TypeScript-Code mithilfe von NuGet](../javascript/compile-typescript-code-nuget.md) und [Kompilieren von TypeScript-Code mithilfe von tsc](../javascript/compile-typescript-code-npm.md).

## <a name="projects"></a>Projekte

UWP-JavaScript-Apps werden in Visual Studio 2019 nicht mehr unterstützt. Sie können keine JavaScript-UWP-Projekte erstellen oder öffnen (Dateien mit der Erweiterung *.jsproj*). Weitere Informationen finden Sie in unserer [Dokumentation zum Erstellen von progressiven Web-Apps (PWAs), die sich gut unter Windows ausführen lassen](/microsoft-edge/progressive-web-apps/get-started).
