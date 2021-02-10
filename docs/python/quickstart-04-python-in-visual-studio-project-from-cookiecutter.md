---
title: 'Schnellstart: Erstellen von Python-Projekten mit Cookiecutter'
description: In diesem Schnellstart erstellen Sie ein Visual Studio-Projekt für Python mithilfe einer Cookiecutter-Vorlage.
ms.date: 02/25/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 4c8a3727faa01b69962dd3dc456ac7b704f62882
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902434"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Schnellstart: Erstellen eines Projekts aus einer Cookiecutter-Vorlage

Sobald Sie die [Python-Unterstützung in Visual Studio installiert haben](installing-python-support-in-visual-studio.md), können Sie ganz einfach ein neues Projekt aus einer Cookiecutter-Vorlage erstellen. Viele dieser Vorlagen wurden bereits auf GitHub veröffentlicht. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) stellt eine grafische Benutzeroberfläche bereit, auf der Sie Vorlagen ermitteln, Vorlageoptionen eingeben und Projekte und Dateien erstellen können. Die Erweiterung ist im Lieferumfang von Visual Studio 2017 und höher enthalten und kann separat in früheren Versionen von Visual Studio installiert werden.

1. Installieren Sie für diesen Schnellstart zuerst die Python-Verteilung Anaconda3. Sie enthält die erforderlichen Python-Pakete für die hier gezeigte Cookiecutter-Vorlage. Führen Sie den Visual Studio-Installer aus, klicken Sie auf **Ändern**, erweitern Sie rechts die Optionen für **Python-Entwicklung**, und wählen Sie **Anaconda3** aus (32-Bit oder 64-Bit). Die Installation kann je nach Geschwindigkeit Ihres Internets einige Zeit in Anspruch nehmen. Dies ist jedoch der einfachste Weg, die erforderlichen Pakete zu installieren.

1. Starten Sie Visual Studio.

1. Klicken Sie auf **Datei** > **Neu** > **Aus Cookiecutter**. Mit diesem Befehl wird ein Fenster in Visual Studio geöffnet, in dem Sie Vorlagen durchsuchen können.

    ![Neues Projekt aus einer Cookiecutter-Vorlage erstellen](media/projects-from-cookiecutter1.png)

1. Wenn Sie die Vorlage **Microsoft/python-sklearn-classifier-cookiecutter** ausgewählt haben, klicken Sie auf **Weiter**. (Der Prozess kann einige Minuten beanspruchen, wenn Sie eine bestimmte Vorlage zum ersten Mal verwenden, da Visual Studio die erforderlichen Python-Pakete installiert.)

1. Legen Sie als Nächstes über das Feld **Erstellen in** einen Speicherort für das neue Projekt fest, und klicken Sie dann auf **Projekt erstellen und öffnen**.

    ![Zweiter Schritt mit Cookiecutter, Festlegen von Projekteigenschaften](media/projects-from-cookiecutter2.png)

1. Wenn der Prozess abgeschlossen ist, sehen Sie die Meldung **Successfully created files using template...** (Dateien wurden erfolgreich mit der Vorlage erstellt). Das Projekt wird automatisch im Projektmappen-Explorer geöffnet.

1. Drücken Sie **STRG**+**F5**, oder wählen Sie **Debuggen** > **Ohne Debuggen starten** aus, um das Programm auszuführen.

    ![Ausgabe des Vorlagenprojekts „python-sklearn-classifier-cookiecutter“](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Tutorial: Arbeiten mit Python in Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Siehe auch

- [Verwenden der Cookiecutter-Erweiterung](using-python-cookiecutter-templates.md)
- [Manuelles Identifizieren eines vorhandenen Python-Interpreters](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Installieren der Python-Unterstützung für Visual Studio 2015 und früher](installing-python-support-in-visual-studio.md)
- [Installationsspeicherorte](installing-python-support-in-visual-studio.md#install-locations)
