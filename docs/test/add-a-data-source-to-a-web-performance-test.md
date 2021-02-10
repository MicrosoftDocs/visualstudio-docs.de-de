---
title: Hinzufügen einer Datenquelle für einen Webleistungstest
description: Lernen Sie, Daten zu binden, um dem gleichen Test verschiedene Werte bereitzustellen, z. B. um den Formularbereitstellungsparametern verschiedene Werte bereitzustellen.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, data binding (database)
ms.assetid: 2ada376d-f168-455d-9643-6acb535360c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: fc7367db64f096ce5a90e9b51a8f5df162779f36
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971218"
---
# <a name="add-a-data-source-to-a-web-performance-test"></a>Hinzufügen einer Datenquelle für einen Webleistungstest

Binden Sie Daten, um dem gleichen Test verschiedene Werte bereitzustellen, z. B. um den Formularbereitstellungsparametern verschiedene Werte bereitzustellen.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

![Datenbindung an einen Webleistungstest](../test/media/web_test_databinding_conceptual.png)

Es wird eine ASP.NET-Beispielanwendung verwendet. Sie hat drei *ASPX-Seiten*: die Standardseite, die Seite „Red“ und die Seite „Blue“. Die Standardseite enthält ein Optionsfeld für die Auswahl von "Red" oder "Blue" sowie eine Schaltfläche zum Senden. Die anderen beiden *ASPX-Seiten* sind sehr einfach. Eine hat die Bezeichnung "Red" und die andere die Bezeichnung "Blue". Wenn Sie auf der Standardseite "Senden" auswählen, wird eine der beiden anderen Seiten angezeigt. Sie können das Beispiel [ColorWebApp](https://code.msdn.microsoft.com/Sample-ColorWebApp-76ff7506) herunterladen oder einfach mit Ihrer eigenen Web-App fortfahren.

![Ausführen der zu testenden Webanwendung](../test/media/web_test_databinding_runwebapp.png)

Die Projektmappe sollte auch einen Webleistungstest enthalten, der die Seiten der Webanwendung durchsucht.

![Projektmappe mit Webleistungstest](../test/media/web_test_databinding_solution.png)

## <a name="create-a-sql-database"></a>Erstellen einer SQL-Datenbank

::: moniker range="vs-2017"

1. Wenn Sie nicht über Visual Studio Enterprise verfügen, können Sie das Programm über die Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) herunterladen.

2. Erstellt eine SQL-Datenbank.

     ![Eine neue SQL-Datenbank hinzufügen](../test/media/web_test_databinding_sql_addnewdb.png)

3. Erstellen Sie ein Datenbankprojekt.

     ![Neues Projekt aus Datenbank erstellen](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Fügen Sie der Datenbank eine Tabelle hinzu.

     ![Eine neue Tabelle zum Datenbankprojekt hinzufügen](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Fügen Sie der Tabelle Felder hinzu.

     ![Felder zur Tabelle hinzufügen](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Veröffentlichen Sie das Datenbankprojekt.

     ![Datenbankprojekt über den Projektmappen-Explorer veröffentlichen](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Fügen Sie den Feldern Daten hinzu.

     ![Daten zu den Feldern hinzufügen](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

::: moniker range="vs-2019"

1. Wenn Sie nicht über Visual Studio Enterprise verfügen, können Sie das Programm über die Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads) herunterladen.

2. Erstellt eine SQL-Datenbank.

     ![Eine neue SQL-Datenbank hinzufügen](../test/media/web_test_databinding_sql_addnewdb.png)

3. Erstellen Sie ein Datenbankprojekt.

     ![Neues Projekt aus Datenbank erstellen](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Fügen Sie der Datenbank eine Tabelle hinzu.

     ![Eine neue Tabelle zum Datenbankprojekt hinzufügen](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Fügen Sie der Tabelle Felder hinzu.

     ![Felder zur Tabelle hinzufügen](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Veröffentlichen Sie das Datenbankprojekt.

     ![Datenbankprojekt über den Projektmappen-Explorer veröffentlichen](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Fügen Sie den Feldern Daten hinzu.

     ![Daten zu den Feldern hinzufügen](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

## <a name="add-the-data-source"></a>Hinzufügen der Datenquelle

1. Fügen Sie eine Datenquelle hinzu.

     ![Datenquelle zum Webleistungstest hinzufügen](../test/media/web_test_databinding_sql_adddatasource.png)

2. Wählen Sie den Typ der Datenquelle aus, und geben Sie ihr einen Namen.

     ![Namen für die Datenbankquelle angeben](../test/media/web_test_databinding_sql_adddatasourcedialog.png)

3. Erstellen Sie eine Verbindung.

     ![Wählen Sie "Neue Verbindung" aus](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

     Geben Sie die Verbindungsdetails ein.

     ![Eigenschaften der SQL-Datenbankverbindung eingeben](../test/media/web_test_databinding_sql_adddatasourcedialogconnection.png)

4. Wählen Sie die Tabelle aus, die Sie für den Test verwenden möchten.

     ![Tabelle "Color" als Datenquelle hinzufügen](../test/media/web_test_databinding_sql_adddatasourcedialogaddtable.png)

     Die Tabelle wird an den Test gebunden.

     ![Der Knoten "Datenquellen" wird zum Webleistungstest hinzugefügt](../test/media/web_test_databinding_requestnodeadded_mdb.png)

5. Speichern Sie den Test.

## <a name="bind-the-data"></a>Binden der Daten

1. Binden Sie das **ColorName**-Feld.

     ![ColorName-Feld an RadioButtonList1-Wert binden](../test/media/web_test_databinding_sql_binddatasource.png)

2. Öffnen Sie die Datei *Local.testsettings* im **Projektmappen-Explorer**, und wählen Sie die Option **Ein Testlauf pro Datenquellenzeile** aus.

     ![Bearbeiten Sie die Testeinstellungsdatei.](../test/media/web_test_databinding_sql_testsettings.png)

3. Speichern Sie den Webleistungstest.

## <a name="run-the-test-with-the-data"></a>Ausführen des Tests mit Daten

1. Führen Sie den Test aus.

     ![Webleistungstest ausführen, um Bindung zu überprüfen](../test/media/web_test_databinding_sql_runtest.png)

     Die zwei Testläufe werden für jede Datenzeile angezeigt. Testlauf 1 sendet eine Anforderung für die Seite *Red.aspx*, und Testlauf 2 sendet eine Anforderung für die Seite *Blue.aspx*.

     ![Ergebnisse des Testlaufs](../test/media/web_test_databinding_sql_runresults.png)

     Wenn Sie eine Bindung an eine Datenquelle durchführen, können Sie gegen die Standardregel "Antwort-URL" verstoßen. In diesem Fall wird der Fehler in Testlauf 2 von der Regel ausgelöst, die die Seite *Red.aspx* der ursprünglichen Testaufzeichnung erwartet. Aufgrund der Datenbindung wird sie aber zur Seite *Blue.aspx* geleitet.

2. Korrigieren Sie den Validierungsfehler, indem Sie die Validierungsregel **Antwort-URL** löschen und den Test erneut ausführen.

     ![Validierungsregel für die Antwort-URL löschen](../test/media/web_test_databinding_sql_deleteresponseurl.png)

     Der Webleistungstest ist jetzt mit Datenbindung erfolgreich.

     ![Mithilfe der Datenbindung ist der Test erfolgreich](../test/media/web_test_databinding_sql_deleteresponseurlrunresults.png)

## <a name="q--a"></a>Fragen und Antworten

### <a name="q-what-databases-can-i-use-as-a-data-source"></a>F: Welche Datenbanken kann ich als Datenquelle verwenden?

**A:** Es stehen Ihnen folgende Möglichkeiten zur Verfügung:

- Microsoft SQL Azure.

- Jede Version von Microsoft SQL Server 2005 oder höher.

- Microsoft SQL Server-Datenbankdatei (einschließlich SQL Express).

- Microsoft ODBC.

- Microsoft Access-Datei, die den .NET Framework-Anbieter für OLE DB verwendet.

- Oracle 7.3, 8i, 9i oder 10g.

### <a name="q-how-do-i-use-a-comma-separated-value-csv-text-file-as-a-data-source"></a>F: Wie verwende ich eine CSV-Textdatei (Comma Separated Value) als Datenquelle?

**A:** Gehen Sie folgendermaßen vor:

1. Erstellen Sie einen Ordner zur Organisation der Projektdatenbankartefakte, und fügen Sie ein Element hinzu.

     ![Neues Element zum Datenordner hinzufügen](../test/media/web_test_databinding_foldernewitem.png)

2. Erstellen einer Textdatei

     ![Nennen Sie die neue Textdatei "ColorData.csv"](../test/media/web_test_databinding_foldernewitemtextfile.png)

3. Bearbeiten Sie die Textdatei, und fügen Sie folgenden Text hinzu:

    ```text
    ColorId, ColorName
    0,Red
    1,Blue
    ```

4. Befolgen Sie die Schritte unter [Hinzufügen der Datenquelle](#add-the-data-source), wählen Sie jedoch „CSV-Datei“ als Datenquelle aus.

     ![Namen eingeben und CSV-Datei auswählen](../test/media/web_test_databinding_adddatasourcedialog.png)

### <a name="q-what-if-my-existing-csv-file-does-not-contain-column-headers"></a>F: Was muss ich tun, wenn die vorhandene CSV-Datei keine Spaltenüberschriften enthält?

**A:** Wenn Sie keine Spaltenüberschriften hinzufügen können, können Sie eine Schemabeschreibungsdatei verwenden und die CSV-Datei wie eine Datenbank behandeln.

1. Fügen Sie eine neue Textdatei namens *schema.ini* hinzu.

     ![Eine schema.ini-Datei hinzufügen](../test/media/web_test_databinding_schemafile.png)

2. Bearbeiten Sie die Datei *schema.ini*, um die Informationen hinzuzufügen, mit denen die Struktur der Daten beschrieben wird. Eine Schemadatei, die die CSV-Datei beschreibt, kann folgendermaßen aussehen:

    ```text
    [testdata.csv]
    ColNameHeader=False
    ```

3. Fügen Sie dem Test eine Datenquelle hinzu.

     ![Datenquelle zum Webleistungstest hinzufügen](../test/media/web_test_databinding_sql_adddatasource.png)

4. Wenn Sie die Datei *schema.ini* verwenden, wählen Sie **Datenbank** (nicht die CSV-Datei) als Datenquelle aus, und geben Sie ihr einen Namen.

     ![Datenbankdatenquelle hinzufügen](../test/media/web_test_databinding_adddatasourcecolortext.png)

5. Erstellen Sie eine neue Verbindung.

     ![Wählen Sie "Neue Verbindung" aus](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

6. Wählen Sie den .NET Framework-Datenanbieter für OLE DB aus.

     ![.NET Framework-Datenanbieter für OLE DB auswählen](../test/media/web_test_databinding_adddatasourcecolortext2.png)

7. Wählen Sie **Erweitert** aus.

     !["Erweitert" auswählen](../test/media/web_test_databinding_advanced.png)

8. Wählen Sie für die Eigenschaft „Anbieter“ die Option „Microsoft.Jet.OLEDB.4.0“ aus, und legen Sie anschließend **Erweiterte Eigenschaften** auf „Text; HDR=NO“ fest.

     ![Erweiterte Eigenschaften anwenden](../test/media/web_test_databinding_advancedproperties.png)

9. Geben Sie den Namen des Ordners ein, der die Schemadatei enthält, und testen Sie die Verbindung.

     ![Pfad zum Datenordner eingeben](../test/media/web_test_databinding_adddatasourcecolortext5.png)

10. Wählen Sie die CSV-Datei aus, die Sie verwenden möchten.

     ![Textdatei auswählen](../test/media/web_test_databinding_adddatasourcecolortext6.png)

     Wenn Sie damit fertig sind, wird die CSV-Datei als Tabelle angezeigt.

     ![Zum Test hinzugefügte Datenquelle](../test/media/web_test_databinding_adddatasourcecolortext7.png)

### <a name="q-how-do-i-use-an-xml-file-as-a-data-source"></a>F: Wie verwende ich eine XML-Datei als Datenquelle?

**A:** Ja.

1. Erstellen Sie einen Ordner zur Organisation der Projektdatenbankartefakte, und fügen Sie ein Element hinzu.

     ![Neues Element zum Datenordner hinzufügen](../test/media/web_test_databinding_foldernewitem.png)

2. Erstellen Sie eine XML-Datei.

     ![ColorData.xml-Datei hinzufügen](../test/media/web_test_databinding_additemxmlfile.png)

3. Bearbeiten Sie die XML-Datei, und fügen Sie die Daten hinzu:

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <ColorData>
        <Color>
            <ColorId>0</ColorId>
            <ColorName>Red</ColorName>
        </Color>
        <Color>
            <ColorId>1</ColorId>
            <ColorName>Blue</ColorName>
        </Color>
    </ColorData>
    ```

4. Befolgen Sie die Schritte unter [Hinzufügen der Datenquelle](#add-the-data-source), wählen Sie jedoch „XML-Datei“ als Datenquelle aus.

     ![Namen eingeben und XML-Datei auswählen](../test/media/web_test_databinding_adddatasourcedialogxml.png)

### <a name="q-can-i-add-data-binding-to-a-web-service-request-that-uses-soap"></a>F: Kann ich einer Webdienstanforderung, die SOAP verwendet, eine Datenbindung hinzufügen?

**A:** Ja; Sie müssen den SOAP-XML-Code manuell ändern.

1. Wählen Sie in der Anforderungsstruktur die Webdienstanforderung und im Fenster "Eigenschaften" die Auslassungszeichen (...) in der Eigenschaft "Zeichenfolgentext".

     ![Zeichenfolgentext des Webdiensts bearbeiten](../test/media/web_test_databinding_webservicerequest.png)

2. Ersetzen Sie die Werte im SOAP-Text durch datengebundene Werte, und verwenden Sie dabei folgende Syntax:

    ```xml
    {{DataSourceName.TableName.ColumnName}}
    ```

    Wenn Ihr Code beispielsweise folgendermaßen lautet:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>string</userName> <password>string</password> <orderID>int</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

    Können Sie in Folgenden ändern:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>{{DataSourceName.Users.Name}}</userName> <password>{{DataSourceName.Users.Password}}</password> <orderID>{{DataSourceName.Orders.OrderID}}</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

3. Speichern Sie den Test.
