---
title: Entwerfen von XAML in Visual Studio und in Blend für Visual Studio
titleSuffix: ''
description: Erfahren Sie mehr über die Funktionen der visuellen Entwurfs Tools in Visual Studio und Blend für Visual Studio zum Erstellen von Benutzeroberflächen und Erfahrungen in XAML.
ms.custom: SEO-VS-2020
ms.date: 02/28/2020
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: fc6c05b925c8dac5c488ce3eea79ca683b590b72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876419"
---
# <a name="design-xaml-in-visual-studio-and-blend-for-visual-studio"></a>Entwerfen mithilfe von XAML in Visual Studio und Blend für Visual Studio

Visual Studio und Blend für Visual Studio sind visuelle Tools zum Erstellen ansprechender Benutzeroberflächen und Rich-Media-Umgebungen mit XAML für eine Vielzahl von App-Typen. Beide integrierten Entwicklungsumgebungen (IDE) teilen sich eine Reihe von Funktionen, wie z.B. einen visuellen XAML-Editor (Designer). Blend für Visual Studio, das die WPF-und UWP-Plattformen unterstützt, stellt zusätzliche Tools zum Entwerfen von visuellen Zuständen und zum Erstellen von Animationen bereit.

Sie können zwischen Visual Studio und Blend für Visual Studio wechseln. Sie können sogar in beiden IDEs dasselbe Projekt geöffnet haben. Änderungen an XAML-Dateien in einer IDE lassen sich beim Wechsel zur anderen IDE automatisch neu laden. Sie können das Neuladen Verhalten **Steuern, indem Sie**  >    >    >  in beiden IDE zu Extras Optionen Umgebungs **Dokumente** navigieren.

## <a name="installation"></a>Installation

- Um WPF-Apps zu erstellen, installieren Sie die Workload **.NET-Desktopentwicklung** in Visual Studio. Blend für Visual Studio wird ebenfalls installiert.

     ![Screenshot der Arbeitsauslastung der .net-Desktop Entwicklung aus der Visual Studio-Installer](../xaml-tools/media/dotnet-desktop-dev-workload.png)

- Um UWP-Apps zu erstellen, installieren Sie die Workload **Universelle Windows-Plattformentwicklung** in Visual Studio. Blend für Visual Studio wird ebenfalls installiert.

     ![Screenshot der Arbeitsauslastung der universelle Windows-Plattform Entwicklung aus der Visual Studio-Installer](../xaml-tools/media/uwp-workload.png)

- Um Xamarin.Forms-Apps zu erstellen, installieren Sie die Workload **Mobile-Entwicklung mit .NET** in Visual Studio. Blend für Visual Studio wird *nicht* installiert. Xamarin.Forms-Apps werden in Blend nicht unterstützt.

     ![Screenshot der Mobile-Entwicklung mit .NET-Arbeitsauslastung aus der Visual Studio-Installer](../xaml-tools/media/mobile-dev-dotnet-workload.png)

## <a name="shared-capabilities"></a>Gemeinsam genutzte Funktionen

Für die meisten grundlegenden Entwicklungsaufgaben teilen sich Visual Studio und Blend für Visual Studie denselben Fenster- und Funktionssatz, mit einigen geringfügigen Unterschieden. Einige Highlights:

- **IntelliSense:** Beide IDES unterstützen IntelliSense-Funktionen wie Anweisungs Vervollständigung.

- **Debuggen:** Sie können in [Visual Studio](inspect-xaml-properties-while-debugging.md) Debuggen und [Blend für Visual Studio](../xaml-tools/debug-xaml-in-blend.md). Hierzu gehören auch das Festlegen von Haltepunkten im Code zum Debuggen einer laufenden app und das Verwenden von [Hot Upload](../xaml-tools/xaml-hot-reload.md) zum Ändern des XAML-Codes, während die app ausgeführt wird. Für ein einheitliches Debugerlebnis in Visual Studio beinhaltet Blend für Visual Studio die meisten der Debugfenster und -symbolleisten von Visual Studio.

- **Datei neu laden:** Sie können Ihre XAML-Dateien entweder in Visual Studio oder Blend für Visual Studio bearbeiten. Bearbeitete Dateien, die gespeichert wurden, werden automatisch neu geladen, wenn Sie zwischen den IDES wechseln. Sie können das Neuladen Verhalten **Steuern, indem Sie**  >    >    >  in beiden IDE zu Extras Optionen Umgebungs **Dokumente** navigieren.

- **Synchronisierte Layouts und Einstellungen:** Entwurfs Anpassungs Tool Fensterlayouts und Einstellungen Einstellungen für Visual Studio oder Blend für Visual Studio werden auf Ihren Geräten und Versionen synchronisiert, wenn Sie sich mit demselben Personalisierungs Konto anmelden. Weitere Informationen finden Sie unter[Synchronisieren von Visual Studio-Einstellungen auf mehreren Computern](../ide/synchronized-settings-in-visual-studio.md).

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Erweiterte Funktionen in Blend für Visual Studio

Verwenden Sie Blend für Visual Studio für die folgenden Aufgaben, um Ihre Produktivität zu steigern. Dies sind die Bereiche, in denen Blend mehr Funktionalität bietet als Visual Studio-Designer oder Code allein.

| Aufgabe | Visual Studio | Blend for Visual Studio | Weitere Informationen |
| - | - | - | - |
| **Visuelle Zustände für Designs** | Es gibt kein Tool, das Sie beim Entwerfen visueller Zustände unterstützt. Sie müssen sie programmgesteuert erstellen. | Verwenden Sie Designtools, um das Erscheinungsbilds eines Steuerelements basierend auf dessen Status zu ändern. | [Visuelle Zustände](modify-the-style-of-objects-in-blend.md#visual-states) |
| **Erstellen von Animationen** |Es gibt kein Designwerkzeug für Animationen; Sie müssen sie programmgesteuert erstellen. Dies erfordert ein grundlegendes Verständnis des Animations- und Zeitsteuerungssystems in WPF sowie umfangreiche Codierungskenntnisse.|Sie können Animationen in Blend für Visual Studio visuell erstellen und eine Vorschau anzeigen. Dies ist schneller und präziser, als Animationen in Code zu erstellen. Sie können Trigger hinzufügen, um die Benutzerinteraktion zu verarbeiten, und Sie können zum Code wechseln, um Ereignishandler und andere Funktionen zu verarbeiten.|[Animieren von Objekten](../xaml-tools/animate-objects-in-xaml-designer.md)|
|**Umwandeln von Formen und Text in Pfade für eine einfachere Bearbeitung**|Wird nicht unterstützt.|Sie können geringfügige oder erhebliche Änderungen an den Formen (z. B. Rechtecke und Ellipsen) vornehmen, indem Sie sie in Pfade konvertieren, die eine bessere Bearbeitungssteuerung bieten. Sie können Pfade umformen oder kombinieren und zusammengesetzte Pfade aus mehreren Formen erstellen.<br /><br />Sie können auch Textblöcke in Pfade umwandeln, um sie als Vektorgrafiken zu bearbeiten.|[Zeichnen von Formen und Pfaden](../xaml-tools/draw-shapes-and-paths.md)|
|**Bearbeiten von Steuerelementen, Vorlagen und Stilen**|Erfordert die Codierung von sowie Kenntnisse über WPF-Stile und -Vorlagen.|Wandeln Sie ein Bild in ein Steuerelement um.<br /><br />Verwenden Sie die Tools zum Bearbeiten von Vorlagen, um Steuerelemente, Stile und Vorlagen mit nur wenigen Mausklicks zu ändern.<br /><br />Beispielsweise können Sie Blend für Visual Studio-Ressourcen verwenden, um WPF-Standardsteuerelemente (z. B. Schaltflächen, Listenfeldern, Bildlaufleisten, Menüs usw.) zu implementieren und um die Farbe, den Stil oder die zugrunde liegende Vorlage direkt in Blend zu ändern. Sie können dann, falls gewünscht, zum Code wechseln, um Ihrer Arbeit den letzten Schliff zu geben.|[Ändern des Stils von Objekten](modify-the-style-of-objects-in-blend.md)|
|**Verbinden der Benutzeroberfläche mit Daten**|Sie können eine Datenquelle aus Ressourcen, wie SQL Server-Datenbanken, WCF oder Webdiensten, Objekten oder SharePoint-Listen, erstellen und die Datenquelle mit den Steuerelementen der Benutzeroberfläche verknüpfen.<br /><br />Daten müssen für ein interaktives Designerlebnis zur Entwurfszeit manuell erstellt werden.|Für .NET Framework-Apps erstellen Sie mühelos die Beispieldaten für die Prototyperstellung und für Tests. Wechseln Sie zu den Livedaten, wenn Sie bereit sind.<br /><br />Die Blend-Funktionen zur Datengenerierung von Visual Studio sind hervorragend. Sie können Namen, Zahlen, URLs und Fotos problemlos bei laufendem Betrieb hinzufügen, wodurch Sie viel Zeit sparen können.<br /><br />Bei Live-Daten können Sie die Steuerelemente der Benutzeroberfläche mit einer XML-Datei oder einer beliebigen CLR-Datenquelle verknüpfen.|[Anzeigen von Daten](display-data-in-blend.md)|

Informationen zu erweiterten XAML-Designs finden Sie unter [Erstellen einer Benutzeroberfläche mit Blend für Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen

- [Übersicht über XAML](xaml-overview.md)
- [Übersicht über Blend für Visual Studio](creating-a-ui-by-using-blend-for-visual-studio.md)
