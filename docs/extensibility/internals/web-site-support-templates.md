---
title: Vorlagen für die Website Unterstützung | Microsoft-Dokumentation
description: Erfahren Sie mehr über Website-Support Vorlagen. Die Visual Studio-Website Projekt-und-Element Vorlagen bieten wiederverwendbare und anpassbare Website Projekt-und-elementstubelemente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d7bb3d669dadf7c33fa81231adf26ae30e999c51
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487854"
---
# <a name="web-site-support-templates"></a>Vorlagen für die Websiteunterstützung
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Website Projekt-und-Element Vorlagen stellen wiederverwendbare und anpassbare Website Projekt-und-elementstubvorgänge bereit, die den Entwicklungsprozess beschleunigen, indem Sie die Notwendigkeit entfernen, neue Website Projekte und Elemente von Grund auf neu zu erstellen. Weitere Informationen zu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Vorlagen finden Sie unter [Erstellen von Projekt-und Element Vorlagen](../../ide/creating-project-and-item-templates.md).

## <a name="project-template-folder"></a>Projektvorlagen Ordner
 Webprojekt Vorlagen werden in der Regel unter [*Visual Studio-Installationspfad*] \common7\ide\projecttemplates\web installiert \\ , jeweils in einem Unterordner, der nach der webprogrammier Sprache benannt ist.

## <a name="project-file"></a>Projektdatei
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) erfordert eine Projektdatei Erweiterung, damit eine Vorlage dem richtigen Projekttyp zugeordnet werden kann. Da Webprojekte nicht über eine Projektdatei verfügen, wird die Dateierweiterung. WEBPROJ der Dummyprojekt Datei registriert, um die Vorlage dem Projekttyp zuzuordnen.

 Optional kann der Vorlage eine Zeichenfolge für den Sprachen Namen hinzugefügt werden, damit das Webprojekt System im Dialogfeld **Neues Element hinzufügen** den Standardwert für Elemente festlegen kann, die auf der Vorlage basieren. Die Zeichenfolge muss die erste Zeile der Datei sein. Er muss mit dem Namen übereinstimmen, der unter additemlanguagename in der IntelliSense-Engine-Registrierung registriert ist, und dem Namen, der unter Project SubType (VSTEMPLATE) registriert ist. Weitere Informationen finden Sie [unter Attribute der Website Unterstützung](../../extensibility/internals/web-site-support-attributes.md).

 Wenn die Zeichenfolge nicht vorhanden ist, versucht das Webprojekt System anhand des sprach Attributs und der Dateierweiterungen der Seiten, die dem Webprojekt von der Projektvorlage hinzugefügt werden, die Standardsprache zu bestimmen.

## <a name="project-templates"></a>Projektvorlagen
 Website Projektvorlagen werden verwendet, um neue Websites als Reaktion auf den Befehl " **neue Website** " im Menü " **Datei** " zu erstellen. Drei Projekttypen von Websites werden zurzeit unterstützt:

- Leere Website Projekte

- Website Projekte

- Webdienst Projekte

### <a name="empty-web-site-projects"></a>Leere Website Projekte
 Diese Dateien erstellen eine neue leere Website als Reaktion auf den **leeren Website** Befehl, der nach der Auswahl von " **Datei**  >  **neu**"-Website verfügbar ist:

- Emptyweb. vstemplate

     Die Vorlagen Datei, die die Erstellung der neuen leeren Website steuert.

- Emptyweb. WEBPROJ

     Diese Datei ist ein Element des-Projektvorlagen Systems. Er erfüllt den Projektdatei Verweis in der emptyweb. VSTEMPLATE-Datei.

### <a name="web-site-projects"></a>Website Projekte
 Diese Dateien erstellen eine neue Website als Reaktion auf den **ASP.NET-Website** Befehl, der nach der Auswahl von " **Datei**  >  **neu**"-Website verfügbar ist:

- Default.aspx

     Die Standard-Startseite für die neue Website. Das Language-Attribut gibt die Code Behind-Sprache an, und das CodeFile-Attribut gibt die abhängige Datei an, die den Code Behind-Code enthält, der dieser Seite zugeordnet ist.

- Default. aspx. *Erweiterung*

     Die abhängige Datei, die den Code Behind-Code für die Standard Startseite enthält. Die Code Behind-Sprache bestimmt die *Erweiterung* dieser Datei.

- web.config

     Die Web. Site-Stamm Konfigurationsdatei.

- WebApplication. vstemplate

     Die Vorlagen Datei, die den Inhalt der Website Lösung bestimmt und erzwingt, dass der App_Data Ordner erstellt wird.

- WebApplication. WEBPROJ

     Diese Datei ist ein Element des-Projektvorlagen Systems. Der Projektdatei Verweis in der Datei "WebApplication. vstemplate" wird erfüllt.

### <a name="web-service-projects"></a>Webdienst Projekte
 Diese Dateien erstellen eine neue Website als Reaktion auf den **ASP.NET-Webdienst** Befehl, der nach der Auswahl von " **Datei**  >  **neu**"-Website verfügbar ist:

- Dienst. asmx

     Die HTML-Seite für den neuen Webdienst. Das Language-Attribut gibt die Code Behind-Sprache an, und das Code Behind-Attribut gibt die abhängige Datei an, die den Code Behind-Code enthält, der diesem Dienst zugeordnet ist.

- Dienst: *extension*

     Die abhängige Datei, die die Dienstklasse implementiert. Die Code Behind-Sprache bestimmt die *Erweiterung* dieser Datei.

- web.config

- Die Web. Site-Stamm Konfigurationsdatei.

- Webservice. vstemplate

     Die Vorlagen Datei, die den Inhalt der Website Lösung bestimmt und erzwingt, dass die Ordner "App_Data" und "App_Code" erstellt werden. Der Dienst. die *Erweiterungs* Datei wird in den App_Code Ordner kopiert.

- Webservice. WEBPROJ

     Diese Datei ist ein Element des-Projektvorlagen Systems. Er erfüllt den Projektdatei Verweis in der Datei "Webservice. vstemplate".

## <a name="project-item-template-folder"></a>Ordner für Projekt Element Vorlage
 Webprojekt-Element Vorlagen werden in der Regel in [*Visual Studio-Installationspfad*] \common7\ide\itemtemplates\web installiert \\ , jeweils in einem Unterordner, der nach der zugehörigen webprogrammier Sprache benannt ist.

## <a name="project-item-templates"></a>Projektelementvorlagen
 Website-Projekt Element Vorlagen werden verwendet, um einer Website neue Webseiten als Antwort auf den Befehl **Vorhandenes Element hinzufügen** hinzuzufügen. Diese Arten von Webseiten werden zurzeit unterstützt:

- Neue Klasse

- Neue HTML-Seite

- Neues Webformular

- Neue Master Seite

### <a name="new-class"></a>Neue Klasse
 Mit dieser Vorlage wird eine neue Quelldatei erstellt, die eine leere Klasse als Reaktion auf den Befehl **neue Klasse hinzufügen** definiert.

- Klasse. *extension*

     Die Quelldatei, die die leere Klasse implementiert. Die Code Behind-Sprache bestimmt die *Erweiterung* dieser Datei.

- Class. vstemplate

     Die Vorlagen Datei, die die Quelldatei erstellt und ihren Inhalt bestimmt.

### <a name="new-html-page"></a>Neue HTML-Seite
 Diese Vorlage erstellt eine neue Webseite als Antwort auf den Befehl **neue HTML-Seite hinzufügen** .

- HTMLPage.htm

     Der Start Inhalt der Webseite. Dieser Webseite ist in der Regel keine zugeordnete Code Behind-abhängige Datei zugeordnet. Verwenden Sie stattdessen die Web Form-Vorlage, um eine SmartPage mit einer zugeordneten Code Behind-Datei zu erstellen.

- HtmlPage. vstemplate

     Die Vorlagen Datei, mit der die Webseite erstellt und deren Inhalt bestimmt wird.

### <a name="new-webform"></a>Neues Webformular
 Diese Vorlage erstellt eine neue Smart Web Page als Antwort auf den Befehl **neuen Webformular hinzufügen** .

 Um eine abhängige Code Behind-Quelldatei zu erstellen, wählen Sie **Code in separater Datei platzieren aus**. Andernfalls wird eine einzelne Webseite erstellt, die über einen leeren Skriptblock und keine \<% Page %> Direktiven zum Verbinden einer abhängigen Datei verfügt.

 Wählen Sie zum Erstellen einer Inhaltsseite für eine ausgewählte Master Seite **Master Seite auswählen** aus.

- Webform. aspx

     Der Start Inhalt der Webseite. Diese Webseite weist keine zugehörige Code Behind-abhängige Datei auf.

- WebForm_cb. aspx

     Der Start Inhalt der Webseite. Diese Webseite verfügt über eine zugehörige Code Behind-abhängige Datei.

- Code Behind. *extension*

     Die abhängige Datei, die die Webform-Klasse implementiert. Die Code Behind-Sprache bestimmt die *Erweiterung* dieser Datei.

- "ContentPage. aspx"

     Der Start Inhalt der Webseite als Inhaltsseite. Diese Webseite weist keine zugehörige Code Behind-abhängige Datei auf.

- ContentPage_cb. aspx

     Der Start Inhalt der Webseite als Inhaltsseite. Diese Webseite verfügt über eine zugehörige Code Behind-abhängige Datei.

- Webform. vstemplate

     Die Vorlagen Datei, die den Inhalt der neuen Webseite und ihrer abhängigen Datei bestimmt (sofern vorhanden).

### <a name="new-master-page"></a>Neue Master Seite
 Diese Vorlage erstellt eine neue Master Seite als Reaktion auf den Befehl **neue Master Seite hinzufügen** .

 Um eine abhängige Code Behind-Quelldatei zu erstellen, wählen Sie **Code in separater Datei platzieren aus**. Andernfalls wird eine einzelne Webseite erstellt, die über einen leeren Skriptblock und keine \<% Page %> Direktiven zum Verbinden einer abhängigen Datei verfügt.

- MasterPage. Master

     Der Start Inhalt der Master Seite. Diese Master Seite verfügt über keine zugehörige Code Behind-abhängige Datei.

- MasterPage_cb. Master

     Der Start Inhalt der Master Seite. Diese Master Seite verfügt über eine zugehörige Code Behind-abhängige Datei.

- Code Behind. *Erweiterung*

     Die abhängige Datei, die die Master Page-Klasse implementiert. Die Code Behind-Sprache bestimmt die *Erweiterung* dieser Datei.

- MasterPage. vstemplate

     Die Vorlagen Datei, die den Inhalt der neuen Master Seite und ihrer abhängigen Datei bestimmt, sofern vorhanden.

## <a name="see-also"></a>Weitere Informationen
- [Websiteunterstützung](../../extensibility/internals/web-site-support.md)
