---
title: Sichern von ClickOnce-Anwendungen | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Auswirkungen von Einschränkungen der Code Zugriffssicherheit in der .NET Framework, die den Zugriff auf Code für Ihre ClickOnce-Anwendungen einschränken können.
ms.custom: SEO-VS-2020
ms.date: 02/17/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce security
- ClickOnce deployment, security
- deploying applications, ClickOnce security
ms.assetid: a05b5f2f-d1f2-471a-8096-8b11f7554265
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aa698fc0ac0e46fa645ede54d6608b79dd031655
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949661"
---
# <a name="secure-clickonce-applications"></a>Sichern von ClickOnce-Anwendungen
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungen unterliegen in .NET Framework Einschränkungen in Bezug auf die Codezugriffssicherheit, um den Zugriff zu begrenzen, den Code auf geschützte Ressourcen und Vorgänge hat. Daher ist es wichtig, dass Sie sich mit dem Thema Codezugriffssicherheit auseinandersetzen und diese Kenntnisse beim Schreiben von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungen anwenden. Die Anwendungen können Zonen mit voller Vertrauenswürdigkeit oder teilweise vertrauenswürdige Zonen verwenden, z. B. die Internet- und Intranetzonen, um den Zugriff einzuschränken.

 Außerdem verwendet ClickOnce Zertifikate, um die Echtheit des Herausgebers einer Anwendung zu überprüfen und die Anwendungs- und Bereitstellungsmanifeste zu signieren. Auf diese Weise wird sichergestellt, dass die Dateien nicht manipuliert wurden. Das Signieren ist ein optionaler Schritt, der das Ändern der Anwendungsdateien nach dem Generieren der Manifeste vereinfacht. Ohne signierte Manifeste ist es jedoch schwierig sicherzustellen, dass das Installationsprogramm der Anwendung nicht durch Man-in-the-middle-Sicherheitsangriffe manipuliert wird. Aus diesem Grund wird empfohlen, das Anwendungs- und Bereitstellungsmanifest zu signieren, um die Anwendungen zu schützen.

## <a name="zones"></a>Zones
 Anwendungen, die mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Technologie bereitgestellt werden, sind auf einen Berechtigungssatz und Aktionen beschränkt, die von der Sicherheitszone definiert werden. Sicherheitszonen werden in Internet Explorer definiert und basieren auf dem Speicherort der Anwendung. In der folgenden Tabelle werden die Standardberechtigungen aufgelistet, die auf dem Bereitstellungsspeicherort beruhen:

|Bereitstellungsort|Sicherheitszone|
|-------------------------|-------------------|
|Ausführen vom Web|Internetzone|
|Installieren vom Web|Internetzone|
|Installieren aus einer Dateifreigabe im Netzwerk|Zone "Lokales Intranet"|
|Installieren von CD-ROM|Voll vertrauenswürdig|

 Die Standardberechtigungen basieren auf dem Speicherort, von dem aus die Originalversion der Anwendung bereitgestellt wurde. Updates der Anwendung erben diese Berechtigungen. Falls die Anwendung so konfiguriert ist, dass sie an einem Web- oder Netzwerkspeicherort nach Updates sucht und eine neuere Version zur Verfügung steht, kann die ursprüngliche Installation statt der Berechtigung Volle Vertrauenswürdigkeit u. U. Berechtigungen für die Internet- oder Intranetzone erhalten. Um zu verhindern, dass Benutzer Eingabeaufforderungen erhalten, kann ein Systemadministrator eine ClickOnce-Bereitstellungsrichtlinie angeben, die einen bestimmten Anwendungsherausgeber als vertrauenswürdige Quelle definiert. Für Computer, auf denen diese Richtlinie bereitgestellt wurde, werden Berechtigungen automatisch gewährt, und es werden keine Aufforderungen an Benutzer ausgegeben. Weitere Informationen finden Sie unter [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md). Um die Bereitstellung vertrauenswürdiger Anwendungen zu konfigurieren, kann das Zertifikat auf Computer- oder Unternehmensebene installiert werden. Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen eines vertrauenswürdigen Herausgebers zu einem Clientcomputer für ClickOnce-Anwendungen](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

## <a name="code-access-security-policies"></a>Richtlinien der Codezugriffssicherheit
 Berechtigungen für eine Anwendung werden von den Einstellungen im [ \<trustInfo> Element](../deployment/trustinfo-element-clickonce-application.md) Element des Anwendungs Manifests bestimmt. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generiert diese Informationen automatisch basierend auf den Einstellungen auf der Eigenschaften Seite **Sicherheit** des Projekts. Einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung werden nur die speziellen Berechtigungen gewährt, die diese anfordert. Wenn für den Dateizugriff beispielsweise Berechtigungen für volle Vertrauenswürdigkeit erforderlich sind und die Anwendung eine Dateizugriffsberechtigung anfordert, wird ihr nur eine Berechtigung für den Dateizugriff und keine volle Vertrauenswürdigkeit gewährt. Beim Entwickeln der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung sollten Sie sicherstellen, dass Sie nur die spezifischen Berechtigungen anfordern, die für die Anwendung erforderlich sind. In den meisten Fällen können Sie die Zonen "Internet" oder "Lokales Intranet" verwenden, um Ihre Anwendung auf teilweise Vertrauenswürdigkeit zu beschränken. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen einer Sicherheitszone für eine ClickOnce-Anwendung](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md). Wenn die Anwendung benutzerdefinierte Berechtigungen erfordert, können Sie eine benutzerdefinierte Zone erstellen. Weitere Informationen finden Sie unter Gewusst [wie: Festlegen benutzerdefinierter Berechtigungen für eine ClickOnce-Anwendung](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

 Das Einschließen einer Berechtigung, die nicht zum Standardberechtigungssatz der Zone gehört, aus der die Anwendung bereitgestellt wird, führt dazu, dass der Endbenutzer bei der Installation oder bei einem Update zum Gewähren der Berechtigung aufgefordert wird. Um zu verhindern, dass Benutzer Eingabeaufforderungen erhalten, kann ein Systemadministrator eine ClickOnce-Bereitstellungsrichtlinie angeben, die einen bestimmten Anwendungsherausgeber als vertrauenswürdige Quelle definiert. Auf Computern, auf denen diese Richtlinie bereitgestellt wurde, werden Berechtigungen automatisch gewährt, und es werden keine Aufforderungen an Benutzer ausgegeben.

 Als Entwickler müssen Sie sicherstellen, dass Ihre Anwendung mit den geeigneten Berechtigungen ausgeführt wird. Wenn die Anwendung während der Laufzeit Berechtigungen außerhalb einer Zone anfordert, wird ggf. eine Sicherheitsausnahme angezeigt. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ermöglicht es Ihnen, Ihre Anwendung in der Ziel Sicherheitszone zu Debuggen und bietet Hilfe bei der Entwicklung sicherer Anwendungen. Weitere Informationen finden Sie unter [Debuggen von ClickOnce-apps, die System. Deployment. Application verwenden](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md).

 Weitere Informationen zur Codezugriffssicherheit und zu ClickOnce finden Sie unter [Codezugriffssicherheit für ClickOnce-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="code-signing-certificates"></a>Codesignaturzertifikate
 Um eine Anwendung mithilfe der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Bereitstellung zu veröffentlichen, können Sie die Anwendungs- und Bereitstellungsmanifeste für die Anwendung mit einem Schlüsselpaar aus öffentlichem und privatem Schlüssel signieren. Die Tools zum Signieren eines Manifests sind im **Projekt-Designer** auf der Seite **Signierung** verfügbar. Weitere Informationen finden Sie unter [Signing Page, Project Designer](../ide/reference/signing-page-project-designer.md).

 Nach dem Signieren der Manifeste werden dem Benutzer während der Installation die Herausgeberinformationen auf der Grundlage der Authenticode-Signatur im Dialogfeld für Berechtigungen angezeigt, um nachzuweisen, dass die Anwendung aus einer vertrauenswürdigen Quelle stammt.

 Weitere Informationen zu ClickOnce und Zertifikaten finden Sie unter [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md).

## <a name="aspnet-form-based-authentication"></a>Formularbasierte ASP.NET-Authentifizierung
 Wenn Sie steuern möchten, auf welche Bereitstellung Benutzer jeweils zugreifen können, sollten Sie den anonymen Zugriff auf [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungen, die auf einem Webserver bereitgestellt wurden, verhindern. Stattdessen sollten Sie Benutzern vorrangig Zugriff auf die Bereitstellungen gewähren, die mithilfe der Windows-Authentifizierung unter der Identität des jeweiligen Benutzers installiert wurden.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] unterstützt keine ASP.NET-Formularauthentifizierung, da ClickOnce permanente Cookies verwendet. Diese Cookies stellen ein Sicherheitsrisiko dar, weil sie im Internet Explorer-Cache gespeichert sind und von Hackern ausspioniert werden können. Wenn Sie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungen bereitstellen, wird daher außer der Windows-Authentifizierung kein anderes Authentifizierungsszenario unterstützt.

## <a name="pass-arguments"></a>Übergeben von Argumenten
 Ein weiterer Sicherheitsaspekt muss berücksichtigt werden, wenn Sie Argumente in eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung übergeben müssen. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ermöglicht es Entwicklern, für Anwendungen über das Internet eine Abfragezeichenfolge bereitzustellen. Die Abfragezeichenfolge besteht aus einer Reihe von Name/Wert-Paaren am Ende der URL, mit der die Anwendung gestartet wird:

 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`

 Abfragezeichenfolgenargumente werden standardmäßig deaktiviert. Um sie zu aktivieren, muss das `trustUrlParameters` -Attribut im Bereitstellungsmanifest der Anwendung festgelegt werden. Dieser Wert kann von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und von MageUI.exe aus festgelegt werden. Eine ausführliche Beschreibung der Schritte zum Aktivieren der Übergabe von Abfragezeichenfolgen finden Sie unter [Gewusst wie: Abrufen von Abfragezeichenfolgen-Informationen in einer Online-ClickOnce-Anwendung](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).

 Übergeben Sie Argumente, die über eine Abfragezeichenfolge abgerufen wurden, nie an eine Datenbank oder an die Befehlszeile, ohne die Argumente auf ihre Sicherheit zu überprüfen. Unsichere Argumente sind Argumente, die Datenbank- oder Befehlszeilen-Escapezeichen enthalten, mit denen böswillige Benutzer die Möglichkeit erhalten können, Ihre Anwendung für die Ausführung beliebiger Befehle zu manipulieren.

> [!NOTE]
> Abfragezeichenfolgenargumente sind die einzige Möglichkeit, Argumente beim Starten an eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung zu übergeben. Über die Befehlszeile können Sie keine Argumente an eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung übergeben.

## <a name="deploying-obfuscated-assemblies"></a>Bereitstellen von verborgenen Assemblys
 Visual Studio umfasst die kostenlose [PreEmptive Protection – Dotfuscator Community](../ide/dotfuscator/index.md), die Sie verwenden können, um Ihre ClickOnce-Anwendungen mithilfe von Codeobfuskation und aktiver Schutzmaßnahmen zu schützen.  Weitere Informationen finden Sie [im Abschnitt „ClickOnce“ des Dotfuscator Community Edition User Guide](https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/advanced_clickonce.html).

## <a name="see-also"></a>Weitere Informationen
- [ClickOnce-Sicherheit und -Bereitstellung](../deployment/clickonce-security-and-deployment.md)
- [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md)
