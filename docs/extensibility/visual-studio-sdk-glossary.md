---
title: Visual Studio SDK-Glossar | Microsoft-Dokumentation
description: Dieses Glossar enthält Definitionen für Begriffe, die in der Visual Studio SDK-Dokumentation verwendet werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec8f6508c6b387ec51872f6e5b59b3f72a57d432
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863898"
---
# <a name="visual-studio-sdk-glossary"></a>Visual Studio SDK-Glossar
Dieses Glossar enthält Definitionen für Begriffe, die in der- [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Dokumentation verwendet werden.

## <a name="terms"></a>Bestimmungen
 Add-in: eine hilfsprogrammanwendung, ein Treiber oder eine andere Software, die einer primären Anwendung hinzugefügt wurde. In der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio ist ein Add-in eine Automatisierungs basierte Anwendung, die die Funktionen der IDE erweitert.

 Automation-Modell das Automatisierungs Modell, das in früheren Versionen von Visual Studio als Erweiterbarkeits Modell bekannt ist, ist eine Programmierschnittstelle, die Ihnen den Zugriff auf die zugrunde liegenden Routinen ermöglicht, die die IDE steuern. Add-Ins, Assistenten und Makros verwenden Objekte im Automatisierungs Modell, um die Funktionalität der IDE zu steuern oder zu erweitern.

 Befehls Benutzeroberflächen-Kontext Zuordnung einer GUID mit der Sichtbarkeit eines UI-Befehls oder-Elements, z. b. einer Symbolleiste. Der Kontext der Befehls Benutzeroberfläche ist anders als der Auswahl Kontext, da er nicht an ein Fenster angefügt ist.

 Der Befehls Benutzeroberflächen Kontext kann für Folgendes verwendet werden:

- Zuweisen einer GUID zu einer Symbolleiste, die angezeigt wird, wenn ein bestimmtes Fenster aktiviert wird.

- Weisen Sie der Verfügbarkeit eines Befehls eine GUID zu, ohne ein VSPackage laden oder ausführen zu müssen.

- Weisen Sie eine GUID zu, um die aktive schlüsselbindung zu beeinflussen.

- Weisen Sie eine GUID zu, um die Makro Aufzeichnung zu aktivieren.

- Weisen Sie eine GUID zu, um den Debugmodus zu aktivieren oder zwischen dem Entwurfs-und dem Lauf Modus in einem Editor zu wechseln.

  Komponente Software, die Teil der Funktionalität einer Anwendung sein kann, ohne dass diese Anwendung bereits vorhandene Informationen zur Implementierung der Software hat. Die Kommunikation zwischen einer Komponente und einer Anwendung erfolgt ausschließlich über Schnittstellen im OLE-Stil.

  Komponenten-Manager ein Dienst, `SOleComponentManager` , der nicht-Benutzeroberflächen-Koordinationsdienste für Komponenten der obersten Ebene bereitstellt. Der `SOleComponentManager` Dienst implementiert die- `IOleComponentManager` Schnittstelle.

  Component UI Manager A Service, `SOleComponentUIManager` , der Benutzeroberflächen-Koordinationsdienste bereitstellt. Der `SOleComponentUIManager` Dienst implementiert die `IOleComponentUIManager` -und- `IOleInPlaceComponentUIManager` Schnittstellen.

  Kontext Behälter ein `IVsUserContext` Objekt (com-Objekt), das an eine Umgebungs Komponente angefügt ist. Dieses Objekt enthält Such Schlüsselwörter, **F1** -Schlüsselwörter und Attribute, die mit der Komponente in Beziehung stehen. Kontext Behälter zeigen zusätzlich auf alle unter Kontext Behälter, die mit Ihnen verknüpft sind.

  Kontext Anbieter eine Komponente in der IDE, der ein Kontext Behälter zugeordnet ist. Zu diesen Komponenten gehören ein Tool Fenster, ein Editor oder eine Projekt Hierarchie.

  Designer eine Programmierschnittstelle, die es Benutzern ermöglicht, Elemente der Benutzeroberfläche (Formulare, Schaltflächen und andere Steuerelemente) zu bearbeiten.

  Docdata: ein COM-Objekt, das die zugrunde liegenden Daten eines Dokuments in einer Welt kapselt, in der die Dokument-/ansichttrennung vorliegt (z. b. im Text-Editor-Fall ist dies der Text Puffer, der allen Text-Editor-Ansichten zugrunde liegt). Wenn die Editorfactory dieses Objekt nicht bereitstellt, wird eine von der IDE in Ihrem Namen bereitgestellt. Die Verantwortung für dieses Objekt besteht darin, die Daten Persistenz und die Freigabe Semantik für mehrere Ansichten zu verwalten `DocData` . Wenn das `DocData` Objekt die- `IOleCommandTarget` Schnittstelle unterstützt, ist es im Befehls Routing von uiShell enthalten.

  DocObject-Technologie, mit der die Benutzeroberfläche in einem Frame gehostet wird, der vom Host bereitgestellt wird. Genauer gesagt bezieht sich dieser Begriff auf alle Einbettungen, die die `IOleDocument` und die zugehörigen Schnittstellen unterstützen. Diese Technologie verfügt über zahlreiche potenzielle Anwendungen, wie z. b. ein Implementierungsdetail von com-Dokumenten, Tool Fenster in Visual Basic 5,0, ActiveX-Designern in Visual Basic 6,0 usw.

  Dokument, das verwendet wird, um generisch auf das Dokument als Ganzes zu verweisen – sowohl als `DocData` auch die `DocView` . Ein documentframe enthält z. b. einen `DocView` , behält aber auch einen Verweis auf, `DocData` um die Persistenz zu verarbeiten.

  DocView: DocObject/Einbettungs/Windows Pane, mit dem der Benutzer interagiert, um den zugrunde liegenden anzuzeigen und zu bearbeiten `DocData` . Die Benutzer können die Trennung von Dokumenten/Ansichten nicht nutzen, die Teil des `DocObject` Schnittstellen Entwurfs ist. Benutzer verwenden ein gesamtes DocObject-Objekt, um als Ansicht zu fungieren, anstatt ein abstraktes (und weniger formalisiertes) Konzept der zugrunde liegenden Daten zu verwenden, die als bezeichnet werden `DocData` . `DocView` Objekte werden immer mit Dokument Rahmen Objekten (untergeordnete MDI-Fenster) der IDE eingebettet.

  DTE das `DTE` Objekt (Erweiterbarkeit der Entwicklungs Tools) ist der oberste Zugriffspunkt im Visual Studio-Automatisierungs Modell, mit dem Sie die IDE Programm gesteuert automatisieren und erweitern können.

  Tool Fenster für dynamische Hilfefenster, das von der IDE implementiert wird und eine Liste mit Such Schlüsselwörtern oder **F1** -Hilfe Themen anzeigt.

  Editor-Code (Klasse, CLSID), der implementiert `DocView` . Es implementiert auch, `DocData` Wenn die Ansicht und die Trennung von Daten unterstützt werden.

  Erweiterung eine Funktion, mit der eine IDE geändert, angepasst oder einer IDE hinzugefügt wird. Sie erstellen Erweiterungen mit dem Automatisierungs Modell oder VSPackages.

  externer Editor ein Editor, der nicht spezifisch für die IDE ist, z. b. Microsoft Word. Es wurde über seine eigenen Mechanismen registriert und kann außerhalb der IDE verwendet werden. Wenn dieser Editor eingebettet werden kann, wird er in einem Fenster in der IDE angezeigt. Wenn Sie nicht eingebettet werden kann, wird ein separates Fenster der obersten Ebene erstellt.

  Hierarchiestruktur von Knoten, jeder Knoten, der einem Satz von Eigenschaften zugeordnet ist.

  unabhängige Komponente der obersten Ebene eine Komponente, die ein nicht modalem Fenster der obersten Ebene verwendet und effektiv als eigenständiges Anwendungsfenster fungieren kann, jedoch als in-Process-Objekt implementiert wird. Daher muss eine unabhängige Komponente der obersten Ebene die Modalität und Nachrichten Schleifen Dienste mit der IDE koordinieren. In-Process-Objekte haben keine eigene Nachrichten Schleife.

  Informationsanbieter: der Informationsanbieter ist ein Modul, das Schlüsselwörter suchen und eine Liste von Themen in Form von Objekten zurückgeben kann `IVsUserContextItem` . Um **F1** -und Suche-Schlüsselwort Elemente für den Informationsanbieter bereitzustellen, registrieren Sie die kompilierte Hilfedatei (*. HxS*) mit dem System. Die Hilfe Themen in diesen Dateien stellen die Liste der Themen bereit, die im Fenster Dynamische Hilfe angezeigt werden, und zeigen an, ob ein Benutzer **F1** drückt.

  direkte Komponente ein VSPackage-Objekt, das die- `IOleInPlaceComponent` Schnittstelle zum Verwalten eines Fensters implementiert, das in einem Dokument Fenster, das sich im Besitz der IDE befindet, visuell enthalten ist. Direkte Komponenten nehmen nicht an der standardmäßigen OLE-Menü Zusammenführung Teil. Stattdessen integrieren Sie die Elemente der Benutzeroberfläche in die IDE.

  Es gibt zwei Arten von direkten Komponenten: hart verdrahtete direkte Komponenten und Komponenten Steuerelemente.

  Direkt verdrahtete direkte Komponenten verfügen über Menüs, Symbolleisten und Befehle, die eng in die Benutzeroberfläche der IDE integriert sind und so angezeigt werden, als würden Sie direkt in die IDE integriert.

  Komponenten Steuerelemente verfügen über keine eigenen Benutzeroberflächen Elemente, die in die IDE integriert sind. Stattdessen verwenden Sie die Menüs, Befehle und Symbolleisten der IDE. Beispielsweise könnte mit dem Befehl Bold ein ausgewähltes Wort in einem Rich-Text-Steuerelement fett formatiert werden, das in ein Formular eingebettet ist. Komponenten Steuerelemente können jedoch anfordern, dass dynamisch installierte Komponenten spezifische UI-Elemente angezeigt werden.

  Sprachdienst: ein Satz von Objekten, mit dem VSPackage-Entwickler Features von Computer Sprachcode-Editoren implementieren können, z. b. Textmarkierung und farbige Farbgebung.

  Sonstige Dateien Projekt Projekt, das zum beherbergen offener Dateien verwendet wird, die sich nicht in einem Projekt befinden. Die Liste der Elemente in diesem Projekt wird nicht beibehalten.

  Projekt Projekte bestehen aus Hierarchie Objekten oder COM-Objekten, die die- `IVsHierarchy` Schnittstelle implementieren.

  projektspezifischer Designer oder Editor ein Designer, der nicht unabhängig vom Projekttyp verwendet werden kann. Alle projektspezifischen Designer müssen ihre Editorfactory-Informationen in der Registrierung eingeben. Die IDE kann dann den Designer instanziieren, wenn ein bestimmter Dateityp in einem bestimmten Projekt geöffnet wird.

  Projekttyp Fenster ein Fenster, in dem die derzeit aktive Projekt Hierarchie und das Element kontinuierlich aus dem globalen Auswahl Kontext verfolgt werden. Projekttyp Windows verwenden `SVsTrackSelectionEx` Sie den-Dienst, um die IDE der Änderungen zu warnen und dem Benutzer Feedback anzuzeigen. Projektmappen-Explorer ist ein Beispiel für ein Fenster vom Typ Projekt.

  Eigenschaftenfenster früher Eigenschaften Browser.

  Verweis basiertes Projekt Projekt, das nicht erfordert, dass sich die Dateien für das Projekt im selben Verzeichnis befinden. Stattdessen werden Verweise auf Dateien aus anderen nicht verknüpften Verzeichnissen gespeichert und durch das Projekt selbst verwaltet.

  die interne Struktur der Dokument Tabelle wird ausgeführt, mit der die IDE die Liste aller gegenwärtig geöffneten Dokumente verwaltet. Die Liste enthält alle geöffneten Dokumente im Speicher, unabhängig davon, ob die Dokumente gerade bearbeitet werden. Ein Dokument ist ein beliebiges Element, das gespeichert wird, einschließlich gespeicherter Prozeduren, die in einem Editor geöffnet sind, Dateien in einem Projekt oder in der Hauptprojekt Datei (z. b. *. VCPROJ-Datei).

  Auswahl Kontext Daten, die Teil der Details jedes Fensters in der IDE sind und zum Nachverfolgen der aktiven Auswahl verwendet werden. Der Auswahl Kontext besteht aus folgendem:

- Zeiger auf die- `IVsHierarchy` Schnittstelle der Projekt Hierarchie

- Der Element Bezeichner des Projekt Elements.

- Ein Zeiger auf die- `ISelectionContainer` Schnittstelle, die Zugriff auf die Eigenschaften der aktiven-Objekte bereitstellt

- Array von Element Werten.

  Dienst einen Vertrag für eine Gruppe von COM-Schnittstellen, die sich in einem einzelnen COM-Objekt befindet. Wenn Sie einen Dienst erstellen, der durch eine GUID identifiziert wird, definieren Sie den Satz von COM-Schnittstellen, der den Dienst ausführt. Für COM-Objekte werden Dienste verwendet, um miteinander zu kommunizieren.

  projektmappengruppe verwandter Projekte, mit denen ein Benutzer arbeitet.

  Standard Designer ein Designer, der unabhängig vom Projekttyp verwendet werden kann. Alle Standard Designer müssen die Editorfactory-Informationen in der Registrierung eingeben. Die IDE kann dann den Designer instanziieren, wenn eine Datei mit einer bestimmten Erweiterung geöffnet wird. Die Daten müssen in einer Datei gespeichert werden.

  Standard Editor-Editor, der unabhängig von einem bestimmten Projekttyp verwendet werden kann. Bei solchen Editoren sind editorfactorys in der Registrierung registriert. Dies ermöglicht der IDE, den Editor zu finden und aufzurufen.

  Standard-Betriebssystem-Editor eine Einbettung, die nicht Visual Studio-spezifisch ist. Sie wird mit den bekannten Win32-Schlüsseln registriert (z. b. kann der Win32-Explorer aufrufen). Wenn ein solcher Editor eingebettet werden kann, wird der Editor weiterhin in der IDE angezeigt. Andernfalls wird für solche Editoren ein separates Fenster der obersten Ebene erstellt.

  unter Kontext Behälter ein `IVsUserContext` Objekt, das mit einem Kontext Behälter verknüpft ist. Das-Objekt enthält Such Schlüsselwörter, **F1** -Schlüsselwörter und Attribute für eine Auswahl innerhalb einer IDE-Komponente. Beispiele für unter Kontext sind ein Befehl in einem Tool Fenster oder ein Schlüsselwort in einem Editor.

  Aufgabenlisten-Tool Fenster, das von der IDE implementiert wird und eine Liste aktiver Aufgaben anzeigt.

  der allgemeine Name des Text Puffers für das-Objekt `VSTextBuffer` .

  Der allgemeine Name der Text Ansicht für das Objekt `VSTextView` .

  Tool der obersten Ebene einer Komponente, die als nicht modalem Popup Fenster fungiert und eng mit der Benutzeroberfläche der IDE koordiniert wird. Wie unabhängige Komponenten der obersten Ebene müssen auch Tool Komponenten der obersten Ebene die Modalität und Nachrichten Schleifen Dienste mit der IDE koordinieren.

  Komponente der obersten Ebene ein VSPackage-Objekt, das ein nicht modalem Fenster der obersten Ebene anstelle des Client Bereichs eines IDE-Fensters verwaltet. Komponenten der obersten Ebene implementieren die- `IOleComponent` Schnittstelle, um Nachrichten Schleifen Dienste wie den Zugriff auf die Leerlaufzeit zu nutzen.

  UI aktiv ein VSPackage-Objekt, das sichtbar und aktuell den Fokus besitzt.

  UI-Hierarchie ein COM-Objekt, das die- `IVsUIHierarchy` Schnittstelle implementiert, um die Anzeige einer Hierarchie zuzulassen. Das UI-Hierarchie Fenster implementiert die- `ISelectionContainer` Schnittstelle, um die Eigenschaftenfenster zu aktualisieren. andere Projekttyp Fenster können diese Implementierung verwenden, wenn gewünscht.

  Vsct-Visual Studio-Befehls Tabelle. Die vsct-Datei enthält Informationen über die Platzierung und das Verhalten von Menüs, Symbolleisten und Befehlen im XML-Format.

  VSPackage ein installier bares Softwareelement, das die Visual Studio-IDE erweitert, indem eines oder mehrere der folgenden Elemente beigetragen werden: Benutzeroberfläche, Dienste, Projekttypen oder Editor/Designer. Ein VSPackage besteht aus einem COM-Objekt, das die `IVsPackage` -Schnittstelle implementiert, und einem oder mehreren anderen COM-Objekten, die andere Schnittstellen implementieren, um Auswahl und andere Funktionen zu unterstützen. Außerdem gelten für ein VSPackage bestimmte Registrierungsanforderungen.
