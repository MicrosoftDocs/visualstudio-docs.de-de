---
title: Anzeigen zugehöriger Daten in WPF-Anwendungen
description: Zeigen Sie verwandte Daten in WPF-Anwendungen an. Arbeiten Sie mit Daten aus mehreren Tabellen oder Entitäten, die in einer über-/Unterordnungsbeziehung miteinander verknüpft sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 3467b2a3c4f49b22ab36b44ff0d3ea47d143e971
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866956"
---
# <a name="display-related-data-in-wpf-applications"></a>Anzeigen zugehöriger Daten in WPF-Anwendungen

In einigen Anwendungen können Sie mit Daten arbeiten, die aus mehreren Tabellen oder Entitäten stammen, die in einer über-/Unterordnungsbeziehung miteinander verknüpft sind. Beispielsweise können Sie ein Raster anzeigen, in dem Kunden aus einer Tabelle angezeigt werden `Customers` . Wenn der Benutzer einen bestimmten Kunden auswählt, werden in einem anderen Raster die Bestellungen für diesen Kunden aus einer verknüpften `Orders` Tabelle angezeigt.

Sie können Daten gebundene Steuerelemente erstellen, die verwandte Daten anzeigen, indem Sie Elemente aus dem **Datenquellen** Fenster in den WPF-Designer ziehen.

## <a name="to-create-controls-that-display-related-records"></a>So erstellen Sie Steuerelemente, die verknüpfte Datensätze anzeigen

1. Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**, um das Fenster **Datenquellen** zu öffnen.

2. Klicken Sie auf **Neue Datenquelle hinzufügen**, und führen Sie den **Assistenten zum Konfigurieren von Datenquellen** aus.

3. Öffnen Sie den WPF-Designer, und stellen Sie sicher, dass der Designer einen Container enthält, bei dem es sich um ein gültiges Ablage Ziel für die Elemente im **Datenquellen** Fenster handelt.

     Weitere Informationen zu gültigen Drop-Zielen finden [Sie unterbinden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

4. Erweitern Sie im Fenster **Datenquellen** den Knoten, der die übergeordnete Tabelle oder das übergeordnete Objekt in der Beziehung darstellt. Die übergeordnete Tabelle oder das übergeordnete Objekt befindet sich auf der 1-Seite einer 1: n-Beziehung.

5. Ziehen Sie den übergeordneten Knoten (oder einzelne Elemente im übergeordneten Knoten) aus dem **Datenquellen** Fenster auf ein gültiges Ablage Ziel im Designer.

     Visual Studio generiert XAML, das neue Daten gebundene Steuerelemente für jedes Element erstellt, das Sie ziehen. Die XAML fügt den Ressourcen des Ablage Ziels auch ein neues- <xref:System.Windows.Data.CollectionViewSource> Objekt für die übergeordnete Tabelle oder das übergeordnete Objekt hinzu. Für einige Datenquellen generiert Visual Studio auch Code, um die Daten in die übergeordnete Tabelle oder das übergeordnete Objekt zu laden. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. Suchen Sie im Fenster **Datenquellen** nach der zugehörigen untergeordneten Tabelle oder dem entsprechenden Objekt. Verknüpfte untergeordnete Tabellen und Objekte werden im unteren Bereich der Datenliste des übergeordneten Knotens als erweiterbare Knoten angezeigt.

7. Ziehen Sie den untergeordneten Knoten (oder einzelne Elemente im untergeordneten Knoten) aus dem **Datenquellen** Fenster auf ein gültiges Ablage Ziel im Designer.

     Visual Studio generiert XAML, das neue Daten gebundene Steuerelemente für jedes der Elemente erstellt, die Sie ziehen. Die XAML fügt <xref:System.Windows.Data.CollectionViewSource> den Ressourcen des Ablage Ziels auch ein neues für die untergeordnete Tabelle oder das untergeordnete Objekt hinzu. Diese neue <xref:System.Windows.Data.CollectionViewSource> ist an die-Eigenschaft der übergeordneten Tabelle oder des Objekts gebunden, das Sie soeben in den Designer gezogen haben. Für einige Datenquellen generiert Visual Studio auch Code, um die Daten in die untergeordnete Tabelle oder das untergeordnete Objekt zu laden.

     In der folgenden Abbildung wird die Tabelle mit verknüpften **Bestellungen** der **Customers** -Tabelle in einem Dataset im **Datenquellen** Fenster veranschaulicht.

     ![Relation im Datenquellenfenster](../data-tools/media/datasources2.gif)

## <a name="see-also"></a>Weitere Informationen

- [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Erstellen von Nachschlagetabellen in WPF-Anwendungen](../data-tools/create-lookup-tables-in-wpf-applications.md)
