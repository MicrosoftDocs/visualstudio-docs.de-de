---
title: Eigenschaftenseiten, JavaScript
description: Hier erfahren Sie, wie die Eigenschaftenseiten Zugriff auf Projekteinstellungen bieten und wie Sie die Seiten, die auf den Eigenschaftenseiten angezeigt werden, zum Ändern der Projekteigenschaften verwenden können.
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- javascript.project.property.debugging.debuggertype
- javascript.project.property.debugging.requireauthentication
- javascript.project.property.outputpath
- javascript.project.property.debugging.launchapplication
- javascript.project.property.defaultlanguage
- javascript.project.property.debugging.machinename
- javascript.project.property.debugging.allowlocalnetworkloopback
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 30c16e1c76e6f4e12d822f68f2a9530290c15de5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919456"
---
# <a name="property-pages-javascript"></a>Eigenschaftenseiten, JavaScript

Die **Eigenschaftenseiten** bieten Zugriff auf die Projekteinstellungen. Sie können die Seiten, die in den **Eigenschaftenseiten** angezeigt werden, zum Ändern der Projekteigenschaften verwenden.

Um auf die Projekteigenschaften zuzugreifen, wählen Sie im **Projektmappen-Explorer** einen Projektknoten aus. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

Die folgenden Seiten und Optionen werden auf den **Eigenschaftenseiten** angezeigt.

## <a name="configuration-and-platform-page"></a>Konfiguration und Plattformseite

Verwenden Sie die folgenden Optionen zum Auswählen der anzuzeigenden bzw. zu ändernden Konfiguration und Plattform.

 **Configuration**

Gibt die anzuzeigenden bzw. zu ändernden Konfigurationseinstellungen an. Die Einstellungen sind **Debuggen (Standard)**, **Release**, **Alle Konfigurationen** oder eine benutzerdefinierte Konfiguration. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen von Debug- und Releasekonfigurationen in Visual Studio](../../debugger/how-to-set-debug-and-release-configurations.md).

 **Plattform**

Gibt die anzuzeigenden bzw. zu ändernden Plattformeinstellungen an. Die Einstellungen sind **Beliebige CPU** (Standard für [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)]-App), **x64**, **ARM**, **x86** oder eine benutzerdefinierte Plattform. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen von Debug- und Releasekonfigurationen in Visual Studio](../../debugger/how-to-set-debug-and-release-configurations.md).

## <a name="general-page"></a>Seite Allgemein

Verwenden Sie die folgenden Optionen, um die allgemeinen Eigenschaften des Projekts festzulegen.

> [!NOTE]
> Einige Optionen sind nur für UWP-Apps verfügbar.

 **Ausgabepfad**

Legt den Speicherort der Ausgabedateien für die Konfiguration des Projekts fest. Der Pfad ist relativ. Wenn Sie einen absoluten Pfad eingeben, wird der absolute Pfad im Projekt gespeichert. Der Standardpfad ist "bin\Debug".

Bei Verwendung vereinfachter Buildkonfigurationen bestimmt das Projektsystem, ob eine Debug- oder eine Releaseversion erstellt werden soll. Wenn Sie auf **Debuggen** > **Debuggen starten** klicken (oder **F5** drücken), wird der Build unabhängig vom angegebenen **Ausgabepfad** am Speicherort für das Debuggen abgelegt. Mit dem Befehl **Projektmappe erstellen** im Menü **Erstellen** hingegen wird er an dem Speicherort abgelegt, den Sie angeben. Um erweiterte Buildkonfigurationen zu aktivieren, wählen Sie in der Menüleiste die Optionen **Extras** > **Optionen** aus. Erweitern Sie im Dialogfeld **Optionen** die Option **Projekte und Projektmappen**, wählen Sie **Allgemein** aus, und heben Sie anschließend die Markierung des Kontrollkästchens **Erweiterte Buildkonfigurationen anzeigen** auf. Dadurch erlangen Sie die manuelle Steuerung aller Konfigurationswerte, und Sie können festlegen, ob eine Debug- oder eine Releaseversion erstellt werden soll.

 **Standardsprache**

Gibt die Standardsprache für das Projekt an. Die Sprachenoption, die unter **Zeit, Sprache und Region** in der Systemsteuerung ausgewählt ist, gibt die bevorzugte Sprache des Benutzers an. Mit der Angabe einer Standardsprache für das Projekt kann überprüft werden, ob die angegebenen Standardsprachressourcen verwendet werden, wenn die bevorzugte Sprache des Benutzers nicht mit den in der Anwendung bereitgestellten Sprachressourcen übereinstimmt.

## <a name="debug-page"></a>Seite "Debuggen"

Verwenden Sie die folgenden Optionen, um die Eigenschaften für das Debugverhalten im Projekt festzulegen.

> [!NOTE]
> Einige Optionen sind nur für UWP-Apps verfügbar.

 **Zu startender Debugger**

Gibt den Standardhost für den Debugger an.

- Klicken Sie auf **Lokaler Computer**, um die Anwendung auf dem Visual Studio-Hostcomputer zu starten. Weitere Informationen finden Sie unter [Ausführen von Windows Store-Apps auf dem lokalen Computer](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

- Klicken Sie auf **Simulator**, um die Anwendung im Simulator zu starten. Weitere Informationen finden Sie unter [Ausführen von Windows Store-Apps im Simulator](../../debugger/run-windows-store-apps-in-the-simulator.md).

- Klicken Sie auf **Remotecomputer**, um die Anwendung auf einem Remotecomputer zu starten. Weitere Informationen zum Remotedebuggen finden Sie unter [Ausführen von Windows Store-Apps auf einem Remotecomputer](../../debugger/run-windows-store-apps-on-a-remote-machine.md).

**Anwendung starten**

Gibt an, ob die Anwendung gestartet wird, wenn Sie **F5** drücken oder auf **Debuggen** > **Debuggen** starten klicken. Klicken Sie auf **Ja**, um die Anwendung zu starten. Klicken Sie ansonsten auf **Nein**. Wenn Sie auf **Nein** klicken, können Sie bei Verwendung einer anderen Methode zum Starten der Anwendung diese immer noch debuggen.

**Debuggertyp**

Gibt die zu debuggenden Codetypen an. Klicken Sie auf **Nur Skript**, um JavaScript-Code zu debuggen. Klicken Sie auf **Nur verwaltet**, um Code zu debuggen, der von der Common Language Runtime verwaltet wird. Klicken Sie auf **Nur nativ**, um C++-Code zu debuggen. Klicken Sie auf **Nativ mit Skript**, um C++ und JavaScript zu debuggen. Klicken Sie auf **Gemischt (verwaltet und nativ)** aus, um sowohl verwalteten als auch C++-Code zu debuggen.

**Lokales Netzwerkloopback zulassen**

Gibt an, ob Zugriff auf die IP-Loopbackadresse für App-Tests zulässig ist. Klicken Sie auf **Ja**, um die Verwendung der Loopbackadresse zuzulassen, wenn sich die Client-App auf dem gleichen Computer befindet, auf dem die Serveranwendung ausgeführt wird. Klicken Sie ansonsten auf **Nein**. Diese Eigenschaft ist nur verfügbar, wenn die Eigenschaft **Zu startender Debugger** auf **Remotecomputer** festgelegt ist.

**Computername**

Gibt den Namen des Remotecomputers an, auf dem der Debugger gehostet wird. Diese Eigenschaft ist nur verfügbar, wenn **Zu startender Debugger** auf **Remotecomputer** festgelegt ist.

**Authentifizierung erforderlich**

Gibt an, ob für den Remotecomputer eine Authentifizierung erforderlich ist. Diese Eigenschaft ist nur verfügbar, wenn **Zu startender Debugger** auf **Remotecomputer** festgelegt ist.
