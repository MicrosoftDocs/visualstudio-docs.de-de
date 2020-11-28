---
title: Erstellen eines Webdiensttests
description: Lernen Sie, einen Leistungstest für Webdienste zu verwenden und Anforderungen im Webleistungstest-Editor anzupassen, um Webdienstseiten zu suchen.
ms.custom: SEO-VS-2020
ms.date: 06/30/2020
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 32b5a6a91221e8942faeefcb89cfc52dd0cc5895
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95439926"
---
# <a name="how-to-create-a-web-service-test"></a>Vorgehensweise: Erstellen eines Webdiensttests

Sie können Webleistungstests verwenden, um Webdienste zu testen. Sie können im **Webleistungstest-Editor** mithilfe der Optionen **Anforderung einfügen** und **Webdienstanforderung einfügen** einzelne Anforderungen anpassen, um Webdienstseiten zu suchen. Im Allgemeinen werden diese Seiten nicht in der Webanwendung angezeigt. Deshalb müssen Sie die Anforderung anpassen, um Zugriff auf diese Seiten zu erhalten.

>[!NOTE]
> Die Funktionalität der Webleistung und der Auslastungstests ist in Visual Studio 2019 veraltet. Bei Application Insights sind mehrstufige Webtests von Visual Studio-Webtestdateien abhängig. Es wurde [angekündigt](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/), dass Visual Studio 2019 die letzte Version mit Webtestfunktionen sein wird. Es ist wichtig zu verstehen, dass zwar keine neuen Features hinzugefügt werden, aber Webtestfunktionen in Visual Studio 2019 derzeit noch und auch während des Supportlebenszyklus des Produkts weiterhin unterstützt werden. Das Azure Monitor-Produktteam hat Fragen zur Zukunft von mehrstufigen Verfügbarkeitstests [hier](https://github.com/MicrosoftDocs/azure-docs/issues/26050#issuecomment-468814101) behandelt.

**Anforderungen**

Visual Studio Enterprise

## <a name="to-create-a-simple-web-service"></a>Erstellen eines einfachen Webdiensts

Zum Testen können Sie Ihren eigenen Webdienst oder die in Visual Studio enthaltene Basisvorlage Web Service (ASMX) (Webdienst (ASMX)) verwenden. So erstellen Sie einen einfachen Webdienst mithilfe dieser Vorlage:

1. Erstellen Sie in Visual Studio ein neues Projekt mithilfe der Vorlage für eine ASP.NET-Webanwendung (.NET Framework), und wählen Sie die Vorlage **Empty** (Leer) aus, wenn Sie dazu aufgefordert werden. Geben Sie einen Namen ein, und erstellen Sie das Projekt.

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektknoten und dann auf **Hinzufügen** > **Neues Element**. Klicken Sie anschließend auf **Web Service (ASMX)** (Webdienst (ASMX)). Fügen Sie den Webdienst hinzu.

1. Öffnen Sie *WebService1.asmx*, und ersetzen Sie die Standardwebmethode `HelloWorld` durch den folgenden Code.

   ```csharp
   public string HelloWorld(string str)
   {
      return "Hello, " + str;
   }
   ```

## <a name="install-the-load-testing-component"></a>Installieren der Auslastungstestkomponente

Wenn Sie noch keine Komponente für Tools für Webleistung und Auslastungstests installiert haben, müssen Sie diese über den Visual Studio-Installer installieren.

1. Öffnen Sie den **Visual Studio-Installer** über das Windows-**Startmenü**. Sie können auch in Visual Studio über das Dialogfeld „Neues Projekt“ oder durch Klicken auf **Extras** > **Tools und Features abrufen** in der Menüleiste auf den Installer zugreifen.

1. Klicken Sie im **Visual Studio-Installer** auf die Registerkarte **Einzelne Komponenten**, und scrollen Sie nach unten zum Abschnitt **Debuggen und Testen**. Wählen Sie **Tools für Webleistung und Auslastungstests** aus.

   ![Die Komponente „Tools für Webleistung und Auslastungstests“](media/web-perf-load-testing-tools-component.png)

1. Klicken Sie auf die Schaltfläche **Ändern**.

   Die Komponente „Tools für Webleistung und Auslastungstests“ wird installiert.

## <a name="create-a-web-test-project"></a>Erstellen eines Webtestprojekts

Für einen Webtest benötigen Sie die Projektvorlage „Testprojekt für Webleistung und Auslastung“. In diesem Abschnitt wird das Erstellen eines Auslastungstestprojekts in C# erläutert. Wenn Ihnen das lieber ist, können Sie Ihr Auslastungstestprojekt auch in Visual Basic erstellen.

::: moniker range="vs-2017"

1. Öffnen Sie Visual Studio.

   Wenn Sie die Beispielvorlage „Web Service (ASMX)“ (Webdienst (ASMX)) verwenden, können Sie das Webtestprojekt derselben Projektmappe hinzufügen.

2. Wählen Sie auf der Menüleiste **Datei** > **Neu** > **Projekt** aus.

   Das Dialogfeld **Neues Projekt** wird angezeigt.

3. Erweitern Sie im Dialogfeld **Neues Projekt** die Option **Installiert** und dann die Option **Visual C#** , wählen Sie dann die Kategorie **Test** aus. Wählen Sie die Vorlage **Testprojekt für Webleistung und Auslastung** aus.

   ![Vorlage „Testprojekt für Webleistung und Auslastung“](media/web-perf-load-test-project-template.png)

4. Benennen Sie das Projekt, wenn Sie den Standardnamen nicht verwenden möchten, und klicken Sie dann auf **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Öffnen Sie Visual Studio.

   Wenn Sie die Beispielvorlage „Web Service (ASMX)“ (Webdienst (ASMX)) verwenden, können Sie das Webtestprojekt derselben Projektmappe hinzufügen.

2. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

3. Geben Sie auf der Seite **Neues Projekts erstellen** in das Suchfeld **Webtest** ein, und wählen Sie dann die Vorlage **Testprojekt für Webleistung und Auslastung \[veraltet]** für C#. Wählen Sie **Weiter** aus.

4. Benennen Sie das Projekt, wenn Sie den Standardnamen nicht verwenden möchten, und wählen Sie **OK**.

::: moniker-end

   Visual Studio erstellt das Projekt und zeigt die Dateien im **Projektmappen-Explorer** an. Das Projekt enthält zu Beginn nur eine Webtestdatei namens *WebTest1.webtest*.

## <a name="to-test-a-web-service"></a>So testen Sie einen Webdienst

1. Starten Sie den Webdienst, und klicken Sie bei Bedarf auf **Stopp**, um den Dienst anzuhalten.

1. Öffnen Sie im Webtestprojekt *WebTest1.webtest*, wodurch der Webleistungstest-Editor geöffnet wird. Klicken Sie im Test-Editor mit der rechten Maustaste auf den Webleistungstest und dann auf **Webdienstanforderung hinzufügen**.

1. Geben Sie als **URL**-Eigenschaft der neuen Anforderung den Namen des Webdiensts ein, z.B. **https://localhost:44318/WebService1.asmx** .

1. Öffnen Sie für den Webdienst ein neues Browserfenster, und geben Sie in der **Adressensymbolleiste** die URL der *ASMX*-Seite ein. Wählen Sie oben auf der Webseite die zu testende Methode aus, und überprüfen Sie die SOAP-Nachricht (Im Beispielwebdienst lautet die Methode „HelloWorld“). Wenn Sie die Methode öffnen, erkennen Sie, dass diese ein `SOAPAction`-Element enthält.

1. Klicken Sie im **Webleistungstest-Editor** mit der rechten Maustaste auf die Anforderung, und wählen Sie **Header hinzufügen** aus, um einen neuen Header hinzuzufügen. Geben Sie `SOAPAction` in der **Name**-Eigenschaft ein. Geben Sie für die Eigenschaft **Wert** den in `SOAPAction` angezeigten Wert ein, z. B. *http://tempuri.org/HelloWorld* .

1. Erweitern Sie den URL-Knoten im Test-Editor, wählen Sie den Knoten **Zeichenfolgentext** aus, und geben Sie für die Eigenschaft **Inhaltstyp** den Wert `text/xml` ein.

1. Kehren Sie zum Browser aus Schritt 4 zurück. Wählen Sie die XML-Komponente der SOAP-Anforderung aus der Webdienst-Beschreibungsseite aus, und kopieren Sie diese in die Zwischenablage.

   Der XML-Inhalt ähnelt dem folgenden Beispiel:

     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
       <soap:Body>
         <HelloWorld xmlns="http://tempuri.org/">
           <str>string</str>
         </HelloWorld>
       </soap:Body>
     </soap:Envelope>
     ```

1. Kehren Sie zum Webleistungstest-Editor zurück, und klicken Sie für die **Zeichenfolgentext**-Eigenschaft auf die Auslassungspunkte **(…)** . Fügen Sie den Inhalt der Zwischenablage in die Eigenschaft ein.

1. Ersetzen Sie alle Platzhalterwerte im XML-Code durch gültige Werte, damit der Test erfolgreich ausgeführt werden kann. Im vorherigen Beispiel würden Sie die Instanz von `string` durch einen Namen ersetzen.

1. Klicken Sie mit der rechten Maustaste auf die Webdienstanforderung, und wählen Sie die Option **QueryString-Parameter für URL hinzufügen** aus.

1. Weisen Sie dem Abfragezeichenfolgen-Parameter einen Namen und einen Wert zu. Im vorherigen Beispiel ist der Name `op` und der Wert `HelloWorld`. Dies identifiziert den auszuführenden Webdienstvorgang.

    > [!NOTE]
    > Sie können Datenbindung im SOAP-Text verwenden, um mithilfe der `{{DataSourceName.TableName.ColumnName}}`-Syntax alle Platzhalterwerte durch datengebundene Werte zu ersetzen.

1. Führen Sie den Test aus. Wählen Sie im oberen Bereich des **Webleistungstest-Ergebnisviewers** die Webdienstanforderung aus. Klicken Sie im unteren Bereich auf die Registerkarte **Webbrowser**. Die vom Webdienst zurückgegebenen XML-Daten sowie die Ergebnisse von möglicherweise ausgeführten Vorgängen werden angezeigt.

   Suchen Sie nach den Ergebnissen für Ihre Webdienstanforderung.

## <a name="see-also"></a>Siehe auch

- [Erstellen von benutzerdefiniertem Code und benutzerdefinierten Plug-Ins für Auslastungstests](../test/create-custom-code-and-plug-ins-for-load-tests.md)
