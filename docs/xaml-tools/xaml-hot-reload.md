---
title: Schreiben und Debuggen von XAML mithilfe von XAML Hot Neuladen
description: XAML Hot Neuladen oder XAML-bearbeiten und Fortfahren ermöglicht es Ihnen, während der Ausführung von apps Änderungen an Ihrem XAML-Code vorzunehmen.
ms.date: 09/23/2020
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25819d8d691836c12c73d9d76e334e36d50b83b4
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668871"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Schreiben und Debuggen von ausgeführtem XAML-Code mit XAML Hot Reload in Visual Studio

Das heiße Laden von XAML unterstützt Sie beim Erstellen der Benutzeroberfläche der WPF-oder UWP-APP, indem Sie Änderungen an XAML-Code vornehmen können, während Ihre APP ausgeführt wird. Hot-Neuladen ist sowohl in Visual Studio als auch in Blend für Visual Studio verfügbar. Mit dieser Funktion können Sie XAML-Code inkrementell erstellen und testen, indem Sie den Datenkontext der ausgelaufenden APP, den Authentifizierungs Status und eine andere reale Komplexität, die während der Entwurfszeit schwer zu simulieren ist, nutzen. Wenn Sie Hilfe bei der Problembehandlung von XAML-laden benötigen, finden Sie weitere Informationen unter Problembehandlung bei [XAML-Hot](xaml-hot-reload-troubleshooting.md)

> [!NOTE]
> Wenn Sie xamarin. Forms verwenden, finden Sie unter [XAML Hot Neuladen für xamarin. Forms](/xamarin/xamarin-forms/xaml/hot-reload)Weitere Informationen.

Das erneute Laden von XAML ist besonders in den folgenden Szenarien hilfreich:

* Behebung von Benutzeroberflächen Problemen in Ihrem XAML-Code, nachdem die APP im Debugmodus gestartet wurde.

* Die Entwicklung einer neuen Benutzeroberflächen Komponente für eine APP, die sich in der Entwicklung befindet, während der Lauf Zeit Kontext ihrer App genutzt wird.

|Unterstützte Anwendungs Typen|Betriebssystem und Tools|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6 und höher und .net Core</br>Windows 7 und höher |
|Universelle Windows-Apps (UWP)|Windows 10 und höher mit dem [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

Die folgende Abbildung zeigt die Verwendung der visuellen echt Zeitstruktur, um den Quellcode zu öffnen, und dann XAML-Hot-Neuladen, um den Schaltflächen Text und die Schaltflächen Farbe zu ändern.

![Neuladen von XAML im laufenden Betrieb](../debugger/media/xaml-hot-reload-using.gif)

> [!NOTE]
> Das Laden von Visual Studio XAML Hot wird zurzeit nur unterstützt, wenn Sie die Anwendung in Visual Studio ausführen oder Blend für Visual Studio mit angefügtem Debugger (**F5** oder **Debuggen starten**). Sie können diese Umgebung nicht mithilfe von [an den Prozess anhängen aktivieren,](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) es sei denn, Sie [legen manuell eine Umgebungsvariable fest](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process).

## <a name="known-limitations"></a>Bekannte Einschränkungen

Im folgenden finden Sie bekannte Einschränkungen für das heiße Laden von XAML. Beenden Sie den Debugger, und schließen Sie den Vorgang ab, um die Einschränkung zu umgehen, die Sie in ausführen.

|Einschränkung|WPF|UWP|Notizen|
|-|-|-|-|
|Verknüpfen von Ereignissen mit Steuerelementen während der Ausführung der APP|Nicht unterstützt|Nicht unterstützt|Siehe Fehler: Fehler beim *sicherstellen des Ereignisses*. Beachten Sie, dass Sie in WPF auf einen vorhandenen Ereignishandler verweisen können. In UWP-apps wird das verweisen auf einen vorhandenen Ereignishandler nicht unterstützt.|
|Erstellen von Ressourcen Objekten in einem Ressourcen Wörterbuch, z. b. in der Seite/im Fenster der APP oder in der *app. XAML*|Unterstützt ab Visual Studio 2019 Update 2|Unterstützt|Beispiel: Hinzufügen eines `SolidColorBrush` zu einem Ressourcen Wörterbuch, das als verwendet werden soll `StaticResource` .</br>Hinweis: Statische Ressourcen, Format Konverter und andere in ein Ressourcen Wörterbuch geschriebene Elemente können beim Verwenden von XAML-Hot-Neuladen angewendet/verwendet werden. Nur die Erstellung der Ressource wird nicht unterstützt.</br> Ändern der Eigenschaft des Ressourcen Wörterbuchs `Source` .|
|Hinzufügen von neuen Steuerelementen, Klassen, Fenstern oder anderen Dateien zu Ihrem Projekt, während die app ausgeführt wird|Nicht unterstützt|Nicht unterstützt|Keine|
|Verwalten von nuget-Paketen (hinzufügen/entfernen/aktualisieren von Paketen)|Nicht unterstützt|Nicht unterstützt|Keine|
|Ändern der Datenbindung, die die {x:Bind}-Markup Erweiterung verwendet|–|Unterstützt ab Visual Studio 2019|Hierfür ist Windows 10 Version 1809 (Build 10.0.17763) erforderlich. Wird in Visual Studio 2017 oder früheren Versionen nicht unterstützt.|
|Das Ändern von x:UID-Direktiven wird nicht unterstützt|NICHT ZUTREFFEND|Nicht unterstützt|Keine|
|Mehrere Prozesse | Unterstützt | Unterstützt | In Visual Studio 2019 [Version 16,6](/visualstudio/releases/2019/release-notes-v16.6) und höher unterstützt |

## <a name="error-messages"></a>Fehlermeldungen

Bei der Verwendung von XAML Hot Neuladen treten möglicherweise die folgenden Fehler auf.

|Fehlermeldung|BESCHREIBUNG|
|-|-|
|Fehler bei Fehler|Der Fehler gibt an, dass Sie versuchen, ein Ereignis an eines der Steuerelemente zu übertragen, was nicht unterstützt wird, während die Anwendung ausgeführt wird.|
|Diese Änderung wird nicht von XAML-Hot-Neuladen unterstützt und wird während der Debugsitzung nicht angewendet.|Der Fehler gibt an, dass die Änderung, die Sie versuchen, von XAML Hot Neuladen nicht unterstützt wird. Nehmen Sie die Debugsitzung an, nehmen Sie die Änderung vor, und starten Sie die Debugsitzung neu. Wenn Sie ein nicht unterstütztes Szenario finden, das Sie unterstützen möchten, verwenden Sie die neue Option "Feature vorschlagen" in der [Visual Studio-Entwickler Community](https://aka.ms/feedback/suggest?space=8). |

## <a name="see-also"></a>Weitere Informationen

* [Problembehandlung beim Neuladen von XAML im laufenden Betrieb](xaml-hot-reload-troubleshooting.md)
* [XAML Hot Reload für Xamarin.Forms](/xamarin/xamarin-forms/xaml/hot-reload)
* [Bearbeiten und Fortfahren (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
