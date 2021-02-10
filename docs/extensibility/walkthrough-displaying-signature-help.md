---
title: 'Exemplarische Vorgehensweise: Anzeigen der Signatur Hilfe | Microsoft-Dokumentation'
description: In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie die Signatur Hilfe für Text Inhaltstyp anzeigen. Signatur Hilfe zeigt die Signatur einer Methode in einer QuickInfo an.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8933822ee5bb63b341ff51296ba2884fef2aeb75
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935910"
---
# <a name="walkthrough-display-signature-help"></a>Exemplarische Vorgehensweise: Anzeigen der Signatur Hilfe
Mit der Signatur Hilfe (auch als *Parameter Info* bezeichnet) wird die Signatur einer Methode in einer QuickInfo angezeigt, wenn ein Benutzer das Parameter Listen-Startzeichen (in der Regel eine öffnende Klammer) eingibt. Wenn ein Parameter und Parameter Trennzeichen (in der Regel ein Komma) eingegeben werden, wird die QuickInfo aktualisiert, um den nächsten Parameter fett anzuzeigen. Auf folgende Weise können Sie die Signatur Hilfe definieren: im Kontext eines sprach dienstanzdienstanzdienstanbieter definieren Sie eine eigene Dateinamenerweiterung und einen Inhaltstyp und zeigen die Signatur Hilfe für diesen Typ an, oder Sie zeigen die Signatur Hilfe für einen vorhandenen Inhaltstyp an (z. b. "Text"). In dieser exemplarischen Vorgehensweise wird gezeigt, wie die Signatur Hilfe für den Inhaltstyp "Text" angezeigt wird.

 Die Signatur Hilfe wird in der Regel durch Eingabe eines bestimmten Zeichens ausgelöst, z. b. "(" (öffnende Klammer), und durch Eingabe eines anderen Zeichens, z. b. ")" (schließende Klammer). IntelliSense-Funktionen, die durch Eingabe eines Zeichens ausgelöst werden, können mithilfe eines Befehls Handlers für die Tastatureingaben (die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Schnittstelle) und eines handleranbieters implementiert werden, der die- <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> Schnittstelle implementiert. Um die Signatur Hilfe Quelle zu erstellen, die die Liste der Signaturen ist, die an der Signatur Hilfe beteiligt sind, implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> -Schnittstelle und einen Quell Anbieter, der die- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> Schnittstelle ausführt. Die Anbieter sind Managed Extensibility Framework Komponenten Komponenten (MEF), die für den Export der Quell-und Controller Klassen und das Importieren von Diensten und Brokern zuständig sind, z. b. das-Element, mit dem <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> Sie im Text Puffer navigieren können, und das-Element <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> , das die Signatur Hilfe Sitzung auslöst.

 In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie die Signatur Hilfe für einen hart codierten Satz von bezeichern einrichten. Bei vollständigen Implementierungen ist die Sprache für die Bereitstellung dieses Inhalts verantwortlich.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Es ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-mef-project"></a>Erstellen eines MEF-Projekts

#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt

1. Erstellen Sie ein c#-VSIX-Projekt. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual c#/Erweiterbarkeit** und dann **VSIX-Projekt** aus.) Benennen Sie die Projekt Mappe `SignatureHelpTest` .

2. Fügen Sie dem Projekt eine Editor-Klassifizierungs Element Vorlage hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Löschen Sie die vorhandenen Klassendateien.

4. Fügen Sie dem Projekt die folgenden Verweise hinzu, und stellen Sie sicher, dass **CopyLocal** auf festgelegt ist `false` :

     Microsoft. VisualStudio. Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft. VisualStudio. Shell. 14,0

     Microsoft. VisualStudio. Text Manager. Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>Implementieren von Signaturen und Parametern der Signatur Hilfe
 Die Signatur Hilfe Quelle basiert auf Signaturen, die implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> , die jeweils Parameter enthalten, die implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> . In einer vollständigen Implementierung werden diese Informationen aus der Sprachdokumentation abgerufen, aber in diesem Beispiel sind die Signaturen hart codiert.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>So implementieren Sie Signaturen und Parameter der Signatur Hilfe

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `SignatureHelpSource`.

2. Fügen Sie die folgenden Importe hinzu.

     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]

3. Fügen Sie eine Klasse mit dem Namen hinzu `TestParameter` , die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .

     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]

4. Fügen Sie einen Konstruktor hinzu, der alle Eigenschaften festlegt.

     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]

5. Fügen Sie die Eigenschaften von hinzu <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .

     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]

6. Fügen Sie eine Klasse mit dem Namen hinzu `TestSignature` , die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> .

     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]

7. Fügen Sie einige private Felder hinzu.

     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]

8. Fügen Sie einen Konstruktor hinzu, der die Felder festlegt und das-Ereignis abonniert <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> .

     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]

9. Deklarieren Sie ein- `CurrentParameterChanged` Ereignis. Dieses Ereignis wird ausgelöst, wenn der Benutzer einen der Parameter in der Signatur ausfüllt.

     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]

10. Implementieren Sie die- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> Eigenschaft, sodass das- `CurrentParameterChanged` Ereignis ausgelöst wird, wenn der-Eigenschafts Wert geändert wird.

     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]

11. Fügen Sie eine Methode hinzu, die das- `CurrentParameterChanged` Ereignis auslöst.

     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]

12. Fügen Sie eine Methode hinzu, die den aktuellen Parameter berechnet, indem Sie die Anzahl von Kommas in der <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> mit der Anzahl von Kommas in der Signatur vergleichen.

     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]

13. Fügen Sie einen Ereignishandler für das- <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Ereignis hinzu, das die- `ComputeCurrentParameter()` Methode aufruft.

     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]

14. Implementiert die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>-Eigenschaft. Diese Eigenschaft enthält ein-Objekt <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , das dem Textabschnitt im Puffer entspricht, für den die Signatur gilt.

     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]

15. Implementieren Sie die anderen Parameter.

     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]

## <a name="implement-the-signature-help-source"></a>Implementieren der Signatur Hilfe Quelle
 Die Signatur Hilfe Quelle ist der Satz von Signaturen, für den Sie Informationen bereitstellen.

#### <a name="to-implement-the-signature-help-source"></a>So implementieren Sie die Signatur Hilfe Quelle

1. Fügen Sie eine Klasse mit dem Namen hinzu `TestSignatureHelpSource` , die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> .

     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]

2. Fügen Sie einen Verweis auf den Text Puffer hinzu.

     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]

3. Fügen Sie einen Konstruktor hinzu, mit dem der Text Puffer und der Signatur Hilfe Quellen-Anbieter festgelegt werden.

     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]

4. Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>-Methode. In diesem Beispiel sind die Signaturen hart codiert, aber in einer vollständigen Implementierung würden Sie diese Informationen aus der Sprachdokumentation erhalten.

     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]

5. Die-Hilfsmethode `CreateSignature()` wird nur zur Veranschaulichung bereitgestellt.

     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]

6. Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>-Methode. In diesem Beispiel gibt es nur zwei Signaturen, von denen jede über zwei Parameter verfügt. Daher ist diese Methode nicht erforderlich. Bei einer umfassenderen Implementierung, bei der mehr als eine Signatur Hilfe Quelle verfügbar ist, wird diese Methode verwendet, um zu entscheiden, ob die Signatur Hilfe Quelle mit der höchsten Priorität eine passende Signatur bereitstellen kann. Wenn dies nicht möglich ist, gibt die Methode NULL zurück, und die Quelle mit der höchsten Priorität wird aufgefordert, eine Entsprechung anzugeben.

     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]

7. Implementieren Sie die- `Dispose()` Methode:

     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]

## <a name="implement-the-signature-help-source-provider"></a>Implementieren des Signatur Hilfe Quellen-Anbieters
 Der Signatur Hilfe Quellen-Anbieter ist für den Export des Komponenten Teils der Managed Extensibility Framework (MEF) und zum Instanziieren der Signatur Hilfe Quelle verantwortlich.

#### <a name="to-implement-the-signature-help-source-provider"></a>So implementieren Sie den Signatur Hilfe Quellen-Anbieter

1. Fügen Sie eine Klasse mit dem Namen hinzu, `TestSignatureHelpSourceProvider` die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> , und exportieren Sie Sie mit <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , einem <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> von "Text" und einem <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> von vor = "Default".

     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]

2. Implementieren Sie <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> durch Instanziieren von `TestSignatureHelpSource` .

     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]

## <a name="implement-the-command-handler"></a>Implementieren des Befehls Handlers
 Die Signatur Hilfe wird in der Regel durch eine öffnende Klammer "(" und durch ein Schließ Endes Klammer Zeichen ")" ausgelöst. Sie können diese Tastatureingaben behandeln, indem Sie eine ausführen <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , sodass Sie eine Signatur Hilfe Sitzung auslöst, wenn Sie ein öffnendes Klammer Zeichen empfängt, dem ein bekannter Methodenname vorangestellt ist, und die Sitzung abschließt, wenn Sie ein Schließ Endes Klammer Zeichen empfängt.

#### <a name="to-implement-the-command-handler"></a>So implementieren Sie den Befehls Handler

1. Fügen Sie eine Klasse mit dem Namen hinzu `TestSignatureHelpCommand` , die implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]

2. Fügen Sie private Felder für den Adapter hinzu (mit dem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Sie den Befehls Handler der Kette von Befehls Handlern hinzufügen können), die Textansicht, die Signatur Hilfe Broker und die Sitzung, eine <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> und die nächste <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]

3. Fügen Sie einen Konstruktor hinzu, um diese Felder zu initialisieren und der Kette von Befehls Filtern den Befehls Filter hinzuzufügen.

     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]

4. Implementieren Sie die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode, um die Signatur Hilfe Sitzung auslöst, wenn der Befehls Filter eine öffnende Klammer "(" nach einem der bekannten Methodennamen empfängt, und um die Sitzung zu schließen, wenn Sie ein Schließ Endes Klammer Zeichen ")" empfängt, während die Sitzung noch aktiv ist. In jedem Fall wird der Befehl weitergeleitet.

     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]

5. Implementieren Sie die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode, sodass Sie den Befehl immer weiterleitet.

     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]

## <a name="implement-the-signature-help-command-provider"></a>Implementieren des Signatur Hilfe-Befehls Anbieters
 Sie können den Signatur Hilfe Befehl bereitstellen, indem Sie implementieren <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> , um den Befehls Handler zu instanziieren, wenn die Textansicht erstellt wird.

### <a name="to-implement-the-signature-help-command-provider"></a>So implementieren Sie den Signatur Hilfe-Befehls Anbieter

1. Fügen Sie eine Klasse `TestSignatureHelpController` mit dem Namen hinzu, die implementiert, <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> und exportieren Sie Sie mit <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> und <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> .

     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]

2. Importieren Sie das (zum Abrufen des- <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> Objekts mit dem angegebenen- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Objekt), das <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> -Objekt (das zum Suchen nach dem aktuellen Wort verwendet wird) und das-Objekt <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (zum auslöst der Signatur Hilfe Sitzung).

     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]

3. Implementieren Sie die- <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> Methode, indem Sie die instanziieren `TestSignatureCommandHandler` .

     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes
 Um diesen Code zu testen, erstellen Sie die Projekt Mappe signaturehelptest, und führen Sie Sie in der experimentellen Instanz aus.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>So erstellen und testen Sie die Projekt Mappe signaturehelptest

1. Erstellen Sie die Projektmappe.

2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

3. Erstellen Sie eine Textdatei, und geben Sie Text ein, der das Wort "Add" sowie eine öffnende Klammer enthält.

4. Nachdem Sie die öffnende Klammer eingefügt haben, sollte eine QuickInfo angezeigt werden, in der eine Liste der beiden Signaturen für die Methode angezeigt wird `add()` .

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
