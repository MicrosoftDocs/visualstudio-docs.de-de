---
title: Initialisierungs Sequenz von Projekt Untertypen | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Initialisierungs Sequenz in der Visual Studio-Umgebung für ein Projekt System, das von mehreren Projekt Untertypen aggregiert wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea784eae808cbab3a5991651961d3b150b641c04
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204708"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Initialisierungssequenz von Projektuntertypen
Die Umgebung erstellt ein Projekt durch Aufrufen der Basis-projektfactory-Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> . Die Erstellung eines Projekt unter Typs beginnt, wenn die Umgebung feststellt, dass die Projekttyp-GUID-Liste für die Erweiterung einer Projektdatei nicht leer ist. Die Projektdatei Erweiterung und die Projekt-GUID geben an, ob das Projekt ein- [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] oder- [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Projekttyp ist Beispielsweise identifizieren die VBPROJ-Erweiterung und {F184B08F-C81C-45F6-A57F-5ABD9991F28F} ein [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekt.

## <a name="environments-initialization-of-project-subtypes"></a>Initialisierung von Projekt Untertypen in der Umgebung
 Im folgenden Verfahren wird die Initialisierungs Sequenz für ein Projekt System erläutert, das von mehreren Projekt Untertypen aggregiert wird.

1. Die Umgebung Ruft die des Basis Projekts auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> , und während das Projekt seine Projektdatei analysiert, erkennt es, dass es sich bei der Liste der Typen des Aggregat Projekt Typs nicht um die Liste handelt `null` . Das Projekt wird nicht mehr direkt mit dem Projekt erstellt.

2. Das Projekt ruft `QueryService` den <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> Dienst auf, um einen Projekt Untertyp mithilfe der Implementierung der-Methode der Umgebung zu erstellen <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> . Innerhalb dieser Methode führt die Umgebung rekursive Funktionsaufrufe an Ihre Implementierungen <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> der <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> -und-Methoden aus, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> während Sie die Liste der Projekttyp-GUIDs durchläuft, beginnend mit dem äußersten Projekt Untertyp.

     Im folgenden werden die Initialisierungs Schritte ausführlich erläutert.

    1. Die Implementierung der-Methode der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> Methode ruft die- `HrCreateInnerProj` Methode mit der folgenden Funktionsdeklaration auf:

         \<CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Wenn diese Funktion zum ersten Mal aufgerufen wird, d. h. für den äußersten Projekt Untertyp, werden die Parameter `pOuter` und `pOwner` als `null` und die-Funktion als der äußerste Projekt Untertyp `IUnknown` auf festgelegt `pOuter` .

    2. Danach ruft die Umgebung die `HrCreateInnerProj` Funktion mit der zweiten Projekttyp-GUID in der Liste auf. Diese GUID entspricht dem zweiten inneren Projekt Untertyp, der in Richtung des Basis Projekts in der Aggregations Sequenz geht.

    3. Der `pOuter` verweist jetzt auf die `IUnknown` des äußersten Projekt unter Typs und ruft die- `HrCreateInnerProj` Implementierung von auf, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> gefolgt von einem Aufruf der-Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> . In <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> der Methode übergeben Sie die Steuerung `IUnknown` des äußersten Projekt unter Typs `pOuter` . Das eigene Projekt (Inner Project SubType) muss das Aggregat Projekt Objekt hier erstellen. In der <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> Methoden Implementierung übergeben Sie einen Zeiger auf den `IUnknown` des inneren Projekts, das aggregiert wird. Diese beiden Methoden erstellen das Aggregations Objekt, und ihre Implementierungen müssen com-Aggregations Regeln befolgen, um sicherzustellen, dass ein Projekt Untertyp keinen Verweis Zähler auf sich selbst enthält.

    4. `HrCreateInnerProj` Ruft die Implementierung von auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> . In dieser Methode führt der Projekt Untertyp seine Initialisierung aus. Sie können z. b. Lösungs Ereignisse in registrieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> .

    5. `HrCreateInnerProj` wird rekursiv aufgerufen, bis die letzte GUID (das Basisprojekt) in der Liste erreicht ist. Für jeden dieser Aufrufe werden die Schritte c bis d wiederholt. `pOuter` zeigt auf den äußersten Projekt Untertyp `IUnknown` für jede Aggregations Ebene.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird der programmgesteuerte Prozess in einer ungefähren Darstellung der-Methode ausführlich beschrieben, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> wie er von der-Umgebung implementiert wird. Der Code ist nur ein Beispiel. Sie ist nicht für die Kompilierung vorgesehen, und die Fehlerüberprüfung wurde aus Gründen der Übersichtlichkeit entfernt.

```cpp
HRESULT CreateAggregateProject
(
    LPCOLESTR lpstrGuids,
    LPCOLESTR pszFilename,
    LPCOLESTR pszLocation,
    LPCOLESTR pszName,
    VSCREATEPROJFLAGS grfCreateFlags,
    REFIID iidProject,
    void **ppvProject)
{
    HRESULT hr = NOERROR;
    CComPtr<IUnknown> srpunkProj;
    CComPtr<IVsAggregatableProject> srpAggProject;
    CComBSTR bstrGuids = lpstrGuids;
    BOOL fCanceled = FALSE;
    *ppvProject = NULL;

    HrCreateInnerProj(
         bstrGuids, NULL, NULL, pszFilename, pszLocation,
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);
    srpunkProj->QueryInterface(
        IID_IVsAggregatableProject, (void **)&srpAggProject));
    srpAggProject->OnAggregationComplete();
    srpunkProj->QueryInterface(iidProject, ppvProject);
}

HRESULT HrCreateInnerProj
(
    WCHAR *pwszGuids,
    IUnknown *pOuter,
    IVsAggregatableProject *pOwner,
    LPCOLESTR pszFilename,
    LPCOLESTR pszLocation,
    LPCOLESTR pszName,
    VSCREATEPROJFLAGS grfCreateFlags,
    IUnknown **ppInner,
    BOOL *pfCanceled
)
{
    HRESULT hr = NOERROR;
    CComPtr<IUnknown> srpInner;
    CComPtr<IVsAggregatableProject> srpAggInner;
    CComPtr<IVsProjectFactory> srpProjectFactory;
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;
    GUID guid = GUID_NULL;
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');
    WCHAR wszText[_MAX_PATH+150] = L"";

    if (pwszNextGuids)
    {
        *pwszNextGuids++ = 0;
    }

    CLSIDFromString(pwszGuids, &guid);
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(
        guid, &srpProjectFactory);
    srpProjectFactory->QueryInterface(
        IID_IVsAggregatableProjectFactory,
        (void **)&srpAggPF);
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);
    srpInner->QueryInterface(
        IID_IVsAggregatableProject, (void **)&srpAggInner);

    if (pOwner)
    {
        IfFailGo(pOwner->SetInnerProject(srpInner));
    }

    if (pwszNextGuids)
    {
        CComPtr<IUnknown> srpNextInner;
        HrCreateInnerProj(
            pwszNextGuids, pOuter ? pOuter : srpInner,
            srpAggInner, pszFilename, pszLocation, pszName,
            grfCreateFlags, &srpNextInner, pfCanceled);
    }

    return srpAggInner->InitializeForOuter(
        pszFilename, pszLocation, pszName, grfCreateFlags,
        IID_IUnknown, (void **)ppInner, pfCanceled);
}
```

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [Projektuntertypen](../../extensibility/internals/project-subtypes.md)
