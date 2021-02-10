---
title: Feld "vertrauenswürdiger Verleger zum Client hinzufügen" (ClickOnce)
description: Erfahren Sie, wie Sie einem Client Computer ein Zertifikat hinzufügen, damit Ihre ClickOnce-Anwendungen mit einer höheren Vertrauens Ebene ausgeführt werden, ohne dass der Benutzer dazu aufgefordert wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c04b8d700d7739f0e4ef1fba259aab0595cea28c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947813"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Vorgehensweise: Hinzufügen eines vertrauenswürdigen Herausgebers zu einem Clientcomputer für ClickOnce-Anwendungen
Mit der Bereitstellung einer vertrauenswürdigen Anwendung können Sie Clientcomputer so konfigurieren, dass Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungen mit einer höheren Vertrauensebene ausgeführt werden ohne den Benutzer dazu aufzufordern. Die folgenden Verfahren zeigen, wie das Befehlszeilentool CertMgr.exe verwendet wird, um das Zertifikat des Herausgebers zum Speicher für vertrauenswürdige Herausgeber auf einem Clientcomputer hinzuzufügen.

 Die von Ihnen verwendeten Befehle weichen leicht davon ab, je nachdem ob die Zertifizierungsstelle, die Ihr Zertifikat herausgegeben hat, Teil eines vertrauenswürdigen Stamms eines Clients ist. Wenn ein Windows-Clientcomputer Teil einer Domäne ist, enthält er in einer Liste Zertifizierungsstellen, die als vertrauenswürdige Stämme gelten. Diese Liste wird normalerweise vom Systemadministrator konfiguriert. Wenn das Zertifikat von einer der vertrauenswürdigen Stämmen oder von einer Zertifizierungsstelle herausgegeben wurde, die mit einer dieser vertrauenswürdigen Stämme verknüpft ist, können Sie das Zertifikat zum vertrauenswürdigen Stammspeicher des Clients hinzufügen. Wenn andererseits das Zertifikat nicht von einem dieser vertrauenswürdigen Stämme ausgestellt wurde, müssen Sie das Zertifikat jeweils dem vertrauenswürdigen Stammspeicher des Clients und dem Speicher des vertrauenswürdigen Herausgebers hinzufügen.

> [!NOTE]
> Sie müssen Zertifikate auf diese Weise jedem Clientcomputer hinzufügen, auf dem Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung bereitstellen möchten, die erweiterte Berechtigungen erfordert. Sie können die Zertifikate entweder manuell oder über eine Anwendung hinzufügen, die Sie für Ihre Clients bereitstellen. Sie müssen diese Computer nur einmal konfigurieren. Danach können Sie eine beliebige Anzahl von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungen signiert mit demselben Zertifikat bereitstellen.

 Sie können ein Zertifikat auch mithilfe der Klasse <xref:System.Security.Cryptography.X509Certificates.X509Store> programmgesteuert zu einem Speicher hinzufügen.

 Einen Überblick über die Bereitstellung vertrauenswürdiger Anwendungen finden Sie unter [Übersicht über die Bereitstellung vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md)

### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>So fügen Sie ein Zertifikat zum Speicher für vertrauenswürdige Herausgeber unter dem vertrauenswürdigen Stamm hinzu

1. Abrufen eines digitales Zertifikats von einer Zertifizierungsstelle.

2. Exportieren Sie das Zertifikat in das Format Base64 X. 509 (*. CER*). Weitere Informationen zu Zertifikat Formaten finden Sie unter [Exportieren eines Zertifikats](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730988(v=ws.10)).

3. Führen Sie über die Eingabeaufforderung auf Clientcomputern den folgenden Befehl aus:

     **certmgr.exe -add certificate.cer -c -s -r localMachine TrustedPublisher**

### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>So fügen Sie ein Zertifikat zum Speicher für vertrauenswürdige Herausgeber unter einem anderen Stamm hinzu

1. Abrufen eines digitales Zertifikats von einer Zertifizierungsstelle.

2. Exportieren Sie das Zertifikat in das Format Base64 X. 509 (*. CER*). Weitere Informationen zu den Zertifikatformaten finden Sie unter [Exportieren eines Zertifikats](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730988(v=ws.10)).

3. Führen Sie über die Eingabeaufforderung auf Clientcomputern den folgenden Befehl aus:

     **certmgr.exe -add good.cer -c -s -r localMachine Root**

     **certmgr.exe -add good.cer -c -s -r localMachine TrustedPublisher**

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)
- [Codezugriffssicherheit für ClickOnce-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md)
- [Übersicht über das Bereitstellen vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md)
- [Gewusst wie: Aktivieren von ClickOnce-Sicherheitseinstellungen](../deployment/how-to-enable-clickonce-security-settings.md)
- [Vorgehensweise: Festlegen einer Sicherheitszone für eine ClickOnce-Anwendung](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Gewusst wie: Festlegen benutzerdefinierter Berechtigungen für eine ClickOnce-Anwendung](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Gewusst wie: Debuggen einer ClickOnce-Anwendung mit eingeschränkten Berechtigungen](securing-clickonce-applications.md)
- [Vorgehensweise: Hinzufügen eines vertrauenswürdigen Herausgebers zu einem Clientcomputer für ClickOnce-Anwendungen](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Vorgehensweise: Erneutes Signieren von Anwendungs- und Bereitstellungsmanifesten](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
- [Gewusst wie: Konfigurieren des Verhaltens der ClickOnce-Vertrauens Aufforderung](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)