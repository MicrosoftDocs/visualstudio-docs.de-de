---
title: Neue Verbindungen hinzufügen
description: Fügen Sie eine Verbindung in Visual Studio zu einer Datenbank oder einem Dienst hinzu, und untersuchen Sie Datenbankinhalte und-Schemas, indem Sie Server-Explorer, Cloud-Explorer oder SQL Server-Objekt-Explorer verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: ddcc5dd06a4e71d445c94c860b2a3ab92429ab2e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859384"
---
# <a name="add-new-connections"></a>Neue Verbindungen hinzufügen

Sie können die Verbindung mit einer Datenbank oder einem Dienst testen und Datenbankinhalte und-Schemas mithilfe von **Server-Explorer**, **Cloud-Explorer** oder **SQL Server-Objekt-Explorer** untersuchen. Die Funktionalität dieser Fenster überschneidet sich in gewisser Weise. Die grundlegenden Unterschiede lauten:

- Server-Explorer

   Standardmäßig in Visual Studio installiert. Kann verwendet werden, um Verbindungen zu testen und SQL Server Datenbanken, alle anderen Datenbanken mit installiertem ADO.NET-Anbieter und einige Azure-Dienste anzuzeigen. Zeigt auch Objekte auf niedriger Ebene, z. b. Systemleistungs Indikatoren, Ereignisprotokolle und Nachrichten Warteschlangen. Wenn eine Datenquelle keinen ADO.NET-Anbieter aufweist, wird Sie hier nicht angezeigt, Sie können Sie jedoch auch in Visual Studio verwenden, indem Sie Programm gesteuert eine Verbindung herstellen.

- Cloud-Explorer

   Installieren Sie dieses Fenster manuell als Visual Studio-Erweiterung von [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.CloudExplorerForVS). Bietet spezialisierte Funktionen zum untersuchen und verbinden mit Azure-Diensten.

- SQL Server-Objekt-Explorer

   Installiert mit SQL Server Data Tools und im Menü **Ansicht** sichtbar. Wenn Sie dort nicht angezeigt wird, navigieren Sie in der Systemsteuerung zu **Programme und Funktionen** , suchen Sie nach Visual Studio, und wählen Sie dann **ändern** aus, um den Installer erneut auszuführen, nachdem Sie das Kontrollkästchen für SQL Server Data Tools ausgewählt haben. Verwenden Sie **SQL Server-Objekt-Explorer** zum Anzeigen von SQL-Datenbanken (wenn Sie über einen ADO.NET-Anbieter verfügen), erstellen Sie neue Datenbanken, ändern Sie Schemas, erstellen Sie gespeicherte Prozeduren, rufen Sie Verbindungs Zeichenfolgen, Daten anzeigen usw. SQL-Datenbanken, die keinen ADO.NET-Anbieter installiert haben, werden hier nicht angezeigt, aber Sie können weiterhin Programm gesteuert eine Verbindung mit Ihnen herstellen.

## <a name="add-a-connection-in-server-explorer"></a>Hinzufügen einer Verbindung in Server-Explorer

Um eine Verbindung mit der Datenbank herzustellen, klicken Sie in **Server-Explorer** auf das Symbol **Verbindung hinzufügen** , oder klicken Sie mit der rechten Maustaste auf **Server-Explorer** auf dem Knoten **Datenverbindungen** , und wählen Sie **Verbindung hinzufügen** aus. Von hier aus können Sie auch eine Verbindung mit einer Datenbank auf einem anderen Server, einem SharePoint-Dienst oder einem Azure-Dienst herstellen.

![Symbol "neue Verbindung Server-Explorer"](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

Dadurch wird das Dialogfeld **Verbindung hinzufügen** geöffnet. Hier haben wir den Namen der SQL Server localdb-Instanz eingegeben.

![Neue Verbindung hinzufügen](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>Ändern des Anbieters

Wenn die Datenquelle nicht Ihren Wünschen entspricht, klicken Sie auf die Schaltfläche **ändern** , um eine neue Datenquelle und/oder einen neuen ADO.NET-Datenanbieter auszuwählen. Je nachdem, wie Sie Sie konfiguriert haben, kann der neue Anbieter ihre Anmelde Informationen anfordern.

![Ändern der AD0.NET-Datenanbieter](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>Testen der Verbindung

Nachdem Sie die Datenquelle ausgewählt haben, klicken Sie auf **Verbindung testen**. Wenn dies nicht gelingt, müssen Sie basierend auf der Dokumentation des Herstellers eine Problembehandlung durchführen.

![Testen der Verbindung](../data-tools/media/raddata-test-connection.png)

Wenn der Test erfolgreich ist, können Sie eine *Datenquelle* erstellen, die ein Visual Studio-Begriff ist, der tatsächlich ein *Datenmodell* ist, das auf der zugrunde liegenden Datenbank oder dem zugrunde liegenden Dienst basiert.

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
