---
title: Bereitstellen von Windows Store-Apps
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 73b4350a2e7f277a11f4d6650d8089df0f87fe4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177471"
---
# <a name="deploy-windows-store-apps-from-visual-studio"></a>Bereitstellen von Windows Store-Apps aus Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gilt nur für Windows] (.. /Image/windows_only_content.png "windows_only_content")

 Die Bereitstellungsfunktion von Visual Studio erstellt und registriert Windows Store-Apps, die mit Visual Studio erstellt wurden, auf einem Zielgerät. Wie genau die App registriert wird, hängt davon ob, ob sich das Zielgerät lokal oder remote befindet:

- Handelt es sich bei dem Ziel um einen lokalen Visual Studio-Computer, registriert Visual Studio die App vom Erstellungsordner aus.

- Handelt es sich bei dem Ziel um ein Remotegerät, kopiert Visual Studio die erforderlichen Dateien auf den Remotecomputer und registriert anschließend die App auf dem Gerät.

  Die Bereitstellung erfolgt automatisch, wenn Sie Ihre App über Visual Studio mit der Option **Debuggen starten** (Tastatur: F5) oder **Starten ohne Debuggen** (Tastatur: STRG+F5) debuggen. Sie können die App auch manuell bereitstellen. Die manuelle Bereitstellung ist in folgenden Szenarios nützlich:

- Ad-Hoc-Tests auf einem lokalen oder Remotecomputer.

- Bereitstellen einer App, die eine andere App startet, welche Sie debuggen möchten.

- Bereitstellen einer App, deren Debugging beim Start durch eine andere App oder Methode erfolgen soll.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> In diesem Thema
 Hier erfahren Sie Folgendes:

 [Bereitstellen von Windows Store-Apps](#BKMK_How_to_deploy_a_Windows_Store_app)

 [Angeben eines Remote Geräts](#BKMK_How_to_specify_a_remote_device)

 [Bereitstellungsoptionen](#BKMK_Deployment_options)

## <a name="how-to-deploy-a-windows-store-app"></a><a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Bereitstellen einer Windows Store-App
 Das manuelle Bereitstellen einer App ist ein einfacher Vorgang:

1. Wenn Sie ein Remotegerät bereitstellen, geben Sie den Namen oder die IP-Adresse des Geräts auf der Projekteigenschaftenseite des Startprojekts der App an. (Die entsprechenden Schritte sind weiter unten in diesem Thema aufgelistet.)

2. Wählen Sie auf der Debugger-Symbolleiste von Visual Studio das Bereitstellungsziel aus der Dropdownliste neben der Schaltfläche **Debuggen starten** aus.

     ![Ausführen auf lokalem Computer](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")

3. Klicken Sie im Menü **Erstellen** auf **Bereitstellen**.

## <a name="how-to-specify-a-remote-device"></a><a name="BKMK_How_to_specify_a_remote_device"></a> Festlegen eines Remotegeräts
 **Erforderliche Komponenten**

 So stellen Sie eine App auf einem Remotegerät bereit:

- Die Lizenz eines Entwicklers muss auf dem Remotegerät installiert sein.

- Die Visual Studio Remote Tools müssen auf dem Remotegerät installiert sein, außerdem muss der Remotedebugmonitor ausgeführt werden.

     Bei der Bereitstellung wird der Remotedebugger-Netzwerkkanal verwendet, um die App-Dateien an das Remotegerät zu senden.

#### <a name="to-specify-a-remote-device"></a>So legen Sie ein Remotegerät fest

1. Geben Sie auf der Debugeigenschaftenseite für das Startprojekt den Namen oder die IP-Adresse des Remotebereitstellungsziels an.

2. Wählen Sie zum Öffnen der Debugeigenschaftenseite das Projekt im Projektmappen-Explorer aus, und klicken Sie dann im Kontextmenü auf **Eigenschaften** .

3. Wählen Sie dann den Knoten **Debuggen** im Eigenschaftenseitenfenster aus.

4. Sie können den Namen oder die IP-Adresse des Remotegeräts eingeben, oder es im Dialogfeld **Remotedebuggerverbindung auswählen** auswählen.

    ![Dialogfeld „Remoteverbindung“](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    Im Dialogfeld **Remotedebuggerverbindung auswählen** werden die Geräte im Subnetz des lokalen Netzwerks sowie solche Geräte angezeigt, die direkt mit dem Visual Studio-Computer durch ein Ethernetkabel verbunden sind.

   **Angeben des Remotegeräts auf einer JavaScript- oder Visual C++-Projektseite**

   ![C&#43;&#43;-Projekteigenschaften für Remotedebuggen](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")

5. Wählen Sie **Remote Debugger** in der Liste **Zu startender Debugger** aus.

6. Geben Sie den Netzwerknamen des Remotegeräts in das Feld **Computername** ein. Oder verwenden Sie den nach unten weisenden Pfeil im Feld, um das Gerät im Dialogfeld "Remotedebuggerverbindung auswählen" auszuwählen.

   **Angeben des Remotegeräts auf einer Visual C#- oder Visual Basic-Projektseite**

   ![Verwaltete Projekteigenschaften für Remotedebuggen](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")

7. Wählen Sie in der Liste **Zielgerät** die Option **Remotecomputer** aus.

8. Geben Sie den Netzwerknamen des Remotegeräts in das Feld **Remotecomputer** ein oder klicken Sie auf **Suchen** , um das Gerät im Dialogfeld **Remotedebuggerverbindung auswählen** auszuwählen.

## <a name="deployment-options"></a><a name="BKMK_Deployment_options"></a> Bereitstellungsoptionen
 Sie können die folgenden Bereitstellungsoptionen auf der Debugeigenschaftenseite für das Startprojekt festlegen.

 **Netzwerk Loopback zulassen** Aus Sicherheitsgründen ist eine- [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] app, die standardmäßig installiert wird, nicht berechtigt, Netzwerk Aufrufe an das Gerät vorzunehmen, auf dem Sie installiert ist. Standardmäßig wird durch die Visual Studio-Bereitstellung eine Ausnahme von dieser Regel für die bereitgestellte App erstellt. Diese Ausnahme ermöglicht das Testen von Kommunikationsverfahren auf einem einzelnen Computer. Bevor Sie die App an [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]senden, sollten Sie die App ohne die Ausnahme testen.

 So entfernen Sie die Netzwerkloopbackausnahme aus der App:

- Deaktivieren Sie auf der Debugeigenschaftenseite für C# und VB das Kontrollkästchen **Netzwerkloopback zulassen** .

- Legen Sie auf der Debugeigenschaftenseite für JavaScript den Wert für **Netzwerkloopback zulassen** auf **Nein**fest.

  **Eigenen Code beim Starten nicht starten, sondern Debuggen (c# und VB)/Anwendung starten (JavaScript und C++)** So konfigurieren Sie die Bereitstellung so, dass beim Starten der APP automatisch eine Debugsitzung gestartet wird:

- Aktivieren Sie auf der Debugeigenschaftenseite für C# und VB das Kontrollkästchen **Eigenen Code zunächst nicht starten sondern debuggen** .

- Legen Sie auf der Debugeigenschaftenseite für JavaScript den Wert für **Anwendung starten** auf **Ja**fest.

## <a name="see-also"></a>Weitere Informationen
 [Ausführen von Apps aus Visual Studio](../debugger/run-store-apps-from-visual-studio.md)
