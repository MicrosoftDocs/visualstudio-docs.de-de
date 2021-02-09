---
title: Portieren eines Ports | Microsoft-Dokumentation
description: Erfahren Sie, wie Visual Studio einen Port für die Debug-Engine bereitstellt, um Programmknoten mit dem Port zu registrieren und Anforderungen nach Prozessinformationen zu erfüllen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1f3ee9c145a4c6275f64d357d87ac1cc284bfac6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921296"
---
# <a name="get-a-port"></a>Port erhalten
Ein Port stellt eine Verbindung zu einem Computer dar, auf dem Prozesse ausgeführt werden. Bei diesem Computer kann es sich um den lokalen Computer oder einen Remote Computer handeln (auf dem möglicherweise ein nicht Windows-basiertes Betriebssystem ausgeführt wird; weitere Informationen finden Sie unter [Ports](../../extensibility/debugger/ports.md) ).

Ein Port wird durch die [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) -Schnittstelle dargestellt. Sie dient zum Abrufen von Informationen zu Prozessen, die auf dem Computer ausgeführt werden, mit dem der Port verbunden ist.

Eine Debug-Engine benötigt Zugriff auf einen Port, um Programmknoten mit dem Port zu registrieren und Anforderungen für Prozessinformationen zu erfüllen. Wenn die Debug-Engine z. b. die [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) -Schnittstelle implementiert, kann die Implementierung für die [getproviderprocessdata](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) -Methode den Port auffordern, die erforderlichen Prozessinformationen zu erhalten, die zurückgegeben werden sollen.

Visual Studio stellt den erforderlichen Port für die Debug-Engine bereit und erhält diesen Port von einem Port Lieferanten. Wenn ein Programm an angefügt wird (entweder aus dem Debugger oder aufgrund einer Ausnahme, die das Just-in-Time-Dialogfeld [JIT] auslöst), erhält der Benutzer die Auswahl des Transports (ein anderer Name für einen Port Lieferanten), der verwendet werden soll. Andernfalls gibt das Projekt System den zu verwendenden Port Lieferanten an, wenn der Benutzer das Programm im Debugger startet. In beiden Ereignissen instanziiert Visual Studio den Port Lieferanten, der durch eine [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) -Schnittstelle dargestellt wird, und fordert durch Aufrufen von [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) mit einer [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) -Schnittstelle einen neuen Port an. Dieser Port wird dann in einem oder einem anderen Formular an die Debug-Engine weitergegeben.

## <a name="example"></a>Beispiel
Dieses Code Fragment zeigt, wie Sie den Port, der für [launchangeh alten wird](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) , verwenden, um einen Programmknoten in " [resumeprocess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)" zu registrieren. Nicht direkt mit diesem Konzept verknüpfte Parameter wurden aus Gründen der Übersichtlichkeit ausgelassen.

> [!NOTE]
> Dieses Beispiel verwendet den Port, um den Prozess zu starten und fortzusetzen. dabei wird davon ausgegangen, dass die [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) -Schnittstelle auf dem Port implementiert ist. Dies bedeutet Nein, dass die einzige Möglichkeit zum Ausführen dieser Aufgaben ist, und es ist möglich, dass der Port möglicherweise nicht einmal beteiligt ist, um die [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) des Programms zu erhalten.

```cpp
// This is an IDebugEngineLaunch2 method.
HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,
                                      IDebugPort2 *pPort,
                                      /* omitted parameters */,
                                      IDebugProcess2**ppDebugProcess)
{
    // do stuff here to set up for a launch (such as handling the other parameters)
    ...

    // Now get the IPortNotify2 interface so we can register a program node
    // in CDebugEngine::ResumeProcess.
    CComPtr<IDebugDefaultPort2> spDefaultPort;
    HRESULT hr = pPort->QueryInterface(&spDefaultPort);
    if (SUCCEEDED(hr))
    {
        CComPtr<IDebugPortNotify2> spPortNotify;
        hr = spDefaultPort->GetPortNotify(&spPortNotify);
        if (SUCCEEDED(hr))
        {
            // Remember the port notify so we can use it in ResumeProcess.
            m_spPortNotify = spPortNotify;

            // Now launch the process in a suspended state and return the
            // IDebugProcess2 interface
            CComPtr<IDebugPortEx2> spPortEx;
            hr = pPort->QueryInterface(&spPortEx);
            if (SUCCEEDED(hr))
            {
                // pass on the parameters we were given (omitted here)
                hr = spPortEx->LaunchSuspended(/* omitted parameters */,ppDebugProcess)
            }
        }
    }
    return(hr);
}

HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)
{
    // Make a program node for this process
    HRESULT hr;
    CComPtr<IDebugProgramNode2> spProgramNode;
    hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);
    if (SUCCEEDED(hr))
    {
        hr = m_spPortNotify->AddProgramNode(spProgramNode);
        if (SUCCEEDED(hr))
        {
            // resume execution of the process using the port given to us earlier.
            // (Querying for the IDebugPortEx2 interface is valid here since
            // that's how we got the IDebugPortNotify2 interface in the first place.)
            CComPtr<IDebugPortEx2> spPortEx;
            hr = m_spPortNotify->QueryInterface(&spPortEx);
            if (SUCCEEDED(hr))
            {
                hr = spPortEx->ResumeProcess(pDebugProcess);
            }
        }
    }
    return(hr);
}
```

## <a name="see-also"></a>Weitere Informationen
- [Programm wird registriert](../../extensibility/debugger/registering-the-program.md)
- [Aktivieren eines deaktivierte Programms](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [Port Lieferanten](../../extensibility/debugger/port-suppliers.md)
- [Ports](../../extensibility/debugger/ports.md)
