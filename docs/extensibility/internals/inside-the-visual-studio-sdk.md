---
title: Innerhalb des Visual Studio SDK | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Erweiterungen im Visual Studio SDK, einschließlich Visual Studio-Architektur,-Komponenten,-Dienste,-Schemas und-Hilfsprogramme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c2d67c3d9f998c8dd5192363cf8ff8fae2ce4b57
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839858"
---
# <a name="inside-the-visual-studio-sdk"></a>Im Visual Studio SDK

Dieser Abschnitt enthält ausführliche Informationen zu Visual Studio-Erweiterungen, einschließlich Visual Studio-Architektur,-Komponenten,-Diensten,-Schemas,-Hilfsprogramme und der like.

## <a name="extensibility-architecture"></a>Erweiterbarkeits Architektur
 Die folgende Abbildung zeigt die Erweiterbarkeits Architektur von Visual Studio. VSPackages bieten Anwendungsfunktionen, die in der gesamten IDE als Dienste gemeinsam genutzt werden. Die Standard-IDE bietet auch eine Vielzahl von Diensten, wie z <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> . b., die Zugriff auf die IDE-windowingfunktionen bieten.

 ![Grafik zur Umgebungs Architektur](../../extensibility/internals/media/environment.gif "Environment") Allgemeine Ansicht der Visual Studio-Architektur

## <a name="vspackages"></a>VSPackages
 VSPackages sind Softwaremodule, die Visual Studio um Benutzeroberflächenelemente, Dienste, Projekte, Editoren und Designer erweitern. VSPackages sind die zentrale architektonische Einheit von Visual Studio. Weitere Informationen finden Sie unter [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="visual-studio-shell"></a>Visual Studio Shell
 Die Visual Studio-Shell stellt grundlegende Funktionen bereit und unterstützt die Kommunikation zwischen den Komponenten-VSPackages und MEF-Erweiterungen. Weitere Informationen finden Sie unter [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).

## <a name="user-experience-guidelines"></a>Richtlinien zur Benutzerfreundlichkeit
 Wenn Sie beabsichtigen, neue Features für Visual Studio zu entwerfen, sollten Sie sich die folgenden Richtlinien für Entwurfs-und Nutzbarkeits Tipps ansehen: Richtlinien für die Benutzerfreundlichkeit von [Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="commands"></a>Befehle
 Befehle sind Funktionen, mit denen Aufgaben wie das Drucken eines Dokuments, das Aktualisieren einer Ansicht oder das Erstellen einer neuen Datei ausgeführt werden können.

 Wenn Sie Visual Studio erweitern, können Sie Befehle erstellen und in der Visual Studio-Shell registrieren. Sie können angeben, wie diese Befehle in der IDE angezeigt werden, z. b. in einem Menü oder einer Symbolleiste. In der Regel wird ein benutzerdefinierter Befehl **im Menü Extras** angezeigt, und ein Befehl zum Anzeigen eines Tool Fensters wird im Untermenü **andere Fenster** des Menüs **Ansicht** angezeigt.

 Wenn Sie einen Befehl erstellen, müssen Sie auch einen Ereignishandler dafür erstellen. Der Ereignishandler bestimmt, wann der Befehl sichtbar oder aktiviert ist, ermöglicht Ihnen, den Text zu ändern, und garantiert, dass der Befehl entsprechend reagiert, wenn er aktiviert wird. In den meisten Fällen verarbeitet die IDE Befehle mithilfe der- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle. Befehle in Visual Studio werden beginnend mit dem innersten Befehls Kontext, basierend auf der lokalen Auswahl, verarbeitet und bis zum äußersten Kontext basierend auf der globalen Auswahl fortgesetzt. Befehle, die dem Hauptmenü hinzugefügt werden, sind sofort für die Skripterstellung verfügbar.

 Weitere Informationen finden Sie unter [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="menus-and-toolbars"></a>Menüs und Symbolleisten
 Menüs und Symbolleisten bieten Benutzern die Möglichkeit, Befehle aufzurufen. Menüs sind Zeilen oder Spalten von Befehlen, die normalerweise als einzelne Textelemente am oberen Rand eines Tool Fensters angezeigt werden. Untermenüs sind sekundäre Menüs, die angezeigt werden, wenn ein Benutzer auf Befehle klickt, die einen kleinen Pfeil enthalten. Kontextmenüs werden angezeigt, wenn ein Benutzer mit der rechten Maustaste auf bestimmte Benutzeroberflächen Elemente klickt. Einige allgemeine Menü Namen sind **File**, **Edit**, **View** und **Window**. Weitere Informationen finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).

 Symbolleisten sind Zeilen oder Spalten von Schaltflächen und anderen Steuerelementen, z. b. Kombinations Felder, Listenfelder und Textfelder. Symbolleisten Schaltflächen verfügen in der Regel über Symbolbilder, z. b. ein Ordnersymbol für einen **geöffneten Datei** Befehl oder einen Drucker für einen **Druck** Befehl. Allen Symbolleisten Elementen sind Befehle zugeordnet. Wenn Sie auf eine Symbolleisten Schaltfläche klicken, wird der zugehörige Befehl ausgeführt. Im Fall eines Dropdown-Steuer Elements wird jedes Element in der Dropdown Liste einem anderen Befehl zugeordnet. Einige Symbolleisten-Steuerelemente, z. b. ein Splitter Steuerelement, sind Hybride. Eine Seite des Steuer Elements ist eine Symbolleisten-Schaltfläche, und die andere Seite ist ein Pfeil nach unten, auf dem mehrere Befehle angezeigt werden, wenn darauf geklickt wird.

## <a name="tool-windows"></a>Toolfenster
 Tool Fenster werden in der IDE zum Anzeigen von Informationen verwendet. **Toolbox**, **Projektmappen-Explorer**, **Eigenschaften** Fenster und **Webbrowser** sind Beispiele für Tool Fenster.

 Tool Fenster bieten in der Regel verschiedene Steuerelemente, mit denen der Benutzer interagieren kann. Beispielsweise ermöglicht das Fenster " **Eigenschaften** " dem Benutzer das Festlegen von Eigenschaften von Objekten, die einem bestimmten Zweck dienen. Das **Eigenschaften** Fenster ist in diesem Sinne spezialisiert, aber auch allgemein, da es in vielen verschiedenen Situationen verwendet werden kann. Entsprechend ist das **Ausgabe** Fenster spezialisiert, weil es eine textbasierte Ausgabe bereitstellt, aber allgemein, da viele Subsysteme in Visual Studio es verwenden können, um die Ausgabe für den Visual Studio-Benutzer bereitzustellen.

 Sehen Sie sich das folgende Bild von Visual Studio an, das mehrere Tool Fenster enthält:

 ![Screenshot](../../extensibility/internals/media/t1gui.png "T1gui")

 Einige der Tool Fenster werden in einem einzelnen Bereich nebeneinander angedockt, der das Projektmappen-Explorer Tool Fenster anzeigt und die anderen Tool Fenster verbirgt, indem Sie auf Registerkarten klicken. Die Abbildung zeigt zwei weitere Tool Fenster, das Fenster " **Fehlerliste** und **Ausgabe** ", das in einem einzelnen Bereich angedockt ist.

 Außerdem wird der Hauptdokument Bereich angezeigt, in dem mehrere Editor Fenster angezeigt werden. Obwohl Tool Fenster in der Regel nur eine Instanz haben (Sie können z. b. nur ein **Projektmappen-Explorer** öffnen), können Editor Fenster mehrere-Instanzen aufweisen, die jeweils zum Bearbeiten eines separaten Dokuments verwendet werden, aber alle im gleichen Bereich angedockt sind. Die Abbildung zeigt einen Dokumentbereich mit zwei Editor Fenstern, einem Formular-Designer-Fenster. Alle Fenster im Dokumentbereich sind durch Klicken auf Tabstopps verfügbar, aber das Editor Fenster, das EditorPane.cs-Datei enthält, ist sichtbar und aktiv.

 Wenn Sie Visual Studio erweitern, können Sie Tool Fenster erstellen, mit denen Visual Studio-Benutzer mit ihrer Erweiterung interagieren können. Sie können auch eigene Editoren erstellen, mit denen Visual Studio-Benutzer Dokumente bearbeiten können. Da Ihre Tool Fenster und Editoren in Visual Studio integriert werden, müssen Sie Sie nicht so programmieren, dass Sie auf einer Registerkarte ordnungsgemäß Andocken oder angezeigt werden. Wenn Sie in Visual Studio ordnungsgemäß registriert sind, verfügen Sie automatisch über die typischen Features von Tool Fenstern und Dokument Fenstern in Visual Studio. Weitere Informationen finden Sie unter [erweitern und Anpassen von Tool Fenstern](../../extensibility/extending-and-customizing-tool-windows.md).

## <a name="document-windows"></a>Dokumentfenster
 Ein Dokument Fenster ist ein untergeordnetes Fenster eines MDI-Fensters (Multiple Document Interface). Dokument Fenster werden in der Regel zum Hosten von Text-Editoren, Formular-Editoren (auch als Designer bezeichnet) oder zum Bearbeiten von Steuerelementen verwendet, Sie können jedoch auch andere funktionale Typen hosten. Das Dialogfeld **neue Datei** enthält Beispiele für Dokument Fenster, die Visual Studio bereitstellt.

 Die meisten Editoren sind spezifisch für eine Programmiersprache oder einen Dateityp, z. b. HTML-Seiten, Framesets, C++-Dateien oder Header Dateien. Wenn Sie im Dialogfeld " **neue Datei** " eine Vorlage auswählen, erstellt ein Benutzer dynamisch ein Dokument Fenster für den Editor für den Dateityp, der der Vorlage zugeordnet ist. Ein Dokument Fenster wird auch erstellt, wenn ein Benutzer eine vorhandene Datei öffnet.

 Dokument Fenster sind auf den MDI-Client Bereich beschränkt. Jedes Dokument Fenster enthält eine Registerkarte oben, und die Tab-Reihenfolge ist mit anderen Fenstern verknüpft, die im MDI-Bereich geöffnet sein können. Wenn Sie mit der rechten Maustaste auf die Registerkarte eines Dokument Fensters klicken, wird ein Kontextmenü angezeigt, das Optionen zum Aufteilen des MDI-Bereichs in mehrere horizontale oder vertikale Registerkarten Gruppen enthält. Wenn Sie den MDI-Bereich aufteilen, können mehrere Dateien gleichzeitig angezeigt werden. Weitere Informationen finden Sie unter [Dokument Fenster](../../extensibility/internals/document-windows.md).

## <a name="editors"></a>Editoren
 Der Visual Studio-Editor ermöglicht es Ihnen, ihn anzupassen und für Ihren eigenen Inhaltstyp mithilfe der Managed Extensibility Framework (MEF) zu verwenden. In vielen Fällen müssen Sie kein VSPackage erstellen, um den Editor zu erweitern. Wenn Sie jedoch Features aus der Shell (z. b. einen Menübefehl oder eine Tastenkombination) einschließen möchten, können Sie eine MEF-Erweiterung mit einem VSPackage kombinieren.

 Sie können auch einen benutzerdefinierten Editor erstellen, z. b. Wenn Sie eine Datenbank lesen und in eine Datenbank schreiben möchten, oder wenn Sie einen Designer verwenden möchten. Sie können auch einen externen Editor verwenden, z. b. Notepad oder Microsoft WordPad. Weitere Informationen finden Sie unter [Editor-und Sprachdienst Erweiterungen](../../extensibility/editor-and-language-service-extensions.md).

## <a name="language-services"></a>Sprachdienste
 Wenn Sie möchten, dass der Visual Studio-Editor neue Programmier Schlüsselwörter oder sogar eine neue Programmiersprache unterstützt, erstellen Sie einen Sprachdienst. Jeder Sprachdienst kann bestimmte Editor Features vollständig, teilweise oder gar nicht implementieren. Abhängig von der Konfiguration kann der Sprachdienst Syntax Hervorhebung, zugehörige Klammern, IntelliSense-Unterstützung und andere Features im Editor bereitstellen.

 Der Kern eines sprach Dienstanbieter ist ein Parser und ein Scanner. Ein Scanner (oder Lexer) unterteilt eine Quelldatei in Elemente, die als Token bezeichnet werden, und ein Parser stellt die Beziehungen zwischen diesen Token her. Wenn Sie einen Sprachdienst erstellen, müssen Sie den Parser und den Scanner implementieren, damit Visual Studio die Token und Grammatik der Sprache verstehen kann. Sie können verwaltete oder nicht verwaltete Sprachdienste erstellen. Weitere Informationen finden Sie unter [Erweiterbarkeit des Legacy sprach Dienstanbieter](../../extensibility/internals/legacy-language-service-extensibility.md).

## <a name="projects"></a>Projekte

In Visual Studio sind Projekte die Container, die Entwickler zum organisieren und Erstellen des Quellcodes und anderer Ressourcen verwenden. Mit Projekten können Sie Quellcode, Verweise auf Webdienste und Datenbanken sowie andere Ressourcen organisieren, erstellen, Debuggen und bereitstellen. VSPackages können das Visual Studio-Projekt System erweitern, indem Sie Projekttypen, Projekt Untertypen und benutzerdefinierte Tools bereitstellen.

Projekte können auch zusammen in einer Projekt Mappe gesammelt werden, bei der es sich um eine Gruppierung von einem oder mehreren Projekten *handelt, die* zusammenarbeiten, um eine Anwendung zu erstellen. Projekt-und Statusinformationen, die sich auf die Lösung beziehen, werden in zwei Projektmappendateien gespeichert, der textbasierten [Projektmappendatei (. sln)](solution-dot-sln-file.md) und der Benutzer Option für die binäre Projekt [Mappe (. suo)](solution-user-options-dot-suo-file.md). Diese Dateien ähneln den in früheren Versionen von Visual Basic verwendeten Gruppen Dateien (. VBG) und den Arbeitsbereichs Dateien (. DSW) und Benutzeroptionen (. opt), die in früheren Versionen von C++ verwendet wurden.

Weitere Informationen finden Sie unter [Projekte](../../extensibility/internals/projects.md) und [](../../extensibility/internals/solutions-overview.md)Projektmappen.

## <a name="project-and-item-templates"></a>Projekt- und Elementvorlagen
 Visual Studio enthält vordefinierte Projektvorlagen und Projekt Element Vorlagen. Sie können auch eigene Vorlagen erstellen oder Vorlagen aus der Community abrufen und Sie dann in Visual Studio integrieren. In der [MSDN Code Gallery](https://code.msdn.microsoft.com/site/search?query=visual%20studio) finden Sie Vorlagen und Erweiterungen.

 Vorlagen enthalten die Projektstruktur und die grundlegenden Dateien, die zum Erstellen einer bestimmten Art von Anwendung, Steuerung, Bibliothek oder Klasse erforderlich sind. Wenn Sie Software entwickeln möchten, die einer der Vorlagen ähnelt, erstellen Sie ein Projekt, das auf der Vorlage basiert, und ändern Sie dann die Dateien in diesem Projekt.

> [!NOTE]
> Diese Vorlagen Architektur wird für-Projekte nicht unterstützt [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] .

 Weitere Informationen finden Sie unter [Hinzufügen von Projekt-und Projekt Element Vorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="properties-and-options"></a>Eigenschaften und Optionen
 Im Fenster **Eigenschaften** werden die Eigenschaften von einzelnen oder mehreren ausgewählten Elementen angezeigt: die Erweiterungs [Eigenschaften](../../extensibility/internals/extending-properties.md) Optionen Seiten enthalten Gruppen von Optionen, die sich auf eine bestimmte Komponente beziehen, z. b. eine Programmiersprache oder ein VSPackage: [Optionen und Options Seiten](../../extensibility/internals/options-and-options-pages.md). Einstellungen sind im allgemeinen Benutzeroberflächen bezogene Features, die importiert und exportiert werden können: [Unterstützung für Benutzereinstellungen](../../extensibility/internals/support-for-user-settings.md).

## <a name="visual-studio-services"></a>Visual Studio-Dienste
 Ein Dienst stellt einen bestimmten Satz von Schnittstellen für die zu nutzenden Komponenten bereit. Visual Studio stellt eine Reihe von Diensten bereit, die von beliebigen Komponenten, einschließlich Erweiterungen, verwendet werden können. Mithilfe von Visual Studio-Diensten können Tool Fenster z. b. dynamisch angezeigt oder ausgeblendet werden, sodass Sie den Zugriff auf Hilfe, Statusleiste oder Benutzeroberflächen Ereignisse aktivieren können. Der Visual Studio-Editor bietet auch Dienste, die von Editor-Erweiterungen importiert werden können. Weitere Informationen finden Sie unter [verwenden und Bereitstellen von Diensten](../../extensibility/using-and-providing-services.md).

## <a name="debugger"></a>Debugger
 Der Debugger ist die Benutzeroberfläche der sprachspezifischen debuggingkomponenten. Wenn Sie einen neuen Sprachdienst erstellt haben, müssen Sie ein bestimmtes Debug-Modul erstellen, um eine Verbindung mit dem Debugger herzustellen. Weitere Informationen finden Sie unter [Visual Studio Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="source-control"></a>Quellcodeverwaltung
 Informationen zum Implementieren eines Quellcodeverwaltungs-Plug-ins oder VSPackages finden Sie unter [Quell](../../extensibility/internals/source-control.md)Code Verwaltung.

## <a name="wizards"></a>Assistenten
 Sie können einen Assistenten in Verbindung mit einem neuen Projekttyp erstellen, damit der Assistent die richtigen Entscheidungen treffen kann, wenn Sie ein neues Projekt dieses Typs erstellen. Weitere Informationen finden Sie unter [Assistenten](../../extensibility/internals/wizards.md).

## <a name="custom-tools"></a>Benutzerdefinierte Tools
 Mithilfe von benutzerdefinierten Tools können Sie ein Tool einem Element in einem Projekt zuordnen und dieses Tool ausführen, wenn die Datei gespeichert wird. Weitere Informationen finden Sie unter [benutzerdefinierte Tools](../../extensibility/internals/custom-tools.md).

## <a name="vssdk-utilities"></a>VSSDK-Hilfsprogramme
 Das VSSDK umfasst eine Reihe von Hilfsprogrammen, die Sie möglicherweise benötigen, um mit verschiedenen Aspekten von VSPackages zu arbeiten. Weitere Informationen finden Sie unter [VSSDK-Hilfsprogramme](../../extensibility/internals/vssdk-utilities.md).

## <a name="using-windows-installer"></a>Verwenden von Windows Installer
 In einigen Fällen müssen Sie möglicherweise die Windows Installer anstelle des VSIX-Installers verwenden. beispielsweise müssen Sie möglicherweise in die Registrierung schreiben. Weitere Informationen zur Verwendung von Windows Installer mit ihren Erweiterungen finden Sie unter [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

## <a name="help-viewer"></a>Help Viewer
 Sie können Ihre eigene Hilfe und F1-Seiten in den Help Viewer integrieren. Weitere Informationen finden Sie unter [Microsoft Help Viewer SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).
