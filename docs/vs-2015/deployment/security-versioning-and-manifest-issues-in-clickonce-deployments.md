---
title: Probleme mit Sicherheit, Versionsverwaltung und Manifesten in ClickOnce-bereit Stellungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- versioning, ClickOnce applications
- ClickOnce applications, Windows Vista User Account Control
- ClickOnce applications, versioning issues
- security, ClickOnce applications
- Windows 7, ClickOnce deployments
- ClickOnce applications, manifest issues
- User Account Control, ClickOnce applications
- Windows Vista, ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, security issues
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4864d37cb5930075b292ee765bce9b288794019
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840976"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Probleme mit Sicherheit, Versionsverwaltung und Manifesten in ClickOnce-Bereitstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Es gibt eine Vielzahl von Problemen mit der [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Sicherheit, der Anwendungs Versionsverwaltung und der Manifestressource und der Semantik, die dazu führen können, dass eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellung nicht erfolgreich ist.  
  
## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce-und Windows Vista-Benutzerkontensteuerung  
 In [!INCLUDE[windowsver](../includes/windowsver-md.md)] werden Anwendungen standardmäßig als Standardbenutzer ausgeführt, auch wenn der aktuelle Benutzer mit einem Konto angemeldet ist, das über Administrator Berechtigungen verfügt. Wenn eine Anwendung eine Aktion ausführen muss, für die Administrator Berechtigungen erforderlich sind, wird dem Betriebssystem mitgeteilt, dass der Benutzer aufgefordert wird, seine Administrator Anmelde Informationen einzugeben. Diese Funktion mit dem Namen Benutzerkontensteuerung (User Account Control, UAC) verhindert, dass Anwendungen Änderungen vornehmen, die das gesamte Betriebssystem ohne explizite Genehmigung des Benutzers beeinträchtigen können. Windows-Anwendungen deklarieren, dass Sie diese Berechtigungs Erweiterung benötigen, indem Sie das- `requestedExecutionLevel` Attribut im- `trustInfo` Abschnitt Ihres Anwendungs Manifests angeben.  
  
 Aufgrund des Risikos, dass Anwendungen für Angriffe durch Sicherheitserweiterungen verfügbar gemacht werden, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] können Anwendungen keine Berechtigungs Erweiterung anfordern, wenn die UAC für den Client aktiviert ist. Jede [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung, die versucht, das zugehörige- `requestedExecutionLevel` Attribut auf oder zu `requireAdministrator` `highestAvailable` installieren [!INCLUDE[windowsver](../includes/windowsver-md.md)] .  
  
 In einigen Fällen kann es vorkommen, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dass Ihre Anwendung mit Administrator Berechtigungen ausgeführt wird, da die installationserkennungs-Logik für installiert ist [!INCLUDE[windowsver](../includes/windowsver-md.md)] . In diesem Fall können Sie das- `requestedExecutionLevel` Attribut im Anwendungs Manifest auf festlegen `asInvoker` . Dies bewirkt, dass die Anwendung selbst ohne Rechte Erweiterung ausgeführt wird. [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] fügt dieses Attribut automatisch allen Anwendungs Manifesten hinzu.  
  
 Wenn Sie eine Anwendung entwickeln, für die für die gesamte Lebensdauer der Anwendung Administrator Berechtigungen erforderlich sind, sollten Sie stattdessen die Bereitstellung der Anwendung mithilfe von Windows Installer-Technologie (MSI) in Erwägung gezogen. Weitere Informationen finden Sie unter [Windows Installer Grundlagen](../extensibility/internals/windows-installer-basics.md).  
  
## <a name="online-application-quotas-and-partial-trust-applications"></a>Online-Anwendungs Kontingente und teilweise vertrauenswürdige Anwendungen  
 Wenn die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung nicht über eine Installation, sondern online ausgeführt wird, muss Sie in das Kontingent passen, das für Online Anwendungen reserviert wurde. Außerdem darf eine Netzwerk Anwendung, die mit teilweiser Vertrauenswürdigkeit ausgeführt wird, z. b. mit einem eingeschränkten Satz von Sicherheits Berechtigungen, nicht größer als die Hälfte der Kontingent Größe sein.  
  
 Weitere Informationen und Anweisungen zum Ändern des Online Anwendungs Kontingents finden Sie unter Übersicht über den [ClickOnce-Cache](../deployment/clickonce-cache-overview.md).  
  
## <a name="versioning-issues"></a>Versions Probleme  
 Möglicherweise treten Probleme auf, wenn Sie der Assembly starke Namen zuweisen und die Versionsnummer der Assembly erhöhen, um eine Anwendungs Aktualisierung widerzuspiegeln. Jede Assembly, die mit einem Verweis auf eine Assembly mit starkem Namen kompiliert wird, muss selbst neu kompiliert werden, oder die Assembly versucht, auf die ältere Version zu verweisen. Die Assembly wird dies versuchen, da die Assembly den alten Versions Wert in der Bindungs Anforderung verwendet.  
  
 Nehmen wir beispielsweise an, dass Sie eine Assembly mit starkem Namen in einem eigenen Projekt mit der Version 1.0.0.0 haben. Nachdem Sie die Assembly kompiliert haben, fügen Sie Sie als Verweis auf das Projekt hinzu, das Ihre Hauptanwendung enthält. Wenn Sie die Assembly aktualisieren, die Version auf 1.0.0.1 erhöhen und versuchen, Sie bereitzustellen, ohne dass die Anwendung auch neu kompiliert wird, kann die Anwendung die Assembly zur Laufzeit nicht laden.  
  
 Dieser Fehler kann nur auftreten, wenn Sie die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Manifeste manuell bearbeiten. dieser Fehler sollte nicht auftreten, wenn Sie die Bereitstellung mit generieren [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] .  
  
## <a name="specifying-individual-net-framework-assemblies-in-the-manifest"></a>Angeben einzelner .NET Framework Assemblys im Manifest  
 Die Anwendung kann nicht geladen werden, wenn Sie eine Bereitstellung manuell bearbeitet haben [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , um auf eine ältere Version einer Assembly zu verweisen [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Wenn Sie z. b. einen Verweis auf die System.NET-Assembly für eine Version von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] vor der im Manifest angegebenen Version hinzugefügt haben, tritt ein Fehler auf. Im Allgemeinen sollten Sie nicht versuchen, Verweise auf einzelne Assemblys anzugeben [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , da die Version von, für [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] die die Anwendung ausgeführt wird, als Abhängigkeit im Anwendungs Manifest angegeben wird.  
  
## <a name="manifest-parsing-issues"></a>Probleme bei der Manifeste-Verarbeitung  
 Die Manifestressourcen, die von verwendet werden [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , sind XML-Dateien, und Sie müssen beide wohl geformt und gültig sein: Sie müssen die XML-Syntax Regeln einhalten und nur im relevanten XML-Schema definierte Elemente und Attribute verwenden.  
  
 Etwas, das in einer Manifestressource Probleme verursachen kann, ist die Auswahl eines Namens für die Anwendung, die ein Sonderzeichen enthält, z. b. ein einzelnes oder doppeltes Anführungszeichen. Der Name der Anwendung ist Teil seiner [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Identität. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] analysiert derzeit keine Identitäten, die Sonderzeichen enthalten. Wenn die Anwendung nicht aktiviert werden kann, stellen Sie sicher, dass Sie nur alphabetische und numerische Zeichen für den Namen verwenden, und versuchen Sie, die Anwendung erneut bereitzustellen.  
  
 Wenn Sie Ihre Bereitstellungs-oder Anwendungs Manifeste manuell bearbeitet haben, haben Sie Sie möglicherweise unbeabsichtigt beschädigt. Durch ein beschädigtes Manifest wird eine korrekte [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Installation verhindert. Sie können solche Fehler zur Laufzeit debuggen, indem Sie im Dialogfeld **ClickOnce-Fehler** auf **Details** klicken und die Fehlermeldung im Protokoll lesen. Im Protokoll wird eine der folgenden Meldungen angezeigt:  
  
- Eine Beschreibung des Syntax Fehlers und die Zeilennummer und Zeichenposition, an der der Fehler aufgetreten ist.  
  
- Der Name eines Elements oder Attributs, das als Verstoß gegen das Schema des Manifests verwendet wird. Wenn Sie ihren Manifesten XML manuell hinzugefügt haben, müssen Sie die Ergänzungen mit den manifestressschemas vergleichen. Weitere Informationen finden Sie unter [ClickOnce-Bereitstellungs Manifest](../deployment/clickonce-deployment-manifest.md) und [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md).  
  
- Ein ID-Konflikt. Abhängigkeits Verweise in Bereitstellungs-und Anwendungs Manifesten müssen in Ihren `name` -und-Attributen eindeutig sein `publicKeyToken` . Wenn beide Attribute zwischen zwei Elementen innerhalb eines Manifests Stimmen, wird die Manifeste-Verarbeitung nicht erfolgreich durchgeführt.  
  
## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Vorsichtsmaßnahmen beim manuellen Ändern von Manifesten oder Anwendungen  
 Wenn Sie ein Anwendungs Manifest aktualisieren, müssen Sie sowohl das Anwendungs Manifest als auch das Bereitstellungs Manifest neu signieren. Das Bereitstellungs Manifest enthält einen Verweis auf das Anwendungs Manifest, das den Hash der Datei und Ihre digitale Signatur enthält.  
  
### <a name="precautions-with-deployment-provider-usage"></a>Vorsichtsmaßnahmen bei Verwendung des Bereitstellungs Anbieters  
 Das [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellungs Manifest verfügt über eine- `deploymentProvider` Eigenschaft, die auf den vollständigen Pfad des Speicher Orts verweist, von dem die Anwendung installiert und gewartet werden soll:  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 Dieser Pfad wird festgelegt, wenn [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] die Anwendung von erstellt wird und für installierte Anwendungen obligatorisch ist. Der Pfad zeigt auf den Standard Speicherort, an dem das [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Installationsprogramm die Anwendung installiert und nach Updates sucht. Wenn Sie den **xcopy** -Befehl verwenden, um eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung an einen anderen Speicherort zu kopieren, ohne die Eigenschaft zu ändern `deploymentProvider` , [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wird beim Versuch, die Anwendung herunterzuladen, weiterhin auf den ursprünglichen Speicherort zurückverwiesen.  
  
 Wenn Sie eine Anwendung verschieben oder kopieren möchten, müssen Sie auch den Pfad aktualisieren `deploymentProvider` , damit der Client tatsächlich vom neuen Speicherort installiert wird. Wenn Sie Anwendungen installiert haben, ist das Aktualisieren dieses Pfades größtenteils von Bedeutung. Bei Online Anwendungen, die immer über die ursprüngliche URL gestartet werden, ist das Festlegen von `deploymentProvider` optional. Wenn `deploymentProvider` festgelegt ist, wird Sie berücksichtigt. andernfalls wird die URL, die zum Starten der Anwendung verwendet wird, als Basis-URL zum Herunterladen von Anwendungs Dateien verwendet.  
  
> [!NOTE]
> Jedes Mal, wenn Sie das Manifest aktualisieren, müssen Sie es auch erneut signieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Problembehandlung bei ClickOnce-bereit Stellungen](../deployment/troubleshooting-clickonce-deployments.md)   
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md)
