---
title: Verwalten von Paketabhängigkeiten mit einer requirements.txt-Datei
description: In einer Datei „requirements.txt“ werden die Abhängigkeiten eines Projekts beschrieben. Wenn Sie ein Projekt erhalten, das eine requirements.txt-Datei enthält, können Sie diese Abhängigkeiten ganz einfach in nur einem Schritt installieren.
ms.date: 03/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: f535f9d6ad4aa917cde493dfcfe089896634d706
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948113"
---
# <a name="manage-required-packages-with-requirementstxt"></a>Verwalten von erforderlichen Paketen mit „requirements.txt“

Wenn Sie ein Projekt für andere Benutzer freigeben, ein Buildsystem verwenden oder ein Projekt an einen anderen Ort kopieren möchten, an dem eine Umgebung wiederhergestellt werden muss, müssen Sie die externen Pakete angeben, die das Projekt benötigt. Der empfohlene Ansatz ist die Verwendung einer [requirements.txt-Datei](https://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org), die eine Liste der Befehle für pip enthält, mit denen die erforderlichen Versionen der abhängigen Pakete installiert werden. Der gängigste Befehl ist `pip freeze > requirements.txt`, der die aktuelle Paketliste einer Umgebung in *requirements.txt* protokolliert.

Eigentlich kann jeder Dateiname zum Nachverfolgen von Anforderungen verwendet werden (mit `-r <full path to file>` beim Installieren eines Pakets), aber Visual Studio bietet spezielle Unterstützung für *requirements.txt*:

- Wenn Sie ein Projekt geladen haben, das *requirements.txt* enthält, und alle in der Datei aufgeführten Pakete installieren möchten, erweitern Sie den Knoten **Python-Umgebungen** im **Projektmappen-Explorer**, klicken Sie dann mit der rechten Maustaste auf den Umgebungsknoten, und wählen Sie **Aus „requirements.txt“ installieren** aus:

    ![Installieren aus „requirements.txt“](media/environments/environments-requirements-txt-install.png)

- Wenn Sie die Abhängigkeiten in einer virtuellen Umgebung installieren möchten, erstellen und aktivieren Sie zuerst die Umgebung, und verwenden Sie den Befehl **Aus „Requirements.txt“ installieren**. Weitere Informationen zum Erstellen einer virtuellen Umgebung finden Sie unter [Verwenden von virtuellen Umgebungen](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Wenn Sie alle erforderlichen Pakete bereits in einer Umgebung installiert haben, können Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf diese Umgebung klicken und **„requirements.txt“ generieren** auswählen, um die erforderliche Datei zu erstellen. Wenn die Datei bereits vorhanden ist, werden Sie zum Aktualisieren der Datei aufgefordert:

    ![Optionen für die Aktualisierung von „requirements.txt“](media/environments/environments-requirements-txt-replace.png)

  - **Gesamte Datei ersetzen** entfernt alle vorhandenen Elemente, Kommentare und Optionen.
  - **Vorhandene Einträge aktualisieren** erkennt Paketanforderungen und aktualisiert die Versionsbezeichner entsprechend der derzeit installierten Version.
  - **Aktualisieren und Einträge hinzufügen** aktualisiert alle gefundenen Anforderungen und fügt alle anderen Pakete am Ende der Datei hinzu.

Da mit *requirements.txt*-Dateien die Anforderungen einer Umgebung fixiert werden sollen, werden alle installierten Pakete mit genauen Versionen aufgeführt. Wenn Sie genaue Versionen verwenden, wird sichergestellt, dass Sie Ihre Umgebung leicht auf einem anderen Computer reproduzieren können. Pakete werden aufgenommen, selbst wenn sie mit einem Versionsbereich, als Abhängigkeit von einem anderen Paket oder mit einen anderen Installationsprogramm als pip installiert wurden.

Wenn ein Paket nicht von pip installiert werden kann und in einer *requirements.txt*-Datei enthalten ist, schlägt die gesamte Installation fehl. Bearbeiten Sie in diesem Fall die Datei manuell, um dieses Paket ausschließen oder [pip-Optionen](https://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) zu verwenden, um auf eine installierbare Version des Pakets zu verweisen. Sie könnten beispielsweise [`pip wheel`](https://pip.readthedocs.org/en/latest/reference/pip_wheel.html) verwenden, um eine Abhängigkeit zu kompilieren und die Option `--find-links <path>` Ihrer Datei *requirements.txt* hinzuzufügen:

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

## <a name="see-also"></a>Weitere Informationen

- [Verwalten von Python-Umgebungen in Visual Studio](managing-python-environments-in-visual-studio.md)
- [Auswählen eines Interpreters für ein Projekt](selecting-a-python-environment-for-a-project.md)
- [Suchpfade](search-paths.md)
- [Das Fenster „Python-Umgebungen“](python-environments-window-tab-reference.md)
