---
title: 'Exemplarische Vorgehensweise: Implementieren von Code Ausschnitten | Microsoft-Dokumentation'
description: Sie können Code Ausschnitte erstellen und in eine Editor-Erweiterung einschließen. In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie Code Ausschnitte erstellen und registrieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 5a36590c0e56f1e1a2c01f8e084f0b95442607a5
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877116"
---
# <a name="walkthrough-implement-code-snippets"></a>Exemplarische Vorgehensweise: Implementieren von Code Ausschnitten
Sie können Code Ausschnitte erstellen und in einer Editor-Erweiterung einschließen, damit Benutzer der Erweiterung Sie Ihrem eigenen Code hinzufügen können.

 Ein Code Ausschnitt ist ein Fragment von Code oder anderem Text, der in eine Datei eingebunden werden kann. Wenn Sie alle Ausschnitte anzeigen möchten **, die für** bestimmte Programmiersprachen registriert wurden, klicken Sie im Menü Extras auf **Code Ausschnitt-Manager**. Um einen Ausschnitt in eine Datei einzufügen, klicken Sie mit der rechten Maustaste auf den gewünschten Ausschnitt, klicken Sie auf Ausschnitt einfügen oder **Umschließen mit**, suchen Sie den gewünschten Ausschnitt, und doppelklicken Sie darauf. Drücken  Sie die Tab-oder **UMSCHALT** + **Registerkarte** , um die relevanten Teile des Code Ausschnitts zu ändern, und drücken Sie dann die **Eingabe** Taste oder **ESC** , um die Weitere Informationen finden Sie unter [Code Ausschnitte](../ide/code-snippets.md).

 Ein Code Ausschnitt ist in einer XML-Datei mit der Dateinamenerweiterung ". Ausschnitt *" enthalten. Ein Code Ausschnitt kann Felder enthalten, die nach dem Einfügen des Ausschnitts hervorgehoben werden, damit der Benutzer Sie finden und ändern kann. Eine codeausschnittsdatei enthält auch Informationen zum **Code Ausschnitt-Manager** , sodass der Ausschnitt Name in der richtigen Kategorie angezeigt werden kann. Weitere Informationen zum Code Ausschnitt Schema finden Sie unter [Schema Referenz für Code Ausschnitte](../ide/code-snippets-schema-reference.md).

 In dieser exemplarischen Vorgehensweise wird erläutert, wie Sie diese Aufgaben ausführen:

1. Erstellen und registrieren Sie Code Ausschnitte für eine bestimmte Sprache.

2. Fügen Sie einem Kontextmenü den Befehl **Ausschnitt einfügen** hinzu.

3. Code Ausschnitt Erweiterung implementieren.

   Diese exemplarische Vorgehensweise basiert auf der exemplarischen Vorgehensweise [: Anweisungs Vervollständigung anzeigen](../extensibility/walkthrough-displaying-statement-completion.md).

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Es ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-and-register-code-snippets"></a>Erstellen und Registrieren von Code Ausschnitten
 In der Regel sind Code Ausschnitte einem registrierten Sprachdienst zugeordnet. Sie müssen jedoch keine implementieren, <xref:Microsoft.VisualStudio.Package.LanguageService> um Code Ausschnitte zu registrieren. Geben Sie stattdessen einfach eine GUID in der codeausschnittsindexdatei an, und verwenden Sie dann die gleiche GUID in der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> , die Sie dem Projekt hinzufügen.

 Die folgenden Schritte veranschaulichen, wie Sie Code Ausschnitte erstellen und einer bestimmten GUID zuordnen.

1. Erstellen Sie die folgende Verzeichnisstruktur:

    **%INSTALLDIR%\testsnippeer \snipp\1033\\**

    Dabei ist " *% INSTALLDIR%* " der Visual Studio-Installationsordner. (Obwohl dieser Pfad in der Regel verwendet wird, um Code Ausschnitte zu installieren, können Sie einen beliebigen Pfad angeben.)

2. Erstellen Sie im Ordner "\ 1033 \" eine *XML* -Datei, und benennen Sie Sie **TestSnippets.xml**. (Obwohl dieser Name in der Regel für eine codeausschnittsindexdatei verwendet wird, können Sie einen beliebigen Namen angeben, sofern er die Dateinamenerweiterung *. XML* aufweist.) Fügen Sie den folgenden Text hinzu, und löschen Sie dann die Platzhalter-GUID, und fügen Sie Ihr eigenes hinzu.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <SnippetCollection>
       <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}">
           <SnippetDir>
               <OnOff>On</OnOff>
               <Installed>true</Installed>
               <Locale>1033</Locale>
               <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath>
               <LocalizedName>Snippets</LocalizedName>
           </SnippetDir>
       </Language>
   </SnippetCollection>
   ```

3. Erstellen Sie eine Datei im Ausschnitt Ordner, nennen Sie Sie " **Test**" `.snippet` , und fügen Sie dann den folgenden Text hinzu:

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
       <CodeSnippet Format="1.0.0">
           <Header>
               <Title>Test replacement fields</Title>
               <Shortcut>test</Shortcut>
               <Description>Code snippet for testing replacement fields</Description>
               <Author>MSIT</Author>
               <SnippetTypes>
                   <SnippetType>Expansion</SnippetType>
               </SnippetTypes>
           </Header>
           <Snippet>
               <Declarations>
                   <Literal>
                     <ID>param1</ID>
                       <ToolTip>First field</ToolTip>
                       <Default>first</Default>
                   </Literal>
                   <Literal>
                       <ID>param2</ID>
                       <ToolTip>Second field</ToolTip>
                       <Default>second</Default>
                   </Literal>
               </Declarations>
               <References>
                  <Reference>
                      <Assembly>System.Windows.Forms.dll</Assembly>
                  </Reference>
               </References>
               <Code Language="TestSnippets">
                   <![CDATA[MessageBox.Show("$param1$");
        MessageBox.Show("$param2$");]]>
               </Code>
           </Snippet>
       </CodeSnippet>
   </CodeSnippets>
   ```

   Die folgenden Schritte zeigen, wie die Code Ausschnitte registriert werden.

### <a name="to-register-code-snippets-for-a-specific-guid"></a>So registrieren Sie Code Ausschnitte für eine bestimmte GUID

1. Öffnen Sie das Projekt **completiontest** . Weitere Informationen zum Erstellen dieses Projekts finden Sie unter Exemplarische Vorgehensweise [: Anzeigen der Anweisungs Vervollständigung](../extensibility/walkthrough-displaying-statement-completion.md).

2. Fügen Sie im-Projekt Verweise auf die folgenden Assemblys hinzu:

    - Microsoft. VisualStudio. Text Manager. Interop

    - Microsoft. VisualStudio. Text Manager. Interop. 8.0

    - Microsoft. MSXML

3. Öffnen Sie im Projekt die Datei " **Source. Extension. vsixmanifest** ".

4. Stellen Sie sicher, dass die Registerkarte **Assets** einen **VSPackage** -Inhaltstyp enthält und dass das **Projekt** auf den Namen des Projekts festgelegt ist.

5. Wählen Sie das Projekt completiontest aus, und legen Sie im Eigenschaftenfenster die Option **pkgdef-Datei generieren** auf **true** fest. Speichern Sie das Projekt.

6. Fügen Sie `SnippetUtilities` dem Projekt eine statische Klasse hinzu.

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7. Definieren Sie in der snipptilities-Klasse eine GUID, und versehen Sie Sie mit dem Wert, den Sie in der *SnippetsIndex.xml* -Datei verwendet haben.

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8. Fügen Sie der- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> `TestCompletionHandler` Klasse hinzu. Dieses Attribut kann jeder öffentlichen oder internen (nicht statischen) Klasse im Projekt hinzugefügt werden. (Möglicherweise müssen Sie eine- `using` Direktive für den Microsoft. VisualStudio. Shell-Namespace hinzufügen.)

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. Erstellen Sie das Projekt, und führen Sie es aus. In der experimentellen Instanz von Visual Studio, die gestartet wird, wenn das Projekt ausgeführt wird, sollte der soeben registrierte Ausschnitt im Code Ausschnitt- **Manager** unter der Sprache " **testsnippets** " angezeigt werden.

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Fügen Sie dem Kontextmenü den Befehl Ausschnitt einfügen hinzu.
 Der Befehl **Ausschnitt einfügen** ist nicht im Kontextmenü für eine Textdatei enthalten. Daher müssen Sie den Befehl aktivieren.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>So fügen Sie dem Kontextmenü den Befehl "Ausschnitt einfügen" hinzu

1. Öffnen Sie die `TestCompletionCommandHandler` Klassendatei.

     Da diese Klasse implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , können Sie den Befehl **Ausschnitt einfügen** in der- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode aktivieren. Überprüfen Sie vor dem Aktivieren des Befehls, dass diese Methode nicht innerhalb einer Automatisierungsfunktion aufgerufen wird, da beim Klicken auf den Befehl **Ausschnitt einfügen** die Benutzeroberfläche für die Ausschnitt Auswahl angezeigt wird.

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2. Erstellen Sie das Projekt, und führen Sie es aus. Öffnen Sie in der experimentellen Instanz eine Datei mit der Dateinamenerweiterung *. zzz* , und klicken Sie dann mit der rechten Maustaste auf eine beliebige Stelle. Der Befehl **Ausschnitt einfügen** sollte im Kontextmenü angezeigt werden.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Implementieren der Ausschnitt Erweiterung in der Benutzeroberfläche der Ausschnitt Auswahl
 In diesem Abschnitt wird gezeigt, wie Sie die Code Ausschnitt Erweiterung implementieren, damit die Benutzeroberfläche für die Ausschnitt Auswahl angezeigt wird, wenn Sie im Kontextmenü auf **Ausschnitt einfügen** klicken. Ein Code Ausschnitt wird auch erweitert, wenn ein Benutzer die Verknüpfung mit dem Code Ausschnitt eingibt, und dann die **Tab**-Taste drückt.

 Verwenden Sie die-Methode, um die Benutzeroberfläche für die Ausschnitt Auswahl anzuzeigen und die Code Ausschnitt Akzeptanz zu aktivieren <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> . Die Einfügung selbst wird von der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> Methode behandelt.

 Die Implementierung der Code Ausschnitt Erweiterung verwendet Legacy <xref:Microsoft.VisualStudio.TextManager.Interop> Schnittstellen. Beachten Sie beim Übersetzen der aktuellen Editor-Klassen in den Legacy Code, dass die Legacy Schnittstellen eine Kombination aus Zeilennummern und Spalten Nummern verwenden, um Orte in einem Text Puffer anzugeben, die aktuellen Klassen jedoch einen Index verwenden. Wenn ein Puffer aus drei Zeilen besteht, von denen jeder 10 Zeichen aufweist (plus ein Zeilen Vorstrich, der als ein Zeichen zählt), befindet sich das vierte Zeichen in der dritten Zeile in der aktuellen Implementierung an der Position 27, aber es befindet sich in Zeile 2, Position 3 in der alten Implementierung.

#### <a name="to-implement-snippet-expansion"></a>So implementieren Sie die Ausschnitt Erweiterung

1. Fügen Sie der Datei, die die `TestCompletionCommandHandler` Klasse enthält, die folgenden `using` Direktiven hinzu.

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2. Legen Sie die- `TestCompletionCommandHandler` Klasse für die Implementierung der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> Schnittstelle

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3. Importieren Sie in der- `TestCompletionCommandHandlerProvider` Klasse <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> .

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4. Fügen Sie einige private Felder für die Code Erweiterungs Schnittstellen und hinzu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5. Legen Sie im Konstruktor der- `TestCompletionCommandHandler` Klasse die folgenden Felder fest.

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6. Fügen Sie der-Methode den folgenden Code hinzu, um die Ausschnitt Auswahl anzuzeigen, wenn der Benutzer auf den Befehl **Ausschnitt einfügen** klickt <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> . (Um diese Erklärung besser lesbar zu machen, `Exec()` wird der Code, der für die Anweisungs Vervollständigung verwendet wird, nicht angezeigt. stattdessen werden Code Blöcke der vorhandenen Methode hinzugefügt.) Fügen Sie den folgenden Codeblock nach dem Code hinzu, der auf ein Zeichen prüft.

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7. Wenn ein Ausschnitt über Felder verfügt, die navigiert werden können, bleibt die Erweiterungs Sitzung geöffnet, bis die Erweiterung explizit akzeptiert wird. Wenn der Code Ausschnitt keine Felder enthält, wird die Sitzung geschlossen und `null` von der-Methode zurückgegeben <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> . Fügen Sie in der- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode nach dem UI-Code Ausschnitt Auswahl, den Sie im vorherigen Schritt hinzugefügt haben, den folgenden Code hinzu, um die Ausschnitt Navigation zu verarbeiten (wenn der Benutzer die **Tab** -oder **UMSCHALT**- + **Registerkarte** nach dem Einfügen des Code Ausschnitts drückt).

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8. Fügen Sie der-Methode Code hinzu, um den Code Ausschnitt einzufügen, wenn der Benutzer die entsprechende Verknüpfung eingibt, und dann die **Tab**-Taste drückt <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> . Die private Methode, mit der der Ausschnitt eingefügt wird, wird in einem späteren Schritt angezeigt. Fügen Sie den folgenden Code nach dem Navigations Code hinzu, den Sie im vorherigen Schritt hinzugefügt haben.

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. Implementieren Sie die Methoden der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> Schnittstelle. In dieser Implementierung sind nur die zu berücksichtigenden Methoden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> . Die anderen Methoden sollten nur zurückgeben <xref:Microsoft.VisualStudio.VSConstants.S_OK> .

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>-Methode. Die Hilfsmethode, die die Erweiterungen tatsächlich einfügt, wird in einem späteren Schritt behandelt. Der <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> enthält Zeilen-und Spalten Informationen, die Sie aus dem erhalten können <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. Die folgende private Methode fügt einen Code Ausschnitt ein, der entweder auf der Verknüpfung oder dem Titel und Pfad basiert. Anschließend wird die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> Methode mit dem Code Ausschnitt aufgerufen.

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>Build-und Test Code Ausschnitt Erweiterung
 Sie können testen, ob die Ausschnitt Erweiterung in Ihrem Projekt funktioniert.

1. Erstellen Sie die Projektmappe. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

2. Öffnen Sie eine Textdatei, und geben Sie Text ein.

3. Klicken Sie mit der rechten Maustaste auf den Text, und klicken Sie dann auf **Ausschnitt einfügen**.

4. Die Benutzeroberfläche der Ausschnitt Auswahl sollte mit einem Popup Fenster angezeigt werden, in dem die **Test Ersetzungs Felder** aufgeführt sind. Doppelklicken Sie auf das Popup.

     Der folgende Code Ausschnitt sollte eingefügt werden.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     Drücken **Sie die Eingabe** Taste oder **ESC** nicht.

5. Drücken Sie die **Tab-** Taste und die **UMSCHALT** + **Registerkarte** , um zwischen "First" und "Second" zu wechseln.

6. Nehmen Sie die Einfügung durch Drücken der **Eingabe** Taste oder **ESC** an.

7. Geben Sie in einem anderen Textabschnitt "Test" ein, und drücken Sie dann die **Tab**-Taste. Da "Test" die Code Ausschnitt Verknüpfung ist, sollte der Ausschnitt erneut eingefügt werden.

## <a name="next-steps"></a>Nächste Schritte
