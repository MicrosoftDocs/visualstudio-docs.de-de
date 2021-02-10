---
title: Zeilenumbruch
description: Hier erfahren Sie, wie Sie im Code-Editor die Option „Zeilenumbruch“ ein- und ausschalten.
ms.custom: SEO-VS-2020
ms.date: 11/07/2018
ms.topic: how-to
helpviewer_keywords:
- word wrap
- editors, text viewing
- Code Editor, word wrap
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 57e218dadfe04d8cad034f2638ffefb9346e5a41
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894594"
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>Vorgehensweise: Verwalten von Zeilenumbrüchen im Editor

Sie können die Option **Zeilenumbruch** aktivieren und deaktivieren. Wenn diese Option aktiviert ist, wird der Teil einer langen Zeile, der über die aktuelle Breite des Code-Editor-Fensters hinausgeht, auf der nächsten Zeile angezeigt. Wenn diese Option deaktiviert ist, können Sie nach rechts scrollen, um ans Ende von langen Zeilen zu gelangen, z.B. um die Verwendung der Zeilennummerierung zu erleichtern.

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Quellcode-Editor: Zeilenumbruch](/visualstudio/mac/source-editor#word-wrap).

## <a name="to-set-word-wrap-preferences"></a>So legen Sie Einstellungen für den Zeilenumbruch fest

1. Klicken Sie im Menü **Extras** auf **Optionen**.

2. Wählen Sie im Ordner **Text-Editor** im Unterordner **Alle Sprachen** die Option **Allgemein** aus, um diese Option global festzulegen.

     \- oder -

     Wählen Sie die Optionen **Allgemein** im Unterordner für die Sprache aus, in der Sie programmieren.

3. Aktivieren oder Deaktivieren Sie in **Einstellungen** die Option **Zeilenumbruch**.

     Wenn die Option **Zeilenumbruch** aktiviert ist, wird die Option **Visuelle Symbole für Zeilenumbruch anzeigen** aktiviert.

4. Wählen Sie die Option **Visuelle Symbole für Zeilenumbruch anzeigen** aus, wenn Sie beim Umbruch einer langen Zeile auf eine zweite Zeile lieber einen Indikator in Form eines Rückwärtspfeils anzeigen lassen möchten. Deaktivieren Sie diese Option, wenn Sie diese Indikatoren nicht anzeigen möchten.

    > [!NOTE]
    > Diese Markierungspfeile werden nicht in Ihren Code eingefügt, sie dienen lediglich der Anzeige.

## <a name="known-issues"></a>Bekannte Probleme

Wenn Sie mit Zeilenumbrüchen in Notepad++, Sublime Text oder Visual Studio Code vertraut sind, beachten Sie folgende Probleme, bei denen Visual Studio sich anders als andere Editoren verhält:

* [Triple click doesn't select whole line (Durch dreifaches Klicken wird nicht die gesamte Zeile ausgewählt)](https://developercommunity.visualstudio.com/content/problem/268989/triple-click-doesnt-select-whole-line-when-word-wr.html)
* [Pressing End key twice does not move cursor to end of line (Durch doppeltes Drücken der Taste „Ende“ wird der Zeiger nicht zum Zeilenende bewegt)](https://developercommunity.visualstudio.com/content/problem/138274/pressing-end-key-twice-should-move-cursor-to-end-o.html)

## <a name="see-also"></a>Siehe auch

- [Features des Code-Editors](../../ide/writing-code-in-the-code-and-text-editor.md)
