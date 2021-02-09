---
title: Service Essentials | Microsoft-Dokumentation
description: Erfahren Sie mehr über Dienste, die Schnittstellen für ein anderes VSPackage sind. Dienste in einem VSPackage können integrierte oder andere Dienste überschreiben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 145097b9e012d8c09df1424747d04148df3cae8f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911013"
---
# <a name="service-essentials"></a>Dienstgrundlagen
Ein Dienst ist ein Vertrag zwischen zwei VSPackages. Ein VSPackage stellt einen bestimmten Satz von Schnittstellen für ein anderes VSPackage bereit, das verwendet werden soll. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist selbst eine Sammlung von VSPackages, die Dienste für andere VSPackages bereitstellt.

 Beispielsweise können Sie den Dienst SVsActivityLog zum Abrufen einer IVsActivityLog-Schnittstelle verwenden, die Sie verwenden können, um in das Aktivitätsprotokoll zu schreiben. Weitere Informationen finden Sie unter Gewusst [wie: Verwenden des Aktivitäts Protokolls](../../extensibility/how-to-use-the-activity-log.md).

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bietet auch einige integrierte Dienste, die nicht registriert sind. VSPackages können integrierte oder andere Dienste durch Bereitstellen einer Dienst Überschreibung ersetzen. Nur eine Dienst Außerkraftsetzung ist für einen beliebigen Dienst zulässig.

 Dienste können nicht gefunden werden. Daher müssen Sie die Dienst Kennung (SID) eines dienstanzdienstaners kennen, den Sie verwenden möchten, und Sie müssen wissen, welche Schnittstellen Sie bereitstellt. Diese Informationen finden Sie in der Referenz Dokumentation für den-Dienst.

- VSPackages, die Dienste bereitstellen, werden als Dienstanbieter bezeichnet.

- Dienste, die für andere VSPackages bereitgestellt werden, werden als globale Dienste bezeichnet.

- Dienste, die nur für das VSPackage, das Sie implementiert, oder für ein beliebiges Objekt verfügbar sind, werden als lokale Dienste bezeichnet.

- Dienste, die integrierte Dienste oder Dienste ersetzen, die von anderen Paketen bereitgestellt werden, werden als Dienst Überschreibungen bezeichnet.

- Dienste oder Dienst Überschreibungen werden bei Bedarf geladen, d. h., der Dienstanbieter wird geladen, wenn der bereitgestellte Dienst von einem anderen VSPackage angefordert wird.

- Um das Bedarfs gesteuerte laden zu unterstützen, registriert ein Dienstanbieter seine globalen Dienste bei [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Weitere Informationen finden Sie unter Vorgehens [Weise: Bereitstellen eines Dienstanbieter](../../extensibility/how-to-provide-a-service.md).

- Nachdem Sie einen Dienst abgerufen haben, verwenden Sie [QueryInterface](/cpp/atl/queryinterface) (nicht verwalteter Code) oder Umwandlungs (verwalteter Code), um die gewünschte Schnittstelle abzurufen, z. b.:

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Verwalteter Code bezieht sich auf einen Dienst über seinen Typ, wohingegen nicht verwalteter Code über seine GUID auf einen Dienst verweist.

- Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ein VSPackage lädt, übergibt es einen Dienstanbieter an das VSPackage, um dem VSPackage Zugriff auf globale Dienste zu verschaffen. Dies wird als "siting" des VSPackage bezeichnet.

- VSPackages können Dienstanbieter für die Objekte sein, die Sie erstellen. Beispielsweise kann ein Formular eine Anforderung für einen Farb Dienst an seinen Frame senden, der die Anforderung möglicherweise an übergibt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- Verwaltete Objekte, die tief geschachtelt sind oder überhaupt nicht positioniert sind, können <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> für den direkten Zugriff auf globale Dienste aufrufen.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>Verwenden von GetGlobalService

Manchmal müssen Sie möglicherweise einen Dienst von einem Tool Fenster oder einem Steuerelement Container erhalten, der nicht mit der sitsierung vertraut ist, oder wenn Sie mit einem Dienstanbieter vertraut sind, der den gewünschten Dienst nicht kennt. Beispielsweise können Sie in einem-Steuerelement in das Aktivitätsprotokoll schreiben. Weitere Informationen zu diesen und anderen Szenarien finden Sie unter Gewusst [wie:](../../extensibility/how-to-troubleshoot-services.md)Problembehandlung bei Diensten.

Sie können die meisten Visual Studio-Dienste abrufen, indem Sie die statische- <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Methode aufrufen.

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> basiert auf einem zwischengespeicherten Dienstanbieter, der initialisiert wird, wenn ein von einem Paket abgeleitetes VSPackage das gleiche ist. Sie müssen sicherstellen, dass diese Bedingung erfüllt ist, oder Sie müssen auf einen NULL-Dienst vorbereitet werden.

Glücklicherweise <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> funktioniert meistens ordnungsgemäß.

- Wenn ein VSPackage einen Dienst bereitstellt, der nur einem anderen VSPackage bekannt ist, wird das VSPackage, das den Dienst anfordert, positioniert, bevor das VSPackage, das den Dienst bereitstellt, geladen wird.

- Wenn ein Tool Fenster durch ein VSPackage erstellt wird, wird das VSPackage vor dem Erstellen des Tool Fensters positioniert.

- Wenn ein Steuerelement Container von einem Tool Fenster gehostet wird, das von einem VSPackage erstellt wurde, wird das VSPackage vor dem Erstellen des Steuerelement Containers positioniert.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>So erhalten Sie einen Dienst in einem Tool Fenster oder Steuerelement Container

- Fügen Sie diesen Code in den Konstruktor, das Tool Fenster oder den Steuerelement Container ein:

    ```csharp
    IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
        if (log == null) return;
    ```

    ```vb
    Dim log As IVsActivityLog = TryCast(Package.GetGlobalService(GetType(SVsActivityLog)), IVsActivityLog)
    If log Is Nothing Then
        Return
    End If
    ```

    Dieser Code Ruft einen SVsActivityLog-Dienst ab und wandelt ihn in eine IVsActivityLog-Schnittstelle um, die zum Schreiben in das Aktivitätsprotokoll verwendet werden kann. Ein Beispiel finden Sie unter Gewusst [wie: Verwenden des Aktivitäts Protokolls](../../extensibility/how-to-use-the-activity-log.md).

## <a name="see-also"></a>Weitere Informationen

- [Liste der verfügbaren Dienste](../../extensibility/internals/list-of-available-services.md)
- [Verwenden und Bereitstellen von Diensten](../../extensibility/using-and-providing-services.md)
- [Umwandlung und Typkonvertierungen](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Umwandlung](/cpp/cpp/casting)
