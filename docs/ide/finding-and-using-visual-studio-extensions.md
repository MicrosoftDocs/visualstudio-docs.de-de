---
title: Finden und Installieren von Erweiterungen
description: Informieren Sie sich über die Erweiterungen in Visual Studio und deren Verwaltung, damit Sie über alle Steuerelemente, Beispiele, Vorlagen, Tools und andere Komponenten verfügen, die Sie benötigen.
ms.custom: SEO-VS-2020
ms.date: 09/18/2019
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bb088954833f42e35de6c8316e5553d0f9e3fc68
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945590"
---
# <a name="manage-extensions-for-visual-studio"></a>Verwalten von Erweiterungen für Visual Studio

Erweiterungen sind Codepakete, die innerhalb von Visual Studio ausgeführt werden und neue oder verbesserte Features bereitstellen. Bei Erweiterungen kann es sich um Steuerelemente, Beispiele, Vorlagen, Tools oder andere Komponenten handeln, die Funktionen zu Visual Studio hinzufügen, z. B. [Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsls-vs) oder [Visual Studio IntelliCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.VSIntelliCode).

Informationen zum Erstellen von Visual Studio-Erweiterungen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Informationen zur Verwendung von Erweiterungen finden Sie auf den individuellen Erweiterungsseiten im [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker range="vs-2017"

## <a name="extensions-and-updates-dialog-box"></a>Dialogfeld „Erweiterungen und Updates“

Verwenden Sie das Dialogfeld **Erweiterungen und Updates**, um Visual Studio-Erweiterungen zu installieren und zu verwalten. Wählen Sie **Extras** > **Erweiterungen und Updates** aus, oder geben Sie **Erweiterungen** in das Suchfeld **Schnellstart** ein, um das Dialogfeld **Erweiterungen und Updates** zu öffnen.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="manage-extensions-dialog-box"></a>Dialogfeld „Erweiterungen verwalten“

Verwenden Sie das Dialogfeld **Erweiterungen verwalten**, um Visual Studio-Erweiterungen zu installieren und zu verwalten. Wählen Sie **Erweiterungen** > **Erweiterungen verwalten** aus, um das Dialogfeld **Erweiterungen verwalten** zu öffnen. Geben Sie alternativ im Suchfeld **Erweiterungen** ein, und wählen Sie **Erweiterungen verwalten** aus.

::: moniker-end

![Fenster „Erweiterungen“ in Visual Studio](media/finding-using-visual-studio-extensions/extensions-and-updates.png)

Im linken Bereich werden die Erweiterungen nach installierten Erweiterungen, im Visual Studio Marketplace (**Online**) verfügbaren Erweiterungen und Erweiterungen, für die Updates verfügbar sind, kategorisiert. Der **Roaming-Erweiterungs-Manager** enthält eine Liste aller Visual Studio-Erweiterungen, die Sie auf jeglichen Computern oder Instanzen von Visual Studio installiert haben. Er ist dazu konzipiert, dass Sie Ihre bevorzugten Erweiterungen einfacher finden können.

## <a name="find-and-install-extensions"></a>Finden und Installieren von Erweiterungen

::: moniker range="vs-2017"

Sie können Erweiterungen über den [Visual Studio Marketplace](https://marketplace.visualstudio.com) oder über das Dialogfeld „Erweiterungen und Updates“ in Visual Studio installieren.

So installieren Sie Erweiterungen innerhalb von Visual Studio:

1. Suchen Sie in **Tools** > **Erweiterungen und Updates** nach der Erweiterung, die Sie installieren möchten. Wenn Sie den Namen der Erweiterung oder einen Teil des Namens kennen, können Sie im Fenster **Suche** nach ihr suchen.

2. Wählen Sie **Download** aus.

   Die Erweiterung wird der Warteschlange für die Installation hinzugefügt. Die Erweiterung wird installiert, sobald alle Instanzen von Visual Studio geschlossen wurden.

Wenn Sie versuchen, eine Erweiterung zu installieren, die Abhängigkeiten enthält, wird vom Installationsprogramm überprüft, ob diese bereits installiert sind. Sind sie nicht installiert, werden im Dialogfeld **Erweiterungen und Updates** die vor der Installation der Erweiterung zu installierenden Abhängigkeiten aufgeführt.

### <a name="install-without-using-the-extensions-and-updates-dialog-box"></a>Installieren ohne das Dialogfeld „Erweiterungen und Updates“

Erweiterungen, die in *VSIX-Dateien* gepackt wurden, sind möglicherweise an anderen Orten als Visual Studio Marketplace verfügbar. Diese Dateien können mit dem Dialogfeld **Tools** > **Erweiterungen und Updates** nicht erkannt werden. Sie können eine *VSIX*-Datei jedoch installieren, indem Sie auf die Datei doppelklicken oder sie auswählen und die **EINGABETASTE** drücken. Befolgen Sie dann die angezeigten Anweisungen. Wenn die Erweiterung installiert ist, können Sie das Dialogfeld **Erweiterungen und Updates** zum Aktivieren, Deaktivieren oder Deinstallieren der Erweiterung verwenden.

> [!NOTE]
> - Visual Studio Marketplace enthält sowohl VSIX- als auch MSI-Erweiterungen. Über das Dialogfeld „Erweiterungen und Updates“ können MSI-basierte Erweiterungen nicht aktiviert oder deaktiviert werden.
> - Wenn eine MSI-basierte Erweiterung eine *extension.vsixmanifest-Datei* enthält, wird die Erweiterung im Dialogfeld **Erweiterungen und Updates** angezeigt.

::: moniker-end

::: moniker range=">=vs-2019"

Sie können Erweiterungen über den [Visual Studio Marketplace](https://marketplace.visualstudio.com) oder das Dialogfeld „Erweiterungen verwalten“ in Visual Studio installieren.

So installieren Sie Erweiterungen innerhalb von Visual Studio:

1. Suchen Sie in **Erweiterungen** > **Erweiterungen verwalten** nach der Erweiterung, die Sie installieren möchten. (Wenn Sie den Namen der Erweiterung oder einen Teil des Namens kennen, können Sie im Fenster **Suche** danach suchen.)

2. Wählen Sie **Herunterladen** aus.

   Die Erweiterung wird der Warteschlange für die Installation hinzugefügt. Die Erweiterung wird installiert, sobald alle Instanzen von Visual Studio geschlossen wurden.

Wenn Sie versuchen, eine Erweiterung zu installieren, die Abhängigkeiten enthält, wird vom Installationsprogramm überprüft, ob diese bereits installiert sind. Sind sie nicht installiert, werden im Dialogfeld **Erweiterungen verwalten** die Abhängigkeiten aufgeführt, die vor der Installation der Erweiterung installiert werden müssen.

### <a name="install-without-using-the-manage-extensions-dialog-box"></a>Installieren ohne das Dialogfeld „Erweiterungen verwalten“

Erweiterungen, die in *VSIX-Dateien* gepackt wurden, sind möglicherweise an anderen Orten als Visual Studio Marketplace verfügbar. Diese Dateien werden vom Dialogfeld **Erweiterungen** > **Erweiterungen verwalten** nicht erkannt. Sie können jedoch eine *VSIX*-Datei installieren, indem Sie auf die Datei doppelklicken oder sie auswählen und die **EINGABETASTE** drücken. Befolgen Sie dann die angezeigten Anweisungen. Wenn die Erweiterung installiert ist, können Sie sie über das Dialogfeld **Erweiterungen verwalten** aktivieren, deaktivieren oder deinstallieren.

> [!NOTE]
> - Visual Studio Marketplace enthält sowohl VSIX- als auch MSI-Erweiterungen. Über das Dialogfeld „Erweiterungen verwalten“ können MSI-basierte Erweiterungen nicht aktiviert oder deaktiviert werden.
> - Wenn eine MSI-basierte Erweiterung eine Datei vom Typ *extension.vsixmanifest* enthält, wird die Erweiterung im Dialogfeld **Erweiterungen verwalten** angezeigt.

::: moniker-end

## <a name="uninstall-or-disable-an-extension"></a>Deinstallieren oder Deaktivieren einer Erweiterung

Wenn Sie die Verwendung einer Erweiterung beenden möchten, können Sie diese deaktivieren oder deinstallieren. Beim Deaktivieren einer Erweiterung bleibt sie installiert, wird jedoch nicht geladen. Suchen Sie nach der Erweiterung, und klicken Sie auf **Deinstallieren** oder **Deaktivieren**. Starten Sie Visual Studio neu, um deaktivierte Erweiterungen zu entladen.

> [!NOTE]
> Sie können VSIX-Erweiterungen deaktivieren. Erweiterungen, die mit MSI installiert wurden, können nicht deaktiviert werden. Mit MSI installierte Erweiterungen können nur deinstalliert werden.

## <a name="per-user-and-administrative-extensions"></a>Erweiterungen pro Benutzer und Verwaltungserweiterungen

Die meisten Erweiterungen sind Pro-Benutzer-Erweiterungen und werden im Ordner *%LocalAppData%\Microsoft\VisualStudio\\<Visual Studio-Version>\>\Extensions\\* installiert. Bei einigen Erweiterungen handelt es sich um Verwaltungserweiterungen, und diese werden im Ordner *\<Visual Studio installation folder>\Common7\IDE\Extensions\\* installiert.

Um das System vor Erweiterungen zu schützen, in denen möglicherweise Fehler oder bösartiger Code enthalten ist, können Sie das Laden von Erweiterungen pro Benutzer dahingehend einschränken, dass sie nur geladen werden, wenn Visual Studio mit normalen Benutzerberechtigungen ausgeführt wird. Das bedeutet, dass Pro-Benutzer-Erweiterungen deaktiviert sind, wenn Visual Studio mit erhöhten Rechten ausgeführt wird.

So schränken Sie ein, wann Pro-Benutzer-Erweiterungen geladen werden:

1. Öffnen Sie die Seite mit den Erweiterungsoptionen (**Extras** > **Optionen** > **Umgebung** > **Erweiterungen**).

2. Deaktivieren Sie das Kontrollkästchen **Pro-Benutzer-Erweiterungen bei Ausführung als Administrator laden**.

3. Starten Sie Visual Studio neu.

## <a name="automatic-extension-updates"></a>Automatische Erweiterungsupdates

Erweiterungen werden automatisch aktualisiert, wenn eine neue Version im Visual Studio Marketplace zur Verfügung steht. Die neue Version der Erweiterung wird im Hintergrund erkannt und installiert. Beim nächsten Öffnen von Visual Studio wird die neue Version der Erweiterung ausgeführt.

Wenn Sie automatische Updates deaktivieren möchten, können Sie das Feature für alle Erweiterungen oder nur für bestimmte Erweiterungen deaktivieren.

::: moniker range="vs-2017"

- Wählen Sie zum Deaktivieren von automatischen Updates für alle Erweiterungen den Link **Einstellungen für die Erweiterungen und Updates ändern** im Dialogfeld **Tools** > **Erweiterungen und Updates** aus. Deaktivieren Sie die Option **Erweiterungen automatisch aktualisieren** im Dialogfeld **Optionen**.

- Deaktivieren Sie zum automatischen Deaktivieren einer bestimmten Erweiterung die Option **Diese Extension automatisch aktualisieren** im Detailbereich der Erweiterung auf der rechten Seite des Dialogfelds **Erweiterungen und Updates**.

::: moniker-end

::: moniker range=">=vs-2019"

- Wenn Sie automatische Updates für alle Erweiterungen deaktivieren möchten, wählen Sie den Link **Ändern Sie die Einstellungen für Erweiterungen** im Dialogfeld **Erweiterungen** > **Erweiterungen verwalten** aus. Deaktivieren Sie die Option **Erweiterungen automatisch aktualisieren** im Dialogfeld **Optionen**.

- Wenn Sie automatische Updates für eine bestimmte Erweiterung deaktivieren möchten, deaktivieren Sie im Detailbereich der Erweiterung auf der rechten Seite des Dialogfelds **Erweiterungen verwalten** die Option **Diese Erweiterung automatisch aktualisieren**.

::: moniker-end

## <a name="crash-and-unresponsiveness-notifications"></a>Benachrichtigungen zu abgestürzten und nicht reagierenden Erweiterungen

Sie werden von Visual Studio benachrichtigt, wenn die Vermutung besteht, dass eine Erweiterung während einer vorherigen Sitzung zu einem Absturz beigetragen hat. Wenn Visual Studio abstürzt, speichert das Programm den Ausnahmestapel. Beim nächsten Start von Visual Studio untersucht es den Stapel. Es beginnt dabei auf der Blattebene und arbeitet sich zur Basis herunter. Wenn Visual Studio ermittelt, dass ein Frame zu einem Modul einer installierten und aktivierten Erweiterung gehört, wird eine Benachrichtigung angezeigt.

Visual Studio sendet Ihnen ebenfalls eine Benachrichtigung, wenn eine Erweiterung vermutlich dazu führt, dass die Benutzeroberfläche nicht mehr reagiert.

Sie können diese Benachrichtigung ignorieren oder eine der folgenden Maßnahmen ergreifen:

::: moniker range="vs-2017"

- Wählen Sie **Disable this extension** (Diese Erweiterung deaktivieren) aus. Visual Studio deaktiviert die Erweiterung und informiert Sie, ob Sie Ihr System neu starten müssen, damit die Deaktivierung wirksam wird. Sie können die Erweiterung bei Bedarf im Dialogfeld **Tools** > **Erweiterungen und Updates** erneut aktivieren.

::: moniker-end

::: moniker range=">=vs-2019"

- Wählen Sie **Disable this extension** (Diese Erweiterung deaktivieren) aus. Visual Studio deaktiviert die Erweiterung und informiert Sie, ob Sie Ihr System neu starten müssen, damit die Deaktivierung wirksam wird. Sie können die Erweiterung auf Wunsch im Dialogfeld **Erweiterungen** > **Erweiterungen verwalten** wieder aktivieren.

::: moniker-end

- Klicken Sie auf **Diese Meldung nicht mehr anzeigen**.

  - Wenn sich die Benachrichtigung auf einen Absturz in einer vorherigen Sitzung bezieht, zeigt Visual Studio keine weiteren Benachrichtigungen an, wenn ein Absturz in Zusammenhang mit dieser Erweiterung auftritt. Visual Studio zeigt weiterhin Benachrichtigungen an, wenn eine nicht reagierende Benutzeroberfläche dieser Erweiterung zugeordnet werden kann, oder wenn ein Absturz oder eine nicht reagierende Benutzeroberfläche mit anderen Erweiterungen in Zusammenhang steht.
  - Wenn sich die Benachrichtigung auf eine nicht reagierende Benutzeroberfläche bezieht, zeigt die IDE (integrierte Entwicklungsumgebung) keine Benachrichtigung mehr an, wenn diese Erweiterung mit einer nicht reagierenden Benutzeroberfläche in Zusammenhang steht. Visual Studio zeigt weiterhin absturzbezogene Benachrichtigungen für diese Erweiterung sowie absturzbezogene Benachrichtigungen und Benachrichtigungen zu einer nicht reagierenden Benutzeroberfläche für andere Erweiterungen an.

- Klicken Sie auf **Weitere Informationen**, um diese Seite aufzurufen.

- Wählen Sie die Schaltfläche **X** am Ende der Benachrichtigung aus, um die Benachrichtigung zu schließen. Für künftige Instanzen der Erweiterung in Zusammenhang mit einem Absturz oder einer nicht reagierenden Benutzeroberfläche wird eine neue Benachrichtigung angezeigt.

> [!NOTE]
> Eine nicht reagierende Benutzeroberfläche oder eine Benachrichtigung zu einem Absturz bedeutet nur, dass eines der Erweiterungsmodule sich im Stapel befand, als die Benutzeroberfläche nicht mehr reagierte oder es zum Absturz kam. Es bedeutet nicht unbedingt, dass die Erweiterung selbst die Ursache für den Absturz oder die nicht reagierende Benutzeroberfläche war. Es ist möglich, dass die Erweiterung Code aufgerufen hat, der Teil von Visual Studio ist, was wiederum dazu führte, dass die Erweiterung abgestürzt ist oder nicht reagiert. Allerdings ist die Benachrichtigung möglicherweise trotzdem hilfreich, wenn das Szenario, das zum Absturz oder zu einer nicht reagierenden Benutzeroberfläche geführt hat, nicht wichtig für Sie ist. In diesem Fall verhindert das Deaktivieren der Erweiterung den Absturz oder die fehlende Reaktion der Benutzeroberfläche, ohne Ihre Produktivität zu beeinträchtigen.

## <a name="samples"></a>Proben

Bei Installation eines Onlinebeispiels wird die Projektmappe an zwei Orten gespeichert:

- Eine Arbeitskopie wird an dem Speicherort gespeichert, den Sie beim Erstellen des Projekts angegeben haben.

- Eine separate Masterkopie wird auf dem Computer gespeichert.

::: moniker range="vs-2017"

Im Dialogfeld **Tools** > **Erweiterungen und Updates** können Sie diese beispielbezogenen Aufgaben ausführen:

::: moniker-end

::: moniker range=">=vs-2019"

Im Dialogfeld **Erweiterungen** > **Erweiterungen verwalten** können Sie diese beispielbezogenen Aufgaben ausführen:

::: moniker-end

- Auflisten der Masterkopien der installierten Beispiele

- Deaktivieren oder deinstallieren der Masterkopie eines Beispiels

- Installieren von Beispielpacks, die Auflistungen von Beispielen zu einer Technologie oder Funktion sind

- Installieren individueller Onlinebeispiele

- Anzeigen von Updatebenachrichtigungen, wenn für installierte Quellcodeänderungen Beispiele veröffentlicht werden

- Aktualisieren Sie die Masterkopie eines installierten Beispiels, wenn Sie über ein Update benachrichtigt werden.

## <a name="see-also"></a>Siehe auch

- [Visual Studio Marketplace](https://marketplace.visualstudio.com)
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
