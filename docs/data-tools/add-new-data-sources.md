---
title: Hinzufügen neuer Datenquellen
description: Fügen Sie neue Datenquellen in Visual Studio hinzu. Eine Datenquelle ist ein .NET-Objekt, das eine Verbindung mit einem Datenspeicher herstellt und die Daten für eine .NET-Anwendung verfügbar macht.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: how-to
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ec58528bfe5e1687c4b4edc7f86451c08b04652c
ms.sourcegitcommit: 63ff7cb85b3baeeb713240d17bb2a18497f3741d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94518673"
---
# <a name="add-new-data-sources"></a>Hinzufügen neuer Datenquellen

:::moniker range="vs-2019"
> [!NOTE]
> Die in diesem Artikel beschriebenen Funktionen gelten für .NET Framework Windows Forms und die WPF-Entwicklung. In Visual Studio 2019 (und früheren Versionen) werden die Funktionen für die .net Core-Entwicklung nicht sowohl für WPF als auch für Windows Forms unterstützt.
:::moniker-end

Im Kontext von .NET Data Tools in Visual Studio bezieht sich der Begriff *Datenquelle* auf .NET-Objekte, die eine Verbindung mit einem Datenspeicher herstellen und die Daten für eine .NET-Anwendung verfügbar machen. Die Visual Studio-Designer können die Ausgabe der Datenquelle nutzen, um den Code Bausteine zu generieren, mit dem die Daten an Formulare gebunden werden, wenn Sie Datenbankobjekte aus dem **Datenquellen** Fenster ziehen und ablegen. Diese Art von Datenquelle kann Folgendes sein:

- Eine Klasse in einem Entity Framework Modell, das einer Art von Datenbank zugeordnet ist.

- Ein DataSet, das einer Art von Datenbank zugeordnet ist.

- Eine Klasse, die einen Netzwerkdienst (z. b. einen Windows Communication Foundation (WCF)-Datendienst oder einen Rest-Dienst darstellt.

- Eine-Klasse, die einen SharePoint-Dienst darstellt.

- Eine Klasse oder Auflistung in der Projekt Mappe.

> [!NOTE]
> Wenn Sie keine Daten Bindungsfunktionen, Datasets, Entity Framework LINQ to SQL, WCF oder SharePoint verwenden, gilt das Konzept einer "Datenquelle" nicht. Stellen Sie einfach eine direkte Verbindung mit der Datenbank her, indem Sie die SqlCommand-Objekte verwenden und direkt mit der Datenbank kommunizieren.

Sie erstellen und bearbeiten Datenquellen mithilfe des **Assistenten zum Konfigurieren von Daten** Quellen in einer Windows Forms oder Windows Presentation Foundation Anwendung. Erstellen Sie für Entity Framework zuerst die Entitäts Klassen, und starten Sie dann den Assistenten, indem Sie **Projekt**  >  **neue Datenquelle hinzufügen** auswählen (Weitere Informationen finden Sie weiter unten in diesem Artikel).

![Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>Datenquellenfenster

Nachdem Sie eine Datenquelle erstellt haben, wird Sie im Fenster **Datenquellen** Tool angezeigt.

> [!TIP]
> Um das Fenster **Datenquellen** zu öffnen, stellen Sie sicher, dass das Projekt geöffnet ist, und drücken Sie dann **UMSCHALT** + **alt** + **D** , oder wählen Sie **View**  >  **andere Windows** -  >  **Datenquellen** anzeigen aus.

Sie können eine Datenquelle aus dem **Datenquellen** Fenster auf eine Formular Entwurfs Oberfläche oder ein Steuerelement ziehen. Dies bewirkt, dass Code Bausteine generiert werden, in dem die Daten aus dem Datenspeicher angezeigt werden.

Die folgende Abbildung zeigt ein DataSet, das auf einem Windows Form abgelegt wurde. Wenn Sie in der Anwendung **F5** auswählen, werden die Daten aus der zugrunde liegenden Datenbank in den Steuerelementen des Formulars angezeigt.

![Datenquellen-Zieh Vorgang](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>Datenquelle für eine Datenbank oder Datenbankdatei

Sie können ein DataSet oder ein Entity Framework Modell erstellen, das als Datenquelle für eine Datenbank oder Datenbankdatei verwendet werden soll.

### <a name="dataset"></a>Dataset

Um ein DataSet als Datenquelle zu erstellen, führen Sie den **Assistenten zum Konfigurieren von Datenquellen** aus, indem Sie **Projekt**  >  **neue Datenquelle hinzufügen** auswählen. Wählen Sie den Daten Quellentyp **Datenbank** aus, und befolgen Sie die Anweisungen, um entweder eine neue oder eine vorhandene Datenbankverbindung oder eine Datenbankdatei anzugeben.

### <a name="entity-classes"></a>Entitätsklassen

So erstellen Sie ein Entity Framework Modell als Datenquelle:

1. Führen Sie den **Entity Data Model Assistenten** aus, um die Entitäts Klassen zu erstellen. Wählen Sie **Project**  >  **Add New Item**  >  **ADO.NET Entity Data Model** aus.

   ![Neues Entity Framework Modell-Projekt Element](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. Wählen Sie die Methode aus, von der Sie das Modell generieren möchten.

   ![Entity Data Model-Assistent](../data-tools/media/raddata-entity-data-model-wizard.png)

1. Fügen Sie das Modell als Datenquelle hinzu. Die generierten Klassen werden im **Assistenten zum Konfigurieren von Datenquellen** angezeigt, wenn Sie die Kategorie **Objekte** auswählen.

   ![Assistent zum Konfigurieren von Datenquellen mit Entitäts Klassen](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>Datenquelle für einen Dienst

Um eine Datenquelle aus einem Dienst zu erstellen, führen Sie den **Assistenten zum Konfigurieren von Datenquellen** aus, und wählen Sie den Daten Quellentyp **Dienst** aus. Dies ist nur eine Verknüpfung zum Dialogfeld **Dienstverweis hinzufügen** , auf das Sie auch zugreifen können, indem Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt klicken und **Dienst Verweis hinzufügen** auswählen.

Wenn Sie eine Datenquelle mit einem Dienst erstellen, fügt Visual Studio einen Dienstverweis auf das Projekt hinzu. Visual Studio erstellt auch Proxy Objekte, die den vom Dienst zurückgegebenen Objekten entsprechen. Zum Beispiel wird ein Dienst, der ein Dataset zurückgibt, im Projekt als Dataset dargestellt. Ein Dienst, der einen bestimmten Typ zurückgibt, wird in dem Projekt als der zurückgegebene Typ dargestellt.

Sie können eine Datenquelle mit den folgenden Diensttypen erstellen:

- [WCF Data Services](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [WCF-Dienste](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- WEB SERVICES

    > [!NOTE]
    > Die Elemente, die im **Datenquellen** Fenster angezeigt werden, sind abhängig von den Daten, die vom Dienst zurückgegeben werden. Einige Dienste stellen möglicherweise nicht genügend Informationen bereit, damit der **Assistent zum Konfigurieren von Datenquellen** bindbare Objekte erstellen kann. Wenn der Dienst beispielsweise ein nicht typisiertes DataSet zurückgibt, werden beim Beenden des Assistenten keine Elemente im **Datenquellen** Fenster angezeigt. Dies ist darauf zurückzuführen, dass nicht typisierte Datasets kein Schema bereitstellen und der Assistent daher nicht über genügend Informationen zum Erstellen der Datenquelle verfügt.

## <a name="data-source-for-an-object"></a>Datenquelle für ein Objekt

Sie können eine Datenquelle mit jedem Objekt erstellen, das mindestens eine öffentliche Eigenschaft durch Ausführen des **Assistenten zum Konfigurieren von Datenquellen** und anschließendes Auswählen des Datenquellentyps **Objekt** verfügbar macht. Alle öffentlichen Eigenschaften eines Objekts werden im Fenster **Datenquellen** angezeigt. Wenn Sie Entity Framework verwenden und ein Modell generiert haben, finden Sie hier die Entitäts Klassen, die die Datenquellen für Ihre Anwendung sind.

Erweitern Sie auf der Seite **Datenobjekte auswählen** die Knoten in der Strukturansicht, um die Objekte zu suchen, an die Sie binden möchten. Die Strukturansicht enthält Knoten für das Projekt und für Assemblys und andere Projekte, auf die von Ihrem Projekt verwiesen wird.

Wenn Sie an ein Objekt in einer Assembly oder einem Projekt binden möchten, das nicht in der Strukturansicht angezeigt wird, klicken Sie auf **Verweis hinzufügen** , und fügen Sie im **Dialog Feldverweis hinzufügen** einen Verweis auf die Assembly oder das Projekt hinzu. Nachdem Sie den Verweis hinzugefügt haben, wird die Assembly oder das Projekt der Strukturansicht hinzugefügt.

> [!NOTE]
> Möglicherweise müssen Sie das Projekt erstellen, das die Objekte enthält, bevor die Objekte in der Strukturansicht angezeigt werden.

> [!NOTE]
> Um die Datenbindung mittels Drag & Drop zu unterstützen, müssen Objekte, die die- <xref:System.ComponentModel.ITypedList> oder- <xref:System.ComponentModel.IListSource> Schnittstelle implementieren, über einen Standardkonstruktor verfügen. Andernfalls kann Visual Studio das Datenquellen Objekt nicht instanziieren und zeigt einen Fehler an, wenn Sie das Element auf die Entwurfs Oberfläche ziehen.

## <a name="data-source-for-a-sharepoint-list"></a>Datenquelle für eine SharePoint-Liste

Sie können eine Datenquelle aus einer SharePoint-Liste erstellen, indem Sie den **Assistenten zum Konfigurieren von Datenquellen** ausführen und den Datenquellentyp **SharePoint** auswählen. SharePoint macht Daten über WCF Data Services verfügbar. Daher ist das Erstellen einer SharePoint-Datenquelle mit dem Erstellen einer Datenquelle aus einem Dienst identisch. Durch Auswahl des **SharePoint** -Elements im **Assistenten zum Konfigurieren von Datenquellen** wird das Dialogfeld **Dienstverweis hinzufügen** geöffnet, in dem Sie durch Zeigen auf den SharePoint-Server eine Verbindung mit dem SharePoint-Datendienst herstellen. Hierfür ist das SharePoint SDK erforderlich.

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
