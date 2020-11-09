---
title: ClickOnce und Authenticode | Microsoft-Dokumentation
description: Informationen zu Zertifikaten, die Authenticode verwendet, um die Authentizität von Anwendungen zu überprüfen. Erfahren Sie, wie Zertifikate überprüft und gespeichert werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- .pfx files
- ClickOnce deployment, Authenticode
- Authenticode, ClickOnce
- ClickOnce deployment, certificates
- ClickOnce deployment, security
ms.assetid: ab5b6712-f32a-4e33-842f-e88ab4818ccf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 07b40cb9c4e1d79390bb4a0541e1cb5bd8862d3a
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383143"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce und Authenticode
*Authenticode* ist eine Microsoft-Technologie, die mithilfe von Industriestandard-Kryptografie Anwendungscode mit digitalen Zertifikaten signiert, die die Echtheit des Herausgebers der Anwendung bestätigen. Durch die Verwendung von Authenticode bei der Bereitstellung einer Anwendung reduziert [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] das Risiko eines trojanischen Pferdes. Ein trojanisches Pferd ist ein Virus oder ein schädliches Programm, das ein böswilliger Drittanbieter als sicheres Programm aus einer bekannten und vertrauenswürdigen Quelle darstellt. Signieren von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Bereitstellungen mit einem digitalen Zertifikat ist ein optionaler Schritt, um sicherzustellen, dass die Assemblys und Dateien nicht manipuliert wurden.

 In den folgenden Abschnitten sind die verschiedenen Typen von digitalen Zertifikaten beschrieben, die in Authenticode verwendet werden, wie Zertifikate durch Zertifizierungsstellen (CAs) überprüft werden, die Rolle des Zeitstempels in Zertifikaten und die Methoden des verfügbaren Speichers für Zertifikate.

## <a name="authenticode-and-code-signing"></a>Authenticode und Codesignatur
 Ein *digitales Zertifikat* ist eine Datei, die ein öffentliches/privates kryptografisches Schlüsselpaar enthält sowie Metadaten über den Herausgeber, für den das Zertifikat ausgestellt wurde, und die Agentur, die das Zertifikat ausgestellt hat.

 Es gibt viele verschiedene Arten von Authenticode-Zertifikaten. Jedes ist für unterschiedliche Arten von Signaturen konfiguriert. Für [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungen benötigen Sie ein Authenticode-Zertifikat, das zum Signieren von Code gültig ist. Wenn Sie versuchen, eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung mit einem anderen Typ von Zertifikat zu signieren, z.B. einem digitalen Zertifikat für E-Mail, funktioniert dies nicht. Weitere Informationen finden Sie unter [Einführung in die Code Signatur](/windows/desktop/seccrypto/cryptography-tools).

 Sie können ein Zertifikat für Codesignaturen auf eine von drei Arten abrufen:

- Sie erwerben es von einem Zertifikatsanbieter.

- Sie erhalten es von einer Abteilung in Ihrem Unternehmen, die für das Erstellen von digitalen Zertifikaten verantwortlich ist.

- Generieren Sie ein eigenes Zertifikat mithilfe des New-SelfSignedCertificate PowerShell-Cmdlets oder mithilfe *MakeCert.exe* , das im Lieferumfang von enthalten ist [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] .

### <a name="how-using-certificate-authorities-helps-users"></a>Wie die Verwendung von Zertifizierungsstellen Benutzern hilft
 Ein mit New-SelfSignedCertificate oder dem *MakeCert.exe* -Hilfsprogramm generiertes Zertifikat wird häufig als *selbst Zertifikat* oder *Test* Zertifikat bezeichnet. Diese Art von Zertifikat funktioniert ähnlich wie eine *SNK* -Datei im .NET Framework. Es besteht ausschließlich aus einem kryptografischen öffentlichen/privaten Schlüsselpaar und enthält keine überprüfbaren Informationen zum Herausgeber. Sie können selbst signierte Zertifikate zum Bereitstellen von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungen mit hoher Vertrauenswürdigkeit in einem Intranet verwenden. Beim Ausführen dieser Anwendungen auf einem Clientcomputer wird [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sie jedoch als von einem unbekannten Herausgeber stammend identifizieren. In der Standardeinstellung können [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Applikationen, die mit selbst signierten Zertifikaten signiert und über das Internet bereitgestellt sind, keine vertrauenswürdige Anwendungsbereitstellung nutzen.

 Wenn Sie dagegen ein Zertifikat von einer Zertifizierungsstelle erhalten, zum Beispiel von einem Zertifikatsanbieter oder einer Abteilung in Ihrem Unternehmen, bietet dieses Zertifikat mehr Sicherheit für Ihre Benutzer. Es identifiziert nicht nur den Herausgeber der signierten Software, sondern überprüft dessen Identität durch Abgleich mit den Daten der Zertifizierungsstelle, die es signiert hat. Wenn die Zertifizierungsstelle nicht die Stammzertifizierungsstelle ist, wird Authenticode auch zurück zur Stammzertifizierungsstelle „verketten“, um zu überprüfen, ob die Zertifizierungsstelle zum Ausstellen von Zertifikaten autorisiert ist. Aus Sicherheitsgründen sollten Sie möglichst ein Zertifikat von einer Zertifizierungsstelle verwenden.

 Weitere Informationen zum Erstellen von selbst Zertifikaten finden Sie unter [New-selfsignedcertificate](/powershell/module/pkiclient/new-selfsignedcertificate) oder [Makecert](/windows/desktop/SecCrypto/makecert).

### <a name="timestamps"></a>Zeitstempel
 Die Zertifikate zum Signieren von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Applikationen laufen nach einem bestimmten Zeitraum ab, in der Regel zwölf Monate. Um nicht ständig mit neuen Zertifikaten neu signieren zu müssen, unterstützt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Timestamps (Zeitstempel). Wenn eine Anwendung mit einem Zeitstempel versehen ist, wird ihr Zertifikat auch nach Ablauf der Gültigkeit des Zertifikats akzeptiert, vorausgesetzt, dass der Zeitstempel gültig ist. Dadurch können [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungen mit abgelaufenen Zertifikaten, aber gültigen Zeitstempeln, heruntergeladen und ausgeführt werden. Außerdem können installierte Programme mit abgelaufenen Zertifikaten weiterhin Updates herunterladen und installieren.

 Um einen Zeitstempel in einen Anwendungsserver einzuschließen, muss ein Timestampserver verfügbar sein. Weitere Informationen zum Auswählen eines Timestampservers finden Sie unter [How to: Sign Application and Deployment Manifests](../ide/how-to-sign-application-and-deployment-manifests.md).

### <a name="update-expired-certificates"></a>Abgelaufene Zertifikate aktualisieren
 In früheren Versionen von .NET Framework verursachte das Aktualisieren einer Anwendung, deren Zertifikat abgelaufen war, den Absturz dieser Anwendung. Sie können eine der folgenden Methoden verwenden, um dieses Problem zu lösen:

- Aktualisieren Sie .NET Framework auf Version 2.0 SP1 oder höher auf Windows XP oder Version 3.5 oder höher auf Windows Vista.

- Deinstallieren Sie die Anwendung, und installieren Sie eine neue Version mit einem gültigen Zertifikat.

### <a name="store-certificates"></a>Zertifikate speichern

- Sie können Zertifikate als *PFX* -Datei im Dateisystem speichern oder in einem Schlüsselcontainer speichern. Ein Benutzer auf einer Windows-Domäne kann über mehrere Schlüsselcontainer verfügen. Standardmäßig werden von *MakeCert.exe* Zertifikate in Ihrem persönlichen Schlüssel Container gespeichert, es sei denn, Sie geben an, dass Sie stattdessen in einer *PFX* -Datei gespeichert werden sollen. *Mage.exe* und *MageUI.exe* , die [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]-Tools zum Erstellen von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Bereitstellungen, ermöglichen es Ihnen, auf beide Arten gespeicherte Zertifikate zu verwenden.

## <a name="see-also"></a>Siehe auch
- [ClickOnce-Sicherheit und-Bereitstellung](../deployment/clickonce-security-and-deployment.md)
- [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)
- [Übersicht über bereit Stellungen vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md)
- [Mage.exe (Tool zum Generieren und Bearbeiten von Manifesten)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)