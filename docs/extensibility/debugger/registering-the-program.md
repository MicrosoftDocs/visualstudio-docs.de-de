---
title: Registrieren des Programms | Microsoft-Dokumentation
description: Erfahren Sie, wie ein zu debuggende Programm mit einem Port registriert wird, nachdem die Debug-Engine einen Port abruft.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80c3d13cc7319e43390a7e9e6f4eb42a5a87c780
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847095"
---
# <a name="register-the-program"></a>Programm registrieren
Nachdem die Debug-Engine einen Port abgerufen hat, der durch eine [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) -Schnittstelle dargestellt wird, besteht der nächste Schritt bei der Aktivierung des zu debuggenden Programms darin, Sie mit dem Port zu registrieren. Nach der Registrierung kann das Programm auf eine der folgenden Weise debuggt werden:

- Der Anfüge Vorgang, mit dem der Debugger die gesamte debugsteuerung einer laufenden Anwendung erhalten kann.

- Just-in-time (JIT)-Debuggen, das das After-the-fact-Debuggen eines Programms ermöglicht, das unabhängig von einem Debugger ausgeführt wird. Wenn die Lauf Zeit Architektur einen Fehler abfängt, wird der Debugger benachrichtigt, bevor das Betriebssystem oder die Laufzeitumgebung den Speicher und die Ressourcen des faulingprogramms freigibt.

## <a name="registering-procedure"></a>Prozedur wird registriert

### <a name="to-register-your-program"></a>So registrieren Sie Ihr Programm

1. Ruft die vom Port implementierte [addprogram Node](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) -Methode auf.

     `IDebugPortNotify2::AddProgramNode` erfordert einen Zeiger auf eine [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) -Schnittstelle.

     Wenn das Betriebssystem oder die Laufzeitumgebung ein Programm lädt, wird normalerweise der Programmknoten erstellt. Wenn die Debug-Engine (de) aufgefordert wird, das Programm zu laden, erstellt und registriert das Programm den Programmknoten.

     Das folgende Beispiel zeigt die Debug-Engine, mit der das Programm gestartet und mit einem Port registriert wird.

    > [!NOTE]
    > Dieses Codebeispiel ist nicht die einzige Möglichkeit, einen Prozess zu starten und fortzusetzen. Dieser Code ist hauptsächlich ein Beispiel für das Registrieren eines Programms mit einem Port.

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
                    hr  = spPortEx->ResumeProcess(pDebugProcess);
                }
            }
        }
        return(hr);
    }

    ```

## <a name="see-also"></a>Siehe auch
- [Portieren eines Ports](../../extensibility/debugger/getting-a-port.md)
- [Aktivieren eines deaktivierte Programms](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
