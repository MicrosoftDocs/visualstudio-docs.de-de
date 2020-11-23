---
title: Datentools für .NET
description: Machen Sie sich mit den Visual Studio-Datentools für .NET vertraut, die API- und Toolunterstützung zum Herstellen einer Verbindung mit Datenbanken, zum Modellieren von Daten im Arbeitsspeicher und zum Anzeigen von Daten auf der Benutzeroberfläche bieten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: a095d0fc026634c13ee9f74c8568e199e09f49db
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998277"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio-Datentools für .NET

Visual Studio und .NET bieten umfassende Unterstützung für APIs und Tools zum Herstellen einer Verbindung mit Datenbanken, zum Modellieren von Daten im Arbeitsspeicher und zum Anzeigen der Daten in der Benutzeroberfläche. Die .NET-Klassen, die Datenzugriffsfunktionen bereitstellen, werden als [ADO.NET](/dotnet/framework/data/adonet/index) bezeichnet. ADO.NET wurde zusammen mit den Datentools in Visual Studio in erster Linie zur Unterstützung relationaler Datenbanken und von XML entwickelt. Heutzutage bieten viele NoSQL-Datenbankanbieter oder Drittanbieter ADO.NET-Anbieter an.

[.NET Core](/dotnet/core/) unterstützt ADO.NET mit Ausnahme von Datasets und ihren zugehörigen Typen. Wenn Sie .NET Core als Ziel verwenden und eine ORM-Ebene (Object-Relational Mapping, objektrelationale Zuordnung) benötigen, verwenden Sie [Entity Framework Core](/ef/core/).

Die folgende Abbildung zeigt eine vereinfachte Ansicht der grundlegenden Architektur:

![ADO.NET-Architektur](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Typischer Workflow

Der typische Workflow sieht wie folgt aus:

1. Installieren einer Entwicklungs- oder Testdatenbank auf dem lokalen Computer. Weitere Informationen finden Sie unter [Installieren von Datenbanksystemen, Tools und Beispielen](../data-tools/installing-database-systems-tools-and-samples.md). Wenn Sie einen Azure-Datendienst verwenden, ist dieser Schritt nicht erforderlich.

2. Testen der Verbindung mit der Datenbank (oder dem Dienst oder der lokalen Datei) in Visual Studio. Weitere Informationen finden Sie unter [Hinzufügen neuer Verbindungen](../data-tools/add-new-connections.md).

3. (Optional) Verwenden der Tools zum Generieren und Konfigurieren eines neuen Modells. Modelle, die auf Entity Framework basieren, sind die Standardempfehlung für neue Anwendungen. Das Modell, das Sie verwenden, ist die Datenquelle, mit der die Anwendung interagiert. Das Modell befindet sich logisch zwischen der Datenbank oder dem Dienst und der Anwendung. Weitere Informationen finden Sie unter [Hinzufügen neuer Datenquellen](../data-tools/add-new-data-sources.md).

4. Ziehen Sie die Datenquelle aus dem Fenster **Datenquellen** auf eine Windows Forms-, ASP.NET- oder Windows Presentation Foundation-Entwurfsoberfläche, um den Datenbindungscode zu generieren, der dem Benutzer die Daten in der von Ihnen angegebenen Weise anzeigt. Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Fügen Sie benutzerdefinierten Code für Dinge wie Geschäftsregeln, Suche und Datenvalidierung hinzu, oder nutzen Sie benutzerdefinierte Funktionen, die die zugrunde liegende Datenbank zur Verfügung stellt.

Sie können Schritt 3 überspringen und eine .NET-Anwendung so programmieren, dass sie Befehle direkt an eine Datenbank ausgibt, anstatt ein Modell zu verwenden. In diesem Fall finden Sie hier auf die entsprechende Dokumentation: [ADO.NET](/dotnet/framework/data/adonet/index). Beachten Sie, dass Sie nach wie vor den **Datenquellenkonfigurations-Assistenten** und Designer verwenden können, um Datenbindungscode zu generieren, wenn Sie Ihre eigenen Objekte im Arbeitsspeicher mit Daten auffüllen und dann eine Datenbindung zwischen UI-Steuerelementen und diesen Objekten herstellen.

## <a name="see-also"></a>Siehe auch

- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
