---
title: Administratorhandbuch für Visual Studio
titleSuffix: ''
description: Erfahren Sie mehr zur Bereitstellung von Visual Studio in einer Unternehmensumgebung.
ms.date: 07/29/2020
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ecf1dc0332a023a67f2627d852ee56a092830b7e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935611"
---
# <a name="visual-studio-administrator-guide"></a>Administratorhandbuch für Visual Studio

In Unternehmensumgebungen stellen Systemadministratoren Installationen für Endbenutzer in der Regel über eine Netzwerkfreigabe oder mithilfe von Systemverwaltungssoftware bereit. Wir haben die Visual Studio-Setup-Engine so gestaltet, dass sie die unternehmensweite Bereitstellung unterstützt. Systemadministratoren können einen Speicherort für die Netzwerkinstallation erstellen, Standardwerte für die Installation vorkonfigurieren, Product Keys während des Installationsvorgangs bereitstellen und nach erfolgreicher Einführung Produktupdates verwalten.

Dieses Handbuch für Administratoren bietet vom jeweiligen Szenario abhängige Anleitungen für die Unternehmensbereitstellung in Netzwerkumgebungen.

## <a name="before-you-begin"></a>Vorbereitungen

Bevor Sie Visual Studio in Ihrem Unternehmen bereitstellen, müssen Sie einige Entscheidungen treffen und folgende Aufgaben abschließen:

::: moniker range="vs-2019"

* Sicherstellen, dass jeder Zielcomputer die [minimalen Installationsanforderungen](/visualstudio/releases/2019/system-requirements/) erfüllt.

* Ihren Wartungsbedarf ermitteln

  Wenn Ihr Unternehmen einen Funktionssatz länger behalten, aber regelmäßige Wartungsupdates erhalten möchten, sollten Sie eine Wartungsbaseline verwenden. Weitere Informationen finden Sie im Abschnitt ***Supportoptionen für Enterprise- und Professional-Kunden*** der Seite [Produktlebenszyklus und Wartung in Visual Studio](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers) sowie auf der Seite [Aktualisieren von Visual Studio innerhalb einer Baseline für die Wartung](update-servicing-baseline.md).

  Wenn Sie Wartungsupdates zusammen mit kumulativen Funktionsupdates anwenden möchten, können Sie die neuesten Bits auswählen.

* Ein Aktualisierungsmodell festlegen

  Wo sollen einzelne Clientcomputer Updates abrufen? Entscheiden Sie insbesondere, ob Sie Updates aus dem Internet oder von einer lokalen Unternehmensfreigabe abrufen möchten. Wenn Sie die lokale Freigabe wählen, müssen Sie entscheiden, ob einzelne Benutzer ihre eigenen Clients aktualisieren können oder ob ein Administrator die Clients programmgesteuert aktualisieren sollen.

  Es ist möglich, ein Layout für die Netzwerkinstallation von Visual Studio mit den neuesten Produktupdates zu aktualisieren, sodass es sowohl als Installationspfad für das neueste Update von Visual Studio als auch zum Warten von Installationen verwendet werden kann, die bereits auf Clientarbeitsstationen bereitgestellt wurden. Weitere Informationen finden Sie unter [Aktualisieren einer netzwerkbasierten Installation von Visual Studio](../install/update-a-network-installation-of-visual-studio.md).

  Für Computer, die nicht mit dem Internet verbunden sind, ist das Erstellen eines minimalen Layouts die einfachste und schnellste Möglichkeit, Ihre Offlineinstanzen in Visual Studio zu aktualisieren. Weitere Informationen finden Sie unter [Aktualisieren von Visual Studio mit einem minimalen Offlinelayout](update-minimal-layout.md).

* Entscheiden, welche [Workloads und Komponenten](workload-and-component-ids.md?view=vs-2019&preserve-view=true) Ihr Unternehmen benötigt

* Entscheiden, ob Sie eine [Antwortdatei](automated-installation-with-response-file.md?view=vs-2019&preserve-view=true) verwenden (die die Verwaltung von Informationen in der Skriptdatei vereinfacht)

* Entscheiden, ob Sie die Gruppenrichtlinie aktivieren und Visual Studio konfigurieren möchten, um Kundenfeedback auf einzelnen Computern zu deaktivieren

::: moniker-end

::: moniker range="vs-2017"

* Sicherstellen, dass jeder Zielcomputer die [minimalen Installationsanforderungen](/visualstudio/productinfo/vs2017-system-requirements-vs/) erfüllt

* Ihren Wartungsbedarf ermitteln

  Wenn Ihr Unternehmen einen Funktionssatz länger behalten, aber regelmäßige Wartungsupdates erhalten möchten, sollten Sie eine Wartungsbaseline verwenden. Weitere Informationen finden Sie im Abschnitt ***Support für ältere Versionen von Visual Studio*** der Seite [Produktlebenszyklus und Wartung in Visual Studio](/visualstudio/releases/2019/servicing#support-for-older-versions-of-visual-studio) sowie auf der Seite [Aktualisieren von Visual Studio innerhalb einer Baseline für die Wartung](update-servicing-baseline.md).

  Wenn Sie Wartungsupdates zusammen mit kumulativen Funktionsupdates anwenden möchten, können Sie die neuesten Bits auswählen.

* Ein Aktualisierungsmodell festlegen

  Wo sollen einzelne Clientcomputer Updates abrufen? Entscheiden Sie insbesondere, ob Sie Updates aus dem Internet oder von einer lokalen Unternehmensfreigabe abrufen möchten. Wenn Sie die lokale Freigabe wählen, müssen Sie entscheiden, ob einzelne Benutzer ihre eigenen Clients aktualisieren können oder ob ein Administrator die Clients programmgesteuert aktualisieren sollen.

  Es ist möglich, ein Layout für die Netzwerkinstallation von Visual Studio mit den neuesten Produktupdates zu aktualisieren, sodass es sowohl als Installationspfad für das neueste Update von Visual Studio als auch zum Warten von Installationen verwendet werden kann, die bereits auf Clientarbeitsstationen bereitgestellt wurden. Weitere Informationen finden Sie unter [Aktualisieren einer netzwerkbasierten Installation von Visual Studio](../install/update-a-network-installation-of-visual-studio.md).

  Für Computer, die nicht mit dem Internet verbunden sind, ist das Erstellen eines minimalen Layouts die einfachste und schnellste Möglichkeit, Ihre Offlineinstanzen in Visual Studio zu aktualisieren. Weitere Informationen finden Sie unter [Aktualisieren von Visual Studio mit einem minimalen Offlinelayout](update-minimal-layout.md).

* Entscheiden, welche [Workloads und Komponenten](workload-and-component-ids.md?view=vs-2017&preserve-view=true) Ihr Unternehmen benötigt

* Entscheiden, ob Sie eine [Antwortdatei](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true) verwenden (die die Verwaltung von Informationen in der Skriptdatei vereinfacht)

* Entscheiden, ob Sie die Gruppenrichtlinie aktivieren und Visual Studio konfigurieren möchten, um Kundenfeedback auf einzelnen Computern zu deaktivieren

::: moniker-end

::: moniker range="vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>Schritt 1: Herunterladen von Visual Studio-Produktdateien

* [Wählen Sie die Workloads und Komponenten](workload-and-component-ids.md?view=vs-2019&preserve-view=true) aus, die Sie installieren möchten.

* [Erstellen Sie eine Netzwerkfreigabe für die Visual Studio-Produktdateien](create-a-network-installation-of-visual-studio.md?view=vs-2019&preserve-view=true).

## <a name="step-2---build-an-installation-script"></a>Schritt 2: Erstellen eines Installationsskripts

* Erstellen Sie ein Installationsskript, das [Befehlszeilenparameter](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) zum Steuern der Installation verwendet.

  >[!NOTE]
  > Sie können Skripts vereinfachen, indem Sie eine [Antwortdatei](automated-installation-with-response-file.md?view=vs-2019&preserve-view=true) verwenden. Erstellen Sie eine Antwortdatei, die Ihre Standardinstallationsoption enthält.

* (Optional) [Wenden Sie einen Volumenlizenz-Produktschlüssel](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019&preserve-view=true) als Teil des Installationsskripts, damit Benutzer die Software nicht separat aktivieren müssen.

* (Optional) Aktualisieren Sie das Netzwerklayout, [um zu steuern, wann und von wo Produktupdates an Ihre Endbenutzer übermittelt werden](controlling-updates-to-visual-studio-deployments.md?view=vs-2019&preserve-view=true).

* (Optional) Legen Sie Registrierungsrichtlinien fest, die Auswirkungen auf die Bereitstellung von Visual Studio haben – z. B. darüber, wo Pakete, die für andere Versionen oder Instanzen freigegeben wurden, installiert werden, [wo Pakete zwischengespeichert werden](disable-or-move-the-package-cache.md?view=vs-2019&preserve-view=true) oder[ ob Pakete zwischengespeichert werden](set-defaults-for-enterprise-deployments.md?view=vs-2019&preserve-view=true).

* (Optional) Legen Sie die Gruppenrichtlinie fest. Sie können auch [Visual Studio konfigurieren, um Kundenfeedback auf einzelnen Computern zu deaktivieren](../ide/visual-studio-experience-improvement-program.md).

## <a name="step-3---deploy"></a>Schritt 3: Bereitstellen

* Führen Sie mit Ihrer gewünschten Bereitstellungstechnologie Ihr Skript auf den Entwicklerarbeitsstationen aus.

## <a name="step-4---deploy-updates"></a>Schritt 4: Bereitstellen von Updates

* [Aktualisieren Sie den Netzwerkspeicherort mit den neuesten Updates](update-a-network-installation-of-visual-studio.md?view=vs-2019&preserve-view=true) für Visual Studio durch regelmäßiges Ausführen des Befehls, den Sie in Schritt 1 verwendet haben, um aktualisierte Komponenten hinzuzufügen.

  Sie können Visual Studio mit einem Updateskript aktualisieren. Verwenden Sie hierzu den Befehlszeilenparameter „[`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true)“.

## <a name="step-5---optional-use-visual-studio-tools"></a>Schritt 5: (Optional) Verwenden von Visual Studio-Tools

Wir haben mehrere Tools zur Verfügung gestellt, mit denen Sie [installierte Instanzen von Visual Studio auf Clientcomputern erkennen und verwalten](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true) können:

## <a name="advanced-configuration"></a>Erweiterte Konfiguration

Standardmäßig ist bei der Installation von Visual Studio die Einbeziehung von benutzerdefinierten Typen in die Bing-Suche anhand der F1-Fehlerliste und von Codelinks aktiviert. Sie können Visual Studio so konfigurieren, dass die Einbeziehung von benutzerdefinierten Benutzertypen in den Suchmechanismus deaktiviert wird. Ändern Sie hierzu den Wert des folgenden Registrierungsschlüssels nach Richtlinie:

**„PutCustomTypeInBingSearch“ DWORD 0**

Die Registrierung befindet sich in Ihrer privaten Registrierungsstruktur im Verzeichnis *Software\Microsoft\VisualStudio\16.0_{InstanceId}\Roslyn\Internal\Diagnostics\*. Anweisungen zum Öffnen der Registrierungsstruktur finden Sie unter [Bearbeiten der Registrierung einer Visual Studio-Instanz](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>Schritt 1: Herunterladen von Visual Studio-Produktdateien

* [Wählen Sie die Workloads und Komponenten](workload-and-component-ids.md?view=vs-2017&preserve-view=true) aus, die Sie installieren möchten.

* [Erstellen Sie eine Netzwerkfreigabe für die Visual Studio-Produktdateien](create-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true).

## <a name="step-2---build-an-installation-script"></a>Schritt 2: Erstellen eines Installationsskripts

* Erstellen Sie ein Installationsskript, das [Befehlszeilenparameter](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017&preserve-view=true) zum Steuern der Installation verwendet.

  >[!NOTE]
  > Sie können Skripts vereinfachen, indem Sie eine [Antwortdatei](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true) verwenden. Erstellen Sie eine Antwortdatei, die Ihre Standardinstallationsoption enthält.

* (Optional) [Wenden Sie einen Volumenlizenz-Produktschlüssel](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017&preserve-view=true) als Teil des Installationsskripts, damit Benutzer die Software nicht separat aktivieren müssen.

* (Optional) Aktualisieren Sie das Netzwerklayout, [um zu steuern, wann und von wo Produktupdates an Ihre Endbenutzer übermittelt werden](controlling-updates-to-visual-studio-deployments.md?view=vs-2017&preserve-view=true).

* (Optional) Legen Sie Registrierungsrichtlinien fest, die Auswirkungen auf die Bereitstellung von Visual Studio haben – z. B. darüber, wo Pakete, die für andere Versionen oder Instanzen freigegeben wurden, installiert werden, [wo Pakete zwischengespeichert werden](disable-or-move-the-package-cache.md?view=vs-2017&preserve-view=true) oder[ ob Pakete zwischengespeichert werden](set-defaults-for-enterprise-deployments.md?view=vs-2019&preserve-view=true).

* (Optional) Legen Sie die Gruppenrichtlinie fest. Sie können auch [Visual Studio konfigurieren, um Kundenfeedback auf einzelnen Computern zu deaktivieren](../ide/visual-studio-experience-improvement-program.md).

## <a name="step-3---deploy"></a>Schritt 3: Bereitstellen

* Führen Sie mit Ihrer gewünschten Bereitstellungstechnologie Ihr Skript auf den Entwicklerarbeitsstationen aus.

## <a name="step-4---deploy-updates"></a>Schritt 4: Bereitstellen von Updates

* [Aktualisieren Sie den Netzwerkspeicherort mit den neuesten Updates](update-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true) für Visual Studio durch regelmäßiges Ausführen des Befehls, den Sie in Schritt 1 verwendet haben, um aktualisierte Komponenten hinzuzufügen.

  Sie können Visual Studio mit einem Updateskript aktualisieren. Verwenden Sie hierzu den Befehlszeilenparameter „[`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true)“.

## <a name="step-5---optional-use-visual-studio-tools"></a>Schritt 5: (Optional) Verwenden von Visual Studio-Tools

Wir haben mehrere Tools zur Verfügung gestellt, mit denen Sie [installierte Instanzen von Visual Studio auf Clientcomputern erkennen und verwalten](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true) können:

## <a name="advanced-configuration"></a>Erweiterte Konfiguration

Standardmäßig ist bei der Installation von Visual Studio die Einbeziehung von benutzerdefinierten Typen in die Bing-Suche anhand der F1-Fehlerliste und von Codelinks aktiviert. Sie können Visual Studio so konfigurieren, dass die Einbeziehung von benutzerdefinierten Benutzertypen in den Suchmechanismus deaktiviert wird. Ändern Sie hierzu den Wert des folgenden Registrierungsschlüssels nach Richtlinie:

**„PutCustomTypeInBingSearch“ DWORD 0**

Die Registrierung befindet sich in Ihrer privaten Registrierungsstruktur im Verzeichnis *Software\Microsoft\VisualStudio\15.0_{InstanceId}\Roslyn\Internal\Diagnostics\*. Anweisungen zum Öffnen der Registrierungsstruktur finden Sie unter [Bearbeiten der Registrierung einer Visual Studio-Instanz](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Beispiele für Befehlszeilenparameter](command-line-parameter-examples.md)
* [Installieren der für eine Offlineinstallation von Visual Studio erforderlichen Zertifikate](install-certificates-for-visual-studio-offline.md)
* [Importieren oder Exportieren von Installationskonfigurationen](import-export-installation-configurations.md)
* [Archive zum Setup von Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/)
* [Projektlebenszyklus und Wartung in Visual Studio](/visualstudio/releases/2019/servicing/)
* [Einstellungen für synchrones automatisches Laden](../extensibility/synchronously-autoloaded-extensions.md)
