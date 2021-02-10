---
title: Remotearbeitsbereiche für R
description: Einrichten von R-Remotearbeitsbereichen und Herstellen von Verbindungen mit ihnen aus Visual Studio.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 96078d1b2fdb5a54c912cbf214024726ce102e4e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851841"
---
# <a name="set-up-remote-workspaces"></a>Einrichten von Remotearbeitsbereichen

In diesem Artikel wird erklärt, wie ein Remoteserver mit SSL und einem geeigneten R-Dienst konfiguriert wird. So kann R Tools für Visual Studio (RTVS) mit einem Remotearbeitsbereich auf diesem Server verbunden werden.

## <a name="remote-computer-requirements"></a>Anforderungen an Remotecomputer

- Windows 10, Windows Server 2016 oder Windows Server 2012 R2 RTVS erfordert ebenfalls
- [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) oder höher

## <a name="install-an-ssl-certificate"></a>Installieren eines SSL-Zertifikats

RTVS erfordert, dass die gesamte Kommunikation mit einem Remoteserver über HTTP abläuft, wofür ein SSL-Zertifikat auf dem Server notwendig ist. Sie können entweder ein von einer vertrauenswürdigen Zertifizierungsstelle signiertes Zertifikat (empfohlen) oder ein selbstsigniertes Zertifikat verwenden. (Ein selbstsigniertes Zertifikat bewirkt, dass RTVS Warnungen auslöst, wenn eine Verbindung besteht.) Unabhängig davon, für welches Sie sich entscheiden, muss das Zertifikat auf dem Computer installiert werden und den Zugriff auf seinen privaten Schlüssel ermöglichen.

### <a name="obtain-a-trusted-certificate"></a>Abrufen eines vertrauenswürdigen Zertifikats

Ein vertrauenswürdiges Zertifikat wird von einer Zertifizierungsstelle ausgestellt (Informationen finden Sie auf [Wikipedia zu Zertifizierungsstellen](https://en.wikipedia.org/wiki/Certificate_authority)). Wie bei der Ausstellung eines Personalausweises ist auch der Prozess der Ausstellung eines vertrauenswürdigen Zertifikats länger und es fallen mögliche Gebühren an, dafür wird die Echtheit der Anforderung und des Anfordernden überprüft.

Das Schlüsselfeld, das im Zertifikat enthalten sein muss, ist der vollqualifizierte Domainname Ihres R-Servercomputers. Die Zertifizierungsstelle fordert einen Nachweis, dass Sie berechtigt sind, einen neuen Server für die Domäne zu erstellen, zu der Ihr Server gehört.

Weitere Informationen finden Sie auf Wikipedia unter [Public-Key-Zertifikat](https://en.wikipedia.org/wiki/Public_key_certificate).

## <a name="install-an-ssl-certificate-on-windows"></a>Installieren eines SSL-Zertifikats unter Windows

Das SSL-Zertifikat muss manuell unter Windows installiert werden. Führen Sie dazu die folgenden Schritte aus.

### <a name="obtain-a-self-signed-certificate-windows"></a>Abrufen eines selbstsignierten Zertifikats (Windows)

Überspringen Sie diesen Abschnitt, wenn Sie bereits ein vertrauenswürdiges Zertifikat haben. Verglichen mit einem Zertifikat von einer vertrauenswürdigen Zertifizierungsstelle ist ein selbstsigniertes Zertifikat wie ein selbst erstellter Ausweis. Dieser Prozess ist zwar einfacher als die Zusammenarbeit mit einer vertrauenswürdigen Zertifikatsstelle, entbehrt aber auch einer starken Authentifizierung. Das bedeutet, dass ein Angreifer ein nicht signiertes Zertifikat durch ein eigenes ersetzen und den gesamten Verkehr zwischen dem Client und dem Server abfangen kann. *Selbstsignierte Zertifikate sollten daher nur für Testszenarios innerhalb eines vertrauenswürdigen Netzwerks eingesetzt werden, niemals in der Produktion.*

Aus diesem Grund gibt RTVS immer die folgende Warnung aus, wenn eine Verbindung mit einem Server mit einem selbstsignierten Zertifikat hergestellt wird:

![Dialogfeld „Warnung zu selbstsigniertem Zertifikat“](media/workspaces-remote-self-signed-certificate-warning.png)

So erstellen Sie ein selbstsigniertes Zertifikat

1. Melden Sie sich mit einem Administratorkonto auf dem R-Servercomputer an.
1. Öffnen Sie eine neue PowerShell-Administratorbefehlszeile, führen Sie den folgenden Befehl aus, und ersetzen Sie dabei `"remote-machine-name"` durch den vollqualifizierten Domänennamen des Servercomputers.

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. Wenn Sie PowerShell zuvor noch nie auf dem R-Servercomputer ausgeführt haben, führen Sie den folgenden Befehl aus, um die explizite Ausführung von Befehlen zu aktivieren:

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

Hintergrundinformationen finden Sie auf Wikipedia unter [Self-signed certificate](https://en.wikipedia.org/wiki/Self-signed_certificate).

### <a name="install-the-certificate"></a>Installieren des Zertifikats

Führen Sie *certlm.msc* (Zertifikat-Manager) über eine Eingabeaufforderung aus, um das Zertifikat auf dem Remotecomputer zu installieren. Klicken Sie mit der rechten Maustaste auf den Ordner **Personal** (Persönlich), und wählen Sie den Befehl **Alle Aufgaben** > **Import** aus:

![Befehl „Zertifikat importieren“](media/workspaces-remote-certificate-import.png)

### <a name="grant-permissions-to-read-the-ssl-certificates-private-key"></a>Gewähren von Leseberechtigungen für den privaten Schlüssel des SSL-Zertifikats

Sobald das Zertifikat importiert wurde, gewährt das `NETWORK SERVICE`-Konto Leseberechtigungen für den privaten Schlüssel, wie im Folgenden beschrieben. `NETWORK_SERVICE` ist das Konto, das für die Ausführung des R Services-Brokers verwendet wird. Mit diesem Dienst werden eingehende SSL-Verbindungen mit dem Servercomputer beendet.

1. Führen Sie *certlm.msc* (Zertifikat-Manager) über eine Eingabeaufforderung als Administrator aus.
1. Erweitern Sie **Personal** > **Certificates** (Persönlich > Zertifikate), klicken Sie mit der rechten Maustaste auf das Zertifikat, und wählen Sie **Alle Aufgaben** > **Privatschlüssel verwalten** aus.
1. Klicken Sie mit der rechten Maustaste auf das Zertifikat, und wählen Sie unter **Alle Aufgaben** den Befehl **Private Schlüssel verwalten** aus.
1. Wählen Sie im sich daraufhin öffnenden Dialogfeld **Hinzufügen** aus, und geben Sie `NETWORK SERVICE` als Kontoname ein:

    ![Dialogfeld „Private Schlüssel verwalten“, NETWORK_SERVICE wird hinzugefügt](media/workspaces-remote-manage-private-key-dialog.png)

1. Wählen Sie **OK** zweimal aus, um die Dialogfelder zu schließen und die Änderungen zu übernehmen.

## <a name="install-an-ssl-certificate-on-ubuntu"></a>Installieren eines SSL-Zertifikats unter Ubuntu

Im Rahmen der Installation installiert das Paket `rtvs-daemon` standardmäßig ein selbstsigniertes Zertifikat.

### <a name="obtain-a-self-signed-certificate-ubuntu"></a>Abrufen eines selbstsignierten Zertifikats (Ubuntu)

Vorteile und Risiken von selbstsignierten Zertifikaten finden Sie in der Windows-Beschreibung. Das Paket `rtvs-daemon` generiert und konfiguriert das selbstsignierte Zertifikat während der Installation. Sie müssen diese Vorgänge nur manuell ausführen, wenn Sie das automatisch generierte selbstsignierte Zertifikat ersetzen möchten.

So erstellen Sie ein selbstsigniertes Zertifikat:

1. Erstellen Sie eine SSH-Verbindung, oder melden Sie sich auf dem Linux-Computer an.
2. Installieren Sie das `ssl-cert`-Paket:

    ```sh
    sudo apt-get install ssl-cert
    ```

3. Führen Sie `make-ssl-cert` aus, um das selbstsignierte SSL-Standardzertifikat zu generieren:

    ```sh
    sudo make-ssl-cert generate-default-snakeoil --force-overwrite
    ```

4. Konvertiert die generierte Schlüssel- und die PEM-Datei in PFX. Die generierten PFX-Dateien sollten sich im Basisordner befinden:

    ```sh
    openssl pkcs12 -export -out ~/ssl-cert-snakeoil.pfx -inkey /etc/ssl/private/ssl-cert-snakeoil.key -in /etc/ssl/certs/ssl-cert-snakeoil.pem -password pass:SnakeOil
    ```

### <a name="configure-rtvs-daemon"></a>Konfigurieren des RTVS-Daemons

Der Dateipfad des SSL-Zertifikats (Pfad zur PFX-Datei) muss in */etc/rtvs/rtvsd.config.json* festgelegt werden. Aktualisieren Sie `X509CertificateFile` und `X509CertificatePassword` mit dem Dateipfad bzw. mit dem Kennwort.

```json
{
  "logging": { "logFolder": "/tmp" },
  "security": {
    "allowedGroup": "",
    "X509CertificateFile": "/etc/rtvs/ssl-cert-snakeoil.pfx",
    "X509CertificatePassword": "SnakeOil"
  },
  "startup": { "name": "rtvsd" },
  "urls": "https://0.0.0.0:5444"
}
```

Speichern Sie die Datei, und starten Sie den Daemon folgendermaßen neu: `sudo systemctl restart rtvsd`.

## <a name="install-r-services-on-windows"></a>Installieren von R Services unter Windows

Um R-Code auszuführen, muss auf dem Remotecomputer ein R-Interpreter wie folgt installiert sein:

1. Laden Sie einen der folgenden herunter, und installieren Sie ihn:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [CRAN R für Windows](https://cran.r-project.org/bin/windows/base/)

     Beide verfügen über identische Funktionen, aber Microsoft R Open profitiert von zusätzlichen hardwarebeschleunigten Bibliotheken für Lineare Algebra, die durch die [Intel Math Kernel Library](https://software.intel.com/intel-mkl) bereitgestellt werden.

2. Führen Sie den [R Services-Installer](https://github.com/Microsoft/RTVS/blob/master/doc/rtvsd/rtvs-remote-downloads.md) aus, und starten Sie den Computer neu, wenn Sie dazu aufgefordert werden. Der Installer führt die folgenden Aktionen aus:

    - Erstellen Sie einen Ordner unter *%PROGRAMFILES%\R Tools for Visual Studio\1.0\\* , und kopieren Sie alle erforderlichen Binärdateien dorthin.
    - `RHostBrokerService` und `RUserProfileService` installieren und für den automatischen Start konfigurieren
    - Den `seclogon`-Dienst für automatischen Start konfigurieren
    - Fügen Sie *Microsoft.R.Host.exe* und *Microsoft.R.Host.Broker.exe* zu den eingehenden Firewallregeln auf dem Standardport 5444 hinzu.

R Services wird automatisch gestartet, wenn der Computer neu startet:

- Der **R-Hostbrokerdienst** verarbeitet den gesamten HTTPS-Datenverkehr zwischen Visual Studio und dem Prozess, in dem der R-Code auf dem Computer ausgeführt wird.
- **R User Profile Service** ist eine privilegierte Komponente, die für die Erstellung von Windows-Benutzerprofilen zuständig ist. Dieser Dienst wird aufgerufen, wenn ein neuer Benutzer sich zum ersten Mal auf dem R-Servercomputer anmeldet.

Sie können diese Dienste in der Diensteverwaltungskonsole (*compmgmt.msc*) anzeigen.

## <a name="install-r-services-on-linux"></a>Installieren von R Services unter Linux

Um R-Code auszuführen, muss auf dem Remotecomputer ein R-Interpreter wie folgt installiert sein:

1. Laden Sie einen der folgenden herunter, und installieren Sie ihn:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [CRAN R für Windows](https://cran.r-project.org/bin/linux/ubuntu/)

     Beide verfügen über identische Funktionen, aber Microsoft R Open profitiert von zusätzlichen hardwarebeschleunigten Bibliotheken für Lineare Algebra, die durch die [Intel Math Kernel Library](https://software.intel.com/intel-mkl) bereitgestellt werden.

2. Führen Sie die Anweisungen unter [Remote R Service für Linux](setting-up-remote-r-service-on-linux.md) aus, die physische Ubuntu-Computer, Azure Ubuntu-VMs, Windows-Subsystem für Linux (WSL) und Dockercontainer abdecken, einschließlich derer, die im Azure Container-Repository ausgeführt werden.

## <a name="configure-r-services"></a>Konfigurieren von R Services

Wenn R Services auf dem Remotecomputer ausgeführt wird, müssen Sie auch Benutzerkonten erstellen, Firewallregeln festlegen und Azure-Netzwerke sowie das SSL-Zertifikat konfigurieren.

1. Benutzerkonten: Erstellen Sie ein Konto für jeden Benutzer, der auf den Remotecomputer zugreift. Sie können entweder ein lokales Standardbenutzerkonto (ohne Berechtigungen) erstellen, oder Sie können Ihren R-Servercomputer mit Ihrer Domäne verknüpfen und der `Users`-Sicherheitsgruppe die angemessenen Sicherheitsgruppen hinzufügen.

1. Firewallregeln: `R Host Broker` lauscht standardmäßig an TCP-Port 5444. Daher müssen Sie sicherstellen, dass die Windows-Firewallregeln für eingehenden und ausgehenden Datenverkehr aktiviert sind (der ausgehende Verkehr ist für die Installation von Paketen und ähnliche Szenarios notwendig).  Der R Services-Installer legt diese Regeln automatisch für die integrierte Windows-Firewall fest. Wenn Sie eine Drittanbieter-Firewall verwenden, müssen Sie Port 5444 für den `R Host Broker` jedoch manuell öffnen.

1. Azure-Konfiguration: Wenn der Remotecomputer ein virtueller Azure-Computer ist, müssen Sie Port 5444 für eingehenden Datenverkehr auch innerhalb von Azure-Netzwerken öffnen, die unabhängig von der Windows-Firewall sind. Weitere Informationen finden Sie in der Azure-Dokumentation unter [Filtern des Netzwerkdatenverkehrs mit Netzwerksicherheitsgruppen](/azure/virtual-network/virtual-networks-nsg).

1. Weisen Sie den R-Hostbroker an, ein bestimmtes SSL-Zertifikat zu laden: Wenn Sie das Zertifikat auf einem Intranetserver installieren, ist der vollqualifizierte Domänenname Ihres Servers wahrscheinlich mit dem NETBIOS-Namen identisch. In diesem Fall müssen Sie nichts tun, da das Standardzertifikat geladen wird.

    Wenn Sie Ihr Zertifikat allerdings auf einem Server mit Internetzugriff (z.B. einer Azure-VM) installieren, verwenden Sie den vollqualifizierten Domänenname (Fully Qualified Domain Name, FQDN) des Servers, da der FQDN eines mit dem Internet verbundenen Servers nie mit dem NETBIOS-Namen übereinstimmt.

    Navigieren Sie zum Verwenden des FQDN zum Speicherort von R Services (standardmäßig *%PROGRAM FILES%\R Remote Service for Visual Studio\1.0*), öffnen Sie die Datei *Microsoft.R.Host.Broker.Config.json* in einem Text-Editor, ersetzen Sie deren Inhalt durch Folgendes, und weisen Sie dabei CN dem FQDN Ihres Servers zu, z.B. `foo.westus.cloudapp.azure.com`:

    ```json
    {
      "server.urls": "https://0.0.0.0:5444",
      "security": {
        "X509CertificateName": "CN=your-server-fully-qualified-domain-name"
      }
    }
    ```

    Speichern Sie die Datei, und starten Sie den Computer neu, um die Änderungen zu übernehmen.

## <a name="troubleshooting"></a>Problembehandlung

**F. Der R-Servercomputer reagiert nicht, was kann ich tun?**

Versuchen Sie, den Remotecomputer über die Befehlszeile zu pingen: `ping remote-machine-name`. Wenn der Ping fehlschlägt, stellen Sie sicher, dass der Computer angeschaltet ist.

**F. Das interaktive R-Fenster meldet, dass der Remotecomputer an ist. Aber warum wird der Dienst nicht ausgeführt?**

Es gibt drei mögliche Gründe:

- [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) oder höher ist nicht auf dem Computer installiert.
- Für eingehende und ausgehende Verbindungen an Port 5444 sind keine Firewallregeln für `Microsoft.R.Host.Broker` und `Microsoft.R.Host` aktiviert.
- Es wurde kein SSL-Zertifikat mit `CN=<remote-machine-name>` installiert.

Starten Sie den Computer nach einer der oben beschriebenen Änderungen neu. Stellen Sie dann sicher, dass `RHostBrokerService` und `RUserProfileService` entweder über den Task-Manager (Registerkarte „Dienste“) oder über *services.msc* ausgeführt werden.

**F. Warum meldet das interaktive Fenster während der Verbindungserstellung mit dem R-Server „401 Zugriff verweigert“?**

Es gibt zwei mögliche Ursachen:

- Es ist sehr wahrscheinlich, dass das `NETWORK SERVICE`-Konto keinen Zugriff auf den privaten Schlüssel des SSL-Zertifikats hat. Folgen Sie der vorherigen Anleitung, um sicherzustellen, dass `NETWORK SERVICE` Zugriff auf den privaten Schlüssel hat.
- Stellen Sie sicher, dass der `seclogon`-Dienst ausgeführt wird. Verwenden Sie *services.msc*, um `seclogon` für den automatischen Start zu konfigurieren.

**F. Warum meldet das interaktive Fenster während der Verbindungserstellung mit dem R-Server „404 Nicht gefunden“?**

Dieser Fehler liegt wahrscheinlich an fehlenden verteilbaren Visual C++-Bibliotheken. Überprüfen Sie das interaktive R-Fenster, um festzustellen, ob eine Meldung über eine fehlende Bibliothek (DLL) vorliegt. Überprüfen Sie dann, ob Visual C++ Redistributable für Visual Studio 2015 und R installiert sind.

**F. Ich kann über das interaktive R-Fenster nicht auf Internet/Ressource zugreifen. Was kann ich tun?**

Stellen Sie sicher, dass die Firewallregeln für `Microsoft.R.Host.Broker` und `Microsoft.R.Host` ausgehenden Zugriff auf Port 5444 zulassen. Starten Sie den Computer neu, nachdem Sie die Änderungen vorgenommen haben.

**F. Ich habe alle genannten Lösungen ausprobiert, und es funktioniert trotzdem nicht. Was nun?**

Durchsuchen Sie die Protokolldateien unter *C:\Windows\ServiceProfiles\NetworkService\AppData\Local\Temp*. Dieser Ordner enthält eine separate Protokolldatei für jede Instanz des R-Brokerdiensts, die ausgeführt wurde. Immer wenn der Dienst neu gestartet wird, wird eine neue Protokolldatei erstellt. Überprüfen Sie die aktuellste Protokolldatei auf Anzeichen, wo der Fehler liegen könnte.
