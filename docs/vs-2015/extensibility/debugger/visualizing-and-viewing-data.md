---
title: Visualisieren und Anzeigen von Daten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 719a2b3d073d90ff3977496c7f98ebecb1ab48a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696312"
---
# <a name="visualizing-and-viewing-data"></a>Visualisieren und Anzeigen von Daten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Typvisualisierungen und benutzerdefinierte Viewer stellen Daten auf eine Weise dar, die für einen Entwickler schnell sinnvoll ist. Die Ausdrucks Auswertung (EE) kann typvisualisierungen von Drittanbietern unterstützen und eigene benutzerdefinierte Viewer bereitstellen.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bestimmt, wie viele typvisualisierungen und benutzerdefinierte Viewer dem Objekttyp zugeordnet werden, indem die [getcustomviewercount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) -Methode aufgerufen wird. Wenn mindestens eine typschnell Ansicht oder ein benutzerdefinierter Viewer verfügbar ist, ruft Visual Studio die [getcustomviewerlist](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) -Methode auf, um eine Liste mit diesen Visualisierungen und Viewern (tatsächlich eine Liste von en, die die schnell Ansichten `CLSID` und Viewer implementieren) abzurufen und dem Benutzer zu präsentieren.  
  
## <a name="supporting-type-visualizers"></a>Unterstützende typvisualisierungen  
 Es gibt eine Reihe von Schnittstellen, die von der EE implementiert werden müssen, um typvisualisierungen zu unterstützen. Diese Schnittstellen können in zwei allgemeine Kategorien aufgeteilt werden: solche, die die typvisualisierungen auflisten, und diejenigen, die auf die Eigenschaften Daten zugreifen.  
  
### <a name="listing-type-visualizers"></a>Auflisten von typvisualisierungen  
 Der EE unterstützt das Auflisten der typvisualisierungen in der Implementierung von `IDebugProperty3::GetCustomViewerCount` und `IDebugProperty3::GetCustomViewerList` . Diese Methoden übergeben den-Befehl an die entsprechenden Methoden [getcustomviewercount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) und [getcustomviewerlist](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).  
  
 Der [ieevisualizerservice](../../extensibility/debugger/reference/ieevisualizerservice.md) wird durch Aufrufen von [createvisualizerservice](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)abgerufen. Diese Methode erfordert die [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) -Schnittstelle, die von der [idebugbinder](../../extensibility/debugger/reference/idebugbinder.md) -Schnittstelle abgerufen wird, die an [evaluatesync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)übergeben wird. `IEEVisualizerServiceProvider::CreateVisualizerService` erfordert auch die [idebugsymbolprovider](../../extensibility/debugger/reference/idebugsymbolprovider.md) -Schnittstelle und die [idebugaddress](../../extensibility/debugger/reference/idebugaddress.md) -Schnittstelle, die an übergeben wurden `IDebugParsedExpression::EvaluateSync` . Die letzte Schnittstelle, die zum Erstellen der `IEEVisualizerService` Schnittstelle erforderlich ist, ist die [ieevisualizerdataprovider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) -Schnittstelle, die der EE implementiert. Diese Schnittstelle ermöglicht das vornehmen von Änderungen an der Eigenschaft, die visualisiert wird. Alle Eigenschafts Daten werden in einer [idebugobject](../../extensibility/debugger/reference/idebugobject.md) -Schnittstelle gekapselt, die auch vom EE implementiert wird.  
  
### <a name="accessing-property-data"></a>Zugreifen auf Eigenschafts Daten  
 Der Zugriff auf Eigenschaften Daten erfolgt über die [ipropertyproxyeeside](../../extensibility/debugger/reference/ipropertyproxyeeside.md) -Schnittstelle. Um diese Schnittstelle zu erhalten, ruft Visual Studio [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) für das Property-Objekt auf, um die [ipropertyproxyprovider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) -Schnittstelle abzurufen (implementiert auf das gleiche Objekt, das die [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle implementiert) und ruft dann die [getpropertyproxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) -Methode auf, um die `IPropertyProxyEESide` Schnittstelle abzurufen  
  
 Alle Daten, die an die Schnittstelle übertragen werden, werden `IPropertyProxyEESide` in der [ieedatastorage](../../extensibility/debugger/reference/ieedatastorage.md) -Schnittstelle gekapselt. Diese Schnittstelle stellt ein Bytearray dar und wird von Visual Studio und der EE implementiert. Wenn die Daten einer Eigenschaft geändert werden sollen, erstellt Visual Studio ein `IEEDataStorage` Objekt, das die neuen Daten enthält, und ruft " [kreatereplacementobject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) " mit diesem Datenobjekt auf, um ein neues Objekt zu erhalten, `IEEDataStorage` das wiederum an " [inplaceupdateobject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) " übergeben wird, um die Daten der Eigenschaft zu aktualisieren. `IPropertyProxyEESide::CreateReplacementObject` ermöglicht es dem EE, seine eigene Klasse zu instanziieren, die die- `IEEDataStorage` Schnittstelle implementiert.  
  
## <a name="supporting-custom-viewers"></a>Unterstützen benutzerdefinierter Viewer  
 Das-Flag `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` wird im- `dwAttrib` Feld der [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) Struktur festgelegt (zurückgegeben durch einen [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)-Befehl), um anzugeben, dass dem Objekt ein benutzerdefinierter Viewer zugeordnet ist. Wenn dieses Flag festgelegt ist, ruft Visual Studio die [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle mithilfe von [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)von der [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle ab.  
  
 Wenn der Benutzer einen benutzerdefinierten Viewer auswählt, instanziiert Visual Studio den benutzerdefinierten Viewer mithilfe der `CLSID` von der-Methode bereitgestellten Viewer `IDebugProperty3::GetCustomViewerList` . Visual Studio ruft dann [displayvalue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) auf, um dem Benutzer den Wert anzuzeigen.  
  
 Normalerweise `IDebugCustomViewer::DisplayValue` stellt eine schreibgeschützte Ansicht der Daten dar. Um Änderungen an den Daten zuzulassen, muss der EE eine benutzerdefinierte Schnittstelle implementieren, die das Ändern von Daten in einem Eigenschafts Objekt unterstützt. Die `IDebugCustomViewer::DisplayValue` Methode verwendet diese benutzerdefinierte Schnittstelle, um das Ändern der Daten zu unterstützen. Die-Methode sucht in der `IDebugProperty2` Schnittstelle, die als Argument weitergegeben wird, nach der benutzerdefinierten Schnittstelle `pDebugProperty` .  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Unterstützen von typvisualisierungen und benutzerdefinierten Viewern  
 Ein EE kann sowohl typvisualisierungen als auch benutzerdefinierte Viewer in der [getcustomviewercount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) -Methode und der [getcustomviewerlist](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) -Methode unterstützen. Zuerst fügt der EE die Anzahl von benutzerdefinierten Viewern, die er bereitstellt, dem Wert hinzu, der von der [getcustomviewercount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) -Methode zurückgegeben wird. Zweitens fügt der EE die `CLSID` e seiner eigenen benutzerdefinierten Viewer an die von der [getcustomviewerlist](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) -Methode zurückgegebene Liste an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugtasks](../../extensibility/debugger/debugging-tasks.md)   
 [Typschnellansicht und benutzerdefinierter Viewer](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
