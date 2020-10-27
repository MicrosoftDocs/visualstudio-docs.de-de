---
title: Reduzieren und Erweitern von Codebereichen
description: Hier erfahren Sie, wie Sie die Befehle zum Auf- und Zuklappen verwenden, damit sie im Gliederungsmodus in Visual Studio funktionieren.
ms.custom: SEO-VS-2020
ms.date: 10/15/2020
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e45d7192c35ed60442fadf1a3eb302997fbaf381
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136666"
---
# <a name="outlining"></a>Gliedern

Sie können festlegen, dass bestimmter Code in der Ansicht ausgeblendet wird, indem Sie einen Codebereich reduzieren, der dann unterhalb eines Pluszeichens ( **+** ) angezeigt wird. Sie erweitern einen reduzierten Bereich, indem Sie auf das Pluszeichen klicken. Wenn Sie eine Tastatur verwenden, können Sie **STRG**+**M**+**M** drücken, um Bereiche zu reduzieren bzw. zu erweitern. Sie können einen Gliederungsbereich auch reduzieren, indem Sie am Gliederungsrand auf eine beliebige Zeile im Bereich doppelklicken, der direkt auf der linken Seite des Codes angezeigt. Sie können den Inhalt eines reduzierten Bereichs als QuickInfo sehen, wenn Sie auf den reduzierten Bereich zeigen.

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Quellcode-Editor (Visual Studio für Mac)](/visualstudio/mac/source-editor).

Bereiche am Gliederungsrand werden auch hervorgehoben, wenn Sie mit der Maus auf den Rand zeigen. Die standardmäßige Hervorhebungsfarbe wird möglicherweise in einigen Farbkonfigurationen etwas schwach angezeigt. Diese können Sie unter **Extras** > **Optionen** > **Umgebung** > **Schriftarten und Farben** > **Reduzierbarer Bereich** ändern.

Wenn Sie mit Code mit Rand arbeiten, können Sie die Bereiche erweitern, an denen Sie arbeiten, sie reduzieren, wenn Sie fertig sind, und dann mit anderen Bereichen fortfahren. Wenn Sie die Gliederung nicht anzeigen möchten, können Sie mit dem Befehl **Gliederung entfernen** die Gliederungsinformationen entfernen, ohne damit zugrunde liegenden Code zu beeinträchtigen.

Diese Aktionen werden durch die Befehle **Rückgängig** und **Wiederholen** im Menü **Bearbeiten** beeinflusst. Bei den Befehlen **Kopieren** , **Ausschneiden** und **Einfügen** sowie bei Drag & Drop-Vorgängen werden Gliederungsinformationen beibehalten, der Zustand des zuklappbaren Bereichs jedoch nicht. Wenn Sie beispielsweise einen zugeklappten Bereich kopieren, wird der kopierte Text beim Vorgang **Einfügen** als aufgeklappter Bereich eingefügt.

> [!CAUTION]
> Wenn Sie einen gegliederten Bereich ändern, geht die Gliederung möglicherweise verloren. Beispielsweise wird durch Löschvorgänge oder **Suchen und Ersetzen** das Ende des Bereichs möglicherweise gelöscht.

Die folgenden Befehle befinden sich im Untermenü **Bearbeiten** > **Gliedern** .

|name|Beschreibung|
|-|-|
|Aktuelles Element umschalten|( **STRG**+**M** , **STRG**+**H** ): Reduziert einen ausgewählten Codeblock, der normalerweise nicht für eine Gliederung verfügbar wäre, beispielsweise einen `if`-Block. Verwenden Sie die Option **Gliederung in aktuellem Element entfernen** , oder drücken Sie **STRG**+**M** , **STRG**+**U** , um den benutzerdefinierten Bereich zu entfernen. Nicht in Visual Basic verfügbar.|
|Gliederungserweiterung umschalten| **STRG**+**M** , **STRG**+**M** kehrt den aktuellen Zustand (ausgeblendet oder erweitert) des innersten Gliederungsbereichs um, wenn sich der Cursor in einem verschachtelten reduzierten Bereich befindet.|
|Alle Gliederungen umschalten|( **STRG**+**M** , **STRG**+**L** ): Legt alle Bereiche auf denselben reduzierten oder erweiterten Zustand fest. Wenn einige Bereiche erweitert und andere reduziert sind, werden die reduzierten Bereiche erweitert.|
|Gliederung entfernen|( **STRG**+**M** , **STRG**+**P** ): Entfernt alle Gliederungsinformationen für das gesamte Dokument.|
|Gliederung in aktuellem Element entfernen|( **STRG**+**M** , **STRG**+**U** ): Entfernt die Gliederungsinformationen für den aktuell ausgewählten benutzerdefinierten Bereich. Nicht in Visual Basic verfügbar.|
|Nur Definitionen anzeigen|( **STRG**+**M** , **STRG**+**O** ): Reduziert die Members aller Typen.|
|Block reduzieren:\<logical boundary>|(C++) Reduziert einen Bereich in der Funktion mit der Einfügemarke. Wenn beispielsweise die Einfügemarke innerhalb einer Schleife platziert ist, wird die Schleife ausgeblendet.|
|Alle reduzieren in:\<logical structures>|(C++) Reduziert alle Strukturen innerhalb der Funktion.|

Sie können auch das Visual Studio SDK verwenden, um die Textbereiche zu definieren, die Sie erweitern oder reduzieren möchten. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Gliedern](../extensibility/walkthrough-outlining.md).

## <a name="see-also"></a>Siehe auch

- [Features des Code-Editors](../ide/writing-code-in-the-code-and-text-editor.md)
- [Quellcode-Editor (Visual Studio für Mac)](/visualstudio/mac/source-editor)
