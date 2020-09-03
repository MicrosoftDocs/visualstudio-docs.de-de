---
title: Eigenschaften von Domänen Rollen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 5a7bb18c-638e-45e8-9d79-9aa6a9e14b0e
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a0cddfb3d5c95e5636e9dac069106e3010bedff8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671469"
---
# <a name="properties-of-domain-roles"></a>Eigenschaften von Domänenrollen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Eigenschaften in der folgenden Tabelle sind einer Domänen Rolle zugeordnet. Weitere Informationen zu Domänen Rollen finden Sie Untergrund Legendes zu [Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md). Weitere Informationen zur Verwendung dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Eigenschaft|Beschreibung|Standard|
|--------------|-----------------|-------------|
|Sammlungstyp|Wenn diese Rolle eine Multiplizität von 0.. * oder 1.. aufweist \* , passt diese Eigenschaft den generischen Typ an, der zum Speichern der Auflistung von Links verwendet wird.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> wird verwendet|
|Benutzerdefinierte Attribute|Attribute, die Sie hier angeben, werden der generierten Code Klasse als Attribute hinzugefügt.|\<none>|
|Ist Eigenschaften suchbar|Wenn `True` , und wenn die Multiplizität der Beziehung 0.. 1 oder 1.. 1 ist, kann die Role-Eigenschaft vom Benutzer im **Eigenschaften** Fenster durchsucht werden. Die-Eigenschaft zeigt den Namen des Elements am anderen Ende des Beziehungslinks an.|`True`|
|Ist Property Generator|Wenn `True` der Wert ist, wird für diese Rolle eine Rollen Eigenschaft generiert, die Sie verwenden können, um die Beziehung im Programmcode zu durchlaufen. Wenn Sie diese Einstellung auf "false" festlegen, können Sie die Beziehung auf weniger effiziente Weise durchlaufen, indem Sie statische Methoden der Domänen Beziehung verwenden.|`True`|
|Zugriffs Modifizierer für Eigenschaften Getter|Der Zugriffsmodifizierer für den Getter der generierten Eigenschaft ( `public` , `internal` , `private` , `protected` oder `protected internal` ).|`public`|
|Zugriffs Modifizierer für Eigenschaften Setter|Der Zugriffsmodifizierer für den Setter für die generierte Eigenschaft ( `public` , `internal` , `private` , `protected` oder `protected internal` ).|`public`|
|Multiplizität|Die Anzahl der Modellelemente, die die entgegengesetzte Rolle wiedergeben können ( `0..1` , `1..1` , `0..*` oder `1..*` ). Wenn die Multiplizität `0..*` oder ist `1..*` , stellt die generierte Eigenschaft eine Auflistung dar; andernfalls stellt die generierte Eigenschaft ein einzelnes Modellelement dar.|Hängt vom Beziehungstyp und davon ab, ob dies die Quell-oder Zielrolle in der Beziehung ist.|
|Name|Der Name der Domänen Rolle. Diese Eigenschaft darf keine Leerzeichen enthalten.|Der Name der Domänen Klasse des Rollen Players für diese Rolle.|
|Überträgt Copy|`DoNotPropagateCopy` -Der kopierte Rollen Inhaber hat keine Kopie dieses Links.<br /><br /> `PropagateCopyToLinkOnly` -Der kopierte Link verweist auf den vorhandenen entgegengesetzten Rollen Inhaber.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` -Der kopierte Link verweist auf eine Kopie des entgegengesetzten Rollen Players.|`PropagateCopyToLinkAndOppositeRolePlayer` für die Quell Rollen von Einbettungen.<br /><br /> `DoNotPropagateCopy` für andere Rollen.<br /><br /> Weitere Informationen finden Sie unter [Anpassen des Kopier Verhaltens](../modeling/customizing-copy-behavior.md) .|
|Überträgt DELETE|`True` , um das Element zu löschen, das diese Rolle wieder gibt, wenn der zugehörige Link gelöscht wird.|`True` für das Ziel einer Einbettungs Rolle.<br /><br /> `False` für andere Rollen.<br /><br /> Weitere Informationen finden Sie unter [Anpassen des Lösch Verhaltens](../modeling/customizing-deletion-behavior.md).|
|Eigenschaftenname|Der Name der Eigenschaft, die im Code des Rollen Players generiert wurde. Dieser Name darf keine Leerzeichen enthalten.|Der Name der gegenüberliegenden Rolle, wenn diese Rolle über eine Null-zu-eins-oder eine 1:1-Multiplizität verfügt. andernfalls der pluralisierte Name der entgegengesetzten Rolle.|
|Rollen Inhaber|Die Domänen Klasse des Elements, das diese Rolle in der Beziehung wiedergeben kann. Diese Eigenschaft ist schreibgeschützt.|Die Domänen Klasse des Rollen Players für diese Rolle.|
|Notizen|Informelle Hinweise, die der Domänen Rolle zugeordnet sind.|\<none>|
|Category|Die Kategorie, unter der die generierte Eigenschaft im **Eigenschaften** Fenster des generierten Designers angezeigt wird. Wenn diese Eigenschaft leer ist, wird die generierte Eigenschaft unter **der Kategorie "** Verschiedenes" angezeigt.|\<none>|
|Beschreibung|Die Beschreibung, die verwendet wird, um Code zu dokumentieren, und wird in der Benutzeroberfläche des generierten Designers verwendet.<br /><br /> Die Beschreibung wird in der IntelliSense-QuickInfo für die generierte Eigenschaft für die Role Player-Klasse angezeigt.|`Description for`*der vollständige Name der Rolle* .|
|Anzeigename|Der Name, der im generierten Designer für die Domänen Rolle angezeigt wird.|Der angepasste Wert der Name-Eigenschaft.|
|Hilfsschlüsselwort|Das optionale Schlüsselwort, das zum Indizieren der F1-Hilfe für die Domänen Rolle verwendet wird.|\<none>|
|Anzeige Name der Eigenschaft|Der Name, der im generierten Designer für die generierte Role-Eigenschaft angezeigt wird.|Der angepasste Wert der Eigenschaft für den Eigenschaftsnamen.|

> [!NOTE]
> Der Standardwert eines anzeigen Amens basiert auf dem zugeordneten Eigenschafts Wert, indem Leerzeichen vor jedem Großbuchstaben eingefügt werden, dem ein Kleinbuchstabe vorangestellt wird und auf das kein anderes Großbuchstabe folgt.

## <a name="see-also"></a>Weitere Informationen
 [Eigenschaften von Domänenbeziehungen](../modeling/properties-of-domain-relationships.md)
