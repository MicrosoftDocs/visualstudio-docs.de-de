---
title: 'Vorgehensweise: Bereitstellen von Automatisierung für Windows | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fec2b9ef6612a294dc70d129cf4bdd3dde843262
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905258"
---
# <a name="how-to-provide-automation-for-windows"></a>Vorgehensweise: Bereitstellen von Automatisierung für Windows

Sie können die Automatisierung für Dokument-und Tool Fenster bereitstellen. Das Bereitstellen von Automatisierung ist ratsam, wenn Sie Automation-Objekte in einem Fenster verfügbar machen möchten und die Umgebung nicht bereits ein vorgefertigte Automatisierungs Objekt bereitstellt, wie es bei einer Aufgabenliste der Fall ist.

## <a name="automation-for-tool-windows"></a>Automatisierung für Tool Fenster

Die Umgebung ermöglicht die Automatisierung in einem Tool Fenster, indem ein Standard Objekt zurückgegeben wird, <xref:EnvDTE.Window> wie im folgenden Verfahren erläutert:

1. Wenden Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> Methode über die Umgebung mit [__VSFPROPID an. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) als `VSFPROPID` Parameter, um das `Window` Objekt zu erhalten.

2. Wenn ein Aufrufer ein VSPackage-spezifisches Automatisierungs Objekt für das Tool Fenster durch anfordert <xref:EnvDTE.Window.Object%2A> , ruft die Umgebung die `QueryInterface` `IExtensibleObject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> Schnittstellen, oder auf `IDispatch` . `IExtensibleObject`Und `IVsExtensibleObject` stellen eine- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> Methode bereit.

3. Wenn die Umgebung dann die `GetAutomationObject` -Methode übergibt `NULL` , reagieren Sie, indem Sie das VSPackage-spezifische Objekt zurückgibt.

4. Wenn für und ein Fehler auftritt `QueryInterface` `IExtensibleObject` `IVsExtensibleObject` , ruft die Umgebung `QueryInterface` für auf `IDispatch` .

## <a name="automation-for-document-windows"></a>Automatisierung für Dokument Fenster

Ein Standard <xref:EnvDTE.Document> Objekt steht auch in der Umgebung zur Verfügung, obwohl ein Editor über eine eigene Implementierung des Objekts verfügen kann, indem er eine <xref:EnvDTE.Document> `IExtensibleObject` Schnittstelle implementiert und auf antwortet `GetAutomationObject` .

Außerdem kann ein Editor ein VSPackage-spezifisches Automatisierungs Objekt bereitstellen, das durch die-Methode abgerufen wird, <xref:EnvDTE.Document.Object%2A> indem die-Schnittstelle oder die-Schnittstelle implementiert wird `IVsExtensibleObject` `IExtensibleObject` . Die [VSSDK-Beispiele](https://github.com/Microsoft/VSSDK-Extensibility-Samples) tragen zu einem RTF-Dokument spezifischen Automatisierungs Objekt bei.

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
