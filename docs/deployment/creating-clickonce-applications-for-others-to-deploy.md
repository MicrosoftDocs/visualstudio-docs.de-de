---
title: Erstellen von ClickOnce-Anwendungen für die Bereitstellung durch andere Benutzer | Microsoft-Dokumentation
description: Erfahren Sie mehr über von Kunden gehostete ClickOnce-Anwendungen, die in .NET Framework 3,5 und früheren Versionen der .NET Framework entwickelt wurden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- preserved branding information
- useManifestForTrust element
- customer deployments [ClickOnce]
- multiple ClickOnce deployment and branding
- ClickOnce applications, previous .NET Framework versions
- application manifests [ClickOnce]
- <useManifestForTrust> element
- manifests [ClickOnce]
- trust applications, ClickOnce
- ClickOnce applications, deployed by others
- ClickOnce applications, previous .NET Framework
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9554cad786669ae4aa3b9aa84ecd6b996ee196f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888471"
---
# <a name="create-clickonce-applications-for-others-to-deploy"></a>Erstellen von ClickOnce-Anwendungen für die Bereitstellung durch Dritte
Nicht alle Entwickler, die ClickOnce-bereit Stellungen erstellen, planen, die Anwendungen selbst bereitzustellen. Viele von Ihnen Verpacken einfach Ihre Anwendung mithilfe von ClickOnce und übergeben die Dateien dann an einen Kunden, z. b. ein großes Unternehmen. Der Kunde ist der Verantwortliche, der für das Hosting der Anwendung im Netzwerk zuständig ist. In diesem Thema werden einige der Probleme erläutert, die in Versionen des .NET Framework vor Version 3,5 in solchen bereit Stellungen auftreten. Anschließend wird eine neue Lösung beschrieben, die mit dem neuen Feature "Manifest für Vertrauensstellung verwenden" in der .NET Framework 3,5 bereitgestellt wird. Schließlich schließt er mit empfohlenen Strategien zum Erstellen von ClickOnce-bereit Stellungen für Kunden, die weiterhin ältere Versionen des .NET Framework verwenden.

## <a name="issues-involved-in-creating-deployments-for-customers"></a>Probleme beim Erstellen von bereit Stellungen für Kunden
 Wenn Sie planen, eine Bereitstellung für einen Kunden bereitzustellen, treten mehrere Probleme auf. Das erste Problem betrifft die Code Signatur. Damit das Bereitstellungs Manifest und das Anwendungs Manifest einer ClickOnce-Bereitstellung über ein Netzwerk bereitgestellt werden können, müssen beide mit einem digitalen Zertifikat signiert werden. Dies löst die Frage aus, ob das Zertifikat des Entwicklers oder das Zertifikat des Kunden beim Signieren der Manifeste verwendet werden soll.

 Die Frage, welches Zertifikat zu verwenden ist, ist wichtig, da die Identität einer ClickOnce-Anwendung auf der digitalen Signatur des Bereitstellungs Manifests basiert. Wenn der Entwickler das Bereitstellungs Manifest signiert, kann dies zu Konflikten führen, wenn der Kunde ein großes Unternehmen ist, und mehr als eine Division des Unternehmens eine angepasste Version der Anwendung bereitstellt.

 Nehmen wir beispielsweise an, dass Adventure Works über eine Finanzabteilung und eine Personalabteilung verfügt. Beide Abteilungen lizenzieren eine ClickOnce-Anwendung von Microsoft Corporation, die Berichte aus Daten generiert, die in einer SQL-Datenbank gespeichert sind. Microsoft stellt jeder Abteilung eine Version der Anwendung bereit, die für Ihre Daten angepasst ist. Wenn die Anwendungen mit demselben Authenticode-Zertifikat signiert sind, würde ein Benutzer, der versucht, beide Anwendungen zu verwenden, einen Fehler erhalten, da ClickOnce die zweite Anwendung als identisch mit der ersten Anwendung betrachtet. In diesem Fall könnte der Kunde unvorhersehbare und unerwünschte Nebeneffekte haben, die den Verlust aller lokal von der Anwendung gespeicherten Daten einschließen.

 Ein zusätzliches Problem im Zusammenhang mit der Code Signatur ist das- `deploymentProvider` Element im Bereitstellungs Manifest, das ClickOnce mitteilt, wo nach Anwendungs Updates gesucht werden soll. Dieses Element muss dem Bereitstellungs Manifest vor der Signierung hinzugefügt werden. Wenn dieses Element danach hinzugefügt wird, muss das Bereitstellungs Manifest neu signiert werden.

### <a name="require-the-customer-to-sign-the-deployment-manifest"></a>Verlangen Sie, dass der Kunde das Bereitstellungs Manifest signiert.
 Eine Lösung für dieses Problem bei nicht eindeutigen bereit Stellungen besteht darin, dass der Entwickler das Anwendungs Manifest signiert und das Bereitstellungs Manifest vom Kunden signiert wird. Während dieses Ansatzes funktioniert, werden andere Probleme eingeführt. Da ein Authenticode-Zertifikat ein geschütztes Asset bleiben muss, kann der Kunde das Zertifikat nicht einfach dem Entwickler zuweisen, um die Bereitstellung zu signieren. Der Kunde kann das Bereitstellungs Manifest selbst mithilfe von Tools signieren, die mit dem .NET Framework SDK kostenlos verfügbar sind, dies erfordert jedoch möglicherweise mehr technische Informationen, als der Kunde bereitstellen oder bereitstellen kann. In solchen Fällen erstellt der Entwickler in der Regel eine Anwendung, eine Website oder einen anderen Mechanismus, über den der Kunde seine Version der Anwendung zum Signieren einreichen kann.

### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>Auswirkungen der Kunden Signierung auf die ClickOnce-Anwendungssicherheit
 Selbst wenn der Entwickler und der Kunde der Meinung sind, dass der Kunde das Anwendungs Manifest Signieren soll, lösen Sie dadurch andere Probleme aus, die die Identität der Anwendung umschließen, insbesondere, da Sie für die Bereitstellung vertrauenswürdiger Anwendungen gilt. (Weitere Informationen zu dieser Funktion finden Sie unter [Übersicht über die Bereitstellung vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md).) Beispielsweise möchte Adventure Works seine Client Computer so konfigurieren, dass jede von der Microsoft Corporation bereitgestellte Anwendung mit voller Vertrauenswürdigkeit ausgeführt wird. Wenn Adventure Works das Bereitstellungs Manifest signiert, verwendet ClickOnce die Sicherheits Signatur von Adventure work, um die Vertrauens Ebene der Anwendung zu bestimmen.

## <a name="create-customer-deployments-by-using-application-manifest-for-trust"></a>Erstellen von Kunden Bereitstellungen mithilfe des Anwendungs Manifests für die Vertrauensstellung
 ClickOnce im .NET Framework 3,5 enthält ein neues Feature, das Entwicklern und Kunden eine neue Lösung für das Szenario bietet, in dem die Manifeste signiert werden sollen. Das ClickOnce-Anwendungs Manifest unterstützt ein neues Element mit dem Namen `<useManifestForTrust>` , das es Entwicklern ermöglicht, anzugeben, dass die digitale Signatur des Anwendungs Manifests zum Treffen von Vertrauens Entscheidungen verwendet werden soll. Der Entwickler verwendet ClickOnce-pakettools – z. b. *Mage.exe*, *MageUI.exe* und Visual Studio –, um dieses Element in das Anwendungs Manifest aufzunehmen, sowie den Verleger Namen und den Namen der Anwendung in das Manifest einzubetten.

 Bei Verwendung `<useManifestForTrust>` von muss das Bereitstellungs Manifest nicht mit einem Authenticode-Zertifikat signiert werden, das von einer Zertifizierungsstelle ausgestellt wurde. Stattdessen kann Sie mit einem selbst signierten Zertifikat signiert werden. Ein selbst signiertes Zertifikat wird vom Kunden oder dem Entwickler mithilfe der Standard-.NET Framework SDK-Tools generiert und dann mithilfe der standardmäßigen ClickOnce-Bereitstellungs Tools auf das Bereitstellungs Manifest angewendet. Weitere Informationen finden Sie unter [Makecert](/windows/desktop/SecCrypto/makecert).

 Die Verwendung eines selbst signierten Zertifikats für das Bereitstellungs Manifest bietet mehrere Vorteile. Durch die Notwendigkeit, dass der Kunde kein eigenes Authenticode-Zertifikat erwerben oder erstellen muss, `<useManifestForTrust>` vereinfacht die Bereitstellung für den Kunden, während der Entwickler seine eigene Branding-Identität für die Anwendung behalten kann. Das Ergebnis ist ein Satz signierter bereit Stellungen, die sicherer sind und über eindeutige Anwendungs Identitäten verfügen. Dadurch entfällt der potenzielle Konflikt, der durch die Bereitstellung der gleichen Anwendung für mehrere Kunden auftreten kann.

 Schritt-für-Schritt-Anleitungen zum Erstellen einer ClickOnce-Bereitstellung mit `<useManifestForTrust>` aktiviertem finden Sie unter Exemplarische Vorgehensweise [: Manuelles Bereitstellen einer ClickOnce-Anwendung, die keine erneute Signierung erfordert und Brandinginformationen beibehält](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).

### <a name="how-application-manifest-for-trust-works-at-run-time"></a>Funktionsweise des Anwendungs Manifests für die Vertrauensstellung zur Laufzeit
 Um besser zu verstehen, wie das Anwendungs Manifest für die Vertrauensstellung zur Laufzeit funktioniert, betrachten Sie das folgende Beispiel. Eine ClickOnce-Anwendung, die auf den .NET Framework 3,5 abzielt, wird von Microsoft erstellt. Das Anwendungs Manifest verwendet das `<useManifestForTrust>` -Element und wird von Microsoft signiert. Adventure Works signiert das Bereitstellungs Manifest mithilfe eines selbst signierten Zertifikats. Adventure Works-Clients werden so konfiguriert, dass Sie allen von Microsoft signierten Anwendungen vertrauen.

 Wenn ein Benutzer auf einen Link zum Bereitstellungs Manifest klickt, wird die Anwendung von ClickOnce auf dem Computer des Benutzers installiert. Die Zertifikat-und Bereitstellungs Informationen identifizieren die Anwendung auf dem Client Computer eindeutig mit ClickOnce. Wenn der Benutzer versucht, dieselbe Anwendung erneut von einem anderen Speicherort zu installieren, kann ClickOnce diese Identität verwenden, um zu bestimmen, ob die Anwendung bereits auf dem Client vorhanden ist.

 Anschließend überprüft ClickOnce das Authenticode-Zertifikat, das verwendet wird, um das Anwendungs Manifest zu signieren, das die Vertrauens Ebene bestimmt, die von ClickOnce erteilt wird. Da Adventure Works seine Clients so konfiguriert hat, dass es jeder von Microsoft signierten Anwendung vertraut, wird dieser ClickOnce-Anwendung volle Vertrauenswürdigkeit gewährt. Weitere Informationen finden Sie unter [Übersicht über die Bereitstellung vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md).

## <a name="create-customer-deployments-for-earlier-versions"></a>Erstellen von Kunden Bereitstellungen für frühere Versionen
 Was geschieht, wenn ein Entwickler ClickOnce-Anwendungen für Kunden bereitstellt, die ältere Versionen des .NET Framework verwenden? In den folgenden Abschnitten werden einige empfohlene Lösungen zusammen mit den Vorteilen und Nachteilen der einzelnen Lösungen zusammengefasst.

### <a name="sign-deployments-on-behalf-of-customer"></a>Signieren von bereit Stellungen im Auftrag des Kunden
 Eine mögliche Bereitstellungs Strategie besteht darin, dass Entwickler einen Mechanismus zum Signieren von bereit Stellungen im Auftrag ihrer Kunden mithilfe des privaten Schlüssels des Kunden erstellen. Dadurch wird verhindert, dass der Entwickler private Schlüssel oder mehrere Bereitstellungs Pakete verwalten muss. Der Entwickler stellt dem einzelnen Kunden lediglich die gleiche Bereitstellung zur Verfügung. Der Kunde kann ihn mithilfe des Signatur Dienstanbieter für Ihre Umgebung anpassen.

 Ein Nachteil dieser Methode ist die Zeit und die Kosten, die für die Implementierung erforderlich sind. Während ein solcher Dienst mithilfe der im .NET Framework SDK bereitgestellten Tools erstellt werden kann, wird dem Produktlebenszyklus mehr Entwicklungszeit hinzugefügt.

 Wie bereits weiter oben in diesem Thema erwähnt, besteht ein weiterer Nachteil darin, dass die Anwendungs Version jedes Kunden die gleiche Anwendungs Identität hat, was zu Konflikten führen könnte. Wenn dies ein Problem ist, kann der Entwickler das Namensfeld ändern, das beim Erstellen des Bereitstellungs Manifests verwendet wird, um jeder Anwendung einen eindeutigen Namen zu geben. Dadurch wird eine separate Identität für jede Version der Anwendung erstellt, und es werden mögliche Identitätskonflikte vermieden. Dieses Feld entspricht dem `-Name` -Argument für Mage.exe und dem Feld **Name** auf der Registerkarte **Name** in MageUI.exe.

 Angenommen, der Entwickler hat eine Anwendung mit dem Namen Anwendung1 erstellt. Anstatt eine einzelne Bereitstellung zu erstellen, bei der das Feld "Name" auf Anwendung1 festgelegt ist, kann der Entwickler mehrere bereit Stellungen mit einer kundenspezifischen Variation dieses Namens erstellen, z. b. Anwendung1-CustomerA, Anwendung1-customerb usw.

### <a name="deploy-using-a-setup-package"></a>Bereitstellen mithilfe eines Setup Pakets
 Eine zweite mögliche Bereitstellungs Strategie besteht darin, ein Microsoft Setup-Projekt zu generieren, um die erste Bereitstellung der ClickOnce-Anwendung auszuführen. Dies kann in einem von mehreren unterschiedlichen Formaten angegeben werden: als MSI-Bereitstellung, als ausführbare Setup Datei (. EXE) oder als CAB-Datei (CAB-Datei) in Verbindung mit einem Batch Skript.

 Mithilfe dieser Technik würde der Entwickler dem Kunden eine Bereitstellung bereitstellen, die die Anwendungs Dateien, das Anwendungs Manifest und ein Bereitstellungs Manifest enthält, das als Vorlage fungiert. Der Kunde führt das Setup Programm aus, das Sie zur Eingabe einer Bereitstellungs-URL (dem Server oder Dateifreigabe Speicherort, von dem die Benutzer die ClickOnce-Anwendung installieren) und einem digitalen Zertifikat auffordern würde. Von der Setup Anwendung können auch zusätzliche ClickOnce-Konfigurationsoptionen angefordert werden, z. b. das Überprüfungs Intervall für Updates. Nachdem diese Informationen gesammelt wurden, generiert das Setup Programm das tatsächliche Bereitstellungs Manifest, signiert es und veröffentlicht die ClickOnce-Anwendung am vorgesehenen Server Speicherort.

 Es gibt drei Möglichkeiten, wie der Kunde das Bereitstellungs Manifest in dieser Situation Signieren kann:

1. Der Kunde kann ein gültiges Zertifikat verwenden, das von einer Zertifizierungsstelle (Certification Authority, ca) ausgestellt wurde.

2. Als Variation dieses Ansatzes können Kunden auswählen, Ihr Bereitstellungs Manifest mit einem selbst signierten Zertifikat zu signieren. Der Nachteil hierbei ist, dass die Anwendung die Wörter "Unbekannter Verleger" anzeigt, wenn der Benutzer gefragt wird, ob die Anwendung installiert werden soll. Der Vorteil besteht jedoch darin, dass kleinere Kunden nicht die Zeit und das Geld aufwenden müssen, die für ein von einer Zertifizierungsstelle ausgestelltes Zertifikat benötigt werden.

3. Schließlich kann der Entwickler sein eigenes selbst signiertes Zertifikat in das Setup Paket einschließen. Dadurch werden die potenziellen Probleme mit der Anwendungs Identität eingeführt, die weiter oben in diesem Thema erläutert wurden.

   Der Nachteil der Setup-Bereitstellungs Projekt Methode ist die Zeit und die Kosten, die zum Erstellen einer benutzerdefinierten Bereitstellungs Anwendung erforderlich sind.

### <a name="have-customer-generate-deployment-manifest"></a>Vom Kunden generiertes Bereitstellungs Manifest
 Eine dritte mögliche Bereitstellungs Strategie besteht darin, nur die Anwendungs Dateien und das Anwendungs Manifest an den Kunden zu übergeben. In diesem Szenario ist der Kunde für die Verwendung des .NET Framework SDK zum Generieren und Signieren des Bereitstellungs Manifests verantwortlich.

 Der Nachteil dieser Methode besteht darin, dass der Kunde die .NET Framework SDK-Tools installieren und einen Entwickler oder Systemadministrator verwenden muss, der für die Verwendung durch den Entwickler zuständig ist. Einige Kunden benötigen möglicherweise eine Lösung, bei der nur wenig oder gar kein technischer Aufwand erforderlich ist.

## <a name="see-also"></a>Weitere Informationen
- [Bereitstellen von ClickOnce-Anwendungen für Test-und Produktionsserver ohne erneutes Signieren](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)
- [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung, die keine erneute Signierung erfordert und Brandinginformationen beibehält](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)