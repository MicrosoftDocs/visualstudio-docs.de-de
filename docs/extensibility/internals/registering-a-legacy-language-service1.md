---
title: Registrieren einer Legacy Sprache Service1 | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Registrieren eines Legacy sprach Dienstanbieter bei einem VSPackage mit Visual Studio, indem Sie Registrierungsschlüssel und Einträge hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], registering
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e92c831ad3d2f4d75d57c48cfc7ba666d19b7a5e
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875203"
---
# <a name="registering-a-legacy-language-service-1"></a>Registrieren eines Legacy sprach Dienstanbieter 1
Im Managed Package Framework (MPF) wird der Sprachdienst von einem VSPackage (siehe [VSPackages](../../extensibility/internals/vspackages.md)) bereitgestellt und mit registriert, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] indem Registrierungsschlüssel und Einträge hinzugefügt werden. Dieser Registrierungsvorgang erfolgt teilweise während der Installation und teilweise zur Laufzeit.

## <a name="register-the-language-service-by-using-attributes"></a>Registrieren des sprach Dienstanbieter mithilfe von Attributen
 Die folgenden Attribute werden zum Registrieren eines sprach Dienstanbieter verwendet.

- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>

  Diese Attribute werden unten erläutert.

### <a name="provideserviceattribute"></a>Provide Service Attribute
 Dieses Attribut registriert ihren Sprachdienst als Dienst.

### <a name="example"></a>Beispiel

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideServiceAttribute(typeof(TestLanguageService),
                             ServiceName = "Test Language Service")]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguageserviceattribute"></a>Providelta anguageserviceattribute
 Mit diesem Attribut wird der Sprachdienst speziell als Sprachdienst registriert. Hiermit können Sie Optionen festlegen, die die von Ihrem Sprachdienst angebotenen Features angeben. Das Beispiel zeigt eine Teilmenge der Optionen, die ein Sprachdienst bereitstellen kann. Den vollständigen Satz von Sprachdienst Optionen finden Sie unter <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> .

### <a name="example"></a>Beispiel

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageServiceAttribute(typeof(TestLanguageService),
                             "Test Language",
                             106,             // resource ID of localized language name
                             CodeSense = true,             // Supports IntelliSense
                             RequestStockColors = false,   // Supplies custom colors
                             EnableCommenting = true,      // Supports commenting out code
                             EnableAsyncCompletion = true  // Supports background parsing
                             )]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguageextensionattribute"></a>Providelta anguageextensionattribute
 Mit diesem Attribut wird der Sprachdienst einer Dateierweiterung zugeordnet. Wenn eine Datei mit dieser Erweiterung geladen wird, wird der Sprachdienst in jedem Projekt gestartet und zum Anzeigen des Datei Inhalts verwendet.

### <a name="example"></a>Beispiel

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageExtensionAttribute(typeof(TestLanguageService),
                                       ".Testext")]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguagecodeexpansionattribute"></a>Providelta anguagecodeexpansionattribute
 Dieses Attribut registriert einen Speicherort, von dem Code Erweiterungs-oder Ausschnitt Vorlagen abgerufen werden. Diese Informationen werden vom- **Code Ausschnitt Browser** und vom-Editor verwendet, wenn ein Code Ausschnitt in die Quelldatei eingefügt wird.

### <a name="example"></a>Beispiel

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageCodeExpansionAttribute(
             typeof(TestLanguageService),
             "Test Language", // Name of language used as registry key.
             106,           // Resource ID of localized name of language service.
             "testlanguage",  // language key used in snippet templates.
             @"%InstallRoot%\Test Language\SnippetsIndex.xml",  // Path to snippets index
             SearchPaths = @"%InstallRoot%\Test Language\Snippets\%LCID%\Snippets\;" +
                           @"%TestDocs%\Code Snippets\Test Language\Test Code Snippets"
             )]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguageeditoroptionpageattribute"></a>Providelta optionpageattribute
 Dieses Attribut registriert eine Eigenschaften Seite, die im Dialogfeld **Optionen** unter der Kategorie **Text-Editor** angezeigt werden soll. Verwenden Sie eines dieser Attribute für jede Seite, die für Ihren Sprachdienst angezeigt werden soll. Wenn Sie die Seiten in einer Baumstruktur organisieren müssen, verwenden Sie zusätzliche Attribute, um jeden Knoten der Struktur zu definieren.

### <a name="example"></a>Beispiel
 In diesem Beispiel werden zwei Eigenschaften Seiten, **Optionen** und **Einzug** sowie ein Knoten angezeigt, der die zweite Eigenschaften Seite enthält.

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageEditorOptionPageAttribute(
             "Test Language",  // Registry key name for language
             "Options",      // Registry key name for property page
             "#242",         // Localized name of property page
             OptionPageGuid = "{A2FE74E1-FFFF-3311-4342-123052450768}"  // GUID of property page
             )]
    [ProvideLanguageEditorOptionPageAttribute(
             "Test Language",  // Registry key name for language
             "Advanced",     // Registry key name for node
             "#243",         // Localized name of node
             )]
    [ProvideLanguageEditorOptionPageAttribute(
             "Test Language",  // Registry key name for language
             @"Advanced\Indenting",     // Registry key name for property page
             "#244",         // Localized name of property page
             OptionPageGuid = "{A2FE74E2-FFFF-3311-4342-123052450768}"  // GUID of property page
             )]

    public class TestLanguagePackage : Package
    {
    }
}
```

## <a name="proffer-the-language-service-at-run-time"></a>Proxy des sprach Dienstanbieter zur Laufzeit
 Wenn Sie das Sprachpaket geladen haben, müssen Sie wissen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , dass der Sprachdienst bereit ist. Hierzu wird der Dienst angeboten. Dies erfolgt in der <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>-Methode. Außerdem müssen Sie einen Timer starten, der Ihren Sprachdienst während der Leerlaufzeit aufruft, damit die Hintergrundverarbeitung erreicht werden kann. Dieser Leerlaufzeit Geber wird auch zum Aktualisieren von Dokumenteigenschaften verwendet, wenn Sie durch die-Klasse implementiert haben <xref:Microsoft.VisualStudio.Package.DocumentProperties> . Um einen Timer zu unterstützen, muss das Paket die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> Schnittstelle implementieren (nur die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> Methode muss vollständig implementiert werden. die restlichen Methoden können Standardwerte zurückgeben).

### <a name="example"></a>Beispiel
 Dieses Beispiel zeigt eine typische Vorgehensweise zum Bereitstellen eines Diensts und Bereitstellen eines Timers im Leerlauf.

```csharp

using System;
using System.Runtime.InteropServices;
using System.ComponentModel.Design;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.OLE.Interop;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    [Microsoft.VisualStudio.Shell.ProvideService(typeof(TestLanguageService))]
    [Microsoft.VisualStudio.Shell.ProvideLanguageExtension(typeof(TestLanguageService), ".testext")]
    [Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(TestLanguageService), "Test Language", 0,
        AutoOutlining = true,
        EnableCommenting = true,
        MatchBraces = true,
        ShowMatchingBrace = true)]
    [Guid("00000000-0000-0000-0000-00000000000")] //provide a unique GUID for the package

    public class TestLanguagePackage : Package, IOleComponent
    {
        private uint m_componentID;

        protected override void Initialize()
        {
            base.Initialize();  // required

            // Proffer the service.
            IServiceContainer serviceContainer = this as IServiceContainer;
            TestLanguageService langService      = new TestLanguageService();
            langService.SetSite(this);
            serviceContainer.AddService(typeof(TestLanguageService),
                                        langService,
                                        true);

            // Register a timer to call our language service during
            // idle periods.
            IOleComponentManager mgr = GetService(typeof(SOleComponentManager))
                                       as IOleComponentManager;
            if (m_componentID == 0 && mgr != null)
            {
                OLECRINFO[] crinfo = new OLECRINFO[1];
                crinfo[0].cbSize            = (uint)Marshal.SizeOf(typeof(OLECRINFO));
                crinfo[0].grfcrf            = (uint)_OLECRF.olecrfNeedIdleTime |
                                              (uint)_OLECRF.olecrfNeedPeriodicIdleTime;
                crinfo[0].grfcadvf          = (uint)_OLECADVF.olecadvfModal |
                                              (uint)_OLECADVF.olecadvfRedrawOff |
                                              (uint)_OLECADVF.olecadvfWarningsOff;
                crinfo[0].uIdleTimeInterval = 1000;
                int hr = mgr.FRegisterComponent(this, crinfo, out m_componentID);
            }
        }

        protected override void Dispose(bool disposing)
        {
            if (m_componentID != 0)
            {
                IOleComponentManager mgr = GetService(typeof(SOleComponentManager))
                                           as IOleComponentManager;
                if (mgr != null)
                {
                    int hr = mgr.FRevokeComponent(m_componentID);
                }
                m_componentID = 0;
            }

            base.Dispose(disposing);
        }

        #region IOleComponent Members

        public int FDoIdle(uint grfidlef)
        {
            bool bPeriodic = (grfidlef & (uint)_OLEIDLEF.oleidlefPeriodic) != 0;
            // Use typeof(TestLanguageService) because we need to
            // reference the GUID for our language service.
            LanguageService service = GetService(typeof(TestLanguageService))
                                      as LanguageService;
            if (service != null)
            {
                service.OnIdle(bPeriodic);
            }
            return 0;
        }

        public int FContinueMessageLoop(uint uReason,
                                        IntPtr pvLoopData,
                                        MSG[] pMsgPeeked)
        {
            return 1;
        }

        public int FPreTranslateMessage(MSG[] pMsg)
        {
            return 0;
        }

        public int FQueryTerminate(int fPromptUser)
        {
            return 1;
        }

        public int FReserved1(uint dwReserved,
                              uint message,
                              IntPtr wParam,
                              IntPtr lParam)
        {
            return 1;
        }

        public IntPtr HwndGetWindow(uint dwWhich, uint dwReserved)
        {
            return IntPtr.Zero;
        }

        public void OnActivationChange(IOleComponent pic,
                                       int fSameComponent,
                                       OLECRINFO[] pcrinfo,
                                       int fHostIsActivating,
                                       OLECHOSTINFO[] pchostinfo,
                                       uint dwReserved)
        {
        }

        public void OnAppActivate(int fActive, uint dwOtherThreadID)
        {
        }

        public void OnEnterState(uint uStateID, int fEnter)
        {
        }

        public void OnLoseActivation()
        {
        }

        public void Terminate()
        {
        }

        #endregion
    }
}
```
