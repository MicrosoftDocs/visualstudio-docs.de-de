---
title: Debuggen von Python-Code auf Linux-Remotecomputern
description: Verwenden von Visual Studio zum Debuggen von Python-Code, der auf Linux-Remotecomputern ausgeführt wird, einschließlich der erforderlichen Konfigurationsschritte, Sicherheit und Problembehandlung.
ms.date: 05/12/2020
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: dcc5d9746a556af54ea206528fcb9a402e25d700
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916586"
---
Visual Studio kann Python-Anwendungen sowohl lokal als auch remote (siehe [Remotedebuggen](../../../debugger/remote-debugging.md)) auf einem Windows-Computer starten und debuggen. Mithilfe der [debugpy-Bibliothek](https://pypi.org/project/debugpy/) kann das Remotedebuggen auch auf einem anderen Betriebssystem, einem anderen Gerät oder in einer anderen Python-Implementierung als CPython ausgeführt werden.

Bei Verwendung von debugpy hostet der Python-Code, für den das Debuggen ausgeführt werden soll, den Debugserver, an den Visual Studio angefügt werden kann. Für dieses Hosting ist eine kleine Änderung an Ihrem Code erforderlich, um den Server zu importieren und zu aktivieren. Auf dem Remotecomputer müssen möglicherweise Netzwerk- oder Firewallkonfigurationen geändert werden, sodass TCP-Verbindungen zulässig sind.

> [!NOTE]
> Für Visual Studio 2019, Version 16.4 und früher wurde die [ptvsd-Bibliothek](https://pypi.python.org/pypi/ptvsd) verwendet. Die debugpy-Bibliothek hat ptvsd 4 in Visual Studio 2019, Version 16.5 ersetzt.

## <a name="set-up-a-linux-computer"></a>Einrichten eines Linux-Computers

Die folgenden Elemente sind für diese exemplarische Vorgehensweise nötig:

- Einen Remotecomputer, auf dem Python unter einem Betriebssystem wie Mac OSX oder Linux ausgeführt wird.
- Einen geöffneten Port 5678 (eingehend) auf der Firewall dieses Computers. Dies ist die Standardeinstellung für das Remotedebuggen.

> [!NOTE]
> Diese exemplarische Vorgehensweise basiert auf Visual Studio 2019, Version 16.6.

Sie können problemlos [virtuelle Linux-Computer in Azure](/azure/virtual-machines/linux/creation-choices) erstellen und von Windows aus [über Remotedesktop darauf zugreifen](/azure/virtual-machines/linux/use-remote-desktop). Es ist praktisch, für den virtuellen Computer Ubuntu zu verwenden, da Python standardmäßig installiert ist; andernfalls finden Sie unter [Installieren eines Python-Interpreters Ihrer Wahl](../../installing-python-interpreters.md) eine Liste mit weiteren Python-Downloadspeicherorten.

Weitere Informationen zum Erstellen einer Firewallregel für einen virtuellen Azure-Computer finden Sie unter [Öffnen von Ports für einen virtuellen Computer in Azure mithilfe des Azure-Portals](/azure/virtual-machines/windows/nsg-quickstart-portal).

## <a name="prepare-the-script-for-debugging"></a>Vorbereiten des Skripts für das Debuggen

1. Erstellen Sie auf dem Remotecomputer die Python-Datei *guessing-game.py* mit dem folgenden Code:

    ```python
    import random

    guesses_made = 0
    name = input('Hello! What is your name?\n')
    number = random.randint(1, 20)
    print('Well, {0}, I am thinking of a number between 1 and 20.'.format(name))

    while guesses_made < 6:
        guess = int(input('Take a guess: '))
        guesses_made += 1
        if guess < number:
            print('Your guess is too low.')
        if guess > number:
            print('Your guess is too high.')
        if guess == number:
            break
    if guess == number:
        print('Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made))
    else:
        print('Nope. The number I was thinking of was {0}'.format(number))
    ```

1. Installieren Sie mithilfe von `pip3 install debugpy` das `debugpy`-Paket in Ihrer Umgebung.
   >[!NOTE]
   >Es empfiehlt sich, die installierte Version von debugpy zu notieren, falls Sie diese für die Problembehandlung benötigen. Die [debugpy-Liste](https://pypi.org/project/debugpy/) enthält die verfügbaren Versionen.

1. Aktivieren Sie das Remotedebuggen, indem Sie den untenstehenden Code am frühestmöglichen Punkt in *guessing-game.py* einfügen, also vor jedem anderen Code. (Dies ist zwar nicht zwingend erforderlich, aber es ist unmöglich, Hintergrundthreads zu debuggen, die vor dem Aufruf der Funktion `listen` erzeugt werden.)

   ```python
   import debugpy
   debugpy.listen(5678)
   ```

1. Speichern Sie die Datei, und führen Sie `python3 guessing-game.py` aus. Der Aufruf von `listen` wird im Hintergrund ausgeführt und wartet auf eingehende Verbindungen, da Sie andernfalls mit dem Programm interagieren. Bei Bedarf kann die Funktion `wait_for_client` nach `listen` aufgerufen werden, um das Programm zu blockieren, bis der Debugger angefügt wurde.

> [!Tip]
> Zusätzlich zu `listen` und `wait_for_client` bietet debugpy auch die Hilfsfunktion `breakpoint`, die als programmgesteuerter Haltepunkt fungiert, wenn der Debugger angefügt wird. Es gibt auch eine `is_client_connected`-Funktion, die `True` zurückgibt, wenn der Debugger angefügt wird (das Ergebnis muss vor dem Aufrufen anderer `debugpy`-Funktionen nicht geprüft werden).

## <a name="attach-remotely-from-python-tools"></a>Remoteanfügen über Python Tools

In diesen Schritten legen wir einen einfachen Haltepunkt fest, um den Remoteprozess anzuhalten.

1. Erstellen Sie eine Kopie der Remotedatei auf dem lokalen Computer, und öffnen Sie diese in Visual Studio. Es spielt keine Rolle, wo die Datei gespeichert wird, der Name muss aber dem Namen des Skripts auf dem Remotecomputer entsprechen.

1. (Optional) Um auf dem lokalen Computer IntelliSense für debugpy zu nutzen, können Sie das debugpy-Paket in Ihrer Python-Umgebung installieren.

1. Wählen Sie **Debuggen** > **An den Prozess anhängen** aus.

1. Legen Sie im nun angezeigten Dialogfeld **An den Prozess anhängen** den **Verbindungstyp** auf **Python remote (debugpy)** fest.

1. Geben Sie in das Feld **Verbindungsziel** den Wert `tcp://<ip_address>:5678` ein, wobei `<ip_address>` für die Adresse des Remotecomputers (entweder eine explizite Adresse oder ein Name wie myvm.cloudapp.net) und `:5678` für die Portnummer beim Remotedebuggen steht.

1. Drücken Sie die **EINGABETASTE**, um die Liste der auf diesem Computer verfügbaren debugpy-Prozesse aufzufüllen:

    ![Eingeben des Verbindungsziels und Auflisten von Prozessen](../../media/remote-debugging-attach.png)

    Wenn Sie nach dem Auffüllen dieser Liste ein anderes Programm auf dem Remotecomputer starten, klicken Sie auf die Schaltfläche **Aktualisieren**.

1. Wählen Sie den Prozess zum Debuggen und dann **Anfügen** aus, oder doppelklicken Sie auf den Prozess.

1. Visual Studio wechselt dann in den Debugmodus, während das Skript weiterhin auf dem Remotecomputer ausgeführt wird, und bietet alle üblichen Funktionen zum [Debuggen](../../debugging-python-in-visual-studio.md). Setzen Sie zum Beispiel einen Haltepunkt in die `if guess < number:`-Zeile, wechseln Sie dann zum Remotecomputer, und geben Sie einen anderen Schätzwert ein. Danach stoppt Visual Studio auf dem lokalen Computer an diesem Haltepunkt, zeigt lokale Variablen an usw.:

    ![Visual Studio unterbricht den Debugprozess, sobald der Breakpoint erreicht ist.](../../media/remote-debugging-breakpoint-hit.png)

1. Wenn Sie das Debuggen beenden, wird Visual Studio vom Programm getrennt, das weiterhin auf dem Remotecomputer ausgeführt wird. debugpy lauscht außerdem weiterhin auf angefügte Debugger, sodass Sie den Prozess jederzeit erneut wieder anfügen können.

### <a name="connection-troubleshooting"></a>Problembehandlung bei der Verbindung

1. Stellen Sie sicher, dass Sie **Python remote (debugpy)** als **Verbindungstyp** ausgewählt haben.
1. Überprüfen Sie, ob das Geheimnis im **Verbindungsziel** genau mit dem Geheimnis im Remotecode übereinstimmt.
1. Überprüfen Sie, ob die IP-Adresse im **Verbindungsziel** der des Remotecomputers entspricht.
1. Stellen Sie sicher, dass Sie den Port für das Remotedebuggen auf dem Remotecomputer geöffnet haben, und das Suffix des Ports (z. B. `:5678`) im Verbindungsziel enthalten ist.
    - Wenn Sie einen anderen Port verwenden möchten, können Sie diesen in `listen` als `debugpy.listen((host, port))` angeben. Öffnen Sie in diesem Fall diesen Port in der Firewall.
1. Überprüfen Sie, ob die auf dem Remotecomputer installierte debugpy-Version gemäß Rückgabe durch `pip3 list` mit der Version der in Visual Studio verwendeten Python-Tools übereinstimmt (siehe Tabelle unten). Aktualisieren Sie bei Bedarf debugpy auf dem Remotecomputer.

    | Visual Studio-Version | Python-Tools/debugpy-Version |
    | --- | --- |
    | 2019 16.6 | 1.0.0b5 |
    | 2019 16.5 | 1.0.0b1 |

> [!NOTE]
> Visual Studio 2019, Version 16.0-16.4 verwendet ptvsd, nicht debugpy. Das Verfahren in dieser exemplarischen Vorgehensweise ist für diese Versionen ähnlich, aber die Funktionsnamen unterscheiden sich. Visual Studio 2019, Version 16.5 verwendet debugpy, aber die Funktionsnamen sind dieselben wie in ptvsd. Anstelle von `listen` verwenden Sie `enable_attach`. Anstelle von `wait_for_client` verwenden Sie `wait_for_attach`. Anstelle von `breakpoint` verwenden Sie `break_into_debugger`.

## <a name="using-ptvsd-3x-for-legacy-debugging"></a>Verwenden von ptvsd 3.x für ein Legacydebugging
Visual Studio 2017-Version 15.8 und höher verwendet einen Debugger, der auf ptvsd-Version 4.1 und höher basiert. Visual Studio 2019 verwendet ab Version 16.5 einen Debugger, der auf debugpy basiert. Diese Debuggerversionen sind mit Python 2.7 und Python 3.5+ kompatibel. Wenn Sie Python 2.6, 3.1, 3.4 oder IronPython verwenden, zeigt Visual Studio den Fehler **Diese Python-Umgebung wird vom Debugger nicht unterstützt** an. Die folgenden Informationen gelten nur für das Remotedebuggen mit ptvsd 3.x.

1. Mit ptvsd 3.x erforderte die `enable_attach`-Funktion das Übergeben eines „Geheimnisses“ als erstes Argument, das den Zugriff auf das ausgeführte Skript einschränkt. Sie geben dieses Geheimnis beim Anfügen des Remotedebuggers ein. Obwohl dies nicht empfohlen wird, können Sie allen Benutzern das Herstellen einer Verbindung erlauben, indem Sie `enable_attach(secret=None)` verwenden.

1. Die Verbindungsziel-URL ist `tcp://<secret>@<ip_address>:5678`, wobei `<secret>` die an `enable_attach` im Python-Code übergebene Zeichenfolge ist.

In der Standardeinstellung ist die Verbindung mit dem ptvsd-Remotedebugserver 3.x nur durch den geheimen Schlüssel geschützt, und alle Daten werden als Nur-Text übergeben. Für eine sicherere Verbindung unterstützt ptvsd 3.x SSL mit dem `tcsp`-Protokoll, das folgendermaßen eingerichtet wird:

1. Generieren Sie auf dem Remotecomputer ein eigenständiges selbstsigniertes Zertifikat und Schlüsseldateien mit OpenSSL:

    ```command
    openssl req -new -x509 -days 365 -nodes -out cert.cer -keyout cert.key
    ```

    Verwenden Sie den Hostnamen oder die IP-Adresse (je nachdem, was Sie beim Verbinden verwenden) als **gemeinsamen Namen**, wenn Sie von OpenSSL dazu aufgefordert werden.

    (Weitere Informationen finden Sie unter [Self-signed certificates (Selbstsignierte Zertifikate)](https://docs.python.org/3/library/ssl.html#self-signed-certificates) im Python-Modul `ssl`. Beachten Sie, dass der Befehl in dieser Dokumentation nur eine einzige kombinierte Datei generiert.)

1. Ändern Sie im Code den Aufruf von `enable_attach` so, dass er `certfile`- und `keyfile`-Argumente mit den Dateinamen als Werte enthält (diese Argumente haben dieselbe Bedeutung wie bei der standardmäßigen Python-Funktion `ssl.wrap_socket`):

    ```python
    ptvsd.enable_attach(secret='my_secret', certfile='cert.cer', keyfile='cert.key')
    ```

    Sie können die gleiche Änderung auch in der Codedatei auf dem lokalen Computer vornehmen, aber da dieser Code nicht tatsächlich ausgeführt wird, ist dies nicht zwingend erforderlich.

1. Starten Sie das Python-Programm auf dem Remotecomputer neu, damit es zum Debuggen bereit ist.

1. Sichern Sie den Kanal, indem Sie das Zertifikat der vertrauenswürdigen Stammzertifizierungsstelle auf dem Windows-Computer mit Visual Studio hinzufügen:

    1. Kopieren Sie die Zertifikatdatei vom Remotecomputer auf den lokalen Computer.
    1. Öffnen Sie die **Systemsteuerung**, und navigieren Sie zu **Verwaltung** > **Computerzertifikate verwalten**.
    1. Erweitern Sie im daraufhin angezeigten Fenster auf der linken Seite **Vertrauenswürdige Stammzertifizierungsstellen**, klicken Sie mit der rechten Maustaste auf **Zertifikate**, und wählen Sie **Alle Aufgaben** > **Importieren** aus.
    1. Wählen Sie die *CER*-Datei aus, die vom Remotecomputer kopiert wurde, und klicken Sie sich dann durch den Dialog, um den Import abzuschließen.

1. Wiederholen Sie den Anfügungsprozess wie zuvor beschrieben in Visual Studio, und verwenden Sie nun `tcps://` als Protokoll für das **Verbindungsziel** (oder **Qualifizierer**).

    ![Auswählen des Transports für das Remotedebuggen über SSL](../../media/remote-debugging-qualifier-ssl.png)

1. Visual Studio meldet Ihnen beim Herstellen einer Verbindung über SSL mögliche Zertifikatprobleme. Sie können die Warnungen ignorieren und fortfahren. Obwohl der Kanal dann noch immer gegen Lauschangriffe verschlüsselt ist, kann er jedoch für Man-in-the-Middle-Angriffe geöffnet sein.

    1. Wenn die untenstehende Warnung **Das Remotezertifikat ist nicht vertrauenswürdig** angezeigt wird, bedeutet dies, dass Sie das Zertifikat nicht ordnungsgemäß zur vertrauenswürdigen Stammzertifizierungsstelle hinzugefügt haben. Überprüfen Sie diese Schritte, und versuchen Sie es erneut.

        ![SSL-Zertifikatwarnung Vertrauenswürdigkeit](../../media/remote-debugging-ssl-warning.png)

    1. Wenn die untenstehende Warnung **Der Name des Remotezertifikats stimmt nicht mit dem Hostnamen überein** angezeigt wird, bedeutet dies, dass Sie bei der Erstellung des Zertifikats als **gemeinsamen Namen** nicht den richtigen Hostnamen oder nicht die richtige IP-Adresse eingegeben haben.

        ![SSL-Zertifikatwarnung Hostname](../../media/remote-debugging-ssl-warning2.png)
