---
title: Erstellen einer Erweiterung mit einer Editor-Element Vorlage | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mit Element Vorlagen im Visual Studio SDK grundlegende Editor-Erweiterungen erstellen, mit denen Klassifizierer, Zusatzelemente und Ränder zum Editor hinzugefügt werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c8bfdcd854cf35c392578d9851a7421bacc8cbfe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884987"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>Erstellen einer Erweiterung mit einer Editor-Element Vorlage
Mithilfe von Element Vorlagen, die im Visual Studio SDK enthalten sind, können Sie grundlegende Editor-Erweiterungen erstellen, mit denen Klassifizierer, Zusatzelemente und Ränder zum Editor hinzugefügt werden. Die Editor-Element Vorlagen sind für Visual c#-oder Visual Basic VSIX-Projekte verfügbar.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-classifier-extension"></a>Erstellen einer Klassifizierungs Erweiterung
 Die Element Vorlage für den Editor-Klassifizierer erstellt einen editorklassifizierer, der den entsprechenden Text (in diesem Fall alles) in einer beliebigen Textdatei färbt.

1. Erweitern Sie im Dialogfeld **Neues Projekt** den Eintrag **Visual c#** , oder **Visual Basic** und klicken Sie dann auf **Erweiterbarkeit**. Wählen Sie im Bereich **Vorlagen** die Option **VSIX-Projekt** aus. Geben Sie im Feld **Name**`TestClassifier`ein. Klicken Sie auf **OK**.

2. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie   >  **Neues Element** hinzufügen aus. Wechseln Sie zum Visual c#- **Erweiterbarkeits** Knoten, und wählen Sie **Editor Klassifizierer** aus. Belassen Sie den Standard Dateinamen (*EditorClassifier1.cs*).

3. Es gibt vier Code Dateien, wie im folgenden dargestellt:

    - *EditorClassifier1.cs* enthält die- `EditorClassifier1` Klasse.

    - *EditorClassifier1ClassificationDefinition.cs* enthält die- `EditorClassifier1ClassificationDefinition` Klasse.

    - *EditorClassifier1Format.cs* enthält die- `EditorClassifier1Format`  Klasse.

    - *EditorClassifier1Provider.cs* enthält die- `EditorClassifier1Provider` Klasse.

4. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio wird angezeigt.

     Wenn Sie eine Textdatei öffnen, wird der gesamte Text gegen einen violetten Hintergrund unterstrichen.

## <a name="create-a-text-relative-adornment-extension"></a>Erstellen einer Erweiterung für Text-relative Zusatzelemente
 Mit der Editor-Text Zusatz Vorlage wird ein Text relativer Zusatzelement erstellt, das alle Instanzen des Text Zeichens "a" mit einem Feld mit einer roten Kontur und einem blauen Hintergrund ergänzt. Er ist Text relativ, da das Feld immer die Zeichen "a" überlagert, auch wenn Sie verschoben oder neu formatiert werden.

1. Erweitern Sie im Dialogfeld **Neues Projekt** den Eintrag **Visual c#** , oder **Visual Basic** und klicken Sie dann auf **Erweiterbarkeit**. Wählen Sie im Bereich **Vorlagen** die Option **VSIX-Projekt** aus. Geben Sie im Feld **Name**`TestAdornment`ein. Klicken Sie auf **OK**.

2. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie   >  **Neues Element** hinzufügen aus. Wechseln Sie zum Visual c#- **Erweiterbarkeits** Knoten, und wählen Sie **Editor-Text** Zusatzelement aus. Belassen Sie den Standard Dateinamen (*TextAdornment1.cs/VB*).

3. Es gibt zwei Code Dateien, wie im folgenden dargestellt:

    - *TextAdornment1.cs* enthält die- `TextAdornment1` Klasse.

    - *TextAdornment1TextViewCreationListener.cs* enthält die- `TextAdornment1TextViewCreationListener` Klasse.

4. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird geöffnet. Wenn Sie eine Textdatei öffnen, werden alle "a"-Zeichen im Text rot vor einem blauen Hintergrund dargestellt.

## <a name="create-a-viewport-relative-adornment-extension"></a>Erstellen einer Viewport-relativen Zusatzelement Erweiterung
 Mit der-Editor-Zusatzelement Vorlage wird ein Viewport-relativer Zusatzelement erstellt, das ein violettfeld mit einer roten Kontur in der oberen rechten Ecke des Viewports hinzufügt.

> [!NOTE]
> Der **Viewport** ist der Bereich der aktuell angezeigten Textansicht.

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>So erstellen Sie eine Viewport-Zusatzelement-Erweiterung mithilfe der Editor-Zusatzelement Vorlage

1. Erweitern Sie im Dialogfeld **Neues Projekt** den Eintrag **Visual c#** , oder **Visual Basic** und klicken Sie dann auf **Erweiterbarkeit**. Wählen Sie im Bereich **Vorlagen** die Option **VSIX-Projekt** aus. Geben Sie im Feld **Name**`ViewportAdornment`ein. Klicken Sie auf **OK**.

2. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie   >  **Neues Element** hinzufügen aus. Wechseln Sie zum Visual c#- **Erweiterbarkeits** Knoten, und wählen Sie **Editor Viewport**-Zusatzelement aus. Belassen Sie den Standard Dateinamen (*ViewportAdornment1.cs/VB*).

3. Es gibt zwei Code Dateien, wie im folgenden dargestellt:

    - *ViewportAdornment1.cs* enthält die- `ViewportAdornment1` Klasse.

    - *ViewportAdornment1TextViewCreationListener.cs* enthält die- `ViewportAdornment1TextViewCreationListener` Klasse.

4. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird geöffnet. Wenn Sie eine neue Textdatei erstellen, wird in der oberen rechten Ecke des Viewports ein violettfeld mit einem roten Umriss angezeigt.

## <a name="create-a-margin-extension"></a>Erstellen einer Rand Erweiterung
 Die Vorlage für den Editor Rand erstellt einen grünen Rand, der mit den Wörtern **Hello World!* unterhalb der horizontalen Schiebe Leiste.

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>So erstellen Sie eine Rand Erweiterung mithilfe der Editor-Rand Vorlage

1. Erweitern Sie im Dialogfeld **Neues Projekt** den Eintrag **Visual c#** , oder **Visual Basic** und klicken Sie dann auf **Erweiterbarkeit**. Wählen Sie im Bereich **Vorlagen** die Option **VSIX-Projekt** aus. Geben Sie im Feld **Name**`MarginExtension`ein. Klicken Sie auf **OK**.

2. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie   >  **Neues Element** hinzufügen aus. Wechseln Sie zum Visual c#- **Erweiterbarkeits** Knoten, und wählen Sie **Editor-Rand** aus. Belassen Sie den Standard Dateinamen (EditorMargin1.cs/VB).

3. Es gibt zwei Code Dateien, wie im folgenden dargestellt:

    - *EditorMargin1.cs* enthält die- `EditorMargin1` Klasse.

    - *EditorMargin1Factory.cs* enthält die- `EditorMargin1Factory` Klasse.

4. Erstellen Sie dieses Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird geöffnet. Wenn Sie eine Textdatei öffnen, wird unterhalb der horizontalen Schiebe Leiste ein grüner Rand angezeigt, der die Wörter **Hello EditorMargin1** enthält.

## <a name="see-also"></a>Weitere Informationen
- [Sprachdienst-und Editor-Erweiterungs Punkte](../extensibility/language-service-and-editor-extension-points.md)
