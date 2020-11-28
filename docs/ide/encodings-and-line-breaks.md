---
title: Codierung und Zeilenumbruchzeichen
description: Erfahren Sie mehr über die Zeichen, die von Visual Studio als Zeilenumbrüche interpretiert werden, und darüber, wie die ursprünglichen Codierungs- und Zeilenumbruchzeichen verwaltet werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 889af1c0fd28224b2f31eb80bbeecad28346cd1c
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006639"
---
# <a name="encodings-and-line-endings"></a>Codierungen und Zeilenenden

In Visual Studio werden die folgenden Zeichen als Zeilenumbrüche interpretiert:

- CR LF: Wagenrücklauf und Zeilenvorschub, Unicode-Zeichen 000D und 000A

- LF: Zeilenvorschub, Unicode-Zeichen 000A

- NEL: Nächste Zeile, Unicode-Zeichen 0085

- LS: Zeilentrennzeichen, Unicode-Zeichen 2028

- PS: Absatztrennzeichen, Unicode-Zeichen 2029

In Text, der aus anderen Anwendungen kopiert wurde, bleiben die Codierungen und Zeilenumbruchzeichen unverändert. Wenn Sie beispielsweise Text aus Windows-Editor kopieren und in eine Textdatei in Visual Studio einfügen, weist der Text dieselben Einstellungen auf wie in Windows-Editor.

Wenn Sie eine Datei öffnen, die andere Zeilenumbruchzeichen aufweist, wird evtl. ein Dialogfeld angezeigt, in dem Sie gefragt werden, ob die inkonsistenten Zeilenumbruchzeichen normalisiert werden sollen und welche Art von Zeilenumbrüchen verwendet werden soll.

## <a name="advanced-save-options"></a>Erweiterte Speicheroptionen

Klicken Sie auf **Datei** > **Erweiterte Speicheroptionen**. Über das sich öffnende Dialogfeld können Sie den Typ des Zeilenumbruchs bestimmen. Sie können auch die Codierung einer Datei mit denselben Einstellungen ändern.

![Dialogfeld „Erweiterte Speicheroptionen“](media/line_endings.png)

> [!NOTE]
> Wenn **Erweiterte Speicheroptionen** im **Dateimenü** nicht angezeigt wird, können Sie dies hinzufügen. 
> 1. Wählen Sie **Extras** > **Anpassen** aus. 
> 1. Klicken Sie auf die Registerkarte **Befehle**, aktivieren Sie das Kontrollkästchen **Menüleiste**, und wählen Sie in der entsprechenden Dropdownliste den Eintrag **Datei** aus. Klicken Sie auf die Schaltfläche **Befehl hinzufügen**. 
> 1. Klicken Sie unter **Kategorien** im Dialogfeld **Befehl hinzufügen** auf **Datei**, und klicken Sie dann in der Liste **Befehle** auf **Erweiterte Speicheroptionen**. Klicken Sie auf die Schaltfläche **OK**.
> 1. Verwenden Sie die Schaltflächen **Nach oben verschieben** und auf **Nach unten verschieben**, um den Befehl an eine beliebige Stelle im Menü zu verschieben. Klicken Sie auf **Schließen**, um das Dialogfeld **Anpassen** zu schließen. 
> Weitere Informationen finden Sie unter [Anpassen von Menüs und Symbolleisten](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> Alternativ können Sie über **Datei** >  **\<file\> speichern unter** das Dialogfeld **Erweiterte Speicheroptionen** öffnen. Klicken Sie im Dialogfeld **Datei speichern unter** auf den nach unten weisenden Pfeil neben der Schaltfläche **Speichern**, und klicken Sie auf **Mit Codierung speichern**.

## <a name="see-also"></a>Siehe auch

- [Features des Code-Editors](../ide/writing-code-in-the-code-and-text-editor.md)
