---
title: Vsct-XML-Schema Referenz | Microsoft-Dokumentation
description: In den referenzartikeln zu vsct-XML-Schemas werden Befehls Tabellen-compilerschemas mit zulässigen untergeordneten Elementen und Attributen beschrieben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9cc50d3914f43be0da2f992f1074dc82cf5178ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925736"
---
# <a name="vsct-xml-schema-reference"></a>Vsct-XML-Schema Referenz
Stellt eine Tabelle mit Befehls Tabellen-compilerschemementen mit zulässigen untergeordneten Elementen und Attributen für jede bereit.

 Eine XML-basierte Befehls Tabellen Konfigurationsdatei (vsct) definiert die Befehls Elemente, die ein VSPackage für die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) bereitstellt. Zu diesen Elementen gehören Menü Elemente, Menüs, Symbolleisten und Kombinations Felder.

> [!NOTE]
> Der VSCT-Compiler kann einen Präprozessor in der vsct-Datei ausführen. Da dies in der Regel der C++-Präprozessor ist, können Sie includes-und-Makros definieren, die die gleiche Syntax aufweisen, die in C++-Dateien verwendet wird. Beispiele hierfür sind in der vsct-Datei angegeben, die der Assistent für **neue Projekte** für ein VSPackage-Projekt erstellt.

## <a name="optional-elements"></a>Optionale Elemente
 Einige vsct-Elemente sind optional. Wenn kein- `Parent` Argument angegeben ist, Group_Undefined: 0 wird impliziert. Wenn `Icon` kein Argument angegeben ist, wird "guidofficeicon: msotcidnoicon" impliziert. Wenn eine Tastenkombination definiert ist, ist die Emulation, die in der Regel nicht verwendet wird, optional.

 Bitmapelemente können zur Kompilierzeit eingebettet werden, indem der Speicherort des Bitmap-Streifens im Argument angegeben wird `href` . Der bitmapstrip wird während des Merge kopiert, anstatt aus den Ressourcen der DLL extrahiert zu werden. Wenn ein `href` Argument angegeben wird, `usedList` wird das Argument optional, und alle Slots im bitmapstrip werden als verwendet betrachtet.

 Alle GUID-und ID-Werte müssen mithilfe von symbolischen Namen definiert werden. Diese Namen können in Header Dateien oder in vsct-Abschnitten definiert werden \<Symbols> . Die symbolischen Namen müssen lokal, durch- \<Include> Elemente eingeschlossen oder durch-Elemente referenziert werden \<Extern> . Ein symbolischer Name wird aus einer in einem-Element angegebenen Header Datei importiert, \<Extern> Wenn er auf das einfache Muster #define Symbol Werts folgt. Der Wert kann ein weiteres Symbol sein, solange dieses Symbol zuvor definiert wurde. GUID-Definitionen müssen entweder im Format OLE oder C++ befolgt werden. ID-Werte können dezimale Ziffern oder hexadezimale Ziffern (0x) vorangestellt werden, wie in den folgenden Zeilen dargestellt:

- {6d484634-e53d-4a2c-adcb-55145c9362c8}

- {0x6d484634, 0xe53d, 0x4a2c, {0xAD, 0xCB, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8}}

  Es können XML-Kommentare verwendet werden, aber die Roundtrip-Tools für die grafische Benutzeroberfläche (GUI) können diese verwerfen. Der Inhalt von \<Annotation> Elementen wird garantiert unabhängig vom Format beibehalten.

## <a name="schema-hierarchy"></a>Schemahierarchie
 Eine vsct-Datei verfügt über die folgenden Hauptelemente.

- [Commandtable-Element](../extensibility/commandtable-element.md)

- [Extern-Element](../extensibility/extern-element.md)

- [Include-Element](../extensibility/include-element.md)

- [Define-Element](../extensibility/define-element.md)

- [Commands-Element](../extensibility/commands-element.md)

- [Commandplacement-Element](../extensibility/commandplacements-element.md)

- [Visibilityschränkt-Element](../extensibility/visibilityconstraints-element.md)

- [KeyBinding-Element](../extensibility/keybindings-element.md)

- [Usedcommands-Element](../extensibility/usedcommands-element.md)

- [Übergeordnetes Element](../extensibility/parent-element.md)

- [Icon-Element](../extensibility/icon-element.md)

- [Strings-Element](../extensibility/strings-element.md)

- [Befehlsflag-Element](../extensibility/command-flag-element.md)

- [Symbols-Element](../extensibility/symbols-element.md)

- [Bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>Weitere Informationen
- [Hinzufügen von Elementen der Benutzeroberfläche durch VSPackages](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Befehls Routing in VSPackages](../extensibility/internals/command-routing-in-vspackages.md)
