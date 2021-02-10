---
title: Eigenschaften einer DSL-Definition
description: Erfahren Sie, dass die DslDefinition-Eigenschaften domänenspezifische sprach Definitions Eigenschaften wie die Versionsnummerierung definieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ef8f49e46c554efca89862c787fbfbe97c48c8f4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959115"
---
# <a name="properties-of-a-dsl-definition"></a>Eigenschaften einer DSL-Definition
DslDefinition-Eigenschaften definieren *domänenspezifische sprach* Definitions Eigenschaften, z. b. Versionsnummerierung. Die DslDefinition-Eigenschaften werden im **Eigenschaften** Fenster angezeigt, wenn Sie im *domänenspezifischen sprach Designer* auf einen geöffneten Bereich des Diagramms klicken.

 Weitere Informationen finden Sie unter Vorgehens [Weise beim Definieren einer Domain-Specific Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zur Verwendung dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer Domain-Specific Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition verfügt über die Eigenschaften in der folgenden Tabelle:

|Eigenschaft|BESCHREIBUNG|Standard|
|-|-|-|
|Zugriffsmodifizierer|Bestimmt, ob der Zugriffsmodifizierer für die Domänen Klasse öffentlich oder intern ist.|public|
|Benutzerdefinierte Attribute|Benutzerdefinierte Attribute für die Domänen Klasse.<br /><br /> **Hinweis** Verwenden Sie die Schaltfläche Durchsuchen, um ein Attribut hinzuzufügen.|\<none>|
|Name des Unternehmens|Der Name des aktuellen Firmennamens in der Systemregistrierung.|Aktueller Firmenname|
|Name|Der Name dieser Domänen Klasse.|Aktueller Name|
|Namespace|Der Namespace, der dieser Domänen Klasse angehört.|Aktueller Namespace|
|Paket-GUID|Die GUID für das für diese DSL generierte Visual Studio-Paket.|\<none>|
|Package-Namespace|Der Namespace für das Visual Studio-Paket, das für diese DSL generiert wurde.|\<none>|
|Produktname|Der Name des Produkts, das für das für diese DSL generierte Visual Studio-Paket registriert wird.|\<none>|
|Notizen|Anmerkungen, die dieser Domänen Klasse zugeordnet sind.|\<none>|
|BESCHREIBUNG|Die Beschreibung für diese Domänen Klasse.|\<none>|
|Anzeigename|Der Name, der im generierten Designer für diese Domänen Klasse angezeigt wird.|\<none>|
|Hilfsschlüsselwort|Das Hilfe Schlüsselwort, das dieser Domänen Klasse zugeordnet ist.|\<none>|
|Erstellen|Die inkrementelle Buildnummer für diese domänenspezifische Sprachdefinition.|0|
|Hauptversion|Die inkrementelle Hauptbuildnummer für diese domänenspezifische Sprachdefinition.|1|
|Nebenversion|Die inkrementelle nebenwert-Buildnummer für diese domänenspezifische Sprachdefinition.|0|
|Revision|Die inkrementelle Revisions Buildnummer für diese domänenspezifische Sprachdefinition.|0|

## <a name="see-also"></a>Weitere Informationen

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](/previous-versions/bb126564(v=vs.100))