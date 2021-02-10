---
title: Installieren von Visual Studio
titleSuffix: ''
description: Erfahren Sie Schritt für Schritt, wie Sie Visual Studio installieren.
ms.date: 12/13/2019
ms.custom: contperf-fy21q1
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 97e354dfb1208ec7306cb797049cd8ca82d0d8db
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852119"
---
# <a name="install-visual-studio"></a>Installieren von Visual Studio

::: moniker range="vs-2019"

Willkommen bei Visual Studio 2019. In dieser Version können Sie ganz einfach die Features auswählen und installieren, die Sie benötigen. Und aufgrund des reduzierten minimalen Speicherbedarfs, werden sie schnell und mit weniger Beeinträchtigung des Systems installiert.

::: moniker-end

::: moniker range="vs-2017"

Willkommen bei einer neuen Möglichkeit zur Installation von Visual Studio. In dieser Version ist es noch einfacher, genau die Features auszuwählen und zu installieren, die Sie benötigen. Wir haben außerdem den mindestens benötigten Speicherplatz weiter verringert, sodass Visual Studio sich schneller und mit geringeren Systemauswirkungen als je zuvor installieren lässt.

::: moniker-end

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Installieren von Visual Studio für Mac](/visualstudio/mac/installation/).

::: moniker range="vs-2019"

Sie möchten mehr zu weiteren Neuerungen in dieser Version wissen? Sehen Sie sich die [Anmerkungen zur Version](/visualstudio/releases/2019/release-notes/) an.

::: moniker-end

::: moniker range="vs-2017"

Sie möchten mehr zu weiteren Neuerungen in dieser Version wissen? Sehen Sie sich die [Anmerkungen zur Version](/visualstudio/releasenotes/vs2017-relnotes) an.

::: moniker-end

Bereit für die Installation? Schauen Sie sich diese Schritt-für-Schritt Anleitung an.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Schritt 1: Stellen Sie sicher, dass Ihr Computer für Visual Studio bereit ist

Vor der Installation von Visual Studio:

::: moniker range="vs-2017"

1. Informieren Sie sich über die [Systemanforderungen](/visualstudio/productinfo/vs2017-system-requirements-vs). Anhand dieser Anforderungen können Sie feststellen, ob Ihr Computer Visual Studio 2017 unterstützt.

1. Laden Sie die aktuellen Windows-Updates herunter. So stellen Sie sicher, dass Ihr Computer sowohl die neuesten Sicherheitsupdates als auch die erforderlichen Systemkomponenten für Visual Studio hat.

1. Starten Sie den Computer neu. Dadurch wird sichergestellt, dass keine ausstehenden Installationen oder Updates die Installation von Visual Studio behindern.

1. Geben Sie Speicherplatz frei. Entfernen Sie nicht benötigte Dateien und Anwendungen z.B. mit der Datenträgerbereinigung-App von Ihrem %Systemlaufwerk%.

::: moniker-end

::: moniker range="vs-2019"

1. Informieren Sie sich über die [Systemanforderungen](/visualstudio/releases/2019/system-requirements). Anhand dieser Anforderungen können Sie feststellen, ob Ihr Computer Visual Studio 2019 unterstützt.

1. Laden Sie die aktuellen Windows-Updates herunter. So stellen Sie sicher, dass Ihr Computer sowohl die neuesten Sicherheitsupdates als auch die erforderlichen Systemkomponenten für Visual Studio hat.

1. Starten Sie den Computer neu. Dadurch wird sichergestellt, dass keine ausstehenden Installationen oder Updates die Installation von Visual Studio behindern.

1. Geben Sie Speicherplatz frei. Entfernen Sie nicht benötigte Dateien und Anwendungen z.B. mit der Datenträgerbereinigung-App von Ihrem %Systemlaufwerk%.

::: moniker-end

::: moniker range="vs-2017"

Wenn Sie Fragen zum parallelen Ausführen früherer Versionen von Visual Studio mit Visual Studio 2017 haben, lesen Sie den Abschnitt [Kompatibilität mit vorherigen Versionen](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

::: moniker-end

::: moniker range="vs-2019"

Informationen zur parallelen Ausführung vorheriger Versionen von Visual Studio und Visual Studio 2019 finden Sie auf der Seite [Visual Studio 2019 – Zielplattformen und Kompatibilität](/visualstudio/releases/2019/compatibility/).

::: moniker-end

## <a name="step-2---download-visual-studio"></a>Schritt 2: Herunterladen von Visual Studio

Laden Sie danach die Visual Studio-Bootstrapperdatei herunter.

::: moniker range="vs-2017"

Informationen zum Herunterladen eines Bootstrappers für Visual Studio 2017 finden Sie auf der Downloadseite für [frühere Versionen von Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/).

::: moniker-end

::: moniker range="vs-2019"

Klicken Sie zu diesem Zweck auf die folgende Schaltfläche, wählen Sie die gewünschte Edition von Visual Studio aus, und klicken Sie dann auf **Speichern** und **Ordner öffnen**.

 > [!div class="button"]
 > [Herunterladen von Visual Studio](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="step-3---install-the-visual-studio-installer"></a>Schritt 3: Installieren des Visual Studio-Installers

Führen Sie die Bootstrapperdatei aus, um den Visual Studio-Installer zu installieren. Dieses neue, schlanke Installationsprogramm enthält alle Elemente, die Sie zum Installieren und Anpassen von Visual Studio benötigen.

1. Doppelklicken Sie in Ihrem Ordner **Downloads** auf die Bootstrapperdatei, die einer der folgenden Dateien entspricht oder ähnelt:

   * **vs_community.exe** für Visual Studio Community
   * **vs_professional.exe** für Visual Studio Professional
   * **vs_enterprise.exe** für Visual Studio Enterprise

   Wenn eine Benachrichtigung der Benutzerkontensteuerung angezeigt wird, klicken Sie auf **Ja**.

2. Sie werden gebeten, die Microsoft-[Lizenzbedingungen](https://visualstudio.microsoft.com/license-terms/) und die Microsoft-[Datenschutzbestimmungen](https://privacy.microsoft.com/privacystatement) zu akzeptieren. Klicken Sie auf **Weiter**.

   ![Lizenzbedingungen und Datenschutzbestimmungen](media/privacy-and-license-terms.png "Microsoft-Lizenzbedingungen und -Datenschutzbestimmungen")

## <a name="step-4---choose-workloads"></a>Schritt 4: Auswählen von Workloads

Nach der Installation des Installers können Sie diesen zum Anpassen Ihrer Installation verwenden, indem Sie die Features – oder Arbeitsauslastungen – auswählen, die Sie wünschen. Gehen Sie folgendermaßen vor:

 ::: moniker range="vs-2017"

1. Suchen Sie die gewünschten Workloads im **Visual Studio-Installer**.

   ![Visual Studio 2017: Workload installieren](../install/media/vs-installer-installing-workloads.png)

     Wählen Sie beispielsweise die Workload „.NET Desktopentwicklung“ aus. Sie wird mit dem standardmäßigen Kern-Editor bereitgestellt, der die grundlegende Codebearbeitung für über 20 Sprachen, die Möglichkeit, Code aus einem beliebigen Ordner heraus zu öffnen und zu bearbeiten, ohne dass ein Projekt erforderlich ist, und die integrierte Quellcodekontrolle unterstützt.

1. Nachdem Sie die gewünschten Workloads ausgewählt haben, klicken Sie auf **Installieren**.

    Als Nächstes werden Statusbildschirme angezeigt, die über den Fortschritt der Installation von Visual Studio informieren.

 ::: moniker-end

::: moniker range="vs-2019"

1. Suchen Sie die gewünschten Workloads im **Visual Studio-Installer**.

   ![Visual Studio 2019: Workload installieren](../install/media/vs-2019/vs-installer-workloads.png)

     Wählen Sie beispielsweise die Workload „ASP.NET und Webentwicklung“ aus. Sie wird mit dem standardmäßigen Kern-Editor bereitgestellt, der die grundlegende Codebearbeitung für über 20 Sprachen, die Möglichkeit, Code aus einem beliebigen Ordner heraus zu öffnen und zu bearbeiten, ohne dass ein Projekt erforderlich ist, und die integrierte Quellcodekontrolle unterstützt.

1. Nachdem Sie die gewünschten Workloads ausgewählt haben, klicken Sie auf **Installieren**.

    Als Nächstes werden Statusbildschirme angezeigt, die über den Fortschritt der Installation von Visual Studio informieren.

 ::: moniker-end

> [!TIP]
> Nach der Installation können Sie jederzeit die Installation von Workloads oder Komponenten nachholen. Wenn Sie Visual Studio geöffnet haben, navigieren Sie zu **Extras** > **Tools und Features abrufen…** . Dadurch wird der Visual Studio-Installer geöffnet. Öffnen Sie den **Visual Studio-Installer** alternativ über das Startmenü. Nun können Sie die Workloads oder Komponenten auswählen, die Sie installieren möchten. Klicken Sie anschließend auf **Ändern**.

## <a name="step-5---choose-individual-components-optional"></a>Schritt 5: Auswählen einzelner Komponenten (optional)

Wenn Sie nicht das Feature für Workloads verwenden möchten, um Ihre Visual Studio-Installation anzupassen, oder Sie mehr Komponenten hinzufügen möchten, als von einer Workload installiert werden, können Sie individuelle Komponenten über die Registerkarte **Einzelne Komponenten** installieren bzw. hinzufügen. Wählen Sie die gewünschten Komponenten aus, und führen Sie dann die Anweisungen aus.

::: moniker range="vs-2017"

  ![Visual Studio 2017 – Installieren einzelner Komponenten](media/vs-installer-installing-components.png "Installieren einzelner Komponenten von Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019 – Installieren einzelner Komponenten](media/vs-2019/vs-installer-individual-components.png "Installieren einzelner Komponenten von Visual Studio")

::: moniker-end

## <a name="step-6---install-language-packs-optional"></a>Schritt 6: Installieren von Language Packs (optional)

Standardmäßig versucht das Installationsprogramm bei der ersten Ausführung die Sprache des Betriebssystems zu verwenden. Zum Installieren von Visual Studio in einer Sprache Ihrer Wahl klicken Sie im Visual Studio-Installer auf die Registerkarte **Sprachpakete**, und folgen Sie dann den Anweisungen.

::: moniker range="vs-2017"

  ![Visual Studio 2017 – Installieren von Sprachpaketen](media/vs-installer-installing-language-packs.png "Installieren von Visual Studio-Sprachpaketen")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019 – Installieren von Sprachpaketen](media/vs-2019/vs-installer-language-packs.png "Installieren von Visual Studio-Sprachpaketen")

::: moniker-end

### <a name="change-the-installer-language-from-the-command-line"></a>Ändern der Installersprache über die Befehlszeile

Eine andere Möglichkeit zum Ändern der Standardsprache ist die Ausführung des Installers über die Befehlszeile. Mit dem Befehl `vs_installer.exe --locale en-US` können Sie z.B. erzwingen, dass das Installationsprogramm auf Englisch ausgeführt wird. Das Installationsprogramm speichert diese Einstellung für zukünftige Ausführungen. Der Installer unterstützt die folgenden Sprachtoken: zh-CN, zh-TW, cs-CZ, en-US, es-ES, fr-FR, de-DE, it-IT, ja-JP, ko-KR, pl-PL, pt-BR, ru-RU und tr-TR.

## <a name="step-7---select-the-installation-location-optional"></a>Schritt 7: Auswählen des Installationspfads (optional)

::: moniker range="vs-2017"

**Neues in 15.7:** Der Installationsspeicherbedarf für Visual Studio auf dem Systemlaufwerk kann reduziert werden. Sie können den Downloadcache, freigegebene Komponenten, SDKs und Tools auf andere Datenträger verschieben, und Visual Studio dort belassen, wo es am schnellsten ausgeführt werden kann.

  ![Visual Studio 2017 – Ändern der Installationspfade](media/installation-options-by-location.png "Ändern des Installationspfads")

::: moniker-end

::: moniker range="vs-2019"

Sie können den Speicherbedarf für die Installation von Visual Studio auf Ihrem Systemlaufwerk reduzieren. Sie können den Downloadcache, freigegebene Komponenten, SDKs und Tools auf andere Datenträger verschieben, und Visual Studio dort belassen, wo es am schnellsten ausgeführt werden kann.

  ![Visual Studio 2019 – Auswählen der Installationspfade](media/vs-2019/vs-installer-installation-locations.png "Auswählen des Installationspfads")

::: moniker-end

> [!IMPORTANT]
> Sie können nur bei der ersten Installation von Visual Studio ein anderes Laufwerk auswählen. Wenn Sie Visual Studio bereits installiert haben und das Laufwerk wechseln möchten, müssen Sie Visual Studio deinstallieren und anschließend neu installieren.

Weitere Informationen finden Sie auf der Seite [Auswählen der Installationspfade in Visual Studio](change-installation-locations.md).

## <a name="step-8---start-developing"></a>Schritt 8: Mit dem Entwickeln beginnen

::: moniker range="vs-2017"

1. Klicken Sie nach Abschluss der Visual Studio-Installation auf **Starten**, um mit dem Programmieren in Visual Studio zu beginnen.

2. Klicken Sie auf **Datei**, und wählen Sie dann **Neues Projekt** aus.

3. Wählen Sie einen neuen Projekttyp aus.

   Wenn Sie beispielsweise [eine C++-App erstellen](/cpp/get-started/tutorial-console-cpp) möchten, wählen Sie **Installiert** aus, erweitern Sie **Visual C++** , und wählen Sie dann den C++-Projekttyp aus, den Sie erstellen möchten.

   Klicken Sie zum [Erstellen einer C#-App](../get-started/csharp/tutorial-console.md) auf **Installiert**, erweitern Sie **Visual C#** , und wählen Sie dann den C#-Projekttyp aus, den Sie erstellen möchten.

::: moniker-end

::: moniker range="vs-2019"

1. Klicken Sie nach Abschluss der Visual Studio-Installation auf **Starten**, um mit dem Programmieren in Visual Studio zu beginnen.

1. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

1. Geben Sie den Typ von App im Suchfeld ein, den Sie erstellen möchten, um eine Liste der verfügbaren Vorlagen anzuzeigen. Die Liste der Vorlagen basiert auf den Workloads, die Sie bei der Installation ausgewählt haben. Wählen Sie andere Workloads aus, um andere Vorlagen anzuzeigen.

   Sie können die Suchergebnisse nach bestimmten Programmiersprachen filtern, indem Sie die Dropdownliste **Sprache** verwenden. Sie können außerdem die Listen **Plattform** und **Projekttyp** zum Filtern verwenden.

1. Ihr neues Projekt wird dann in Visual Studio geöffnet, und Sie können damit anfangen, Code zu schreiben.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Visual Studio aktualisieren](update-visual-studio.md)
* [Ändern von Visual Studio](modify-visual-studio.md)
* [Deinstallieren von Visual Studio](uninstall-visual-studio.md)
* [Erstellen einer Offlineinstallation von Visual Studio](create-an-offline-installation-of-visual-studio.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Installieren von Visual Studio für Mac](/visualstudio/mac/installation)
 