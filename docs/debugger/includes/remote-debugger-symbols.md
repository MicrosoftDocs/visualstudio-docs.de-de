---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 5033580f253a5eb42cbc64656e8c4661a2e246c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72912848"
---
Sie sollten Ihren Code mit den auf dem Visual Studio-Computer generierten Symbolen debuggen können. Die Leistung des Remotedebuggers ist viel besser, wenn Sie lokale Symbole verwenden.  Wenn Sie Remotesymbole verwenden müssen, ist es erforderlich, dem Remotedebugmonitor mitzuteilen, dass er auf dem Remotecomputer nach Symbolen suchen soll.  

Ab Visual Studio 2013 Update 2 können Sie über die folgende msvsmon-Befehlszeilenoption Remotesymbole für verwalteten Code verwenden: `Msvsmon /FallbackLoadRemoteManagedPdbs`  

Weitere Informationen finden Sie in der Hilfe zum Remotedebugging (drücken Sie **F1** im Remotedebuggerfenster, oder klicken Sie auf **Hilfe > Verwendung**). Weitere Informationen finden Sie unter [.NET Remote Symbol Loading Changes in Visual Studio 2012 and 2013 (Änderungen beim Laden von Symbolen in der .NET-Remoteinstanz in Visual Studio 2012 und 2013)](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/).
