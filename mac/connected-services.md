---
title: Verbundene Dienste
description: Hier erfahren Sie, wie Sie den Azure-Datenspeicher, die Authentifizierung und Pushbenachrichtigungen über Visual Studio für Mac zu einer plattformübergreifenden Anwendung hinzufügen.
ms.assetid: 41CB62FF-0F39-4CE8-8917-6A77F058719F
author: sayedihashimi
ms.author: sayedha
ms.date: 11/06/2018
ms.topic: how-to
ms.openlocfilehash: 69ad6007283b3c56a8d0e5902cc2b9bdc445f220
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847093"
---
# <a name="connected-services-walkthrough"></a>Exemplarische Vorgehensweise für verbundene Dienste

Mit dem Workflow für verbundene Dienste wird der Workflow für das Azure-Portal in Visual Studio für Mac eingebunden. Daher müssen Sie Ihr Projekt nicht verlassen, um Dienste hinzuzufügen.

Diese exemplarische Vorgehensweise veranschaulicht das Hinzufügen eines Azure-Back-End-Diensts. Dadurch werden Clouddatenspeicher, Authentifizierung und Pushbenachrichtigungen in eine plattformübergreifende Xamarin.Forms-PCL-Anwendung (Portable Class Library, portable Klassenbibliothek) eingebunden.

1. Doppelklicken Sie zunächst in der Projektmappe auf den Knoten **Verbundene Dienste**. Dadurch wird der Katalog der **Dienste** geöffnet.
  Dies ist eine Liste aller verfügbaren Dienste für den Anwendungstyp. Wählen Sie einen Dienst aus (z.B. **Mobiles Back-End mit Azure App Service**), indem Sie darauf klicken.

    [![Knoten „Verbundene Dienste“ in Visual Studio für Mac](media/connected-services-image001-sml.png "Knoten „Verbundene Dienste“ in Visual Studio für Mac")](media/connected-services-image001.png#lightbox)

2. Die Seite „Dienstdetails“ enthält eine Beschreibung des Diensts und der zu installierenden Abhängigkeiten.
  Klicken Sie auf die Schaltfläche **Hinzufügen**, um der App die Abhängigkeiten hinzuzufügen:

    [![Mobiles Back-End mit Azure](media/connected-services-image002-sml.png "Mobiles Back-End mit Azure")](media/connected-services-image002.png#lightbox)

3. Die Abhängigkeiten müssen der PCL und den plattformspezifischen Projekten hinzugefügt werden, damit sie funktionieren.
  Aktivieren Sie die Kontrollkästchen, um den Dienst jedem Projekt hinzuzufügen, das darauf verweisen soll (entweder direkt oder indirekt):

    [![Kontrollkästchen aller Projekte aktivieren, die auf den Dienst verweisen sollen](media/connected-services-image003-sml.png "Kontrollkästchen aller Projekte aktivieren, die auf den Dienst verweisen sollen")](media/connected-services-image003.png#lightbox)

4. Wählen Sie in den Dialogfeldern **Zustimmung zur Lizenz** für die NuGet-Pakete **Zustimmen** aus.
  Es können zwei Dialogfelder für die Zustimmung angezeigt werden: eines für MobileClient und die Abhängigkeiten und das andere für SQLiteStore (das Paket ist für die Offlinedatensynchronisierung erforderlich):

    [![Lizenzbedingungen zustimmen](media/connected-services-image004-sml.png "Lizenzbedingungen zustimmen")](media/connected-services-image004.png#lightbox)

    ![Fenster „Zustimmung zur Lizenz“](media/connected-services-image005.png "Fenster „Zustimmung zur Lizenz“")

5. Sobald die Abhängigkeiten hinzugefügt wurden, werden Sie aufgefordert, sich mit dem Konto anzumelden, das Sie für die Kommunikation mit Azure verwenden möchten.
  Wenn Sie bereits mit einer Microsoft-ID angemeldet sind, versucht Visual Studio für Mac Ihre Azure-Abonnements und alle damit verbundenen App-Dienste abzurufen. Wenn Sie nicht über Abonnements verfügen, können Sie eines hinzufügen, indem Sie sich für eine kostenlose Testversion anmelden oder einen Abonnementplan im Azure-Portal erwerben.

6. Wählen Sie einen App-Dienst aus der Liste aus. Dadurch wird der Vorlagencode für das `MobileServiceClient`-Objekt mit der entsprechenden URL des App-Diensts in Azure ausgefüllt:

    [![App-Dienst in Liste auswählen](media/connected-services-image006-sml.png "App-Dienst in Liste auswählen")](media/connected-services-image006.png#lightbox)

    Wenn keine Dienste aufgeführt sind, klicken Sie auf die Schaltfläche **Neu** (siehe Schritt 9).

7. Kopieren Sie den Vorlagencode für `MobileServiceClient` in die PCL. Der Speicherort der Datei ist nicht wichtig, solange nur eine Instanz davon vorhanden ist.
  Die empfohlene Vorgehensweise ist, eine `AzureService`-Klasse zu erstellen, die alle Azure-Interaktionen verarbeitet und `MobileServiceClient` verwendet:

    ![Kopieren von Konfigurationscode in die App](media/connected-services-image007.png "Kopieren von Konfigurationscode in die App")

8. Befolgen Sie die Dokumentation unter **Nächste Schritte**, um Ihrer App Daten, Offlinesynchronisierung, Authentifizierung und Pushbenachrichtigungen hinzuzufügen:

    [![Die Anweisungen unter „Nächste Schritte“ lesen](media/connected-services-image008-sml.png "Die Anweisungen unter „Nächste Schritte“ lesen")](media/connected-services-image008.png#lightbox)

9. Wenn Sie keine vorhandenen App-Dienste besitzen, können Sie in Visual Studio für Mac neue Dienste erstellen.
  Klicken Sie unten links in der Liste der Dienste auf die Schaltfläche **Neu**, um das Dialogfeld **Neuer App-Dienst** zu öffnen:

    [![Erstellen eines neuen App-Diensts in Visual Studio für Mac](media/connected-services-image009-sml.png "Erstellen eines neuen App-Diensts in Visual Studio für Mac")](media/connected-services-image009.png#lightbox)

Folgende Parameter sind für einen neuen Dienst erforderlich:

- **Name des App-Diensts**: Eindeutiger Name/eindeutige ID für den Plan
- **Abonnement**: Das Abonnement, mit dem Sie für den Dienst bezahlen möchten
- **Ressourcengruppe**: Eine Möglichkeit, alle Azure-Ressourcen für ein Projekt zu organisieren. Es gibt die Option, einen vorhandenen zu verwenden oder einen neuen zu erstellen. Wenn dies Ihr erster Azure-Dienst ist, erstellen Sie eine neue.
- **Dienstplan**: Bestimmt den Speicherort und die Kosten aller Ressourcen, die ihn verwenden. Es gibt die Option, einen vorhandenen zu verwenden oder einen neuen zu erstellen. Wenn dies Ihr erster Azure-Dienst ist, verwenden Sie den Standard, oder erstellen Sie einen neuen im Free-Tarif (F1).

Weitere Informationen finden Sie in der [Dokumentation für mobile Apps](/azure/app-service-mobile/).

## <a name="see-also"></a>Weitere Informationen

- [Verbundene Dienste (Visual Studio unter Windows)](/visualstudio/azure/vs-azure-tools-connected-services-storage)