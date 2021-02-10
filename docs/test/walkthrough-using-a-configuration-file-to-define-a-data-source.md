---
title: Verwenden einer Konfigurationsdatei zum Definieren einer Datenquelle
description: Erfahren Sie, wie Sie eine in einer app.config-Datei definierte Datenquelle für Komponententests verwenden, beginnend mit dem Erstellen einer app.config-Datei, die eine Datenquelle definiert.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f234d0285f5a0ed01567bb77c21e4c2d080a5f64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967877"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>Exemplarische Vorgehensweise: Verwenden einer Konfigurationsdatei zum Definieren einer Datenquelle

Diese exemplarische Vorgehensweise veranschaulicht, wie eine in der Datei *app.config* definierte Datenquelle für Komponententests verwendet wird. Sie erfahren, wie die Datei *app.config* zum Definieren einer Datenquelle erstellt wird, die von der <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>-Klasse verwendet werden kann. Die folgenden Aufgaben werden in dieser exemplarischen Vorgehensweise vorgestellt:

- Erstellen einer *app.config* Datei

- Definieren eines benutzerdefinierten Konfigurationsabschnitts

- Definieren von Verbindungszeichenfolgen

- Definieren der Datenquellen

- Zugreifen auf die Datenquellen über die <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>-Klasse

## <a name="prerequisites"></a>Voraussetzungen

Um diese exemplarische Vorgehensweise nachzuvollziehen, benötigen Sie Folgendes:

- Visual Studio Enterprise

- Microsoft Access oder Microsoft Excel, um Daten für mindestens eine der Testmethoden bereitzustellen

- Eine Visual Studio 2012-Projektmappe, die ein Testprojekt enthält.

## <a name="add-an-appconfig-file-to-the-project"></a>Hinzufügen einer Datei „app.config“ zum Projekt

1. Wenn für das Testprojekt bereits eine [app.config](#define-a-custom-configuration-section)-Datei vorhanden ist, fahren Sie mit *Definieren eines benutzerdefinierten Konfigurationsabschnitts* fort.

2. Klicken Sie erst mit der rechten Maustaste im **Projektmappen-Explorer** auf das Testprojekt und anschließend mit der Linken auf **Hinzufügen** > **Neues Element**.

     Das Fenster **Neues Element hinzufügen** wird geöffnet.

3. Wählen Sie die Vorlage **Anwendungskonfigurationsdatei** aus, und klicken Sie dann auf **Hinzufügen**.

## <a name="define-a-custom-configuration-section"></a>Definieren eines benutzerdefinierten Konfigurationsabschnitts

Sehen Sie sich die Datei *app.config* an. Sie enthält mindestens die XML-Deklaration und ein Stammelement.

### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>So fügen Sie der Datei „app.config“ den benutzerdefinierten Konfigurationsabschnitt hinzu

1. Das Stammelement von *app.config* sollte das **configuration**-Element sein. Erstellen Sie ein **configSections**-Element innerhalb des **configuration**-Elements. **configSections** sollte das erste Element in der Datei *app.config* sein.

2. Erstellen Sie innerhalb des **configSections**-Elements ein **section**-Element.

3. Fügen Sie im **section**-Element ein Attribut mit dem Namen `name` hinzu, und weisen Sie ihm den Wert `microsoft.visualstudio.testtools` zu. Fügen Sie ein weiteres Attribut mit dem Namen `type` hinzu, und weisen Sie ihm den Wert `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions` zu.

Das **section**-Element sollte wie folgt aussehen:

```xml
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions" />
```

> [!NOTE]
> Der Name der Assembly muss der von Ihnen verwendeten Version entsprechen.

## <a name="define-connection-strings"></a>Definieren von Verbindungszeichenfolgen

Die Verbindungszeichenfolgen definieren anbieterspezifische Informationen für den Zugriff auf Datenquellen. In Konfigurationsdateien definierte Verbindungszeichenfolgen enthalten wiederverwendbare Datenanbieterinformationen für eine Anwendung. In diesem Abschnitt erstellen Sie zwei Verbindungszeichenfolgen, die von den im Abschnitt „Benutzerdefinierte Konfiguration“ definierten Datenquellen verwendet werden.

### <a name="to-define-connection-strings"></a>So definieren Sie Verbindungszeichenfolgen

1. Erstellen Sie nach dem **configSections**-Element ein **connectionStrings**-Element.

2. Erstellen Sie innerhalb des **connectionStrings**-Elements zwei **Hinzufügen**-Elemente.

3. Erstellen Sie im ersten **Hinzufügen**-Element die folgenden Attribute und Werte für eine Verbindung mit einer Microsoft Access-Datenbank:

|attribute|Werte|
|-|------------|
|`name`|`"MyJetConn"`|
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|
|`providerName`|`"System.Data.OleDb"`|

Erstellen Sie im zweiten **Hinzufügen**-Element die folgenden Attribute und Werte für eine Verbindung mit einem Microsoft Excel-Arbeitsblatt:

|attribute|Werte|
|-|-|
|`name`|`"MyExcelConn"`|
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5"`|
|`providerName`|`"System.Data.Odbc"`|

Das **connectionStrings**-Element sollte in etwa wie folgt aussehen:

```xml
<connectionStrings>
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
</connectionStrings>
```

## <a name="define-data-sources"></a>Definieren von Datenquellen

Der Abschnitt „Datenquellen“ enthält vier Attribute, die von der Test-Engine zum Abrufen von Daten aus einer Datenquelle verwendet werden.

- `name` definiert die von <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> verwendete Identität, um die zu verwendende Datenquelle anzugeben.

- `connectionString` bezeichnet die im vorhergehenden Abschnitt „Definieren von Verbindungszeichenfolgen“ erstellte Verbindungszeichenfolge.

- `dataTableName` definiert die Tabelle oder das Blatt mit den im Test zu verwendenden Daten.

- `dataAccessMethod` definiert die Technik für den Zugriff auf Datenwerte in der Datenquelle.

In diesem Abschnitt definieren Sie zwei Datenquellen für die Verwendung in einem Komponententest.

### <a name="to-define-data-sources"></a>So definieren Sie Datenquellen

1. Erstellen Sie nach dem **connectionStrings**-Element ein **microsoft.visualstudio.testtools**-Element. Dieser Abschnitt wurde im Abschnitt „Definieren eines benutzerdefinierten Konfigurationabschnitts“ erstellt.

2. Erstellen Sie innerhalb des **microsoft.visualstudio.testtools**-Elements ein **dataSources**-Element.

3. Erstellen Sie innerhalb des **dataSources**-Elements zwei **Hinzufügen**-Elemente.

4. Erstellen Sie im ersten **Hinzufügen**-Element die folgenden Attribute und Werte für eine Microsoft Access-Datenquelle:

|attribute|Werte|
|-|------------|
|`name`|`"MyJetDataSource"`|
|`connectionString`|`"MyJetConn"`|
|`dataTableName`|`"MyDataTable"`|
|`dataAccessMethod`|`"Sequential"`|

Erstellen Sie im zweiten **Hinzufügen**-Element die folgenden Attribute und Werte für eine Microsoft Excel-Datenquelle:

|attribute|Werte|
|-|-|
|`Name`|`"MyExcelDataSource"`|
|`connectionString`|`"MyExcelConn"`|
|`dataTableName`|`"Sheet1$"`|
|`dataAccessMethod`|`"Sequential"`|

Das **microsoft.visualstudio.testtools**-Element sollte in etwa wie folgt aussehen:

```xml
<microsoft.visualstudio.testtools>
    <dataSources>
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
    </dataSources>
</microsoft.visualstudio.testtools>
```

Die endgültige Datei *app.config* sollte in etwa wie folgt aussehen:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <configSections>
        <section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions" />
    </configSections>
    <connectionStrings>
        <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
        <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
    </connectionStrings>
    <microsoft.visualstudio.testtools>
        <dataSources>
            <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
            <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
        </dataSources>
    </microsoft.visualstudio.testtools>
</configuration>
```

## <a name="create-a-unit-test-that-uses-data-sources-defined-in-appconfig"></a>Erstellen eines Komponententests mit in der Datei „app.config“ definierten Datenquellen

Nachdem die Datei *app.config* definiert ist, erstellen Sie einen Komponententest, für den Daten aus den in der Datei *app.config* definierten Datenquellen verwendet werden. In diesem Abschnitt wird Folgendes beschrieben:

- Erstellen Sie die in der Datei *app.config* angegebenen Datenquellen.

- Verwenden der Datenquellen in zwei Testmethoden, bei denen die Werte der beiden Datenquellen verglichen werden

### <a name="to-create-a-microsoft-access-data-source"></a>So erstellen Sie eine Microsoft Access-Datenquelle

1. Erstellen Sie eine Microsoft Access-Datenbank mit dem Namen *testdatasource.accdb*.

2. Erstellen Sie eine Tabelle, und nennen Sie sie `MyDataTable` in *testdatasource.accdb*.

3. Erstellen Sie in `MyDataTable` zwei Felder mit dem Namen `Arg1` und `Arg2` mit dem Datentyp `Number`.

4. Fügen Sie `MyDataTable` fünf Entitäten mit den folgenden Werten für `Arg1` und `Arg2`: (10,50), (3,2), (6,0), (0,8) bzw. (12312,1000).

5. Speichern und schließen Sie die Datenbank.

6. Ändern Sie die Verbindungszeichenfolge, um auf den Speicherort der Datenbank zu verweisen. Ändern Sie den Wert von `Data Source`, um den Speicherort der Datenbank anzugeben.

### <a name="to-create-a-microsoft-excel-data-source"></a>So erstellen Sie eine Microsoft Excel-Datenquelle

1. Erstellen Sie ein Microsoft Excel-Arbeitsblatt mit dem Namen *data.xlsx*.

2. Erstellen Sie ein Arbeitsblatt mit dem Namen `Sheet1`, falls dieses noch nicht in *data.xlsx* vorhanden ist.

3. Erstellen Sie die zwei Spaltenüberschriften `Val1` und `Val2` in `Sheet1`.

4. Fügen Sie `Sheet1` fünf Entitäten mit folgenden Werten für `Val1` und `Val2` hinzu: (1,1), (2,2), (3,3), (4,4) bzw. (5,0).

5. Speichern und schließen Sie das Arbeitsblatt.

6. Ändern Sie die Verbindungszeichenfolge, um auf den Speicherort des Arbeitsblattes zu verweisen. Ändern Sie den Wert von `dbq`, um den Speicherort des Arbeitsblattes anzugeben.

### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>So erstellen Sie einen Komponententest mit in der Datei „app.config“ definierten Datenquellen

1. Fügen Sie dem Testprojekt einen Komponententest hinzu.

2. Ersetzen Sie den automatisch generierten Inhalt des Komponententests durch folgenden Code:

    ```csharp
    using System;
    using Microsoft.VisualStudio.TestTools.UnitTesting;

    namespace TestProject1
    {
         [TestClass]
        public class UnitTest1
        {
            private TestContext context;

            public TestContext TestContext
            {
                get { return context; }
                set { context = value; }
            }

            [TestMethod()]
            [DeploymentItem("MyTestProject\\testdatasource.accdb")]
            [DataSource("MyJetDataSource")]
            public void MyTestMethod()
            {
                int a = Int32.Parse(context.DataRow["Arg1"].ToString());
                int b = Int32.Parse(context.DataRow["Arg2"].ToString());
                Assert.AreNotEqual(a, b, "A value was equal.");
            }

            [TestMethod()]
            [DeploymentItem("MyTestProject\\data.xlsx")]
            [DataSource("MyExcelDataSource")]
            public void MyTestMethod2()
            {
                Assert.AreEqual(context.DataRow["Val1"], context.DataRow["Val2"]);
            }
        }
    }
    ```

3. Sehen Sie sich die DataSource-Attribute an. Beachten Sie die Einstellungsnamen aus der *app.config*-Datei.

4. Erstellen Sie die Projektmappe, und führen Sie die Tests „MyTestMethod“ und „MyTestMethod2“ aus.

> [!IMPORTANT]
> Stellen Sie Elemente wie Datenquellen bereit, damit sie für den Test im Bereitstellungsverzeichnis zugänglich sind.

## <a name="see-also"></a>Siehe auch

- [Ausführen von Komponententests für Code](../test/unit-test-your-code.md)
- [Vorgehensweise: Erstellen eines datengesteuerten Komponententests](../test/how-to-create-a-data-driven-unit-test.md)
