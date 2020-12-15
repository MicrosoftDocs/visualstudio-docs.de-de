---
title: Verwenden von Visual Studio-Interop-Assemblys | Microsoft-Dokumentation
description: Erfahren Sie, wie Visual Studio-Interopassemblys verwalteten Anwendungen den Zugriff auf die COM-Schnittstellen gestatten, die Visual Studio-Erweiterbarkeit bieten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c52dd2cf8c76cdef9be5080950d5f1b9e621e70
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487659"
---
# <a name="using-visual-studio-interop-assemblies"></a>Verwenden von Visual Studio-Interop-Assemblys
Visual Studio Interop-Assemblys ermöglichen verwalteten Anwendungen den Zugriff auf die COM-Schnittstellen, die Visual Studio-Erweiterbarkeit bereitstellen. Es gibt einige Unterschiede zwischen geraden com-Schnittstellen und ihren Interop-Versionen. HRESULTs werden z. b. in der Regel als int-Werte dargestellt und müssen auf die gleiche Weise wie Ausnahmen behandelt werden, und Parameter (insbesondere out-Parameter) werden anders behandelt.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Behandeln von HRESULTs, die von COM an verwalteten Code zurückgegeben werden
 Wenn Sie eine COM-Schnittstelle in verwaltetem Code aufrufen, überprüfen Sie den HRESULT-Wert, und lösen Sie ggf. eine Ausnahme aus. Die <xref:Microsoft.VisualStudio.ErrorHandler>-Klasse enthält die <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>-Methode, die abhängig vom Wert des an sie übergebenen HRESULTs eine COM-Ausnahme auslöst.

 Die <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>-Methode löst standardmäßig eine Ausnahme aus, wenn ihr ein HRESULT mit einem Wert kleiner als 0 (null) übergeben wird. In Fällen, in denen solche HRESULTs zulässige Werte aufweisen und keine Ausnahme ausgelöst werden soll, müssen die Werte der zusätzlichen HRESULTS nach dem Überprüfen der Werte an <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> übergeben werden. Wenn das überprüfte HRESULT explizit an <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> übergebenen HRESULT-Werten entspricht, wird keine Ausnahme ausgelöst.

> [!NOTE]
> Die- <xref:Microsoft.VisualStudio.VSConstants> Klasse enthält Konstanten für allgemeine HRESULTs, z. b. <xref:Microsoft.VisualStudio.VSConstants.S_OK> und <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> , sowie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULTs, z <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> . b <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> . und. <xref:Microsoft.VisualStudio.VSConstants> enthält auch die Methoden <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> und <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>, die den Makros SUCCEEDED und FAILED in COM entsprechen.

 Betrachten Sie beispielsweise den folgenden Funktionsaufruf, bei dem <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> ein zulässiger Rückgabewert ist, aber alle anderen HRESULTs kleiner als 0 (null) einen Fehler darstellen.

 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]

 Wenn es mehrere zulässige Rückgabewerte gibt, können zusätzliche HRESULT-Werte einfach an die Liste in dem Aufruf von <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> angefügt werden.

 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]

## <a name="returning-hresults-to-com-from-managed-code"></a>Von verwaltetem Code an COM zurückgegebene HRESULTS
 Wenn keine Ausnahme auftritt, gibt der verwaltete Code <xref:Microsoft.VisualStudio.VSConstants.S_OK> an die aufrufende COM-Funktion zurück. COM-Interop unterstützt allgemeine Ausnahmen, die in verwaltetem Code stark typisiert sind. Eine Methode, die ein unzulässiges `null`-Argument empfängt, löst beispielsweise eine <xref:System.ArgumentNullException> aus.

 Wenn Sie nicht sicher sind, welche Ausnahme ausgelöst werden soll, aber das HRESULT kennen, das an COM zurückgegeben werden soll, können Sie die <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>-Methode verwenden, um eine entsprechende Ausnahme auszulösen. Dies funktioniert auch bei einem nicht standardmäßigen Fehler, z. B. <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> versucht, das übergebene HRESULT einer stark typisierten Ausnahme zuzuordnen. Wenn dies nicht möglich ist, wird stattdessen eine generische COM-Ausnahme ausgelöst. Als endgültiges Ergebnis wird das an <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> übergebene HRESULT vom verwaltetem Code an die aufrufende COM-Funktion zurückgegeben.

> [!NOTE]
> Ausnahmen beeinträchtigen die Leistung und dienen als Hinweis auf anormale Programmbedingungen. Häufig auftretende Bedingungen sollten inline behandelt werden, statt eine Ausnahme auszulösen.

## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown-Parameter, die als Typ void * * übertragen wurden
 Suchen Sie nach [out]-Parametern, die `void **` in der COM-Schnittstelle als Typ definiert sind, aber `[``iid_is``]` im-Prototyp der Interop-Assemblymethode als definiert sind [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Manchmal generiert eine COM-Schnittstelle ein `IUnknown` Objekt, und die COM-Schnittstelle übergibt sie als Typ `void **` . Diese Schnittstellen sind besonders wichtig, denn wenn die Variable als [out] in der IDL definiert ist, `IUnknown` wird das Objekt mit der-Methode auf Verweis gezählt `AddRef` . Ein Speicherfehler tritt auf, wenn das Objekt nicht ordnungsgemäß behandelt wird.

> [!NOTE]
> Ein `IUnknown` Objekt, das von der COM-Schnittstelle erstellt und in einer [out]-Variablen zurückgegeben wird, verursacht einen Speicherlecks, wenn es nicht explizit freigegeben wird

 Verwaltete Methoden, die solche Objekte verarbeiten <xref:System.IntPtr> , sollten als Zeiger auf ein `IUnknown` -Objekt behandeln und die- <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> Methode zum Abrufen des-Objekts aufzurufen. Der Aufrufer sollte dann den Rückgabewert in den entsprechenden Typ umwandeln. Wenn das Objekt nicht mehr benötigt wird, wird aufgerufen, <xref:System.Runtime.InteropServices.Marshal.Release%2A> um es freizugeben.

 Im folgenden finden Sie ein Beispiel für das Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> -Methode und das korrekte behandeln des- `IUnknown` Objekts:

```
MyClass myclass;
Object object;
IntPtr pObj;
Guid iid = Typeof(MyClass).Guid;
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);
if (NativeMethods.Succeeded(hr))
{
    try
    {
        object = Marshal.GetObjectForIUnknown(pObj);
        myclass = object;
    }
    finally
    {
        Marshal.Release(pObj);
    }
}
else
{
    // error calling QueryViewInterface
}
```

> [!NOTE]
> Die folgenden Methoden sind bekannt, dass `IUnknown` Objekt Zeiger als Typ übergeben werden <xref:System.IntPtr> . Behandeln Sie Sie wie in diesem Abschnitt beschrieben.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>Optionale [out]-Parameter
 Suchen Sie nach Parametern, die als [out]-Datentyp ( `int` , `object` usw.) in der COM-Schnittstelle definiert sind, jedoch als Arrays desselben Datentyps im [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interopassemblymethode-Prototyp definiert sind.

 Einige COM-Schnittstellen, wie z <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> . b., behandeln [out]-Parameter als optional. Wenn ein Objekt nicht erforderlich ist, geben diese COM-Schnittstellen einen `null` Zeiger als Wert dieses Parameters zurück, anstatt das [out]-Objekt zu erstellen. Dies ist beabsichtigt. Für diese Schnittstellen `null` werden Zeiger als Teil des korrekten Verhaltens des VSPackages angenommen, und es wird kein Fehler zurückgegeben.

 Da die CLR den Wert eines [out]-Parameters nicht zulässt `null` , ist ein Teil des entworfenen Verhaltens dieser Schnittstellen nicht direkt in verwaltetem Code verfügbar. Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Interop-AssemblyMethoden für betroffene Schnittstellen umgehen das Problem, indem die relevanten Parameter als Arrays definiert werden, da die CLR das Übergeben von `null` Arrays zulässt.

 Verwaltete Implementierungen dieser Methoden sollten ein- `null` Array in den-Parameter einfügen, wenn nichts zurückgegeben werden muss. Andernfalls erstellen Sie ein Array mit einem Element des richtigen Typs und fügen den Rückgabewert in das Array ein.

 Verwaltete Methoden, die Informationen von Schnittstellen mit optionalen [out]-Parametern empfangen, empfangen den Parameter als Array. Überprüfen Sie einfach den Wert des ersten Elements des Arrays. Wenn dies nicht der Fall ist `null` , behandeln Sie das erste Element, als wäre es der ursprüngliche Parameter.

## <a name="passing-constants-in-pointer-parameters"></a>Übergeben von Konstanten in Zeiger Parametern
 Suchen Sie nach Parametern, die in der COM-Schnittstelle als [in]-Zeiger definiert sind, die <xref:System.IntPtr> im-Prototyp der interopassemblymethode als Typ definiert sind [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Ein ähnliches Problem tritt auf, wenn eine COM-Schnittstelle einen speziellen Wert, z. b. 0,-1 oder-2, anstelle eines Objekt Zeigers übergibt. Im Gegensatz [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] zu lässt die CLR nicht zu, dass Konstanten als-Objekte umgewandelt werden. Stattdessen definiert die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Interop-Assembly den Parameter als <xref:System.IntPtr> Typ.

 Verwaltete Implementierungen dieser Methoden sollten die Tatsache nutzen, dass die <xref:System.IntPtr> -Klasse sowohl `int` -als auch- `void *` Konstruktoren besitzt <xref:System.IntPtr> , um entweder aus einem Objekt oder einer ganzzahligen Konstante zu erstellen.

 Verwaltete Methoden, die <xref:System.IntPtr> Parameter dieses Typs empfangen, sollten die <xref:System.IntPtr> Typkonvertierungs Operatoren verwenden, um die Ergebnisse zu verarbeiten. Konvertieren Sie zuerst den <xref:System.IntPtr> in, `int` und testen Sie ihn anhand relevanter ganzzahliger Konstanten. Wenn keine Werte gefunden werden, konvertieren Sie Sie in ein Objekt des erforderlichen Typs, und fahren Sie fort.

 Beispiele hierfür finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .

## <a name="ole-return-values-passed-as-out-parameters"></a>Als [out] Parameter über gegebene OLE-Rückgabewerte
 Suchen Sie nach Methoden, die über einen `retval` Rückgabewert in der COM-Schnittstelle verfügen, aber einen `int` Rückgabewert und einen zusätzlichen [out]-Array Parameter im [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interopassemblymethode-Prototyp aufweisen. Es sollte klar sein, dass diese Methoden eine besondere Behandlung erfordern, da die Methoden der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interopassemblymethode einen größeren Parameter aufweisen als die COM-Schnittstellen Methoden.

 Viele COM-Schnittstellen, die die OLE-Aktivität behandeln, senden Informationen zum OLE-Status zurück an das aufrufende Programm, das im `retval` Rückgabewert der Schnittstelle gespeichert ist. Anstatt einen Rückgabewert zu verwenden, senden die entsprechenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Interop-AssemblyMethoden die Informationen an das aufrufende Programm zurück, das in einem [out]-Array Parameter gespeichert ist.

 Verwaltete Implementierungen dieser Methoden sollten ein Array mit einem einzelnen Element desselben Typs wie der [out]-Parameter erstellen und im-Parameter ablegen. Der Wert des Array Elements muss mit dem entsprechenden com identisch sein `retval` .

 Verwaltete Methoden, die Schnittstellen dieses Typs aufzurufen, sollten das erste Element aus dem [out]-Array abrufen. Dieses Element kann so behandelt werden, als ob es ein `retval` Rückgabewert von der entsprechenden COM-Schnittstelle wäre.

## <a name="see-also"></a>Siehe auch
- [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)
