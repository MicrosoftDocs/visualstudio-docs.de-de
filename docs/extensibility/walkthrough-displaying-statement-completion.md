---
title: 'Exemplarische Vorgehensweise: Anzeigen der Anweisungs Vervollständigung | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie die sprachbasierte Anweisungs Vervollständigung für Klartext-Inhalte mithilfe dieser exemplarischen Vorgehensweise implementieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: acangialosi
ms.author: anthc
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 95c797de1e68b275fa1a36ec8fa1f97f665cfd18
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873917"
---
# <a name="walkthrough-display-statement-completion"></a>Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung
Sie können die sprachbasierte Anweisungs Vervollständigung implementieren, indem Sie die Bezeichner definieren, für die Sie den Abschluss bereitstellen möchten, und dann eine Beendigungs Sitzung auslösen. Sie können die Anweisungs Vervollständigung im Kontext eines sprach diensdienstanbieter definieren, eine eigene Dateinamenerweiterung und einen Inhaltstyp definieren und dann den Abschluss nur für diesen Typ anzeigen. Oder Sie können den Abschluss für einen vorhandenen Inhaltstyp, z. –. "Klartext", auslassen. In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie die Anweisungs Vervollständigung für den Inhaltstyp "Klartext", der den Inhaltstyp von Textdateien darstellt, auslöst. Der Inhaltstyp "Text" ist der Vorgänger aller anderen Inhaltstypen, einschließlich Code-und XML-Dateien.

 Die Anweisungs Vervollständigung wird in der Regel durch Eingabe bestimmter Zeichen ausgelöst, z. –. durch Eingabe des Anfangs eines Bezeichners, z. b. "using". Sie wird in der Regel durch Drücken der **LEERTASTE**, der **Tab**-Taste oder der **Eingabe** Taste, um eine Auswahl zu übernehmen. Sie können die IntelliSense-Funktionen implementieren, die beim Eingeben eines Zeichens mithilfe eines Befehls Handlers für die Tastatureingaben (die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Schnittstelle) und eines handleranbieters, der die- <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> Schnittstelle implementiert. Zum Erstellen der Vervollständigungs Quelle, bei der es sich um die Liste der Bezeichner handelt, die an der Vervollständigung beteiligt sind, implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> -Schnittstelle und einen Vervollständigungs Quellen Anbieter <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> Die Anbieter sind Managed Extensibility Framework Komponenten Teile (MEF). Sie sind dafür verantwortlich, die Quell-und Controller Klassen zu exportieren und Dienste und Broker zu importieren – z. b. die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , die die Navigation im Text Puffer ermöglicht, und die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> , die die Abschlusssitzung auslöst.

 In dieser exemplarischen Vorgehensweise wird gezeigt, wie die Anweisungs Vervollständigung für einen hart codierten Satz von bezeichern implementiert wird. In vollständigen Implementierungen sind der Sprachdienst und die Sprachdokumentation für die Bereitstellung dieses Inhalts verantwortlich.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Es ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Erstellen eines MEF-Projekts

#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt

1. Erstellen Sie ein c#-VSIX-Projekt. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual c#/Erweiterbarkeit** und dann **VSIX-Projekt** aus.) Benennen Sie die Projekt Mappe `CompletionTest` .

2. Fügen Sie dem Projekt eine Editor-Klassifizierungs Element Vorlage hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Löschen Sie die vorhandenen Klassendateien.

4. Fügen Sie dem Projekt die folgenden Verweise hinzu, und stellen Sie sicher, dass **CopyLocal** auf festgelegt ist `false` :

     Microsoft. VisualStudio. Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft. VisualStudio. Shell. 15,0

     Microsoft. VisualStudio. Shell. immutable. 10.0

     Microsoft. VisualStudio. Text Manager. Interop

## <a name="implement-the-completion-source"></a>Implementieren der Vervollständigungs Quelle
 Die Vervollständigungs Quelle ist für das Erfassen der Gruppe von Bezeichnern und das Hinzufügen des Inhalts zum Vervollständigungs Fenster verantwortlich, wenn ein Benutzer einen Vervollständigungs-, z. b. die ersten Buchstaben eines Bezeichners, eingibt. In diesem Beispiel sind die Bezeichner und ihre Beschreibungen in der-Methode hart codiert <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> . In der Praxis verwenden Sie den Parser der Programmiersprache, um die Token zum Auffüllen der Vervollständigungsliste zu erhalten.

### <a name="to-implement-the-completion-source"></a>So implementieren Sie die Vervollständigungs Quelle

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `TestCompletionSource`.

2. Fügen Sie diese Importe hinzu:

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. Ändern Sie die Klassen Deklaration für `TestCompletionSource` so, dass implementiert wird <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> :

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. Fügen Sie private Felder für den Quell Anbieter, den Text Puffer und eine Liste von <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> Objekten (die den bezeichern entsprechen, die an der Abschlusssitzung beteiligt sind) hinzu:

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. Fügen Sie einen Konstruktor hinzu, der den Quell Anbieter und-Puffer festlegt. Die- `TestCompletionSourceProvider` Klasse wird in späteren Schritten definiert:

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. Implementieren Sie die- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> Methode, indem Sie einen Vervollständigungs Satz hinzufügen, der die Vervollständigungen enthält, die Sie im Kontext bereitstellen möchten. Jeder Vervollständigungs Satz enthält eine Reihe von <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> Vervollständigungen und entspricht einer Registerkarte im Vervollständigungs Fenster. (In Visual Basic-Projekten werden die Registerkarten für das Abschluss Fenster " **Common** " und " **all**" genannt.) Die- `FindTokenSpanAtPosition` Methode wird im nächsten Schritt definiert.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. Die folgende Methode wird verwendet, um das aktuelle Wort von der Position des Cursors zu finden:

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. Implementieren Sie die- `Dispose()` Methode:

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>Implementieren des Vervollständigungs Quell Anbieters
 Der Vervollständigungs Quellen Anbieter ist der MEF-Komponenten Teil, der die Vervollständigungs Quelle instanziiert.

### <a name="to-implement-the-completion-source-provider"></a>So implementieren Sie den Vervollständigungs Quellen Anbieter

1. Fügen Sie eine Klasse mit dem Namen hinzu `TestCompletionSourceProvider` , die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> . Exportieren Sie diese Klasse mit <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Plaintext" und <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "Test Vervollständigung".

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. Importieren Sie einen <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , der das aktuelle Wort in der Vervollständigungs Quelle findet.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. Implementieren Sie die- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> Methode, um die Vervollständigungs Quelle zu instanziieren.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>Implementieren des Vervollständigungs Befehls Handler-Anbieters
 Der Vervollständigungs Befehls Handler-Anbieter wird von einem abgeleitet <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> , der auf ein Text Ansichts Erstellungs Ereignis lauscht und die Ansicht von einem –-Element konvertiert, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> das das Hinzufügen des Befehls zur Befehlskette der Visual Studio Shell – zu ermöglicht <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Da diese Klasse ein MEF-Export ist, können Sie Sie auch verwenden, um die Dienste zu importieren, die für den Befehls Handler selbst erforderlich sind.

#### <a name="to-implement-the-completion-command-handler-provider"></a>So implementieren Sie den Vervollständigungs Befehls Handler-Anbieter

1. Fügen Sie eine Datei namens hinzu `TestCompletionCommandHandler` .

2. Diese using-Direktiven hinzufügen:

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. Fügen Sie eine Klasse mit dem Namen hinzu `TestCompletionHandlerProvider` , die implementiert <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . Exportieren Sie diese Klasse mit <xref:Microsoft.VisualStudio.Utilities.NameAttribute> der "tokenvervollständigungs Handler", " <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Plaintext" und "" <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> von "" <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable> .

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. Importieren Sie den <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , der die Konvertierung von einem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> in einen <xref:Microsoft.VisualStudio.Text.Editor.ITextView> , einen und einen ermöglicht, der den <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> Zugriff auf standardmäßige Visual Studio-Dienste ermöglicht.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. Implementieren Sie die- <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> Methode, um den Befehls Handler zu instanziieren.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>Implementieren des Befehls Handlers für den Abschluss
 Da die Anweisungs Vervollständigung durch Tastatureingaben ausgelöst wird, müssen Sie die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle implementieren, um die Tastatureingaben zu empfangen und zu verarbeiten, die die Abschlusssitzung auslösen, übertragen und verwerfen.

#### <a name="to-implement-the-completion-command-handler"></a>So implementieren Sie den Vervollständigungs Befehls Handler

1. Fügen Sie eine Klasse mit dem Namen hinzu `TestCompletionCommandHandler` , die implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. Fügen Sie private Felder für den nächsten Befehls Handler (an den Sie den Befehl übergeben), die Textansicht, den Befehls Handler-Anbieter (der den Zugriff auf verschiedene Dienste ermöglicht) und eine Beendigungs Sitzung hinzu:

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. Fügen Sie einen Konstruktor hinzu, mit dem die Textansicht und die Anbieter Felder festgelegt werden, und fügen Sie der Befehlskette den Befehl hinzu:

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. Implementieren Sie die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode, indem Sie den Befehl übergeben:

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. Implementieren Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>-Methode. Wenn diese Methode eine Tastenkombination empfängt, muss Sie eine der folgenden Aktionen ausführen:

   - Erlauben Sie, dass das Zeichen in den Puffer geschrieben wird, und starten Sie dann den Abschluss des-oder-Filters. (Dies wird von Druck Zeichen durchführen.)

   - Commit für den Abschluss ausführen, lässt jedoch nicht zu, dass das Zeichen in den Puffer geschrieben wird. (Leerraum, **Tab** und **Eingabe** , wenn eine Vervollständigungs Sitzung angezeigt wird.)

   - Ermöglicht das Weitergeben des Befehls an den nächsten Handler. (Alle anderen Befehle)

     Da diese Methode möglicherweise die Benutzeroberfläche anzeigt, muss aufrufen, <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> um sicherzustellen, dass Sie nicht in einem Automatisierungs Kontext aufgerufen wird:

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. Dieser Code ist eine private Methode, die die Abschlusssitzung auslöst:

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. Das nächste Beispiel ist eine private Methode, die das Abonnement des Ereignisses enthebt <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> :

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes
 Um diesen Code zu testen, erstellen Sie die Projekt Mappe completiontest, und führen Sie Sie in der experimentellen Instanz aus.

#### <a name="to-build-and-test-the-completiontest-solution"></a>So erstellen und testen Sie die completiontest-Projekt Mappe

1. Erstellen Sie die Projektmappe.

2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

3. Erstellen Sie eine Textdatei, und geben Sie Text ein, der das Wort "Add" enthält.

4. Wenn Sie zuerst "a" und dann "d" eingeben, wird eine Liste angezeigt, die "Addition" und "Anpassung" enthält. Beachten Sie, dass Addition ausgewählt ist. Wenn Sie ein anderes "d" eingeben, sollte die Liste nur "Addition" enthalten, das jetzt ausgewählt ist. Sie können einen Commit für "Addition" durchführen, indem Sie die **LEERTASTE**, die **Tab**-Taste oder die **Eingabe** Taste drücken oder die Liste durch Eingabe von ESC oder eines beliebigen anderen Schlüssels verwerfen.

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
