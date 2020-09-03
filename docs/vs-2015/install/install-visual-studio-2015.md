---
title: Installieren von Visual Studio 2015 | Microsoft-Dokumentation
titleSuffix: ''
ms.date: 04/15/2020
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- Visual Studio, installing
- installing Visual Studio
- server installations [Visual Studio]
- Setup [Visual Studio]
- install Visual Studio
- visual studio installer
ms.assetid: da049020-cfda-40d7-8ff4-7492772b620f
caps.latest.revision: 183
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: d593625985924d8c8076e1bdd361ce4d08c1dfbc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548043"
---
# <a name="install-visual-studio-2015"></a>Installieren von Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Seite enthält detaillierte Informationen zum Installieren von **Visual Studio 2015**, der integrierten Sammlung von Produktivitätstools für Entwickler. Wir haben auch Links eingefügt, mit denen Sie schnell Informationen zu [Features](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-version-history), [Systemanforderungen](https://docs.microsoft.com/visualstudio/productinfo/vs2015-sysrequirements-vs), [Downloads](https://visualstudio.microsoft.com/vs/older-downloads/)und mehr erhalten.

## <a name="quick-links"></a>Quicklinks

Bevor wir auf die Details eingehen, finden Sie hier die am häufigsten aufgerufenen Links.

|Titel|BESCHREIBUNG|
|------------------|----------------|
|![Herunterladen von Visual Studio](../install/media/downloads.png "Downloads") |**Downloads**: um Visual Studio 2015 zu installieren, können Sie eine ausführbare Produktdatei von der  [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) -Seite (das erforderliche Abonnement) herunterladen oder die Installationsmedien des geduchten Produkts verwenden. [Erfahren Sie mehr darüber, wie Sie aktuelle oder frühere Versionen von Visual Studio herunterladen](https://www.visualstudio.com/vs/older-downloads/).|
|![Weitere Informationen zu Features](../install/media/features.png "Features") |**Features**: Weitere Informationen zu den Features in Visual Studio 2015 finden Sie in den Anmerkungen zu dieser Version von [RTM](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-rtm-vs), [Update 1](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update1-vs), [Update 2](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update2-vs)und [Update 3](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update3-vs).|
|![Anzeigen der Systemanforderungen](../install/media/system-requirements.png "Systemanforderungen") |**Systemanforderungen**: um die Systemanforderungen für jede Edition von Visual Studio 2015 anzuzeigen, finden Sie weitere Informationen auf der Seite [Visual Studio 2015 Plattform für Zielplattformen und Kompatibilität](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs) .|
|![Suchen des Product Key](../install/media/product-keys.png "Product Keys") |**Product Keys**: Informationen zum Suchen Ihrer Product Key finden Sie im Thema Gewusst [wie: Suchen des Visual Studio Product Key](../install/how-to-locate-the-visual-studio-product-key.md) .|
|![Informationen zur Lizenzierung](../install/media/licensing.png "Lizenzierung") |**Lizenzierung**: Weitere Informationen zu Lizenzierungsoptionen für Einzelpersonen oder Unternehmenskunden finden Sie im [Whitepaper zur Lizenzierung von Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=13350).|

## <a name="default-vs-custom-setup"></a><a name="custom"></a> Standard-und benutzerdefiniertes Setup
 Bei der Installation von Visual Studio 2015 können Sie Komponenten, die Sie täglich verwenden, ein- und ausschließen. Dies bedeutet, dass eine Standardinstallation oft kleiner und schneller erfolgt als eine benutzerdefinierte Installation. Dies bedeutet zudem, dass in früheren Versionen viele standardmäßig installierte Komponenten nun als benutzerdefinierte Komponenten erachtet werden, die Sie explizit in dieser Version auswählen müssen.

 ![Visual Studio 2015-Setupdialogfeld](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Zu den benutzerdefinierten Komponenten gehören Visual C++, Visual F#, SQL Server Data Tools, plattformübergreifende Mobile Tools und sdche sowie sdgs und Erweiterungen von Drittanbietern. Sie können jede der benutzerdefinierten Komponenten zu einem späteren Zeitpunkt installieren, wenn Sie sie während des ersten Setups nicht auswählen.

> [!NOTE]
> Bei einer benutzerdefinierten Installation werden die in einer Standardinstallation enthaltenen Komponenten automatisch mit aufgenommen.

 Die vollständige Liste der benutzerdefinierten Komponenten lautet wie folgt:

|Funktionsgruppen|Komponenten|
|------------------|----------------|
|**Updates**|Visual Studio 2015 Update 3|
|**Programmiersprachen**|Visual C++<br />Visual F#<br />Python Tools for Visual Studio|
|**Windows- und Webentwicklung**|ClickOnce-Tools für die Veröffentlichung<br />LightSwitch<br />Microsoft Office Developer Tools<br />Microsoft SQL Server-Datentools<br /> Microsoft Web Developer Tools<br />PowerShell Tools for Visual Studio (Drittanbieter)<br />Silverlight Development Kit<br />Universal Windows App-Entwicklungstools<br />Windows 10-Tools und -SDKs<br />Windows 8.1- und Windows Phone 8.0/8.1-Tools<br />Windows 8.1-Tools und -SDKs|
|**Plattformübergreifende mobile Entwicklung**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Mobile Visual C++-Entwicklung für iOS / Android<br />Clang mit Microsoft CodeGen|
|**Allgemeine Tools und Software Development Kits**|Android Native Development Kit (Drittanbieter)<br /> Android SDK [Drittanbieter]<br />Android SDK Setup-APIs (Drittanbieter)<br />Apache Ant (Drittanbieter)<br /> Java SE Development Kit (Drittanbieter)<br /> Joyent Node.js (Drittanbieter)|
|**Häufig verwendete Tools**|Git für Windows (Drittanbieter)<br />GitHub-Erweiterung für Visual Studio (Drittanbieter)<br /> Visual Studio-Erweiterbarkeitstools|

## <a name="install-visual-studio"></a><a name="installing"></a> Installieren von Visual Studio
 Sie können Visual Studio mithilfe der Installationsmedien (DVDs) installieren, indem Sie Ihren Visual Studio-Abonnement Dienst von der [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) -Website verwenden, indem Sie einen Webinstaller von der [Visual Studio-Download](https://visualstudio.microsoft.com/vs/older-downloads/) Website herunterladen oder ein Layout für die Offline Installation erstellen (Weitere Informationen finden Sie auf der Seite [Erstellen einer Offline Installation von Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) ).

> [!IMPORTANT]
> Sie benötigen Administratoranmeldeinformationen, um [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]zu installieren. Sie benötigen sie allerdings nicht, um [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nach der Installation zu verwenden.

 Ihr lokales Administratorkonto benötigt die folgenden Berechtigungen, damit Sie alles in Visual Studio installieren können.

|Angezeigter Name des lokalen Richtlinienobjekts|Benutzerrechte|
|--------------------------------------|----------------|
|Sichern von Dateien und Verzeichnissen|SeBackupPrivilege|
|Debuggen von Programmen|SeDebugPrivilege|
|Verwalten von Überwachungs- und Sicherheitsprotokollen|SeSecurityPrivilege|

 Weitere Informationen zu den Anforderungen an das lokale Administratorkonto finden Sie im Knowledge Base-Artikel [SQL Server-Installation schlägt fehl, wenn das Setupkonto nicht über bestimmte Benutzerrechte verfügt](https://support.microsoft.com/kb/2000257).

### <a name="use-installation-media"></a><a name="BKMK_Media"></a> Installationsmedien verwenden
 Führen Sie zum Installieren von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]die Installationsdatei für die gewünschte Edition im Stammverzeichnis des [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Installationsmediums aus:

|Edition|Installationsdatei|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio-Community|vs_community.exe|

### <a name="download-from-the-product-website"></a><a name="BKMK_Website"></a> Von der Produktwebsite herunterladen
 Besuchen Sie die [Visual Studio-Download](https://visualstudio.microsoft.com/vs/older-downloads/) Seite, und wählen Sie die gewünschte Edition von Visual Studio aus.

### <a name="download-from-your-subscription-service"></a>Aus Ihrem Abonnement Dienst herunterladen
 Besuchen Sie die Seite [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) , und wählen Sie die gewünschte Edition von Visual Studio aus.

### <a name="create-an-offline-installation-layout"></a><a name="BKMK_Offline"></a> Erstellen eines Layouts für die Offline Installation
 Wenn Sie nicht über das Installationsmedium verfügen, oder wenn Sie nicht über [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ein Visual Studio-Abonnement verfügen, oder wenn Sie nicht mit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dem Webinstaller installieren möchten, können Sie eine "getrennte" Installation durchführen, indem Sie das als offline-Installations Layout bezeichnete Layout erstellen. Weitere Informationen finden Sie auf der Seite [Erstellen einer Offline Installation von Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) .

## <a name="deploy-visual-studio-in-an-enterprise"></a><a name="enterprise"></a> Bereitstellen von Visual Studio in einem Unternehmen
 Weitere Informationen zur Bereitstellung [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] über ein Netzwerk finden Sie im [Administrator Handbuch für Visual Studio](../install/visual-studio-administrator-guide.md).

### <a name="install-visual-studio-in-a-virtualized-environment"></a><a name="BKMK_Virtualized"></a> Installieren von Visual Studio in einer virtualisierten Umgebung
 **Videoprobleme mit Hyper-V**

 Das Ausführen von Windows Server 2008 R2 mit aktiviertem Hyper-V und beschleunigter Grafikkarte führt möglicherweise zu Systemverlangsamungen.

 Weitere Informationen finden Sie unter [Video Leistung kann abnehmen, wenn auf einem Computer mit Windows Server 2008 oder Windows Server 2008 R2 die Hyper-V-Rolle aktiviert und ein beschleunigter Anzeige Adapter installiert ist](https://support.microsoft.com/kb/961661).

 **Emulieren von Geräten mit Hyper-V**

 Bei der Installation von Visual Studio 2015 auf echter Hardware ohne Virtualisierung können Sie Features auswählen, die eine Emulation von Windows- und Android-Geräten mithilfe von Hyper-V ermöglichen. Bei der Installation in Hyper-V können Sie keine Windows- oder Android-Geräte emulieren. Der Grund hierfür ist, dass die Emulatoren selbst virtuelle Computer sind, und Sie können derzeit keine virtuellen Computer auf anderen virtuellen Computern hosten. Als Problemumgehung verwenden Sie echte Windows- oder Android-Geräte, auf denen Sie Ihre Anwendung direkt bereitstellen und debuggen können .

## <a name="install-optional-components"></a><a name="optionalComponents"></a> Optionale Komponenten installieren
 Wenn Sie Komponenten installieren möchten, die Sie bei der ursprünglichen Installation möglicherweise nicht ausgewählt haben, gehen Sie wie folgt vor.

#### <a name="to-install-optional-components"></a>So installieren Sie optionale Komponenten

1. Wählen Sie in der **Systemsteuerung**auf der Seite **Programme und Funktionen** die Produktversion aus, zu der Sie mindestens eine Komponente hinzufügen möchten, und wählen Sie anschließend **Deinstallieren/Ändern**aus.

2. Wählen Sie im Setup-Assistenten **Ändern**aus, und wählen Sie anschließend die Komponenten aus, die Sie installieren möchten.

3. Wählen Sie **Weiter**aus, und befolgen Sie anschließend die übrigen Anweisungen.

## <a name="install-offline-help-content"></a><a name="helpContent"></a> Offline Hilfe Inhalt installieren
 Nach der Installation von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]können Sie zusätzliche Hilfeinhalte herunterladen, damit diese offline zur Verfügung stehen.

#### <a name="to-install-or-uninstall-help-content"></a>So installieren oder deinstallieren Sie Hilfeinhalt

1. Klicken Sie in der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Menüleiste auf **Hilfe**, **Hilfeinhalte hinzufügen und entfernen**.

2. Wählen Sie in der Registerkarte **Inhalt verwalten** in **Microsoft Help Viewer**die Installationsquelle für den Hilfeinhalt aus.

3. Wenn Sie nach einem bestimmten Hilfethema suchen, geben Sie den Namen oder ein Schlüsselwort in das Textfeld **Suchen** ein und drücken dann die **EINGABETASTE**.

4. Klicken Sie neben dem Namen des Hilfethemas, das Sie installieren möchten, auf **Hinzufügen** oder **Entfernen** .

5. Klicken Sie auf die Schaltfläche **Aktualisieren**.

   Weitere Informationen zum Installieren oder Bereitstellen der Offline Hilfe finden Sie im [Help Viewer-Administrator Handbuch](../ide/help-viewer-administrator-guide.md).

## <a name="check-for-service-releases-and-product-updates"></a><a name="serviceReleases"></a> Auf Dienst Releases und Produkt Updates überprüfen
 Da nicht alle Erweiterungen kompatibel sind, führt Visual Studio kein automatisches Upgrade für Erweiterungen durch, wenn Sie ein Upgrade von früheren Versionen durchführen. Sie müssen die Erweiterungen von der [Visual Studio Marketplace](https://marketplace.visualstudio.com/) oder vom Software Herausgeber neu installieren.

#### <a name="to-automatically-check-for-service-releases"></a>So suchen Sie automatisch nach Service Releases

1. **Wählen Sie**in der Menüleiste Extras, **Optionen**aus.

2. Erweitern Sie **Umgebung** im Dialogfeld **Optionen**und klicken Sie dann auf **Erweiterungen und Updates**. Stellen Sie sicher, dass das Kontrollkästchen **Automatisch nach Updates suchen** markiert ist, und klicken Sie auf **OK**.

## <a name="register-visual-studio"></a>Visual Studio registrieren

1. Wählen Sie in der Menüleiste **Hilfe**dann **Info**aus.

     Im Dialogfeld **Info** wird die Produkt-ID (PID) angezeigt. Sie benötigen die PID und die Anmeldeinformationen für das Windows-Konto (z. B. eine E-Mail-Adresse und das zugehörige Kennwort von Hotmail oder Outlook.com), um das Produkt registrieren zu können.

2. Wählen Sie in der Menüleiste **Hilfe**dann **Produkt registrieren**.

## <a name="repair-visual-studio"></a><a name="repair"></a> Reparieren von Visual Studio

#### <a name="to-repair-visual-studio"></a>So reparieren Sie Visual Studio

1. Wählen Sie in der **Systemsteuerung**auf der Seite **Programme und Funktionen** die Produktversion aus, die Sie reparieren möchten, und wählen Sie anschließend **Ändern**aus.

2. Wählen Sie im Setup-Assistenten **Reparieren**aus, wählen Sie **Weiter**aus, und befolgen Sie anschließend die übrigen Anweisungen.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>So reparieren Sie Visual Studio im unbeaufsichtigten oder passiven Modus (d. h. zur Reparatur aus der Quelle)

1. Öffnen Sie die Windows-Eingabeaufforderung auf dem Computer, auf dem Visual Studio installiert ist.

2. Legen Sie die folgenden Parameter fest:

     *Dvdroot* \\ < *Installationsdatei* \> \<`/quiet|/passive`> [/`norestart`]/`Repair`

## <a name="troubleshoot-an-installation"></a><a name="troubleshooting"></a> Behandeln von Problemen bei einer Installation
 In den folgenden Ressourcen finden Sie Hilfe für Setup- und Installationsprobleme:

- [Einrichtung und Installation in Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/vssetup/threads) – Forum. Lesen Sie Fragen und Antworten von anderen Personen in der Visual Studio-Community. Wenn Sie die gesuchte Antwort nicht finden, stellen Sie eigene Fragen.

- [Hilfe zu Visual Studio](https://visualstudio.microsoft.com/vs/support/vs2015/). Suchen Sie nach Knowledge Base-Artikeln (KB), und erfahren Sie, wie Sie Microsoft-Support Informationen zu Problemen bei der Installation von Visual Studio kontaktieren.

## <a name="related-topics"></a><a name="relatedTopics"></a> Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Erstellen einer Offline Installation von Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)|Hier wird beschrieben, wie Sie Visual Studio installieren, wenn Sie nicht mit dem Internet verbunden sind.
|[Parallele Installation von Visual Studio-Versionen](../install/install-visual-studio-versions-side-by-side.md)|Stellt Informationen zum Installieren mehrerer Versionen von Visual Studio auf demselben Computer bereit.|
|[Verwenden von Befehlszeilen Parametern zum Installieren von Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Listet die Befehlszeilenparameter auf, die Sie verwenden können, wenn Sie Visual Studio über eine Eingabeaufforderung installieren.|
|[Deinstallieren von Visual Studio](../install/uninstall-visual-studio.md)|Hier wird beschrieben, wie Sie Visual Studio deinstallieren.|
|[Administrator Handbuch für Visual Studio](../install/visual-studio-administrator-guide.md)|Stellt Informationen zu Bereitstellungsoptionen für Visual Studio bereit.|
|[Die Visual Studio-Bildbibliothek](../designers/the-visual-studio-image-library.md)|Stellt Informationen zum Installieren von Grafiken bereit, die in Visual Studio-Anwendungen verwendet werden können.|
|[Einstieg in die Entwicklung mit Visual Studio](../ide/get-started-developing-with-visual-studio.md)|Enthält Informationen und Links, die Sie bei der effektiveren Verwendung von Visual Studio unterstützen können.|

## <a name="see-also"></a>Weitere Informationen

- [Anmelden bei Visual Studio](../ide/signing-in-to-visual-studio.md)
