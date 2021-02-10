---
title: 'Tutorial „Python in Visual Studio“, Schritt 5: Installieren von Paketen'
titleSuffix: ''
description: Dies ist Schritt 5 einer grundlegenden Einführung in die Arbeit mit Python in Visual Studio, in dem die Features von Visual Studio zum Verwalten von Paketen in einer Python-Umgebung veranschaulicht werden.
ms.date: 03/09/2020
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c47eacf0c9977e7342bfda17e03ea53728ee9215
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901156"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>Schritt 5: Installieren von Paketen in Ihrer Python-Umgebung

**Vorheriger Schritt: [Ausführen von Code im Debugger](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Die Python-Entwicklercommunity hat Tausende von nützlichen Paketen erzeugt, die Sie in Ihre eigenen Projekte integrieren können. Visual Studio bietet eine Benutzeroberfläche für das Verwalten von Paketen in Ihren Python-Umgebungen.

## <a name="view-environments"></a>Anzeigen von Umgebungen

1. Wählen Sie den Menübefehl **Ansicht** > **Weitere Fenster** > **Python-Umgebungen** aus. Das Fenster **Python-Umgebungen** wird als Peer für den **Projektmappen-Explorer** geöffnet und zeigt die verschiedenen Umgebungen an, die für Sie verfügbar sind. Die Liste enthält die Umgebungen, die Sie mithilfe des Visual Studio-Installationsprogramms installiert haben und die, die Sie separat installiert haben. Dazu gehören globale, virtuelle und Conda-Umgebungen. Die Umgebung in Fettdruck ist die Standardumgebung, die für neue Projekte verwendet wird. Weitere Informationen zur Verwendung von Umgebungen finden Sie unter [Erstellen und Verwalten von Python-Umgebungen in Visual Studio-Umgebungen](managing-python-environments-in-visual-studio.md).

   ![Fenster „Python-Umgebungen“](media/environments/environments-default-view-2019.png)

   > [!NOTE]
   > Sie können das Fenster „Python-Umgebungen“ auch öffnen, indem Sie das Fenster „Projektmappen-Explorer“ auswählen und die Tastenkombination **STRG+K, STRG+`** drücken. Wenn die Tastenkombination nicht funktioniert und Sie das Fenster „Python-Umgebungen“ nicht im Menü finden können, haben Sie die Python-Workload möglicherweise nicht installiert. Anleitungen zum Installieren von Python finden Sie unter [Installieren der Python-Unterstützung in Visual Studio](installing-python-support-in-visual-studio.md).

2. Die Registerkarte **Übersicht** der Umgebung bietet schnellen Zugriff auf ein **interaktives** Fenster für diese Umgebung zusammen mit dem Installationsordner und den Interpretern der Umgebung. Klicken Sie beispielsweise auf **Interaktives Fenster öffnen**, und ein **interaktives** Fenster für diese bestimmte Umgebung wird in Visual Studio angezeigt.

3. Erstellen Sie nun ein Projekt, indem Sie auf **Datei** > **Neu** > **Projekt** klicken und die Vorlage **Python-Anwendung** auswählen. Fügen Sie folgenden Code in die angezeigte Codedatei ein. Dadurch wird eine Kosinuswelle wie in den vorherigen Schritten des Tutorials erstellt, die dieses Mal jedoch grafisch dargestellt wird. Alternativ können Sie das zuvor erstellte Projekt verwenden und den Code darin ersetzen.

    ```python
    from math import radians
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

4. Wenn Sie ein Python-Projekt geöffnet haben, können Sie auch das Fenster „Python-Umgebungen“ öffnen, indem Sie im Projektmappen-Explorer mit der rechten Maustaste auf **Python-Umgebungen** klicken und dann **Alle Python-Umgebungen anzeigen** auswählen.

   ![Umgebung](media/environments/environments-view-all-2019.png)

5. Wenn Sie auf die Import-Anweisungen `numpy` und `matplotlib` zeigen, wird Ihnen auffallen, dass sie nicht aufgelöst wurden. Das liegt daran, dass die Pakete nicht in der globalen Standardumgebung installiert wurden.

   ![Nicht aufgelöste Paketimporte](media/packages-unresolved-import.png)

## <a name="install-packages-using-the-python-environments-window"></a>Installieren von Paketen mithilfe des Fensters „Python-Umgebungen“

1. Wählen Sie im Fenster „Python-Umgebungen“ die Standardumgebung für neue Python-Projekte und dann die Registerkarte **Pakete** aus. Daraufhin wird eine Liste der Pakete angezeigt, die derzeit in der Umgebung installiert sind.

   ![In einer Umgebung installierte Pakete](media/environments/environments-installed-packages-2019.png)

2. Installieren Sie `matplotlib`, indem Sie den Namen in das Suchfeld eingeben und dann die Option **Run command: pip install matplotlib** (Befehl ausführen: pip install matplotlib) auswählen. Dadurch werden `matplotlib` und jegliche Pakete installiert, von denen diese Bibliothek abhängig ist (in diesem Fall wird `numpy` eingeschlossen).

   ![Installieren von matplotlib in der Umgebung](media/environments/environments-add-matplotlib-2019.png)

5. Stimmen Sie zu, wenn Sie zur Erhöhung der Rechte aufgefordert werden.

6. Nachdem das Paket installiert ist, wird es im Fenster der **Python-Umgebung** angezeigt. Über das **X** auf der rechten Seite des Pakets kann dieses deinstalliert werden.

   ![Abschließen der Installation von matplotlib in der Umgebung](media/environments/environments-add-matplotlib2-2019.png)

   > [!NOTE]
   > Unterhalb der Umgebung wird möglicherweise eine kleine Statusanzeige eingeblendet, um darauf hinzuweisen, dass Visual Studio die IntelliSense-Datenbank für neu installierte Pakete erstellt. Die Registerkarte **IntelliSense** zeigt ausführlichere Informationen an. Beachten Sie, dass IntelliSense-Features wie die automatische Vervollständigung und die Syntaxüberprüfung für dieses Paket nicht im Editor aktiv sind, bis die Datenbank vollständig erstellt ist.
   >
   > Ab Visual Studio 2017 Version 15.6 wird eine andere und schnellere Methode für die Arbeit mit IntelliSense verwendet. Auf der Registerkarte **IntelliSense** wird eine Meldung diesbezüglich angezeigt.

## <a name="run-the-program"></a>Ausführen des Programms

1. Da [matplotlib](https://matplotlib.org/) nun installiert ist, führen Sie das Programm mit **F5** oder mit **STRG**+**F5** (ohne Debuggen) aus, um die folgende Ausgabe anzuzeigen:

   ![Ausgabe des matplotlib-Beispiels](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Arbeiten mit Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Ausführlichere Informationen

- [Python-Umgebungen](managing-python-environments-in-visual-studio.md)
- [Informationen zu Django in Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Informationen zu Flask in Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)
