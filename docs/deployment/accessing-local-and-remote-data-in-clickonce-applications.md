---
title: Zugreifen auf lokale & Remote Daten (ClickOnce-Apps)
description: Erfahren Sie mehr über die verschiedenen Optionen, die ClickOnce zum Lesen und Schreiben von Daten bietet, sowohl lokal als auch Remote.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- data access, ClickOnce applications
ms.assetid: be5cbe12-6cb6-49c9-aa59-a1624e1eef3d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c8bc59fd1d47a04b2f4c6ec2be9b9adb035f11e2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837813"
---
# <a name="access-local-and-remote-data-in-clickonce-applications"></a>Zugreifen auf lokale und Remotedaten in einer ClickOnce-Anwendung
Die meisten Anwendungen nutzen oder generieren Daten. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bietet Ihnen eine Vielzahl von Optionen zum Lesen und Schreiben von Daten, sowohl lokal als auch remote.

## <a name="local-data"></a>Lokale Daten
 Mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]laden und speichern Sie Daten lokal mithilfe einer der folgenden Methoden:

- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Datenverzeichnis

- Isolierte Speicherung

- Andere lokale Dateien

### <a name="clickonce-data-directory"></a>ClickOnce-Datenverzeichnis
 Jede auf einem lokalen Computer installierte [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung verfügt über ein Datenverzeichnis, das im Ordner "Dokumente und Einstellungen" des Benutzers gespeichert ist. Jede in einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung enthaltene und als "Daten"-Datei gekennzeichnete Datei wird in dieses Verzeichnis kopiert, wenn eine Anwendung installiert wird. Datendateien können einen beliebigen Dateityp aufweisen. Zu den am häufigsten verwendeten gehören Text, XML und Datenbankdateien, z. B. Microsoft Access-MDB-Dateien.

 Das Datenverzeichnis ist für anwendungsverwaltete Daten konzipiert, d. h. für Daten, die die Anwendung explizit speichert und verwaltet. Alle statischen, unabhängigen Dateien, die im Anwendungsmanifest nicht als "Daten"gekennzeichnet sind, befinden sich dagegen im Anwendungsverzeichnis. Dieses Verzeichnis ist der Ort, an dem sich die ausführbaren Dateien (*.exe*) und die Assemblys der Anwendung befinden.

> [!NOTE]
> Wenn eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung deinstalliert wird, wird das zugehörige Datenverzeichnis ebenfalls entfernt. Verwenden Sie niemals das Datenverzeichnis, um durch den Endbenutzer verwaltete Daten, wie z.B. Dokumente, zu speichern.

#### <a name="mark-data-files-in-a-clickonce-distribution"></a>Markieren von Datendateien in einer ClickOnce-Verteilung
 Um eine vorhandene Datei im Datenverzeichnis abzulegen, müssen Sie sie in der Anwendungsmanifestdatei ihrer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung als Datendatei markieren. Weitere Informationen finden Sie unter Gewusst [wie: Einschließen einer Datendatei in eine ClickOnce-Anwendung](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

#### <a name="read-from-and-write-to-the-data-directory"></a>Lese-und Schreibzugriff auf das Datenverzeichnis
 Zum Lesen aus dem Datenverzeichnis muss Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung eine Leseberechtigung anfordern; analog dazu erfordert das Schreiben in das Verzeichnis eine Schreibberechtigung. Ihre Anwendung verfügt automatisch über diese Berechtigung, wenn sie für die Ausführung mit voller Vertrauenswürdigkeit konfiguriert ist. Weitere Informationen zum Erhöhen der Berechtigungen für Ihre Anwendung mithilfe der Berechtigungs Erweiterung oder der Bereitstellung vertrauenswürdiger Anwendungen finden Sie unter [sichere ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md).

> [!NOTE]
> Wenn Ihre Organisation die Bereitstellung vertrauenswürdiger Anwendungen nicht verwendet und die Berechtigungserweiterung deaktiviert hat, schlägt die Assertion der Berechtigungen fehl.

 Nachdem die Anwendung über diese Berechtigungen verfügt, kann sie auf das Datenverzeichnis zugreifen, indem sie Methodenaufrufe für Klassen innerhalb von <xref:System.IO>verwendet. Den Pfad des Datenverzeichnisses innerhalb einer Windows Forms [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung erhalten Sie mithilfe der in der <xref:System.Deployment.Application.ApplicationDeployment.DataDirectory%2A> -Eigenschaft von <xref:System.Deployment.Application.ApplicationDeployment.CurrentDeployment%2A> definierten <xref:System.Deployment.Application.ApplicationDeployment>-Eigenschaft. Dies ist die einfachste und empfohlene Möglichkeit, auf Ihre Daten zuzugreifen. Im folgenden Codebeispiel wird veranschaulicht, wie Sie mit einer Textdatei mit dem Namen *CSV.txt* vorgehen, die Sie als Datendatei in die Bereitstellung aufgenommen haben.

 [!code-csharp[ClickOnce.OpenDataFile#1](../deployment/codesnippet/CSharp/accessing-local-and-remote-data-in-clickonce-applications_1.cs)]
 [!code-vb[ClickOnce.OpenDataFile#1](../deployment/codesnippet/VisualBasic/accessing-local-and-remote-data-in-clickonce-applications_1.vb)]

 Weitere Informationen über die Kennzeichnung von Dateien in der Bereitstellung als Datendateien finden Sie unter [How to: Include a Data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

 Sie können den Pfad zum Datenverzeichnis auch mit den relevanten Variablen in der <xref:System.Windows.Forms.Application> -Klasse wie z. B. <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A>abrufen.

 Zum Bearbeiten anderer Typen von Dateien sind möglicherweise zusätzliche Berechtigungen erforderlich. Wenn Sie z *. b.* eine Access-Datenbankdatei (MDB-Datei) verwenden möchten, muss Ihre Anwendung volle Vertrauenswürdigkeit bestätigen, um die relevanten Klassen verwenden zu können \<xref:System.Data> .

#### <a name="data-directory-and-application-versions"></a>Datenverzeichnis und Anwendungsversionen
 Jede Version einer Anwendung hat ein eigenes Datenverzeichnis, das von anderen Versionen isoliert ist. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] erstellt dieses Verzeichnis unabhängig davon, ob Datendateien in der Bereitstellung enthalten sind, damit die Anwendung über einen Speicherort verfügt, um neue Datendateien zur Laufzeit zu erstellen. Wenn eine neue Version einer Anwendung installiert wird, kopiert [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] alle vorhandenen Datendateien aus dem Datenverzeichnis vorherigen Version in das der neuen Version – unabhängig davon, ob sie in der ursprünglichen Bereitstellung enthalten waren oder von der Anwendung erstellt wurden.

 Wenn eine Datendatei in der alten Version der Anwendung über einen anderen Hash-Wert als in der neuen Version verfügt, ersetzt[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] die ältere Version der Datei durch die neuere Version des Servers. Auch wenn die frühere Version der Anwendung eine neue Datei mit demselben Namen wie dem einer Datei in der Bereitstellung der neuen Version erstellt hat, überschreibt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] die Datei der alten Version. In beiden Fällen werden die alten Dateien in ein Unterverzeichnis des Datenverzeichnisses mit dem Namen `.pre`eingeschlossen, sodass die Anwendung zu Migrationszwecken weiterhin auf die alten Daten zugreifen kann.

 Wenn Sie eine umfassendere Migration von Daten benötigen, können Sie die API für die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Bereitstellung verwenden, um eine benutzerdefinierte Migration vom alten zum neuen Datenverzeichnis durchzuführen. Dabei suchen Sie zunächst mithilfe von <xref:System.Deployment.Application.ApplicationDeployment.IsFirstRun%2A>einen verfügbaren Download, laden das Update mit <xref:System.Deployment.Application.ApplicationDeployment.Update%2A> oder <xref:System.Deployment.Application.ApplicationDeployment.UpdateAsync%2A>herunter und führen nach abgeschlossenem Update die benutzerdefinierten Schritte zur Datenmigration selbst aus.

### <a name="isolated-storage"></a>Isolierter Speicher
 Die isolierte Speicherung stellt eine API für das Erstellen und den Zugriff auf Dateien über eine einfache API bereit. Der tatsächliche Speicherort der Dateien wird für den Entwickler und Benutzer ausgeblendet.

 Isolierter Speicher funktioniert in allen Versionen der .NET Framework. Isolierte Speicherung funktioniert auch in teilweise vertrauenswürdigen Anwendungen, ohne dass zusätzliche Berechtigungen gewährt werden müssen. Sie sollten isolierte Speicherung verwenden, wenn Ihre Anwendung unter teilweiser Vertrauenswürdigkeit ausgeführt werden, dabei aber anwendungsspezifische Daten verwalten muss.

 Weitere Informationen finden Sie unter [Isolierte Speicherung](/dotnet/standard/io/isolated-storage).

### <a name="other-local-files"></a>Andere lokale Dateien
 Wenn Ihre Anwendung mit Daten von Endbenutzern wie z. B. Berichten, Bildern, Musik usw. arbeiten oder solche Daten speichern muss, benötigt sie <xref:System.Security.Permissions.FileIOPermission> , um Daten im lokalen Dateisystem zu lesen oder in dieses zu schreiben.

## <a name="remote-data"></a>Remotedaten
 An einem gewissen Punkt wird die Anwendung wahrscheinlich Informationen von einer Remotewebsite, wie z. B. Kundendaten oder Marktinformationen, abrufen müssen. Dieser Abschnitt beschreibt die am häufigsten verwendeten Techniken für das Abrufen von Remotedaten.

### <a name="access-files-with-http"></a>Zugreifen auf Dateien mit http
 Sie können auf Daten von einem Webserver zugreifen, indem Sie entweder den <xref:System.Net.WebClient> oder die <xref:System.Net.HttpWebRequest> -Klasse im <xref:System.Net> -Namespace verwenden. Bei den Daten kann es sich entweder um statische Dateien oder [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -Anwendungen handeln, die unformatierten Text oder XML-Daten zurückgeben. Daten im XML-Format können Sie am schnellsten mithilfe der <xref:System.Xml.XmlDocument> -Klasse abrufen, deren <xref:System.Xml.XmlDocument.Load%2A> -Methode eine URL als Argument verwendet. Ein Beispiel finden Sie unter [Lesen eines XML-Dokuments in das DOM](/dotnet/standard/data/xml/reading-an-xml-document-into-the-dom).

 Wenn die Anwendung über HTTP auf Remotedaten zugreift, spielt auch Sicherheit eine Rolle. Der Zugriff der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung auf Netzwerkressourcen ist möglicherweise standardmäßig beschränkt. Dies hängt davon ab, wie die Anwendung bereitgestellt wurde. Diese Beschränkungen sollen verhindern, dass bösartige Programme Zugriff auf privilegierte Remotedaten erhalten oder über einen Benutzercomputer andere Computer im Netzwerk angreifen.

 In der folgenden Tabelle werden mögliche Bereitstellungsstrategien sowie die entsprechenden Standardwebberechtigungen aufgelistet.

|Bereitstellungstyp|Standardmäßige Netzwerkberechtigungen|
|---------------------|---------------------------------|
|Webinstallation|Kann nur auf den Webserver zugreifen, von dem die Anwendung installiert wurde.|
|Installation von Dateifreigabe|Kann auf keine Webserver zugreifen.|
|Installation von CD-ROM|Kann auf jeden beliebigen Webserver zugreifen.|

 Wenn die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung aufgrund von Sicherheitsbeschränkungen nicht auf einen Webserver zugreifen kann, muss die Anwendung <xref:System.Net.WebPermission> für diese Website bestätigen. Weitere Informationen zum erhöhen von Sicherheits Berechtigungen für eine- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung finden Sie unter [sichere ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md).

### <a name="access-data-through-an-xml-web-service"></a>Zugreifen auf Daten über einen XML-Webdienst
 Wenn Sie Daten als XML-Webdienst verfügbar machen, können Sie mithilfe eines XML-Webdienstproxys auf die Daten zugreifen. Der Proxy ist eine .NET Framework Klasse, die Sie mithilfe von erstellen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Die Vorgänge des XML-Webdienstes, z. B. Abrufen von Kunden, Aufgeben von Bestellungen usw., werden als Methoden für den Proxy verfügbar gemacht. Dadurch sind Webdienste viel benutzerfreundlicher als unformatierter Text oder XML-Dateien.

 Wenn ein XML-Webdienst über HTTP ausgeführt wird, gelten für den Dienst dieselben Sicherheitsbeschränkungen wie für die <xref:System.Net.WebClient> -Klasse und die <xref:System.Net.HttpWebRequest> -Klasse.

### <a name="access-a-database-directly"></a>Direktes Zugreifen auf eine Datenbank
 Mithilfe der Klassen im <xref:System.Data> -Namespace können Sie direkte Verbindungen zu einem Datenbankserver im Netzwerk herstellen, z. B. SQL Server, allerdings sind dabei bestimmte Sicherheitsaspekte zu berücksichtigen. Anders als HTTP-Anforderungen sind Datenbankverbindungsanforderungen in einer teilweise vertrauenswürdigen Umgebung standardmäßig unzulässig. Über die entsprechenden Berechtigungen verfügen Sie standardmäßig nur dann, wenn Sie die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung von einer CD-ROM installiert haben. Dadurch erhalten Anwendungen volle Vertrauenswürdigkeit. Um den Zugriff auf eine bestimmte SQL Server-Datenbank zu ermöglichen, muss die Anwendung <xref:System.Data.SqlClient.SqlClientPermission> für diese Datenbank anfordern. Für den Zugriff auf andere Datenbanken als SQL Server muss <xref:System.Data.OleDb.OleDbPermission>angefordert werden.

 In den meisten Fällen ist ein direkter Zugriff auf die Datenbank nicht erforderlich, sondern der Zugriff erfolgt über eine in [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] geschriebene Webserveranwendung oder einen XML-Webdienst. Diese Art des Datenbankzugriffs ist häufig die beste Methode, wenn die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung über einen Webserver bereitgestellt wird. Sie können auf den als teilweise vertrauenswürdig eingestuften Server zugreifen, ohne dass die Berechtigungen der Anwendung erweitert werden müssen.

## <a name="see-also"></a>Weitere Informationen

- [Gewusst wie: Einschließen einer Datendatei in eine ClickOnce-Anwendung](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)