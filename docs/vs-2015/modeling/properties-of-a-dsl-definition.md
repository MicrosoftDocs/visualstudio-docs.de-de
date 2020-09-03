---
title: Eigenschaften einer DSL-Definition | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
ms.assetid: 38debcfe-e1a6-4a3f-9d69-3ab07520f2b6
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8755b1b70051c54157fa87ee0b66dbc9340b5024
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668469"
---
# <a name="properties-of-a-dsl-definition"></a>Eigenschaften einer DSL-Definition
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslDefinition-Eigenschaften definieren *domänenspezifische sprach* Definitions Eigenschaften, z. b. Versionsnummerierung. Die DslDefinition-Eigenschaften werden im **Eigenschaften** Fenster angezeigt, wenn Sie im *domänenspezifischen sprach Designer*auf einen geöffneten Bereich des Diagramms klicken.

 Weitere Informationen finden Sie unter [Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zur Verwendung dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition verfügt über die Eigenschaften in der folgenden Tabelle:

|Eigenschaft|BESCHREIBUNG|Standard|
|--------------|-----------------|-------------|
|Zugriffsmodifizierer|Bestimmt, ob der Zugriffsmodifizierer für die Domänen Klasse öffentlich oder intern ist.|public|
|Benutzerdefinierte Attribute|Benutzerdefinierte Attribute für die Domänen Klasse.<br /><br /> **Hinweis** Verwenden Sie die Schaltfläche Durchsuchen, um ein Attribut hinzuzufügen.|\<none>|
|Name des Unternehmens|Der Name des aktuellen Firmennamens in der Systemregistrierung.|Aktueller Firmenname|
|Name|Der Name dieser Domänen Klasse.|Aktueller Name|
|Namespace|Der Namespace, der dieser Domänen Klasse angehört.|Aktueller Namespace|
|Paket-GUID|Die GUID für das [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Paket, das für diese DSL generiert wurde.|\<none>|
|Package-Namespace|Der Namespace für das [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Paket, das für diese DSL generiert wurde.|\<none>|
|Produktname|Der Name des Produkts, das für das [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] für diese DSL generierte Paket registriert wird.|\<none>|
|Hinweise|Anmerkungen, die dieser Domänen Klasse zugeordnet sind.|\<none>|
|BESCHREIBUNG|Die Beschreibung für diese Domänen Klasse.|\<none>|
|Anzeigename|Der Name, der im generierten Designer für diese Domänen Klasse angezeigt wird.|\<none>|
|Hilfsschlüsselwort|Das Hilfe Schlüsselwort, das dieser Domänen Klasse zugeordnet ist.|\<none>|
|Erstellen|Die inkrementelle Buildnummer für diese domänenspezifische Sprachdefinition.|0|
|Hauptversion|Die inkrementelle Hauptbuildnummer für diese domänenspezifische Sprachdefinition.|1|
|Nebenversion|Die inkrementelle nebenwert-Buildnummer für diese domänenspezifische Sprachdefinition.|0|
|Revision|Die inkrementelle Revisions Buildnummer für diese domänenspezifische Sprachdefinition.|0|

## <a name="see-also"></a>Weitere Informationen
 [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
