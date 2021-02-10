---
title: 'Schnellstart: Erstellen eines Python-Projekts mithilfe einer Vorlage'
description: In diesem Schnellstart erstellen Sie ein Visual Studio-Projekt für Python mithilfe der integrierten Vorlage für eine einfache Flask-App.
ms.date: 12/06/2018
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 81f337cf3feca517f46632e7fe08a9f5a62cd707
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902453"
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Schnellstart: Erstellen eines Python-Projekts aus einer Vorlage in Visual Studio

Wenn Sie die [Python-Unterstützung in Visual Studio installiert haben](installing-python-support-in-visual-studio.md), können Sie ganz einfach ein neues Python-Projekt mithilfe einer Vielzahl von Vorlagen erstellen. In diesem Schnellstart erstellen Sie eine einfache Flask-Anwendung mit einer Vorlage. Das entstehende Projekt ist so ähnlich wie das Projekt, dass Sie unter [Schnellstart: Erstellen einer Web-App mit Flask](../ide/quickstart-python.md) erstellt haben.

1. Starten Sie Visual Studio.

1. Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**, suchen Sie anschließend im Dialogfeld **Neues Projekt** nach „leeres flask“, wählen Sie dann die Vorlage **Leeres Flask-Webprojekt** aus der mittleren Liste aus, benennen Sie das Projekt, und klicken Sie dann auf **OK**:

    ![Erstellen eines neuen Projekts mit der Vorlage „Leeres Flask-Webprojekt“](media/quickstart-python-06-blank-flask-template.png)

1. Visual Studio zeigt die folgende Aufforderung an: **This project requires external packages.** (Für dieses Projekt sind externe Pakete erforderlich.). Dieses Dialogfeld wird angezeigt, weil die Vorlage eine *requirements.txt*-Datei enthält, die eine Abhängigkeit zu Flask enthält. Visual Studio kann die Pakete automatisch installieren. Sie erhalten die Option, sie in einer *virtuellen Umgebung* zu installieren. Das Verwenden einer virtuellen Umgebung ist der Installation in einer globalen Umgebung vorzuziehen. Wählen Sie deshalb **Install into a virtual environment** (In einer virtuellen Umgebung installieren), um fortzufahren.

    ![Flask in einer virtuellen Umgebung installieren](media/quickstart-python-07-install-into-virtual-environment.png)

1. Visual Studio zeigt das Dialogfeld **Virtuelle Umgebung hinzufügen** an. Übernehmen Sie die Standardeinstellungen, und klicken Sie auf **Erstellen**. Stimmen Sie etwaigen Anforderungen von Rechteerweiterungen zu.

    > [!Tip]
    > Wenn Sie mit einem neuen Projekt beginnen, wird dringend empfohlen, zu Beginn eine virtuelle Umgebung zu erstellen. Dazu werden Sie auch von den meisten Visual Studio-Vorlagen aufgefordert. Virtuelle Umgebungen behalten die genauen Anforderungen Ihres Projekts im Laufe der Zeit bei, wenn Bibliotheken hinzugefügt und entfernt werden. Dann können Sie mühelos eine *requirements.txt*-Datei erstellen, die Sie zur erneuten Installation dieser Abhängigkeiten auf anderen Entwicklungscomputern verwenden können (wie bei der Quellcodeverwaltung). Außerdem können Sie diese Datei verwenden, wenn Sie das Projekt auf einem Produktionsserver bereitstellen. Weitere Informationen zu virtuellen Umgebungen und deren Vorzügen finden Sie in den Artikeln [Verwenden von virtuellen Umgebungen](../python/selecting-a-python-environment-for-a-project.md#use-virtual-environments) und [Verwalten von erforderlichen Paketen mit „requirements.txt“](../python/managing-required-packages-with-requirements-txt.md).

1. Nachdem Visual Studio diese Umgebung erstellt hat, sehen Sie im **Projektmappen-Explorer** neben *requirements.txt* auch eine *app.py*-Datei. Öffnen Sie *app.py*. Dann sehen Sie, dass die Vorlage Code bereitgestellt hat, der dem unter [Schnellstart: Erstellen einer Web-App mit Flask](../ide/quickstart-python.md) ähnelt. Er enthält nur einige zusätzliche Bereiche. Der gesamte, unten angezeigte Code wird von der Vorlage erstellt. Sie müssen daher nichts selbst in *app.py* einfügen.

    Der Code beginnt mit den erforderlichen Importvorgängen:

    ```python
    from flask import Flask
    app = Flask(__name__)
    ```

    Darauf folgt diese Zeile, die beim Bereitstellen einer App auf einem Webhost nützlich sein kann:

    ```python
    wsgi_app = app.wsgi_app
    ```

    Anschließend kommt das Decorator-Element der Route als einfache Funktion, die eine Ansicht definiert:

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

    Aufgrund des abschließenden Startcodes können Sie Host und Port anhand von Umgebungsvariablen festlegen, statt sie hartzucodieren. Mit derartigem Code können Sie die Konfiguration auf Entwicklungs- und Produktionscomputern steuern, ohne den Code ändern zu müssen:

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. Klicken Sie auf **Debuggen** > **Ohne Debuggen starten**, um das Programm auszuführen und `localhost:5555` in einem Browser zu öffnen.

**Frage: Welche anderen Python-Vorlagen werden von Visual Studio bereitgestellt?**

**Antwort:** Wenn die Python-Workload installiert ist, stellt Visual Studio verschiedenste Projektvorlagen bereit, darunter Vorlagen für [die Webframeworks Flask, Bottle und Django](../python/python-web-application-project-templates.md), für Azure-Clouddienste, unterschiedliche Machine Learning-Szenarios und sogar eine Vorlage zum Erstellen eines Projekts mit einer bereits vorhandenen Ordnerstruktur, die eine Python-App enthält. Auf diese Vorlagen können Sie über **Datei** > **Neu** > **Projekt** zugreifen. Klicken Sie dafür auf den Knoten für **Python**, und wählen Sie untergeordnete Knoten aus.

Visual Studio bietet auch unterschiedliche Datei- und *Elementvorlagen* zum schnellen Erstellen einer Python-Klasse, eines Python-Pakets, eines Python-Komponententest, von *web.config*-Dateien usw. Wenn Sie ein Python-Projekt geöffnet haben, können Sie über den Menübefehl **Projekt** > **Neues Element hinzufügen** auf Elementvorlagen zugreifen. Weitere Informationen finden Sie in der [Referenz für Python-Elementvorlagen](python-item-templates.md).

Durch das Verwenden von Vorlagen sparen Sie deutlich Zeit, wenn Sie mit einem Projekt beginnen oder eine Datei erstellen. Zudem können Sie durch Vorlagen neue App-Typen und Codestrukturen kennenlernen. Es kann von Vorteil sein, sich etwas Zeit zu nehmen und Projekte und Elemente mit verschiedenen Vorlagen zu erstellen. So können Sie sich mit den zur Verfügung stehenden Vorlagen vertraut machen.

**Frage: Kann ich auch Cookiecutter-Vorlagen verwenden?**

**Antwort**: Ja! Cookiecutter-Vorlagen sind sogar direkt in Visual Studio integriert. Informationen dazu finden Sie unter [Quickstart: Create a project from a Cookiecutter template (Schnellstart: Erstellen eines Projekts mit einer Cookiecutter-Vorlage)](../python/quickstart-04-python-in-visual-studio-project-from-cookiecutter.md).

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Tutorial: Arbeiten mit Python in Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Weitere Informationen

- [Manuelles Identifizieren eines vorhandenen Python-Interpreters](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Installieren der Python-Unterstützung für Visual Studio 2015 und früher](installing-python-support-in-visual-studio.md)
- [Installationsspeicherorte](installing-python-support-in-visual-studio.md#install-locations)
