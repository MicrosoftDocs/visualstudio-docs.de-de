---
title: Private Daten in Problemberichten
description: Erfahren Sie, wie Sie Ihre privaten Daten sicherer machen, wenn Sie Problemberichte zur Überprüfung durch die Entwicklercommunity erstellen.
ms.custom: SEO-VS-2020
ms.date: 06/21/2018
ms.topic: conceptual
helpviewer_keywords:
- developer community privacy
- privacy, developer community
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dccf962aef39227388f86134a9dd1f8c96440a3c
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668546"
---
# <a name="developer-community-data-privacy"></a>Datenschutz in der Developer Community

Standardmäßig sind sämtliche Informationen in Problemberichten der [Entwicklercommunity](https://aka.ms/feedback/suggest?space=8), Kommentare und Antworten inbegriffen, öffentlich sichtbar. Dies ist ein Vorteil, da die gesamte Community Einblicke in die Probleme, Lösungen und Problemumgehungen anderer Benutzer hat. Wenn Sie um den Datenschutz Ihrer Daten oder Ihrer Identität besorgt sind, gibt es jedoch auch andere Optionen.

## <a name="identity-privacy"></a>Identitätsschutz

Wenn Sie Ihre Identität nicht offenlegen möchten, [erstellen Sie ein neues Microsoft-Konto](https://signup.live.com/), das keine personenbezogenen Informationen enthält. Verwenden Sie dieses Konto, um Ihren Bericht zu erstellen.

## <a name="data-privacy"></a>Datenschutz

Wenn Sie um den Datenschutz besorgt sind, fügen Sie keine Informationen, die privat bleiben sollen, in den Titel oder den Inhalt des ursprünglichen Berichts ein, denn dieser ist immer öffentlich. Erstellen Sie stattdessen den Bericht, und achten Sie anschließend darauf, dass Sie die Details privat in einem separaten Kommentar senden. Sobald der Problembericht erstellt wurde, können Sie angeben, wer Ihre Antworten und Anlagen anzeigen darf:

1. Klicken Sie im erstellten Bericht auf **Kommentar hinzufügen**, um eine private Beschreibung des Problems zu erstellen.

2. Verwenden Sie im Antwort-Editor das Steuerelement unter den Schaltflächen **Senden** und **Abbrechen**, um die Zielgruppe für Ihre Antwort anzugeben. Wählen Sie **Viewable by moderators and the original poster** (Sichtbar für Moderatoren und den Verfasser) aus, um die Sichtbarkeit auf Microsoft-Mitarbeiter und sich selbst zu beschränken.

   ![Datenschutz-Steuerelement in der Entwicklercommunity](media/developer-community-privacy-control.png)

   Nur die von Ihnen angegebenen Personen können die Kommentare sowie darin enthaltene Bilder, Links und Code anzeigen. Sämtliche Antworten unter dem Kommentar weisen die gleiche Sichtbarkeit wie der ursprüngliche Kommentar auf. Dies gilt auch dann, wenn das Datenschutz-Steuerelement den Status der eingeschränkten Sichtbarkeit nicht korrekt anzeigt.

3. Fügen Sie die Beschreibung und weitere erforderliche Informationen, Bilder und Dateianlagen für die Reproduktion hinzu. Klicken Sie auf die Schaltfläche **Senden**, um diese Informationen privat zu senden.

   > [!NOTE]
   > Auf der Website der Entwicklercommunity gilt ein Grenzwert von maximal 10 Dateien und maximal 2 GB für angefügte Dateien. Wenn Sie eine größere Datei hochladen müssen, können Sie einen neuen Problembericht senden oder in einem privaten Kommentar bei einem Microsoft-Mitarbeiter eine Upload-URL anfordern.
   > Wenn wir ein Issue schließen, werden zugehörige Anlagen nach 90 Tagen gelöscht.

Wenn Sie Ihre Privatsphäre schützen und vertrauliche Daten nicht veröffentlichen möchten, sollte die gesamte Interaktion mit Microsoft unter einem Kommentar mit eingeschränkter Sichtbarkeit stattfinden. Antworten auf andere Kommentare können dazu führen, dass Sie versehentlich vertrauliche Informationen offenlegen.

## <a name="data-we-collect"></a>Erfasste Daten

Wenn der Visual Studio-Installer den Vorgang **Problem melden** einleitet, wird das aktuelle Setupprotokoll erfasst.

Wenn Visual Studio den Vorgang **Problem melden** einleitet, wird mindestens einer der folgenden Datentypen erfasst:

- Watson- und .NET-Einträge aus dem Ereignisprotokoll

- Visual Studio-Aktivitätsprotokolldatei im Arbeitsspeicher

- PerfWatson-Dateien, wenn die Watson-Sammlung aktiviert ist

- LiveShare-Protokolldateien, sofern vorhanden

- Xamarin-Protokolldateien, sofern vorhanden

- NuGet-Protokolldateien, sofern vorhanden

- Webdebugger-Protokolldateien, sofern vorhanden

- Service Hub-Protokolle und MEF-Fehlerprotokolle, sofern vorhanden

- Python-Protokolle, sofern vorhanden

- Razor-LSP-Editor-Protokolle, sofern vorhanden

- Windows Forms-Protokolle, sofern vorhanden

- Ein Screenshot, sofern dieser einbezogen werden soll

- Aufzeichnungsdaten, sofern eine Aufzeichnung einbezogen werden soll. Diese umfassen:

  - Schritte zum Reproduzieren des Problems

  - ETL-Ablaufverfolgungsdatei

  - Dumpdatei

> [!NOTE]
> Wenn Sie Microsoft Protokolldateien, Screenshots und Aufzeichnungsdaten senden, können wir Ihr Problem schneller nachvollziehen und Ihnen bei der Behebung helfen.  Deshalb sollten Sie solche Daten immer anhängen. Aus Datenschutzgründen werden Protokolldateien, Screenshots und Aufzeichnungsdaten nur dann an Microsoft gesendet, wenn Sie die Berechtigung dazu erteilen. Das tun Sie automatisch, wenn Sie den Fehlerbericht übermitteln, in dem sie enthalten sind. Im Schritt „Zusammenfassung“ des Fensters „Problem melden“ können Sie vor der Übermittlung des Berichts sehen, welche Daten gesendet werden. Sie können Systemprotokolldateien aus dem Bericht ausschließen, indem Sie im Schritt „Zusammenfassung“ den Haken aus dem Kontrollkästchen „Systemprotokolle anfügen“ entfernen. So sieht die Seite „Zusammenfassung“ aus. 
  > ![Problem melden: Zusammenfassung gesammelter Protokolle](media/report-a-problem-logs-collected.png)


## <a name="see-also"></a>Siehe auch

- [Melden eines Problems mit Visual Studio](how-to-report-a-problem-with-visual-studio.md)
- [Datenschutz in C++-Problemberichten](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)
