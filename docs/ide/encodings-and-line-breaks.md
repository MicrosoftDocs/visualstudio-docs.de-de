---
title: Codierung und Zeilenumbruchzeichen
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
ms.openlocfilehash: 6634a0b2715fb83a397b5e8cd0c8c68274771e2a
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93045594"
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
> 1. Klicken Sie auf die Registerkarte **Befehle** , aktivieren Sie das Kontrollkästchen **Menüleiste** , und wählen Sie in der entsprechenden Dropdownliste den Eintrag **Datei** aus. Klicken Sie auf die Schaltfläche **Befehl hinzufügen**. 
> 1. Klicken Sie unter **Kategorien** im Dialogfeld **Befehl hinzufügen** auf **Datei** , und klicken Sie dann in der Liste **Befehle** auf **Erweiterte Speicheroptionen**. Klicken Sie auf die Schaltfläche **OK**.
> 1. Verwenden Sie die Schaltflächen **Nach oben verschieben** und auf **Nach unten verschieben** , um den Befehl an eine beliebige Stelle im Menü zu verschieben. Klicken Sie auf **Schließen** , um das Dialogfeld **Anpassen** zu schließen. 
> Weitere Informationen finden Sie unter [Anpassen von Menüs und Symbolleisten](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> Alternativ können Sie über **Datei** >  **\<file\> speichern unter** das Dialogfeld **Erweiterte Speicheroptionen** öffnen. Klicken Sie im Dialogfeld **Datei speichern unter** auf den nach unten weisenden Pfeil neben der Schaltfläche **Speichern** , und klicken Sie auf **Mit Codierung speichern**.

## <a name="see-also"></a>Siehe auch

- [Features des Code-Editors](../ide/writing-code-in-the-code-and-text-editor.md)
