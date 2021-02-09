---
title: 'Exemplarische Vorgehensweise: Erstellen eines SDK mithilfe von JavaScript | Microsoft-Dokumentation'
description: In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie mithilfe von JavaScript ein einfaches mathematisches SDK als Visual Studio-Erweiterung erstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: db722d945ceb4b3d2cab92b9a11b1e689cd7a9bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895192"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>Exemplarische Vorgehensweise: Erstellen eines SDK mithilfe von JavaScript
In dieser exemplarischen Vorgehensweise wird erläutert, wie Sie JavaScript verwenden, um ein einfaches Math-SDK als Visual Studio-Erweiterung (VSIX) zu erstellen.  Die exemplarische Vorgehensweise ist in folgende Teile unterteilt:

- [So erstellen Sie das simplemathvsix-Erweiterungs-SDK-Projekt](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [So erstellen Sie eine Beispiel-APP, die das SDK verwendet](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  Für JavaScript gibt es keinen Klassenbibliotheks-Projekttyp. In dieser exemplarischen Vorgehensweise wird die Beispiel *arithmetic.js* Datei direkt im VSIX-Projekt erstellt. In der Praxis empfiehlt es sich, zuerst die JavaScript-und CSS-Dateien als Windows Store-App zu erstellen und zu testen – beispielsweise mithilfe der Vorlage **leere App** –, bevor Sie Sie in ein VSIX-Projekt einfügen.

## <a name="prerequisites"></a>Voraussetzungen
 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a> So erstellen Sie das simplemathvsix-Erweiterungs-SDK-Projekt

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

2. Wählen Sie in der Liste der Vorlagen Kategorien unter **Visual c#** die Option **Erweiterbarkeit** aus, und wählen Sie dann die **VSIX-Projekt** Vorlage aus.

3. Geben Sie im Textfeld **Name** `SimpleMathVSIX` die Schaltfläche **OK** an, und wählen Sie Sie aus.

4. Wenn der **Assistent für das Visual Studio-Paket** angezeigt wird, wählen Sie die Schaltfläche **weiter** auf der **Willkommens** Seite aus, und klicken Sie dann auf **Seite 1 von 7** auf die Schaltfläche **Fertig** stellen.

     Obwohl der **Manifest-Designer** geöffnet wird, behalten wir diese exemplarische Vorgehensweise bei, indem wir die Manifest-Datei direkt ändern.

5. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für die Datei " **Source. Extension. vsixmanifest** ", und wählen Sie dann **Code anzeigen** aus. Verwenden Sie diesen Code, um den vorhandenen Inhalt in der Datei zu ersetzen.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
      <Metadata>
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />
        <DisplayName>Simple Math</DisplayName>
        <Description>Does basic arithmetic calculations.</Description>
      </Metadata>
      <Installation Scope="Global" AllUsers="true">
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />
      </Installation>
      <Dependencies>
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />
      </Dependencies>
      <Assets>
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
      </Assets>
    </PackageManifest>
    ```

6. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt **simplemathvsix** , und wählen Sie dann   >  **Neues Element** hinzufügen aus.

7. Wählen Sie in der Kategorie **Daten** die Option **XML-Datei**, benennen Sie die Datei `SDKManifest.xml` , und klicken Sie auf die Schaltfläche **Hinzufügen** .

8. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für die **SDKManifest.xml** -Datei, und wählen Sie dann **Öffnen** aus, um die Datei im **XML-Editor** anzuzeigen.

9. Fügen Sie den folgenden Code in die Datei **SDKManifest.xml** ein.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <FileList
      DisplayName="Simple Math"
      MinVSVersion="14.0"
      AppliesTo="JavaScript+WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">

      <!-- JS -->
      <File Content="js\arithmetic.js" />
    </FileList>

    ```

10. Wählen Sie in **Projektmappen-Explorer** im Kontextmenü für die **SDKManifest.xml** -Datei **Eigenschaften** aus.

11. Legen Sie im Fenster **Eigenschaften** die Eigenschaft **in VSIX einschließen** auf **true** fest.

12. Wählen Sie in **Projektmappen-Explorer** im Kontextmenü für das Projekt **simplemathvsix** die Option   >  **neuen Ordner** hinzufügen aus, und benennen Sie den Ordner `Redist` .

13. Fügen Sie unter "Redist" Unterordner hinzu, um diese Ordnerstruktur zu erstellen:

     *\Redist\commonconfiguration\neutral\simplemath\js\\*

14. Wählen Sie im Kontextmenü für den Ordner **"\js \\** die Option   >  **Neues Element** hinzufügen aus.

15. Wählen Sie unter **Visual c#-Elemente** die Kategorie **Web** aus, und wählen Sie dann das **JavaScript-Datei** Element aus. Benennen Sie die Datei `arithmetic.js` , und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

16. Fügen Sie den folgenden Code in *arithmetic.js* ein:

    ```csharp
    (function (global) {
        "use strict";
        global.Arithmetic = {
            add: function (firstNumber, secondNumber) {
                return firstNumber + secondNumber;
            },

            subtract: function (firstNumber, secondNumber) {
                return firstNumber - secondNumber;
            },

            multiply: function (firstNumber, secondNumber) {
                return firstNumber * secondNumber;
            },

            divide: function (firstNumber, secondNumber) {
                return firstNumber / secondNumber;
            }
        };
    })(this);

    ```

17. Wählen Sie in **Projektmappen-Explorer** im Kontextmenü für die **arithmetic.js** -Datei **Eigenschaften** aus. Diese Eigenschafts Änderungen vornehmen:

    - Legen Sie die Eigenschaft **in VSIX einschließen** auf **true** fest.

    - Legen Sie die Eigenschaft **in Ausgabeverzeichnis kopieren** auf **immer kopieren** fest.

18. Wählen Sie in **Projektmappen-Explorer** im Kontextmenü für das Projekt **simplemathvsix** die Option **Erstellen** aus.

19. Nachdem der Buildvorgang erfolgreich abgeschlossen wurde, wählen Sie im Kontextmenü des Projekts **im Datei-Explorer Ordner öffnen** aus. Navigieren Sie zu **\bin\debug \\**, und führen Sie aus, `SimpleMathVSIX.vsix` um es zu installieren.

20. Wählen Sie die Schaltfläche **Installieren** aus, und lassen Sie die Installation fertig.

21. Starten Sie Visual Studio neu.

## <a name="to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a> So erstellen Sie eine Beispiel-APP, die das SDK verwendet

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

2. Wählen Sie in der Liste der Vorlagen Kategorien unter **JavaScript** den Eintrag **Windows Store** aus, und wählen Sie dann die Vorlage **leere App** aus.

3. Geben Sie im Feld **Name den Namen** an `ArithmeticUI` . Klicken Sie auf die Schaltfläche **OK** .

4. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das **arithmeticui** -Projekt, und wählen Sie dann Verweis **Hinzufügen** aus  >  .

5. Wählen Sie unter **Windows** den Wert **Erweiterungen** aus, und beachten Sie, dass **einfache mathematische** Anzeige angezeigt wird.

6. Aktivieren Sie das Kontrollkästchen **einfache Mathematik** , und klicken Sie dann auf die Schaltfläche **OK** .

7. Beachten Sie in **Projektmappen-Explorer** unter **Verweise**, dass die **einfache mathematische** Referenz angezeigt wird. Erweitern Sie die Datei, und beachten Sie, dass es einen **"\js \\** -Ordner gibt, der **arithmetic.js** enthält. Sie können **arithmetic.js** öffnen, um zu bestätigen, dass der Quellcode installiert wurde.

8. Verwenden Sie den folgenden Code, um die Inhalte *default.htm* zu ersetzen.

   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="utf-8" />
       <title>ArithmeticUI</title>

       <!-- WinJS references -->
       <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />
       <script src="//Microsoft.WinJS.1.0/js/base.js"></script>
       <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>

       <!-- ArithmeticUI references -->
       <link href="/css/default.css" rel="stylesheet" />
       <script src="/js/default.js"></script>
       <script src="/SimpleMath/js/arithmetic.js"></script>
   </head>
   <body>
       <form>
       <div id="calculator" class="ms-grid">
           <input name="firstNumber" id="firstNumber" type="number" step="any">
           <div id="operators">
               <button class="operator" type="button">+</button>
               <button class="operator" type="button">-</button>
               <button class="operator" type="button">*</button>
               <button class="operator" type="button">/</button>
           </div>
           <input id="secondNumber" type="number">
           <button class="calculate" type="button">=</button>
           <input id="result" type="number" name="result" disabled="" readonly="">
       </div>
       </form>
   </body>
   </html>
   ```

9. Verwenden Sie den folgenden Code, um die Inhalte *\js\default.js* zu ersetzen.

    ```csharp
    (function () {
        "use strict";

        var app = WinJS.Application;
        var operation = null;

        function calculateResult() {
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),
                result = 0;

            if (isNaN(firstNumber) || isNaN(secondNumber)) {
                result = 0;
            }
            else {
                switch (operation) {
                    case "+":
                        result = Arithmetic.add(firstNumber, secondNumber);
                        break;
                    case "-":
                        result = Arithmetic.subtract(firstNumber, secondNumber);
                        break;
                    case "*":
                        result = Arithmetic.multiply(firstNumber, secondNumber);
                        break;
                    case "/":
                        result = Arithmetic.divide(firstNumber, secondNumber);
                        break;
                    default:
                }
            }
            document.querySelector("#result").value = result.toString();
        }

        app.onactivated = function (args) {
            document.querySelector("#calculator").addEventListener("click", function (event) {
                if (event.target.tagName.toLowerCase() === "button") {
                    switch (event.target.className) {
                        case "operator":
                            operation = event.target.innerText;
                            break;
                        case "calculate":
                            calculateResult();
                            break;
                        default:
                            break;
                    }
                }
            });
        };

        app.start();
    })();
    ```

10. Ersetzen Sie den Inhalt von *\css\default.CSS* durch folgenden Code:

    ```xml
    form {
        display: -ms-grid;
        -ms-grid-rows: 1fr auto 1fr;
        -ms-grid-columns: 1fr auto 1fr;
        height: 100%;
        width: 100%;
    }

    button, input[type=number] {
        margin-right: 5px;
        -ms-grid-row-align: center;
    }

    #calculator {
        -ms-grid-column: 2;
        -ms-grid-row: 2;
        display: -ms-grid;
        -ms-grid-rows: 1fr;
        -ms-grid-columns: auto min-content auto auto auto;
    }

    .ms-grid input {
        width: 5em;
    }

    #firstNumber {
        -ms-grid-column: 1;
        -ms-grid-row-align: center;
    }

    #operators {
        -ms-grid-column: 2;
        -ms-grid-row-align: center;
    }

        #operators button.operator {
            margin-bottom: 5px;
            height: 40px;
        }

    #secondNumber {
        -ms-grid-column: 3;
    }

    button.calculate {
        -ms-grid-column: 4;
        -ms-grid-row-align: center;
        height: 40px;
    }

    #result {
        -ms-grid-column: 5;
    }

    ```

11. Drücken Sie die Taste **F5** , um die APP zu erstellen und auszuführen.

12. Geben Sie in der App-Benutzeroberfläche zwei Zahlen ein, wählen Sie einen Vorgang aus, und wählen Sie dann die **=** Schaltfläche aus. Das richtige Ergebnis wird angezeigt.

## <a name="see-also"></a>Weitere Informationen
- [Erstellen eines Software Development Kits](../extensibility/creating-a-software-development-kit.md)
