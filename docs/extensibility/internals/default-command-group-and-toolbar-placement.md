---
title: Standardmäßige Befehls-, Gruppen-und Symbolleisten Platzierung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b432b514231e876dda1393bad8a315030272d998
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708889"
---
# <a name="default-command-group-and-toolbar-placement"></a>Standardmäßige Befehls-, Gruppen-und Symbolleisten Platzierung
Bei der Einheitlichkeit und Stabilität von Produkten werden von der Benutzeroberfläche standardmäßig bestimmte Befehls Gruppen angezeigt, und [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Definitionen für Befehle und Befehls Gruppen werden bereitstellt. VSPackages können auch die Standard Befehle und Befehls Gruppen verwenden.

 Die standardmäßigen Befehls Gruppen werden in drei Kategorien unterteilt: IDE-Befehle, Produkt Befehle und Editor-Befehle.

## <a name="default-ide-commands"></a>IDE-Standard Befehle
 Die IDE-Standard Symbolleiste enthält Befehle, die von allen in enthaltenen Produkten gemeinsam genutzt werden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Diese umfassen Befehle im Zusammenhang mit generischen Projekt Vorgängen, wie z. b. den Befehl **Speichern** und den Befehl **Element hinzufügen** . VSPackages sollten diese Symbolleiste nicht hinzufügen oder von dieser entfernen, mit einer Ausnahme: Wenn das Produkt oder das VSPackage ein neues Tool Fenster hinzufügt, sollte das Fenster der Liste der verfügbaren Tool Fenster im Menü **Ansicht** hinzugefügt werden. Neue Produkte oder VSPackages können Ihre eigene Symbolleiste hinzufügen.

## <a name="default-product-commands"></a>Standardprodukt Befehle
 Jedes Produkt kann der IDE eine eigene Standard Symbolleiste bereitstellen, die wichtige und häufig verwendete Befehle enthält. Es ist jedoch am besten, wenn möglich vorhandene Menüs und Symbolleisten zu verwenden und Sie bei Bedarf mit anderen aufgabenspezifischen Symbolleisten zu ergänzen.

 Das Prioritäts Feld für eine Symbolleiste bestimmt die Zeilen Platzierung. Die Priorität 0 legt die Symbolleiste in der dritten Zeile (Zeile 3) unterhalb der Menüleiste (Zeile 1) und der **Standard** Symbolleiste (Zeile 2) ab. Aus diesem Grund werden andere Symbolleisten in Zeile (Priorität + 3) angezeigt. Nachfolgende Symbolleisten werden in derselben Zeile platziert, wenn Platz vorhanden ist. Andernfalls werden Sie automatisch in die nächste Zeile verschoben.

## <a name="default-editor-commands"></a>Standard-Editor-Befehle
 Ein VSPackage, das einen benutzerdefinierten Editor bereitstellt, sollte eine Standard Symbolleiste mit den wichtigsten und häufig verwendeten Befehlen in diesem Editor enthalten. Die Editor-Symbolleiste sollte angezeigt werden, wenn der Editor aktiv ist und ausgeblendet werden sollte, wenn der Editor nicht aktiv ist. Diese Sichtbarkeit wird im- `VisibilityConstraints` Element der *vsct* -Datei gesteuert.

 Editor-Symbolleisten sollten unterhalb der IDE und der Produktsymbol leisten platziert werden.

## <a name="see-also"></a>Weitere Informationen
- [IDE-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)
- [Hinzufügen von Elementen der Benutzeroberfläche durch VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
