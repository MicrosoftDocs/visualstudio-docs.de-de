---
title: Starten von Visual Studio mit DTE
description: Erfahren Sie, wie Sie Visual Studio mithilfe von DTE starten, um parallele Installationen von Hauptversionen zu unterstützen. Dieser Artikel enthält ein Codebeispiel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 04/26/2019
ms.topic: conceptual
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c84d44b3f775f384ed15a0ede1ef9c68ad2fd5a6
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97615876"
---
# <a name="launch-visual-studio-using-dte"></a>Starten von Visual Studio mit DTE

Ab Visual Studio 2017 unterscheidet sich der Mechanismus zum Starten von Visual Studio mit DTE von dem Starten vorheriger Versionen von Visual Studio. Diese Änderung ist erforderlich, da Visual Studio 2017 und höher parallele Installationen von Hauptversionen unterstützt (Sie können z. b. eine Vorschau und eine Releaseversion nebeneinander installiert haben).

Der Rest dieses Artikels zeigt den Code, den Sie zum Starten von Visual Studio 2019 mithilfe von DTE verwenden können.

## <a name="set-up-the-project"></a>Einrichten des Projekts

Um den Start Code in Aktion zu sehen, erstellen Sie ein Projekt, indem Sie die folgenden Schritte ausführen.

1. Erstellen Sie ein neues **Konsolen-App** -Projekt für die .NET Framework.

2. Installieren Sie die [Microsoft.VisualStudio.Setup.Config-urung. Interop](https://www.nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop/) -nuget-Paket und Hinzufügen eines Verweises auf die Assembly.

3. Fügen Sie einen Verweis auf "konvdte" hinzu.

4. Fügen Sie den folgenden [Beispielcode](#example-code) in die Datei *Program.cs* ein.

5. Drücken Sie **F5** , um das Programm auszuführen. Visual Studio 2019 sollte geöffnet werden, bevor das Programm beendet wird.

## <a name="example-code"></a>Beispielcode

```csharp
using Microsoft.VisualStudio.Setup.Configuration;
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.IO;
using System.Linq;
using System.Runtime.InteropServices;
using System.Runtime.InteropServices.ComTypes;
using System.Threading;

namespace ConsoleLauncherApp
{
    class Program
    {
        static void Main(string[] args)
        {
            EnvDTE.DTE dte = LaunchVsDte(isPreRelease: false);

            dte.MainWindow.WindowState = EnvDTE.vsWindowState.vsWindowStateMaximize;
            dte.MainWindow.WindowState = EnvDTE.vsWindowState.vsWindowStateMinimize;
            dte.MainWindow.WindowState = EnvDTE.vsWindowState.vsWindowStateNormal;
            dte.Quit();
        }

        private static EnvDTE.DTE LaunchVsDte(bool isPreRelease)
        {
            ISetupInstance setupInstance = GetSetupInstance(isPreRelease);
            string installationPath = setupInstance.GetInstallationPath();
            string executablePath = Path.Combine(installationPath, @"Common7\IDE\devenv.exe");
            Process vsProcess = Process.Start(executablePath);
            string runningObjectDisplayName = $"VisualStudio.DTE.16.0:{vsProcess.Id}";

            IEnumerable<string> runningObjectDisplayNames = null;
            object runningObject;
            for (int i = 0; i < 60; i++)
            {
                try
                {
                    runningObject = GetRunningObject(runningObjectDisplayName, out runningObjectDisplayNames);
                }
                catch
                {
                    runningObject = null;
                }

                if (runningObject != null)
                {
                    return (EnvDTE.DTE)runningObject;
                }

                Thread.Sleep(millisecondsTimeout: 1000);
            }

            throw new TimeoutException($"Failed to retrieve DTE object. Current running objects: {string.Join(";", runningObjectDisplayNames)}");
        }

        private static object GetRunningObject(string displayName, out IEnumerable<string> runningObjectDisplayNames)
        {
            IBindCtx bindContext = null;
            NativeMethods.CreateBindCtx(0, out bindContext);

            IRunningObjectTable runningObjectTable = null;
            bindContext.GetRunningObjectTable(out runningObjectTable);

            IEnumMoniker monikerEnumerator = null;
            runningObjectTable.EnumRunning(out monikerEnumerator);

            object runningObject = null;
            List<string> runningObjectDisplayNameList = new List<string>();
            IMoniker[] monikers = new IMoniker[1];
            IntPtr numberFetched = IntPtr.Zero;
            while (monikerEnumerator.Next(1, monikers, numberFetched) == 0)
            {
                IMoniker moniker = monikers[0];

                string objectDisplayName = null;
                try
                {
                    moniker.GetDisplayName(bindContext, null, out objectDisplayName);
                }
                catch (UnauthorizedAccessException)
                {
                    // Some ROT objects require elevated permissions.
                }

                if (!string.IsNullOrWhiteSpace(objectDisplayName))
                {
                    runningObjectDisplayNameList.Add(objectDisplayName);
                    if (objectDisplayName.EndsWith(displayName, StringComparison.Ordinal))
                    {
                        runningObjectTable.GetObject(moniker, out runningObject);
                        if (runningObject == null)
                        {
                            throw new InvalidOperationException($"Failed to get running object with display name {displayName}");
                        }
                    }
                }
            }

            runningObjectDisplayNames = runningObjectDisplayNameList;
            return runningObject;
        }

        private static ISetupInstance GetSetupInstance(bool isPreRelease)
        {
            return GetSetupInstances().First(i => IsPreRelease(i) == isPreRelease);
        }

        private static IEnumerable<ISetupInstance> GetSetupInstances()
        {
            ISetupConfiguration setupConfiguration = new SetupConfiguration();
            IEnumSetupInstances enumerator = setupConfiguration.EnumInstances();

            int count;
            do
            {
                ISetupInstance[] setupInstances = new ISetupInstance[1];
                enumerator.Next(1, setupInstances, out count);
                if (count == 1 &&
                    setupInstances != null &&
                    setupInstances.Length == 1 &&
                    setupInstances[0] != null)
                {
                    yield return setupInstances[0];
                }
            }
            while (count == 1);
        }

        private static bool IsPreRelease(ISetupInstance setupInstance)
        {
            ISetupInstanceCatalog setupInstanceCatalog = (ISetupInstanceCatalog)setupInstance;
            return setupInstanceCatalog.IsPrerelease();
        }

        private static class NativeMethods
        {
            [DllImport("ole32.dll")]
            public static extern int CreateBindCtx(uint reserved, out IBindCtx ppbc);

            [DllImport("ole32.dll")]
            public static extern void GetRunningObjectTable(int reserved, out IRunningObjectTable prot);
        }
    }
}
```

## <a name="see-also"></a>Weitere Informationen

- [Suchen nach Visual Studio](locating-visual-studio.md)
- [Exemplarische Vorgehensweise: Zugreifen auf das DTE-Objekt aus einer Editor-Erweiterung](walkthrough-accessing-the-dte-object-from-an-editor-extension.md)
