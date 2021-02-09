---
title: '&lt;Deployment- &gt; Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
description: Das Bereitstellungs Element identifiziert die Attribute, die für die Bereitstellung von Updates und das verfügbar machen des Systems verwendet werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#subscription
- urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup
- urn:schemas-microsoft-com:asm.v2#deploymentProvider
- urn:schemas-microsoft-com:asm.v2#update
- urn:schemas-microsoft-com:asm.v2#deployment
- urn:schemas-microsoft-com:asm.v2#expiration
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 369d48c76ed82825021622af35141ef12ff42c76
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893905"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;Deployment- &gt; Element (ClickOnce-Bereitstellung)
Identifiziert die Attribute, die für die Bereitstellung von Updates und zum Verfügbarmachen für das System verwendet werden.

## <a name="syntax"></a>Syntax

```xml

      <deployment
   install
   minimumRequiredVersion
   mapFileExtensions
   disallowUrlActivation
   trustUrlParameters
>
   <subscription>
         <update>
            <beforeApplicationStartup/>
            <expiration
               maximumAge
               unit
            />
         </update>
   </subscription>
   <deploymentProvider
      codebase
   />
</deployment>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `deployment` -Element ist erforderlich und befindet sich im `urn:schemas-microsoft-com:asm.v2` -Namespace. Das Element weist folgende Attribute auf.

| attribute | Beschreibung |
|--------------------------| - |
| `install` | Erforderlich. Gibt an, ob diese Anwendung eine Anwesenheit im Windows- **Startmenü** und in der Systemsteuerung in der System **Steuerungsanwendung definiert** . Gültige Werte sind `true` und `false`. Wenn `false` , [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wird immer die neueste Version dieser Anwendung aus dem Netzwerk ausgeführt, und das-Element wird nicht erkannt `subscription` . |
| `minimumRequiredVersion` | Dies ist optional. Gibt die Mindestversion dieser Anwendung an, die auf dem Client ausgeführt werden kann. Wenn die Versionsnummer der Anwendung kleiner als die im Bereitstellungs Manifest angegebene Versionsnummer ist, wird die Anwendung nicht ausgeführt. Versionsnummern müssen im Format angegeben werden `N.N.N.N` , wobei `N` eine ganze Zahl ohne Vorzeichen ist. Wenn das- `install` Attribut ist `false` , `minimumRequiredVersion` darf nicht festgelegt werden. |
| `mapFileExtensions` | Optional. Wird standardmäßig auf `false` festgelegt. Gibt `true` an, dass alle Dateien in der Bereitstellung über die Erweiterung. Deployment verfügen müssen. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Diese Erweiterung wird von entfernt, sobald Sie vom Webserver heruntergeladen wird. Wenn Sie die Anwendung mithilfe von veröffentlichen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , wird diese Erweiterung automatisch allen Dateien hinzugefügt. Mit diesem Parameter können alle Dateien in einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung von einem Webserver heruntergeladen werden, der die Übertragung von Dateien blockiert, die mit "unsicheren" Erweiterungen wie z. b. exe enden. |
| `disallowUrlActivation` | Optional. Wird standardmäßig auf `false` festgelegt. Wenn `true` , wird verhindert, dass eine installierte Anwendung gestartet wird, indem Sie auf die URL klicken oder die URL in Internet Explorer eingeben. Wenn das `install` Attribut nicht vorhanden ist, wird dieses Attribut ignoriert. |
| `trustURLParameters` | Optional. Wird standardmäßig auf `false` festgelegt. Wenn `true` , kann die URL Abfrage Zeichen folgen Parameter enthalten, die an die Anwendung übermittelt werden, ähnlich wie Befehlszeilenargumente werden an eine Befehlszeilen Anwendung übermittelt. Weitere Informationen finden Sie unter Gewusst [wie: Abrufen von Abfrage Zeichenfolgen-Informationen in einer Online-ClickOnce-Anwendung](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Wenn das- `disallowUrlActivation` Attribut ist `true` , `trustUrlParameters` muss entweder aus dem Manifest ausgeschlossen oder explizit auf festgelegt werden `false` . |

 Das- `deployment` Element enthält auch die folgenden untergeordneten Elemente.

## <a name="subscription"></a>Abonnement
 Dies ist optional. Enthält das- `update` Element. Das `subscription` -Element weist keine Attribute auf. Wenn das `subscription` Element nicht vorhanden ist, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wird die Anwendung nie nach Updates suchen. Wenn das- `install` Attribut des- `deployment` Elements ist `false` , wird das- `subscription` Element ignoriert, da eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vom Netzwerk gestartete Anwendung immer die neueste Version verwendet.

## <a name="update"></a>aktualisieren
 Erforderlich. Dieses Element ist ein untergeordnetes Element des `subscription` -Elements und enthält entweder das-Element `beforeApplicationStartup` oder das- `expiration` Element. `beforeApplicationStartup` und `expiration` können nicht im selben Bereitstellungs Manifest angegeben werden.

 Das `update` -Element weist keine Attribute auf.

## <a name="beforeapplicationstartup"></a>beforeApplicationStartup
 Dies ist optional. Dieses Element ist ein untergeordnetes Element des `update` -Elements und besitzt keine Attribute. Wenn das `beforeApplicationStartup` -Element vorhanden ist, wird die Anwendung bei der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Überprüfung auf Updates blockiert, wenn der Client online ist. Wenn dieses Element nicht vorhanden ist, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sucht zuerst anhand der für das Element angegebenen Werte nach Updates `expiration` . `beforeApplicationStartup` und `expiration` können nicht im selben Bereitstellungs Manifest angegeben werden.

## <a name="expiration"></a>expiration
 Dies ist optional. Dieses Element ist ein untergeordnetes Element des `update` -Elements und hat keine untergeordneten Elemente. `beforeApplicationStartup` und `expiration` können nicht im selben Bereitstellungs Manifest angegeben werden. Wenn die Update Überprüfung stattfindet und eine aktualisierte Version erkannt wird, wird die neue Version zwischengespeichert, während die vorhandene Version ausgeführt wird. Die neue Version wird dann beim nächsten Start der Anwendung installiert [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

 Das- `expiration` Element unterstützt die folgenden Attribute.

|attribute|Beschreibung|
|---------------|-----------------|
|`maximumAge`|Erforderlich. Gibt an, wie alt das aktuelle Update werden soll, bevor die Anwendung eine Überprüfung auf Aktualisierungen durchführt. Die Zeiteinheit wird durch das- `unit` Attribut bestimmt.|
|`unit`|Erforderlich. Gibt die Zeiteinheit für an `maximumAge` . Gültige Einheiten sind `hours` , `days` und `weeks` .|

## <a name="deploymentprovider"></a>deploymentProvider
 Für den .NET Framework 2,0 ist dieses Element erforderlich, wenn das Bereitstellungs Manifest einen `subscription` Abschnitt enthält. Für den .NET Framework 3,5 und höher ist dieses Element optional und wird standardmäßig auf den Server und den Dateipfad festgestellt, in dem das Bereitstellungs Manifest ermittelt wurde.

 Dieses Element ist ein untergeordnetes Element des `deployment` -Elements und weist folgende Attribute auf.

| attribute | Beschreibung |
|------------| - |
| `codebase` | Erforderlich. Identifiziert den Speicherort als Uniform Resource Identifier (URI) des Bereitstellungs Manifests, das zum Aktualisieren der Anwendung verwendet wird [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Dieses Element ermöglicht außerdem das Weiterleiten von Update-Speicherorten für CD-basierte Installationen. Muss ein gültiger URI sein. |

## <a name="remarks"></a>Bemerkungen
 Sie können Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung so konfigurieren, dass Sie beim Start nach Updates sucht, nach Updates nach dem Start Suchen oder nie nach Updates sucht. Um beim Start nach Updates zu suchen, stellen Sie sicher, dass das- `beforeApplicationStartup` Element unter dem-Element vorhanden ist `update` . Stellen Sie sicher, dass das `expiration` -Element unter dem `update` -Element vorhanden ist und dass Aktualisierungsintervalle bereitgestellt werden, um nach dem Start nach Updates zu suchen.

 Entfernen Sie das-Element, um die Überprüfung auf Updates zu deaktivieren `subscription` . Wenn Sie im Bereitstellungs Manifest angeben, dass keine Updates überprüft werden sollen, können Sie mithilfe der-Methode trotzdem manuell nach Updates suchen <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> .

 Weitere Informationen zur Beziehung zwischen deploymentProvider und Updates finden Sie unter [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md).

## <a name="examples"></a>Beispiele
 Das folgende Codebeispiel veranschaulicht ein- `deployment` Element in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungs Manifest. Im Beispiel wird ein- `deploymentProvider` Element verwendet, um den bevorzugten Update Speicherort anzugeben.

```xml
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">
    <subscription>
      <update>
        <expiration maximumAge="6" unit="hours" />
      </update>
    </subscription>
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />
  </deployment>
```

## <a name="see-also"></a>Weitere Informationen
- [ClickOnce-Bereitstellungs Manifest](../deployment/clickonce-deployment-manifest.md)