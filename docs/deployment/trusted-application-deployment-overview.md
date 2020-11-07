---
title: Übersicht über Bereitstellung vertrauenswürdiger Anwendungen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ClickOnce-Anwendungen mit erhöhten Berechtigungen mithilfe der Bereitstellungs Technologie für vertrauenswürdige Anwendungen bereitstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- ClickOnce deployment, security
- trusted application deployment
ms.assetid: b24a1702-8fbe-45b1-87a0-9618a0708f1d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96dfb98b468782f771d866b33b94b2c18de6276f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350490"
---
# <a name="trusted-application-deployment-overview"></a>Überblick über die Bereitstellung vertrauenswürdiger Anwendungen
Dieses Thema bietet einen Überblick über die Bereitstellung von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungen, die mithilfe der Technologie für die Bereitstellung einer vertrauenswürdigen Anwendung erweiterte Berechtigungen aufweisen.

 Die Bereitstellung einer vertrauenswürdigen Anwendung, Teil der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Bereitstellungstechnologie, erleichtert es Organisationen jeder Größe, einer verwalteten Anwendung zusätzliche Berechtigungen auf sichere Weise ohne Benutzereingabe zu gewähren. Mit der Bereitstellung einer vertrauenswürdigen Anwendung kann eine Organisation einfach einen Clientcomputer so konfigurieren, dass er über eine Liste der vertrauenswürdigen Herausgeber verfügt, die mithilfe von Authenticode-Zertifikaten identifiziert werden. Danach erhält jede [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung, die durch einen dieser vertrauenswürdigen Herausgeber signiert wurde, eine höhere Vertrauensebene.

> [!NOTE]
> Die Bereitstellung einer vertrauenswürdigen Anwendung erfordert eine einmalige Konfiguration des Computer des Benutzers. In verwalteten Desktopumgebungen kann diese Konfiguration mithilfe von globalen Richtlinien ausgeführt werden. Ist dies für Ihre Anwendung nicht wünschenswert, verwenden Sie stattdessen die Berechtigungserweiterung. Weitere Informationen finden Sie unter [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md).

## <a name="trusted-application-deployment-basics"></a>Grundlagen der Bereitstellung einer vertrauenswürdigen Anwendung
 Die folgende Tabelle zeigt die Objekte und die Rollen, die an der Bereitstellung einer vertrauenswürdigen Anwendung beteiligt sind.

|Objekt oder Rolle|BESCHREIBUNG|
|--------------------|-----------------|
|administrator|Die Entität in der Organisation, die verantwortlich für das Aktualisieren und Verwalten von Clientcomputern ist|
|trust manager|Das Subsystem innerhalb der Common Language Runtime (CLR), das verantwortlich für das Erzwingen der Anwendungssicherheit auf Clientcomputern ist.|
|publisher|Die Entität, die die Anwendung schreibt und verwaltet.|
|deployer|Die Entität, die Anwendung für Benutzer packt und an diese verteilt.|
|Zertifikat|Eine kryptografische Signatur, die aus einem öffentlichen und einem privaten Schlüssel besteht; wird im Allgemeinen von einer Zertifizierungsstelle (CA) ausgegeben, die für seine Echtheit bürgen kann.|
|Authenticode certificate|Ein Zertifikat mit eingebetteten Metadaten, das unter anderem die Verwendungsmöglichkeiten für das Zertifikat beschreibt.|
|certification authority|Eine Organisation, die die Identität eines Herausgebers überprüft und Zertifikate ausstellt, die in den Herausgebermetadaten eingebettet sind.|
|Stammzertifizierungsstelle|Eine Zertifizierungsstelle, die andere Zertifizierungsstellen zum Ausstellen von Zertifikaten autorisiert.|
|key container|Ein logischer Speicherplatz in Microsoft Windows zum Speichern von Zertifikaten.|
|trusted publisher|Ein Herausgeber, dessen Authenticode-Zertifikat zu einer Zertifikatsvertrauensliste (CTL) auf einem Clientcomputer hinzugefügt wurde.|

 In größeren Organisationen sind Herausgeber und Bereitsteller häufig zwei separate Entitäten:

- Der Herausgeber ist die Gruppe, die die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung erstellt.

- Der Bereitsteller ist die Gruppe, in der Regel der IT-Abteilung, die die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung auf Desktopcomputern im Unternehmen verteilt.

Führen Sie die folgenden Schritte aus, um die Bereitstellung einer vertrauenswürdigen Anwendung zu nutzen:

1. Rufen Sie ein Zertifikat für den Herausgeber ab.

2. Fügen Sie den Herausgeber zum Speicher für vertrauenswürdige Herausgeber auf allen Clients hinzu.

3. Erstellen Sie Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung.

4. Signieren Sie das Bereitstellungsmanifest mit dem Zertifikat des Herausgebers.

5. Veröffentlichen Sie die Anwendungsbereitstellung auf Clientcomputern.

### <a name="obtain-a-certificate-for-the-publisher"></a>Abrufen eines Zertifikats für den Herausgeber
 Digitale Zertifikate sind eine Kernkomponente des Microsoft Authenticode-Authentifizierungs- und Sicherheitssystems. Authenticode ist ein Standardbestandteil des Windows-Betriebssystems. Alle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungen müssen mit einem digitalen Zertifikat signiert werden, unabhängig davon, ob sie Teil einer Bereitstellung einer vertrauenswürdigen Anwendung sind. Eine vollständige Erläuterung der Funktionsweise von Authenticode mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] finden Sie unter [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md).

### <a name="add-the-publisher-to-the-trusted-publishers-store"></a>Hinzufügen des Herausgebers zum Speicher für vertrauenswürdige Herausgeber
 Damit die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung ein höheres Maß an Vertrauen erhält, müssen Sie das Zertifikat als vertrauenswürdiger Herausgeber auf jedem Clientcomputer hinzufügen, auf dem die Anwendung ausgeführt wird. Bei dieser Aufgabe handelt es sich um eine einmalige Konfiguration. Nachdem sie abgeschlossen wurde, können Sie beliebig viele [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungen bereitstellen, die mit dem Zertifikat Ihres Herausgebers signiert sind, und alle werden auf einer hohen Vertrauensebene ausgeführt.

 Wenn Sie Ihre Anwendung in einer verwalteten Desktopumgebung bereitstellen, zum Beispiel in einem Unternehmensintranet, in dem das Windows-Betriebssystem ausgeführt wird, können Sie vertrauenswürdige Herausgeber einem Clientspeicher hinzufügen, indem Sie eine neue Zertifikatsvertrauensliste (CTL) mithilfe von Gruppenrichtlinien erstellen. Weitere Informationen finden Sie unter [Erstellen einer Zertifikatvertrauensliste für ein Gruppenrichtlinienobjekt](/previous-versions/windows/it-pro/windows-server-2003/cc728449(v=ws.10)).

 Wenn Sie die Anwendung nicht in einer verwalteten Desktopumgebung bereitstellen, haben Sie die folgenden Optionen zum Hinzufügen eines Zertifikats zum Speicher vertrauenswürdiger Herausgeber:

- Der <xref:System.Security.Cryptography?displayProperty=fullName> -Namespace.

- *CertMgr.exe* , die eine Komponente von Internet Explorer ist und daher unter Windows 98 und allen späteren Versionen vorhanden ist. Weitere Informationen finden Sie unter [Certmgr.exe (Certificate Manager-Tool)](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool).

### <a name="create-a-clickonce-application"></a>Erstellen einer ClickOnce-Anwendung
 Bei einer- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung handelt es sich um eine .NET Framework Client Anwendung in Kombination mit Manifest-Dateien, die die Anwendung beschreiben und Installationsparameter angeben Sie können Ihr Programm in eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung mithilfe des Befehls **Veröffentlichen** in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]verwandeln. Alternativ können Sie alle erforderlichen Dateien für die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Bereitstellung mithilfe von Tools, die in [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]enthalten sind, generieren. Ausführliche Schritte zur Bereitstellung finden Sie unter Exemplarische Vorgehensweise [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] [: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

 Die Bereitstellung einer vertrauenswürdigen Anwendung gilt für [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]und kann nur mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungen verwendet werden.

### <a name="sign-the-deployment"></a>Signieren der Bereitstellung
 Nachdem Sie das Zertifikat erhalten haben, müssen Sie damit Ihre Bereitstellung signieren. Bei der Bereitstellung der Anwendung mithilfe des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Webpublishing-Assistenten generiert der Assistent automatisch ein Testzertifikat für Sie, wenn Sie kein Zertifikat selbst angegeben haben. Sie können auch das [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Projektdesignerfenster verwenden, allerdings um ein von einer Zertifizierungsstelle ausgestelltes Zertifikat bereitzustellen.  Siehe auch Gewusst [wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!CAUTION]
> Es wird davon abgeraten, die Anwendung mit einem Testzertifikat bereitzustellen.

 Sie können die Anwendung auch mit den SDK-Tools *Mage.exe* oder *MageUI.exe* signieren. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Eine vollständige Liste der Befehlszeilenoptionen im Zusammenhang mit der Bereitstellungs Signierung finden Sie unter [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

### <a name="publish-the-application"></a>Veröffentlichen der Anwendung
 Sobald Sie Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Manifeste signiert haben, kann die Anwendung am Installationsspeicherort veröffentlichen. Der Installationsspeicherort kann ein Webserver, eine Dateifreigabe oder die lokale Festplatte sein. Wenn ein Client zum ersten Mal auf das Bereitstellungsmanifest zugreift, muss der Trust-Manager auswählen, ob der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung durch einen installierten vertrauenswürdigen Herausgeber die Berechtigung erteilt wurde, auf einer höheren Vertrauensebene ausgeführt zu werden. Der Trust-Manager trifft diese Auswahl durch Vergleichen des Zertifikats zum Signieren der Bereitstellung mit den Zertifikaten im Speicher des vertrauenswürdigen Herausgebers des Clients. Wenn der Trust-Manager eine Übereinstimmung findet, wird die Anwendung mit hoher Vertrauenswürdigkeit ausgeführt.

## <a name="trusted-application-deployment-and-permission-elevation"></a>Bereitstellung einer vertrauenswürdigen Anwendung und Berechtigungserweiterung
 Ist der aktuelle Herausgeber kein vertrauenswürdiger Herausgeber, verwendet der Trust-Manager die Berechtigungserweiterung, um vom Benutzer zu erfahren, ob Ihrer Anwendung erweiterte Berechtigungen gewährt werden sollen. Wenn die Berechtigungserweiterung vom Administrator deaktiviert wurde, kann die Anwendung jedoch keine Berechtigung zum Ausführen erhalten. Die Anwendung wird nicht ausgeführt, und dem Benutzer wird keine Benachrichtigung angezeigt. Weitere Informationen zur Berechtigungs Erweiterung finden Sie unter [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md).

## <a name="limitations-of-trusted-application-deployment"></a>Einschränkungen der Bereitstellung einer vertrauenswürdigen Anwendung
 Sie können die Bereitstellung einer vertrauenswürdigen Anwendung verwenden, um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungen, die über das Internet oder über eine unternehmensweite Dateifreigabe bereitgestellt werden, eine erhöhte Vertrauensstellung zu gewähren. Sie müssen keine Bereitstellung einer vertrauenswürdigen Anwendung für [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungen verwenden, die auf einer CD verteilt werden, da diese Anwendungen standardmäßig die volle Vertrauenswürdigkeit erhalten haben.

## <a name="see-also"></a>Weitere Informationen
- [Mage.exe (Tool zum Generieren und Bearbeiten von Manifesten)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
