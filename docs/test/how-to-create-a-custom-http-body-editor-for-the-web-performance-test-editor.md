---
title: Erstellen eines HTTP-Text-Editors für einen Webleistungstest
description: Lernen Sie, einen benutzerdefinierten Inhalts-Editor zu erstellen, mit dem Sie den Zeichenfolgentextinhalt oder binären Textinhalt einer Webdienstanforderung bearbeiten können.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, custom HTTP body editor
ms.assetid: a0b2d8ff-3e2a-487e-9172-90047174f336
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: e096333d66fffd233bfb4b9de7f40e18f1277846
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966733"
---
# <a name="how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor"></a>Vorgehensweise: Erstellen eines Editors für benutzerdefinierten HTTP-Text für den Webleistungstest-Editor

Sie können einen benutzerdefinierten Inhalts-Editor erstellen, der Ihnen ermöglicht, den Zeichenfolgentextinhalt oder den binären Textinhalt einer Webdienstanforderung zu bearbeiten (z.B. SOAP, REST, asmx, wcf, RIA und andere Webdienstanforderungstypen).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Sie können diese Arten von Editoren implementieren:

- **Zeichenfolgeninhalts-Editor:** Wird mit der <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>-Schnittstelle implementiert.

- **Binärer Inhalts-Editor:** Wird mit der <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>-Schnittstelle implementiert.

Diese Schnittstellen sind im <xref:Microsoft.VisualStudio.TestTools.WebTesting>-Namespace enthalten.

## <a name="create-a-windows-control-library-project"></a>Erstellen eines Windows-Steuerelementbibliothek-Projekts

1. Erstellen Sie in Visual Studio ein neues Projekt **Windows Forms-Steuerelementbibliothek**. Benennen Sie das Projekt **MessageEditors**.

   Das Projekt wird zur neuen Projektmappe hinzugefügt, und im Designer wird ein <xref:System.Windows.Forms.UserControl>-Objekt mit dem Namen *UserControl1.cs* präsentiert.

1. Ziehen Sie von der **Toolbox** unter der Kategorie **Allgemeine Steuerelemente** ein <xref:System.Windows.Forms.RichTextBox>-Element auf die Oberfläche von „UserControl1“.

1. Wählen Sie das Aktionstagsymbol (![Smarttag-Glyphe](../test/media/vs_winformsmttagglyph.gif)) in der oberen rechten Ecke des <xref:System.Windows.Forms.RichTextBox>-Steuerelements aus, und klicken Sie dann auf **In übergeordnetem Container andocken**.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Windows Forms-Bibliotheksprojekt, und wählen Sie **Eigenschaften** aus.

1. Wählen Sie unter **Eigenschaften** die Registerkarte **Anwendung** aus.

1. Wählen Sie in der Dropdownliste **Zielframework** .NET Framework 4 (oder höher) aus.

1. Das Dialogfeld **Änderung des Zielframeworks** wird angezeigt.

1. Klicken Sie auf **Ja**.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **Verweise**, und wählen Sie **Verweise hinzufügen** aus.

1. Das Dialogfeld **Verweis hinzufügen** wird angezeigt.

1. Klicken Sie auf die Registerkarte **.NET**, scrollen Sie nach unten, und wählen Sie **Microsoft.VisualStudio.QualityTools.WebTestFramework** aus. Klicken Sie dann auf **OK**.

1. Wenn der **Ansicht-Designer** nicht mehr geöffnet ist, klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **UserControl1.cs**, und wählen Sie anschließend **Ansicht-Designer** aus.

1. Klicken Sie auf der Designoberfläche mit der rechten Maustaste, und wählen Sie **Code anzeigen** aus.

1. (Optional) Ändern Sie den Namen der Klasse und des Konstruktors von "UserControl1" in einen aussagekräftigen Namen, z. B. "MessageEditorControl":

    > [!NOTE]
    > Im Beispiel wird "MessageEditorControl" verwendet.

    ```csharp
    namespace MessageEditors
    {
        public partial class MessageEditorControl : UserControl
        {
            public MessageEditorControl()
            {
                InitializeComponent();
            }
        }
    }
    ```

1. Fügen Sie die folgenden Eigenschaften hinzu, um das Abrufen und Festlegen des Texts in "RichTextBox1" zu aktivieren. Die <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>-Schnittstelle verwendet EditString, und <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> verwendet EditByteArray:

    ```csharp
    public String EditString
    {
       get
       {
           return this.richTextBox1.Text;
       }
       set
       {
           this.richTextBox1.Text = value;
       }
    }

    public byte[] EditByteArray
    {
       get
       {
           return System.Convert.FromBase64String(richTextBox1.Text);
       }
       set
       {
           richTextBox1.Text = System.Convert.ToBase64String(value, 0, value.Length);
       }
    }
    ```

## <a name="add-a-class-to-the-windows-control-library-project"></a>Hinzufügen einer Klasse zum Projekt der Windows-Steuerelementbibliothek

Fügen Sie dem Projekt eine Klasse hinzu. Diese wird verwendet, um die <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>-Schnittstelle und die <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>-Schnittstelle zu implementieren.

**Übersicht über den Code in dieser Prozedur**

Das <xref:System.Windows.Forms.UserControl> "MessageEditorControl", das in der vorherigen Prozedur erstellt wurde, wird als "messageEditorControl" instanziiert:

```csharp
private MessageEditorControl messageEditorControl
```

Die messageEditorControl-Instanz wird innerhalb des Plug-In-Dialogfelds gehostet, das von der <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.CreateEditor*>-Methode erstellt wird. Darüber hinaus wird das <xref:System.Windows.Forms.RichTextBox> von "messageEditorControl" mit dem Inhalt von <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> aufgefüllt. Das Plug-In kann jedoch nur erstellt werden, wenn <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*>`true` zurückgibt. Bei diesem Editor gibt <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*>`true` zurück, wenn der <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> im <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> "xml" enthält.

Wenn die Bearbeitung des Zeichenfolgentexts abgeschlossen ist und der Benutzer im Plug-In-Dialogfeld auf **OK** klickt, wird <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.GetNewValue*> aufgerufen, um den bearbeiteten Text als Zeichenfolge abzurufen und den **Zeichenfolgentext** in der Anforderung im Webleistungstest-Editor zu aktualisieren.

### <a name="create-a-class-and-implement-the-istringhttpbodyeditorplugin-interface"></a>Erstellen Sie eine Klasse, und implementieren Sie die Schnittstelle IStringHttpBodyEditorPlugin.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt der Windows Forms-Steuerelementbibliothek, und wählen Sie **Neues Element hinzufügen** aus.

   Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

2. Wählen Sie **Klasse** aus.

3. Geben Sie im Textfeld **Name** einen aussagekräftigen Namen für die Klasse ein (z.B. `MessageEditorPlugins`).

4. Wählen Sie **Hinzufügen** aus.

   "Class1" wird dem Projekt hinzugefügt und im Code-Editor präsentiert.

5. Fügen Sie im Code-Editor folgende `using`-Anweisung hinzu:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    ```

6. Fügen Sie folgenden Code ein, um die Schnittstelle zu implementieren:

    ```csharp
    /// <summary>
    /// Editor for generic text based hierarchical messages such as XML and JSON.
    /// </summary>
    public class XmlMessageEditor : IStringHttpBodyEditorPlugin
    {
        public XmlMessageEditor()
        {
        }

        /// <summary>
        /// Determine if this plugin supports the content type.
        /// </summary>
        /// <param name="contentType">The content type to test.</param>
        /// <returns>Returns true if the plugin supports the specified content type.</returns>
        public bool SupportsContentType(string contentType)
        {
            return contentType.ToLower().Contains("xml");
        }

        /// <summary>
        /// Create a UserControl to edit the specified bytes.
        /// This control will be hosted in the
        /// plugin dialog which provides OK and Cancel buttons.
        /// </summary>
        /// <param name="contentType">The content type of the BinaryHttpBody.</param>
        /// <param name="initialValue">The bytes to edit. The bytes are the payload of a BinaryHttpBody.</param>
        /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
        public object CreateEditor(string contentType, string initialValue)
        {
            messageEditorControl = new MessageEditorControl();
            messageEditorControl.EditString = initialValue;
            return this.messageEditorControl;
        }

        /// <summary>
        /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
        /// </summary>
        public string GetNewValue()
        {
            return messageEditorControl.EditString;
        }

        private MessageEditorControl messageEditorControl;
    }
    ```

## <a name="add-a-ibinaryhttpbodyeditorplugin-to-the-class"></a>Hinzufügen eines IBinaryHttpBodyEditorPlugin zur Klasse

Implementieren Sie die <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>-Schnittstelle.

**Übersicht über den Code in dieser Prozedur**

Die Codeimplementierung für die <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>-Schnittstelle ähnelt der für <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> (siehe vorherige Prozedur). Die binäre Version behandelt die Binärdaten jedoch nicht mit einer Zeichenfolge, sondern mithilfe eines Bytearrays.

Das in der ersten Prozedur erstellte <xref:System.Windows.Forms.UserControl> "MessageEditorControl" wird als "messageEditorControl" instanziiert:

```csharp
private MessageEditorControl messageEditorControl
```

Die messageEditorControl-Instanz wird innerhalb des Plug-In-Dialogfelds gehostet, das von der <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.CreateEditor*>-Methode erstellt wird. Darüber hinaus wird das <xref:System.Windows.Forms.RichTextBox> von "messageEditorControl" mit dem Inhalt von <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> aufgefüllt. Das Plug-In kann jedoch nur erstellt werden, wenn <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*>`true` zurückgibt. Bei diesem Editor gibt <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*>`true` zurück, wenn der <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> im <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> "msbin1" enthält.

Wenn die Bearbeitung des Zeichenfolgentexts abgeschlossen ist und der Benutzer im Plug-In-Dialogfeld auf **OK** klickt, wird <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.GetNewValue*> aufgerufen, um den bearbeiteten Text als Zeichenfolge abzurufen und **BinaryHttpBody.Data** in der Anforderung im Webleistungstest-Editor zu aktualisieren.

### <a name="to-add-the-ibinaryhttpbodyeditorplugin-to-the-class"></a>So fügen Sie ein IBinaryHttpBodyEditorPlugin zur Klasse hinzu

- Schreiben oder kopieren Sie den folgenden Code unter der XmlMessageEditor-Klasse, die in der vorherigen Prozedur hinzugefügt wurde, um die Msbin1MessageEditor-Klasse von der <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>-Schnittstelle zu instanziieren und die erforderlichen Methoden zu implementieren:

    ```csharp
    /// <summary>
        /// Editor for MSBin1 content type (WCF messages)
        /// </summary>
        public class Msbin1MessageEditor : IBinaryHttpBodyEditorPlugin
        {
            /// <summary>
            ///
            /// </summary>
            public Msbin1MessageEditor()
            {
            }

            /// <summary>
            /// Determine if this plugin supports a content type.
            /// </summary>
            /// <param name="contentType">The content type to test.</param>
            /// <returns>Returns true if the plugin supports the specified content type.</returns>
            public bool SupportsContentType(string contentType)
            {
                return contentType.ToLower().Contains("msbin1");
            }

            /// <summary>
            /// Create a UserControl to edit the specified bytes. This control will be hosted in the
            /// plugin dialog which provides OK and Cancel buttons.
            /// </summary>
            /// <param name="contentType">The content type of the BinaryHttpBody.</param>
            /// <param name="initialValue">The bytes to edit. The bytes are the payload of a BinaryHttpBody.</param>
            /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
            public object CreateEditor(string contentType, byte[] initialValue)
            {
                messageEditorControl = new MessageEditorControl();
                messageEditorControl.EditByteArray = initialValue;
                return messageEditorControl;
            }

            /// <summary>
            /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
            /// </summary>
            public byte[] GetNewValue()
            {
                return messageEditorControl.EditByteArray;
            }

            private MessageEditorControl messageEditorControl;
            private object originalMessage;
        }
    ```

## <a name="build-and-deploy-the-plug-ins"></a>Erstellen und Bereitstellen der Plug-Ins

1. Klicken Sie im Menü **Build** auf **Build\<Windows Form Control Library project name>** .

2. Schließen Sie alle Instanzen von Visual Studio.

   > [!NOTE]
   > Dadurch wird sichergestellt, dass die *DLL-Datei* nicht gesperrt ist, bevor Sie versuchen, diese zu kopieren.

3. Kopieren Sie die resultierende *DLL-Datei* (z. B. *MessageEditors.dll*) aus dem Ordner *bin\debug* des Projekts in *%ProgramFiles%\Microsoft Visual Studio\2017\\\<edition>\Common7\IDE\PrivateAssemblies\WebTestPlugins*.

4. Öffnen Sie Visual Studio.

   Die *DLL-Datei* wird nun in Visual Studio registriert.

## <a name="verify-the-plug-ins-using-a-web-performance-test"></a>Überprüfen der Plug-Ins mithilfe eines Webleistungstests

1. Erstellen Sie ein Testprojekt.

2. Erstellen Sie einen Webleistungstest, und geben Sie im Browser eine URL zu einem Webdienst ein.

3. Wenn Sie die Aufzeichnung beenden, erweitern Sie im Webleistungstest-Editor die Anforderung für den Webdienst, und wählen Sie die Option **Zeichenfolgentext** oder **Binärer Text** aus.

4. Wählen Sie im Fenster **Eigenschaften** die Option „Zeichenfolgentext“ oder „Binärer Text“ aus, und klicken Sie anschließend auf die Auslassungspunkte **(…)** .

   Das Dialogfeld **HTTP-Textdaten bearbeiten** wird angezeigt.

5. Sie können die Daten jetzt bearbeiten und auf **OK** klicken. Hierdurch wird die anwendbare GetNewValue-Methode aufgerufen, die den Inhalt im <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> aktualisiert.

## <a name="compile-the-code"></a>Kompilieren des Codes

Überprüfen Sie, ob das Zielframework für das Windows-Steuerelementbibliothek-Projekt „.NET Framework 4.5“ ist. Standardmäßig verwenden Windows-Steuerelementbibliothek-Projekte das .NET Framework 4.5-Clientframework als Ziel, sodass der Verweis „Microsoft.VisualStudio.QualityTools.WebTestFramework“ nicht eingeschlossen werden kann.

Weitere Informationen finden Sie unter [Seite „Anwendung“, Projekt-Designer (C#)](../ide/reference/application-page-project-designer-csharp.md).

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.RichTextBox>
- [Erstellen von benutzerdefiniertem Code und benutzerdefinierten Plug-Ins für Auslastungstests](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [How to: Erstellen eines Anforderungsebenen-Plug-Ins](../test/how-to-create-a-request-level-plug-in.md)
- [Kodieren einer benutzerdefinierten Extraktionsregel für einen Webleistungstest](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kodieren einer benutzerdefinierten Validierungsregel für einen Webleistungstest](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [How to: Erstellen eines Auslastungstest-Plug-Ins](../test/how-to-create-a-load-test-plug-in.md)
- [Generieren und Ausführen eines codierten Webleistungstests](../test/generate-and-run-a-coded-web-performance-test.md)
- [How to: Erstellen eines Visual Studio-Add-Ins für den Webleistungstest-Ergebnisviewer](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)
