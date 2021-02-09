---
title: Referenz zur nicht verwalteten API für ClickOnce | Microsoft-Dokumentation
description: Hier finden Sie Informationen zu den nicht verwalteten ClickOnce-APIs von dfshim.dll, einschließlich "CleanOnlineAppCache", "getdeploymentdatafrommanifest" und "launchapplication".
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
api_name:
- CleanOnlineAppCache
- GetDeploymentDataFromManifest
- LaunchApplication
api_location:
- dfshim.dll
api_type:
- COM
topic_type:
- apiref
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- LaunchApplication [ClickOnce unmanaged]
- ClickOnce, unmanaged APIs
- CleanOnlineAppCache [ClickOnce unmanaged]
- CleanOnlineAppCacheW interface [ClickOnce unmanaged]
- GetDeploymentDataFromManifest [ClickOnce unmanaged]
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 88d8147dded05c6bec54682e76c6a8c1826b43e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900794"
---
# <a name="clickonce-unmanaged-api-reference"></a>Referenz zur nicht verwalteten API für ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nicht verwaltete öffentliche APIs aus dfshim.dll.

## <a name="cleanonlineappcache"></a>CleanOnlineAppCache
 Bereinigt oder deinstalliert alle Online Anwendungen aus dem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungscache.

### <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT zurückgegeben, das den Fehler darstellt. Wenn eine verwaltete Ausnahme auftritt, gibt 0x80020009 (DISP_E_EXCEPTION) zurück.

### <a name="remarks"></a>Bemerkungen
 Durch Aufrufen von CleanOnlineAppCache wird der Dienst gestartet, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Wenn er nicht bereits ausgeführt wird.

## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest
 Ruft Bereitstellungs Informationen aus dem Manifest und der Aktivierungs-URL ab.

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|type|
|---------------|-----------------|----------|
|`pcwzActivationUrl`|Ein Zeiger auf `ActivationURL`.|LPCWSTR|
|`pcwzPathToDeploymentManifest`|Ein Zeiger auf `PathToDeploymentManifest`.|LPCWSTR|
|`pwzApplicationIdentity`|Ein Zeiger auf einen Puffer, der eine NULL-terminierte Zeichenfolge empfängt, die die vollständige zurückgegebene Anwendungs Identität angibt.|LPWSTR|
|`pdwIdentityBufferLength`|Ein Zeiger auf ein DWORD, das die Länge des `pwzApplicationIdentity` Puffers in WCHARs ist. Dies schließt den Platz für das NULL-Beendigungs Zeichen ein.|LPDWORD|
|`pwzProcessorArchitecture`|Ein Zeiger auf einen Puffer, der eine NULL-terminierte Zeichenfolge empfängt, die die Prozessorarchitektur der Anwendungs Bereitstellung aus dem Manifest angibt.|LPWSTR|
|`pdwArchitectureBufferLength`|Ein Zeiger auf ein DWORD, das die Länge des `pwzProcessorArchitecture` Puffers in WCHARs ist.|LPDWORD|
|`pwzApplicationManifestCodebase`|Ein Zeiger auf einen Puffer, der eine NULL-terminierte Zeichenfolge empfängt, die die Codebasis des Anwendungs Manifests aus dem Manifest angibt.|LPWSTR|
|`pdwCodebaseBufferLength`|Ein Zeiger auf ein DWORD, das die Länge des `pwzApplicationManifestCodebase` Puffers in WCHARs ist.|LPDWORD|
|`pwzDeploymentProvider`|Ein Zeiger auf einen Puffer, der eine NULL-terminierte Zeichenfolge empfängt, die den Bereitstellungs Anbieter aus dem Manifest angibt (sofern vorhanden). Andernfalls wird eine leere Zeichenfolge zurückgegeben.|LPWSTR|
|`pdwProviderBufferLength`|Ein Zeiger auf ein DWORD, das die Länge von ist `pwzProviderBufferLength` .|LPDWORD|

### <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT zurückgegeben, das den Fehler darstellt. Gibt HRESULTFROMWIN32 (ERROR_INSUFFICIENT_BUFFER) zurück, wenn ein Puffer zu klein ist.

### <a name="remarks"></a>Bemerkungen
 Zeiger dürfen nicht NULL sein. `pcwzActivationUrl` und `pcwzPathToDeploymentManifest` dürfen nicht leer sein.

 Es liegt in der Verantwortung des Aufrufers, die Aktivierungs-URL zu bereinigen. Beispielsweise das Hinzufügen von Escapezeichen, wenn Sie benötigt werden oder die Abfrage Zeichenfolge entfernt wird.

 Es liegt in der Verantwortung des Aufrufers, die Eingabe Länge einzuschränken. Beispielsweise beträgt die maximale URL-Länge 2 KB.

## <a name="launchapplication"></a>LaunchApplication
 Hiermit wird eine Anwendung mithilfe einer Bereitstellungs-URL gestartet oder installiert.

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|type|
|---------------|-----------------|----------|
|`deploymentUrl`|Ein Zeiger auf eine NULL-terminierte Zeichenfolge, die die URL des Bereitstellungs Manifests enthält.|LPCWSTR|
|`data`|Für zukünftige Verwendung reserviert. Muss NULL sein.|LPVOID|
|`flags`|Für zukünftige Verwendung reserviert. Muss den Wert 0 (null) haben.|DWORD|

### <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT zurückgegeben, das den Fehler darstellt. Wenn eine verwaltete Ausnahme auftritt, gibt 0x80020009 (DISP_E_EXCEPTION) zurück.

## <a name="see-also"></a>Weitere Informationen
- <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>