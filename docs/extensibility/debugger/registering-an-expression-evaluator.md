---
title: Registrieren einer Ausdrucks Auswertung | Microsoft-Dokumentation
description: Erfahren Sie, wie sich die Ausdrucks Auswertung als Klassenfactory mit der Windows com-Umgebung und Visual Studio registrieren muss.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1074e8dea5dfdb05571d3b1aa04e5c411530bb1f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961104"
---
# <a name="register-an-expression-evaluator"></a>Registrieren einer Ausdrucks Auswertung
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Die Ausdrucks Auswertung (EE) muss sich selbst als Klassenfactory mit der Windows-com-Umgebung und Visual Studio registrieren. Ein EE ist als DLL eingerichtet, sodass er entweder in den debuggingbereich (de) oder den Visual Studio-Adressraum eingefügt wird, je nachdem, welche Entität den EE instanziiert.

## <a name="managed-code-expression-evaluator"></a>Ausdrucks Auswertung für verwalteten Code
 Ein verwalteter Code EE ist als Klassenbibliothek implementiert, bei der es sich um eine DLL handelt, die sich bei der com-Umgebung registriert, die in der Regel durch einen aufrufsbefehl des VSIP- *regpkg.exe* Programms gestartet wird. Der tatsächliche Prozess zum Schreiben der Registrierungsschlüssel für die com-Umgebung wird automatisch behandelt.

 Eine Methode der Hauptklasse ist mit gekennzeichnet <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> und gibt an, dass die Methode aufgerufen werden soll, wenn die DLL mit com registriert wird. Diese Registrierungsmethode, die häufig aufgerufen `RegisterClass` wird, führt die Aufgabe der Registrierung der dll in Visual Studio aus. Ein entsprechendes `UnregisterClass` (markiert mit <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> ) macht die Auswirkungen von, `RegisterClass` Wenn die DLL deinstalliert wird, nicht mehr.
Die gleichen Registrierungseinträge werden für einen EE erstellt, der in nicht verwaltetem Code geschrieben wurde. der einzige Unterschied besteht darin, dass es keine Hilfsfunktion gibt, wie z `SetEEMetric` . b., um die Arbeit zu erledigen. Im folgenden finden Sie ein Beispiel für die Registrierung und die Aufhebung der Registrierung.

### <a name="example"></a>Beispiel
 Die folgende Funktion zeigt, wie sich ein verwalteter Code EE registriert und sich bei Visual Studio anmeldet.

```csharp
namespace EEMC
{
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]
    public class EEMCClass : IDebugExpressionEvaluator
    {
        #region Register and unregister.
        private static Guid guidMycLang = new Guid("462D4A3E-B257-4AEE-97CD-5918C7531757");
        private static string languageName = "MyC";
        private static string eeName = "MyC Expression Evaluator";

        private static Guid guidMicrosoftVendor = new Guid("994B45C4-E6E9-11D2-903F-00C04FA302A1");
        private static Guid guidCOMPlusOnlyEng = new Guid("449EC4CC-30D2-4032-9256-EE18EB41B62B");
        private static Guid guidCOMPlusNativeEng = new Guid("92EF0900-2251-11D2-B72E-0000F87572EF");

        /// <summary>
        /// Register the expression evaluator.
        /// Set "project properties/configuration properties/build/register for COM interop" to true.
        /// </summary>
         [ComRegisterFunctionAttribute]
        public static void RegisterClass(Type t)
        {
            // Get Visual Studio version (set by regpkg.exe)
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");
            string s = @"SOFTWARE\Microsoft\VisualStudio\"
                        + hive
                        + @"\AD7Metrics\ExpressionEvaluator";

            RegistryKey rk = Registry.LocalMachine.CreateSubKey(s);
            if (rk == null)  return;

            rk = rk.CreateSubKey(guidMycLang.ToString("B"));
            rk = rk.CreateSubKey(guidMicrosoftVendor.ToString("B"));
            rk.SetValue("CLSID", t.GUID.ToString("B"));
            rk.SetValue("Language", languageName);
            rk.SetValue("Name", eeName);

            rk = rk.CreateSubKey("Engine");
            rk.SetValue("0", guidCOMPlusOnlyEng.ToString("B"));
            rk.SetValue("1", guidCOMPlusNativeEng.ToString("B"));
        }
        /// <summary>
        /// Unregister the expression evaluator.
        /// </summary>
         [ComUnregisterFunctionAttribute]
        public static void UnregisterClass(Type t)
        {
            // Get Visual Studio version (set by regpkg.exe)
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");
            string s = @"SOFTWARE\Microsoft\VisualStudio\"
                        + hive
                        + @"\AD7Metrics\ExpressionEvaluator\"
                        + guidMycLang.ToString("B");
            RegistryKey key = Registry.LocalMachine.OpenSubKey(s);
            if (key != null)
            {
                key.Close();
                Registry.LocalMachine.DeleteSubKeyTree(s);
            }
        }
    }
}
```

## <a name="unmanaged-code-expression-evaluator"></a>Ausdrucks Auswertung für nicht verwalteten Code
 Die EE-dll implementiert die- `DllRegisterServer` Funktion, um sich selbst bei der com-Umgebung und Visual Studio zu registrieren.

> [!NOTE]
> Sie finden den Codebeispiel Registrierungscode "mycee" in der Datei " *dllentry. cpp*", die sich in der VSIP-Installation unter "envsdk\mycpkgs\mycee" befindet.

### <a name="dll-server-process"></a>DLL-Server Prozess
 Beim Registrieren des EE-Servers lautet der DLL-Server:

1. Registriert die Klassenfactory gemäß den `CLSID` normalen com-Konventionen.

2. Ruft die Hilfsfunktion `SetEEMetric` auf, um die in der folgenden Tabelle dargestellten EE-Metriken mit Visual Studio zu registrieren. Die `SetEEMetric` -Funktion und die folgenden Metriken sind Teil der *dbgmetric. lib* -Bibliothek. Weitere Informationen finden Sie unter SDK-Hilfsprogramme [für das Debugging](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) .

    |Metrik|BESCHREIBUNG|
    |------------|-----------------|
    |`metricCLSID`|`CLSID` der EE-Klassenfactory|
    |`metricName`|Der Name des EE als anzeigbare Zeichenfolge.|
    |`metricLanguage`|Der Name der Sprache, für die der EE ausgewertet werden soll|
    |`metricEngine`|`GUID`e der debugengines (de), die mit diesem EE arbeiten|

    > [!NOTE]
    > Der `metricLanguage``GUID` identifiziert die Sprache anhand des Namens, aber dies ist das `guidLang` Argument für, `SetEEMetric` das die Sprache auswählt. Wenn der Compiler die debuginformationsdatei generiert, sollte er den entsprechenden schreiben, `guidLang` damit der de weiß, welcher EE verwendet werden soll. Der "de" fragt in der Regel den Symbol Anbieter nach dieser Sprache ab `GUID` , die in der debuginformationsdatei gespeichert ist.

3. Wird bei Visual Studio registriert, indem Schlüssel unter HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *x. y* erstellt werden, wobei *x. y* die Version von Visual Studio ist, bei der die Registrierung erfolgt.

### <a name="example"></a>Beispiel
 Die folgende Funktion zeigt, wie sich ein nicht verwalteter Code (C++) EE registriert und seine Registrierung bei Visual Studio abhebt.

```cpp
/*---------------------------------------------------------
  Registration
-----------------------------------------------------------*/
#ifndef LREGKEY_VISUALSTUDIOROOT
    #define LREGKEY_VISUALSTUDIOROOT L"Software\\Microsoft\\VisualStudio\\8.0"
#endif

static HRESULT RegisterMetric( bool registerIt )
{
    // check where we should register
    const ULONG cchBuffer = _MAX_PATH;
    WCHAR wszRegistrationRoot[cchBuffer];
    DWORD cchFreeBuffer = cchBuffer - 1;
    wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT_NOVERSION);
    wcscat(wszRegistrationRoot, L"\\");

    // this is Environment SDK specific
    // we check for  EnvSdk_RegKey environment variable to
    // determine where to register
    DWORD cchDefRegRoot = lstrlenW(LREGKEY_VISUALSTUDIOROOT_NOVERSION) + 1;
    cchFreeBuffer = cchFreeBuffer - cchDefRegRoot;
    DWORD cchEnvVarRead = GetEnvironmentVariableW(
        /* LPCTSTR */ L"EnvSdk_RegKey", // environment variable name
        /* LPTSTR  */ &wszRegistrationRoot[cchDefRegRoot],// buffer for variable value
        /* DWORD   */ cchFreeBuffer);// size of buffer
    if (cchEnvVarRead >= cchFreeBuffer)
        return E_UNEXPECTED;
    // If the environment variable does not exist then we must use
    // LREGKEY_VISUALSTUDIOROOT which has the version number.
    if (0 == cchEnvVarRead)
        wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT);

    if (registerIt)
    {
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricCLSID,
                    CLSID_MycEE,
                    wszRegistrationRoot );
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricName,
                    GetString(IDS_INFO_MYCDESCRIPTION),
                    wszRegistrationRoot );
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricLanguage, L"MyC",
                    wszRegistrationRoot);

        GUID engineGuids[2];
        engineGuids[0] = guidCOMPlusOnlyEng;
        engineGuids[1] = guidCOMPlusNativeEng;
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricEngine,
                    engineGuids,
                    2,
                    wszRegistrationRoot);
    }
    else
    {
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricCLSID,
                        wszRegistrationRoot);
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricName,
                        wszRegistrationRoot );
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricLanguage,
                        wszRegistrationRoot );
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricEngine,
                        wszRegistrationRoot );
    }

    return S_OK;
}
```

## <a name="see-also"></a>Weitere Informationen
- [Schreiben einer CLR-Ausdrucks Auswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [SDK-Hilfsprogramme zum Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
