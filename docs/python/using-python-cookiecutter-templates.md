---
title: Verwenden der CookieCutter-Vorlagen für Python
description: Visual Studio unterstützt die grafische Cookiecutter-Erweiterung für die Ermittlung von Vorlagen für Python-Code und zum Erstellen von Projekten aus diesen Vorlagen.
ms.date: 01/28/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 08ae2e13f094535eae0447cc3b8d4acf4c806a99
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920612"
---
# <a name="use-the-cookiecutter-extension"></a>Verwenden der Cookiecutter-Erweiterung

[Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) stellt eine grafische Benutzeroberfläche bereit, auf der Sie Vorlagen ermitteln, Vorlageoptionen eingeben und Projekte und Dateien erstellen können. Die Erweiterung ist im Lieferumfang von Visual Studio 2017 und höher enthalten und kann separat in früheren Versionen von Visual Studio installiert werden.

Cookiecutter erfordert Python 3.3 oder höher (32-Bit oder 64-Bit) oder Anaconda 3 4.2 oder höher (32-Bit oder 64 Bit). Wenn kein geeigneter Python-Interpreter verfügbar ist, zeigt Visual Studio eine Warnung an. Wenn Sie einen Python-Interpreter installieren, während Visual Studio ausgeführt wird, wählen Sie auf der Symbolleiste von Cookiecutter die **Startschaltfläche** aus, um den neu installierten Interpreter zu erkennen. (Unter [Python-Umgebungen](managing-python-environments-in-visual-studio.md) finden Sie Informationen zu Umgebungen im Allgemeinen.)

Wählen Sie nach der Installation **Ansicht** > **Cookiecutter-Explorer** aus, um das Fenster von Cookiecutter zu öffnen:

![Cookiecutter – Hauptfenster](media/cookiecutter-overview.png)

## <a name="cookiecutter-workflow"></a>Cookiecutter-Workflow

Beim Arbeiten mit Cookiecutter durchsuchen Sie Vorlagen, wählen eine Vorlage aus, klonen sie auf Ihren lokalen Computer, legen Optionen fest und erstellen dann Code aus dieser Vorlage, wie in den folgenden Abschnitten beschrieben.

### <a name="browse-templates"></a>Durchsuchen der Vorlagen

Die Startseite von Cookiecutter zeigt eine Liste der auswählbaren Vorlagen an, unterteilt in die folgenden Gruppen:

| Gruppieren | Beschreibung |
| --- | --- |
| **Installiert** | Vorlagen, die auf Ihrem lokalen Computer installiert wurden. Bei Verwendung einer Onlinevorlage wird das zugehörige Repository automatisch in einen Unterordner von *~/.cookiecutters* geklont. Sie können eine ausgewählte installierte Vorlage löschen, indem Sie die Taste **ENTF** drücken. |
| **Empfohlen** | Aus dem empfohlenen Feed geladene Vorlagen. Der Standardfeed wird von Microsoft kuratiert. Informationen zum Anpassen des Feeds finden Sie weiter unten im Abschnitt [Cookiecutter-Optionen](#cookiecutter-options). |
| **GitHub** | GitHub-Suchergebnisse für das Stichwort „cookiecutter“. Die Ergebnisse von GitHub sind in Seiten sortiert. Wenn weitere Ergebnisse verfügbar sind, wird am Ende der Liste **Weitere laden** angezeigt. |
| **Benutzerdefiniert** | Wenn ein benutzerdefinierter Speicherort in das Suchfeld eingegeben wurde, wird er in dieser Gruppe angezeigt. Sie können entweder den vollständigen Pfad zum GitHub-Repository oder den vollständigen Pfad zu einem Ordner auf Ihrem lokalen Datenträger eingeben. |

### <a name="cloning"></a>Klonen?

Wenn Sie eine Vorlage auswählen und dann auf **Weiter** klicken, erstellt Cookiecutter eine lokale Kopie zum Arbeiten.

Wenn Sie eine Vorlage aus den Gruppen **Empfohlen** oder **GitHub** auswählen, oder wenn Sie eine benutzerdefinierte URL in das Suchfeld eingeben und dann diese Vorlage auswählen, wird die Vorlage geklont und auf Ihrem lokalen Computer installiert. Wenn diese Vorlage in einer früheren Visual Studio-Sitzung installiert wurde, wird diese automatisch gelöscht und die neueste Version geklont.

Wenn Sie eine Vorlage aus der Gruppe **Installiert** auswählen oder wenn Sie einen benutzerdefinierten Ordnerpfad in das Suchfeld eingeben und dann diese Vorlage auswählen, lädt Visual Studio die Vorlage, ohne sie zu klonen.

> [!Important]
> Cookiecutter-Vorlagen werden in einem einzigen Ordner geklont: *~/.cookiecutters*. Jeder Unterordner wird nach dem entsprechenden Git-Repositorynamen benannt. Dieser enthält nicht den GitHub-Benutzernamen. Wenn Sie verschiedene Vorlagen mit dem gleichen Namen, aber von unterschiedlichen Erstellern klonen, können Konflikte auftreten. In diesem Fall verhindert Cookiecutter das Überschreiben der vorhandenen Vorlage mit einer anderen Vorlage des gleichen Namens. Um die andere Vorlage zu installieren, müssen Sie zunächst die vorhandene löschen.

### <a name="set-template-options"></a>Festlegen von Vorlagenoptionen

Nachdem die Vorlage lokal installiert wurde, zeigt Cookiecutter eine Optionsseite an, auf der Sie angeben können, ob Cookiecutter Dateien generieren soll. Sie können auf der Seite noch weitere Optionen festlegen:

![Cookiecutter – Optionsseite](media/cookiecutter-template-options.png)

Jede Cookiecutter-Vorlage definiert einen eigenen Satz von Optionen und legt einen Standardwert für jede Option fest (angezeigt als vorgeschlagener Text in den jeweiligen Eingabefeldern). Bei einem Standardwert kann es sich um einen Codeausschnitt handeln. Dies ist häufig bei dynamischen Werten der Fall, die weitere Optionen nutzen.

Es ist möglich, Standardwerte für bestimmte Optionen mithilfe einer Benutzerkonfigurationsdatei anzupassen. Wenn die Cookiecutter-Erweiterung eine Benutzerkonfigurationsdatei erkennt, werden die Standardwerte der Vorlage mit den Standardwerten der Benutzerkonfiguration überschrieben. Dieses Verhalten wird im Abschnitt [Benutzerkonfiguration](https://cookiecutter.readthedocs.io/en/latest/advanced/user_config.html) der Cookiecutter-Dokumentation erläutert.

Wenn in der Vorlage bestimmte Visual Studio-Tasks festgelegt sind, die nach dem Generieren des Codes ausgeführt werden sollen, wird die Option **Bei Abschluss zusätzliche Tasks ausführen** angezeigt, mit der Sie diese Tasks deaktivieren können. Die häufigste Verwendung von Tasks ist das Öffnen eines Webbrowsers, das Öffnen von Dateien im Editor, das Installieren von Abhängigkeiten usw.

### <a name="create"></a>Erstellen

Wenn Sie Ihre Optionen festgelegt haben, wählen Sie **Create** (Erstellen), um Code zu generieren (eine Warnung wird angezeigt, wenn der Ausgabeordner nicht leer ist). Wenn Sie die Ausgabe der Vorlage kennen und nichts dagegen haben, dass Dateien überschrieben werden, können Sie die Warnung ignorieren. Andernfalls klicken Sie auf **Abbrechen**, geben einen leeren Ordner an und kopieren die erstellten Dateien dann manuell in Ihren nicht leeren Ausgabeordner.

Nach dem erfolgreichen Erstellen der Dateien bietet Cookiecutter eine Option zum Öffnen der Dateien im **Projektmappen-Explorer**:

![Cookiecutter mit Projektmappen-Explorer-Befehl](media/cookiecutter-files-created.png)

## <a name="cookiecutter-options"></a>Cookiecutter-Optionen

Cookiecutter-Optionen stehen über **Extras** > **Optionen** > **Cookiecutter** zur Verfügung:

![Cookiecutter-Optionen](media/cookiecutter-tools-options.png)

| Option | Beschreibung |
| --- | --- |
| **URL des empfohlenen Feeds** | Der Speicherort des empfohlenen Vorlagenfeeds. Hierbei kann es sich um eine URL oder den Pfad zu einer lokalen Datei handeln. Lassen Sie die URL leer, um den standardmäßigen, von Microsoft kuratierten Feed zu verwenden. Der Feed bietet eine einfache, durch Zeilenumbrüche getrennte Liste mit Vorlagenspeicherorten. Um Änderungen am kuratierten Feed anzufordern, führen Sie eine Pullanforderung in der [Quelle in GitHub](https://github.com/Microsoft/PTVS/blob/master/Python/Product/Cookiecutter/CookiecutterFeed.txt) aus. |
| **Anzeigen von Hilfe** | Steuert die Sichtbarkeit der Hilfeinformationsleiste am oberen Rand des Cookiecutter-Fensters. |

## <a name="optimize-cookiecutter-templates-for-visual-studio"></a>Optimieren von Cookiecutter-Vorlagen für Visual Studio

Grundlegende Informationen zum Erstellen einer Cookiecutter-Vorlage finden Sie in der [Cookiecutter-Dokumentation](https://cookiecutter.readthedocs.io/en/latest/first_steps.html). Die Cookiecutter-Erweiterung für Visual Studio unterstützt Vorlagen, die für Cookiecutter v1.4 erstellt wurden.

Die standardmäßige Umsetzung von Vorlagenvariablen hängt vom Datentyp ab (Zeichenfolge oder Liste):

- Zeichenfolge: Bezeichnung für den Variablennamen, Textfeld zum Eingeben eines Werts und ein Wasserzeichen mit dem Standardwert. Eine QuickInfo im Textfeld zeigt den Standardwert.
- Liste: Bezeichnung für den Variablennamen, Kombinationsfeld zum Auswählen eines Werts. Eine QuickInfo im Kombinationsfeld zeigt den Standardwert.

Dieses Rendering kann verbessert werden, indem Sie zusätzliche Metadaten in Ihrer *cookiecutter.json*-Datei angeben, die speziell für Visual Studio eingerichtet wurde (und von der Cookiecutter-Befehlszeilenschnittstelle ignoriert wird). Alle Eigenschaften sind optional:

| Eigenschaft | Beschreibung |
| --- | --- |
| Bezeichnung | Gibt an, was statt des Variablennamens über dem Editor für die Variable angezeigt werden soll. |
| Beschreibung | Gibt die QuickInfo an, die im Bearbeitungssteuerelement statt des Standardwerts für diese Variable angezeigt werden soll. |
| URL | Ändert die Bezeichnung in einen Hyperlink mit einer QuickInfo, in der die URL angezeigt wird. Durch Auswählen des Hyperlinks wird diese URL im Standardbrowser des Benutzers geöffnet. |
| Auswahl | Ermöglicht die Anpassung des Editors für eine Variable. Folgende Auswahlmöglichkeiten werden zurzeit unterstützt:<ul><li>`string`: Standardtextfeld, standardmäßig für Zeichenfolgen.</li><li>`list`: Standardkombinationsfeld, standardmäßig für Listen.</li><li>`yesno`: Kombinationsfeld zur Auswahl zwischen `y` und `n`, für Zeichenfolgen.</li><li>`odbcConnection`: Textfeld mit einer **...** -Schaltfläche, die ein Dialogfeld für eine Datenbankverbindung öffnet.</li></ul> |

Beispiel:

```json
{
    "site_name": "web-app",
    "python_version": ["3.5.2", "2.7.12"],
    "use_azure": "y",

    "_visual_studio": {
        "site_name": {
            "label": "Site name",
            "description": "E.g. <site-name>.azurewebsites.net (can only contain alphanumeric characters and `-`)"
        },
        "python_version": {
            "label": "Python version",
            "description": "The version of Python to run the site on"
        },
        "use_azure" : {
            "label": "Use Azure",
            "description": "Include Azure deployment files",
            "selector": "yesno",
            "url": "https://azure.microsoft.com"
        }
    }
}
```

### <a name="run-visual-studio-tasks"></a>Ausführen von Visual Studio-Tasks

Cookiecutter verfügt über eine Funktion namens *Post-Generate Hooks*, mit der nach dem Generieren der Dateien beliebiger Python-Code ausgeführt werden kann. Diese Funktion ist zwar flexibel, bietet jedoch keinen einfachen Zugriff auf Visual Studio.

Ein Beispiel: Sie möchten eine Datei im Visual Studio-Editor oder im Webbrowser öffnen oder die Visual Studio-Benutzeroberfläche aufrufen, die den Benutzer dazu auffordert, eine virtuelle Umgebung zu erstellen und erforderliche Paketelemente zu installieren.

Für diese Szenarien sucht Visual Studio in *cookiecutter.json* nach erweiterten Metadaten, mit denen die Befehle beschrieben werden, die ausgeführt werden müssen, nachdem ein Benutzer die generierten Dateien im **Projektmappen-Explorer** geöffnet hat oder nachdem die Dateien zu einem vorhandenen Projekt hinzugefügt wurden. (Auch hier kann der Benutzer die Ausführung der Tasks mithilfe der Vorlagenoption **Run additional tasks on completion** (Bei Abschluss zusätzliche Tasks ausführen) deaktivieren.)

Beispiel:

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": "{{cookiecutter._output_folder_path}}\\readme.txt"
    },
    {
        "name": "Cookiecutter.ExternalWebBrowser",
        "args": "https://docs.microsoft.com"
    },
    {
        "name": "Python.InstallProjectRequirements",
        "args": "{{cookiecutter._output_folder_path}}\\dev-requirements.txt"
    }
]
```

Befehle werden anhand ihres Namens angegeben, und Sie sollten auch in lokalisierten Installationen von Visual Studio die nicht lokalisierten (also englischen) Namen verwenden. Sie können Befehlsnamen im Visual Studio-**Befehlsfenster** testen und ermitteln.

Wenn Sie ein einzelnes Argument übergeben möchten, geben Sie es als Zeichenfolge an, wie im vorherigen Beispiel gezeigt.

Wenn Sie kein Argument übergeben müssen, geben Sie in der JSON eine leere Zeichenfolge an oder lassen die Zeile einfach weg:

```json
"_visual_studio_post_cmds": [
    {
        "name": "View.WebBrowser"
    }
]
```

Wenn Sie mehrere Argumente übergeben möchten, verwenden Sie ein Array. Wenn Sie Schalter verwenden, teilen Sie den Schalter und den zugehörigen Wert in separate Argumente auf und verwenden Sie die korrekten Anführungszeichen. Zum Beispiel:

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": [
            "{{cookiecutter._output_folder_path}}\\read me.txt",
            "/e:",
            "Source Code (text) Editor"
        ]
    }
]
```

Argumente können auf andere Cookiecutter-Variablen verweisen. In den oben stehenden Beispielen wird die interne `_output_folder_path`-Variable verwendet, um einen absoluten Pfad zu den generierten Dateien zu bilden.

Beachten Sie, dass der `Python.InstallProjectRequirements`-Befehl nur beim Hinzufügen von Dateien zu einem vorhandenen Projekt funktioniert. Diese Einschränkung besteht, weil der Befehl vom Python-Projekt im **Projektmappen-Explorer** verarbeitet wird und kein Projekt zum Empfangen der Meldung vorhanden ist, wenn Sie sich in der **Ordneransicht** des **Projektmappen-Explorers** befinden. Wir hoffen, diese Einschränkung in einer zukünftigen Version aufzuheben (und eine bessere Unterstützung der **Ordneransicht** im Allgemeinen zu ermöglichen).

## <a name="troubleshooting"></a>Problembehandlung

### <a name="error-loading-template"></a>Fehler beim Laden der Vorlage

Einige Vorlagen verwenden in der *cookiecutter.json* möglicherweise ungültige Datentypen – z.B. einen booleschen Typ. Melden Sie solche Instanzen dem Autor der Vorlage, indem Sie im Informationsbereich der Vorlage auf den Link **Issues** (Probleme) klicken.

### <a name="hook-script-failed"></a>Fehler beim Hookskript

Einige Vorlagen verwenden möglicherweise Skripts zum Ausführen nach der Generierung, die nicht mit der Cookiecutter-Benutzeroberfläche kompatibel sind. Beispielsweise treten Fehler bei Skripts auf, die eine Eingabe vom Benutzer anfordern, da keine Terminalkonsole vorhanden ist.

### <a name="hook-script-not-supported-on-windows"></a>Keine Unterstützung für Hookskript unter Windows

Wenn die Postskriptdatei eine *.sh*-Datei ist, ist sie möglicherweise mit keiner Anwendung auf Ihrem Windows-Computer verknüpft. Möglicherweise wird ein Windows-Dialogfeld angezeigt, in dem Sie aufgefordert werden, eine kompatible Anwendung im Windows-Store zu suchen.

### <a name="templates-with-known-issues"></a>Vorlagen mit bekannten Fehlern

Klonfehler:

- **wildfish/cookiecutter-django-crud** (ungültiges `|`-Zeichen im Namen des Unterordners)
- **cookiecutter-pyvanguard** (ungültiges `|`-Zeichen im Namen des Unterordners)

Ladefehler:

- **chrisdev/wagtail-cookiecutter-foundation** (verwendet einen booleschen Typ in *cookiecutter.json*)
- **quintoandar/cookiecutter-android** (kein Vorlagenordner)

Ausführungsfehler:

- **iknite/cookiecutter-ansible-role** (Posthookskript erfordert Konsoleneingabe)
- **benregn/cookiecutter-django-ansible** (Jinja-Fehler)

Verwendet Bash (nicht schwerwiegend):

- **openstack-dev/cookiecutter**
