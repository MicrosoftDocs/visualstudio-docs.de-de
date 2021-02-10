---
title: Erstellen eines Builds von der IDE aus | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Verwendung von „Microsoft.VisualStudio.Shell.Interop.IVsBuildManagerAccessor“ zum Auslösen eines Builds für benutzerdefinierte Projektsysteme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- build
ms.assetid: 936317aa-63b7-4eb0-b9db-b260a0306196
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2ee685ebf542dbf9405afce8cfdf5c4a7e060b79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956047"
---
# <a name="start-a-build-from-within-the-ide"></a>Erstellen eines Builds von der IDE aus

Benutzerdefinierte Projektsysteme müssen Builds mithilfe von <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildManagerAccessor> starten. In diesem Artikel werden die Gründe für diese Anforderung beschrieben. Zudem wird die Prozedur erläutert.

## <a name="parallel-builds-and-threads"></a>Parallele Builds und Threads

 Visual Studio lässt parallele Builds zu, sodass für den Zugriff auf allgemeine Ressourcen eine Vermittlung erforderlich ist. Projektsysteme können Builds asynchron ausführen, diese Systeme dürfen jedoch keine Buildfunktionen innerhalb von Rückrufen aufrufen.

 Wenn das Projektsystem Umgebungsvariablen ändert, muss es die Knotenaffinität (NodeAffinity) des Builds auf OutOfProc festlegen. Diese Anforderung bedeutet, dass Sie keine Hostobjekte verwenden können, da sie den prozessinternen Knoten benötigen.

## <a name="use-ivsbuildmanageraccessor"></a>Verwenden von IVSBuildManagerAccessor

 Im Code unten wird eine Methode veranschaulicht, mit der ein Projektsystem einen Build starten kann:

```csharp

public bool Build(Project project, bool isDesignTimeBuild)
{
    // Get the accessor from the IServiceProvider interface for the
    // project system
    IVsBuildManagerAccessor accessor =
        serviceProvider.GetService(typeof(SVsBuildManagerAccessor)) as
        IVsBuildManagerAccessor;
    bool releaseUIThread = false;
    try
    {
        if(accessor != null)
        {
            // Claim the UI thread under the following conditions:
            // 1. The build must use a resource that uses the UI thread
            // or,
            // 2. The build requires the in-proc node AND waits on the
            // UI thread for the build to complete
            if(NeedsUIThread)
            {
                int result = accessor.ClaimUIThreadForBuild();
                if(result != S_OK)
                {
                     // Not allowed to claim the UI thread right now
                     return false;
                }
                releaseUIThread = true;
             }
             if(isDesignTimeBuild)
             {
// Start the design time build
                  int result = accessor.BeginDesignTimeBuild();
                  if(result != S_OK)
                  {
                      // Not allowed to begin a design-time build at
                      // this time. Try again later.
                      return false;
                  }
             }
         }
         bool buildSucceeded = false;
         // perform project-system specific build set up tasks
         // Create your BuildRequestData
         // This assumes a IHostServices variable (hostServices) set
   // to your host services. If you don't use a project instance
         // (you build from a file for example) then use another
         // constructor.
         BuildRequestData requestData = new
             BuildRequestData(project.CreateProjectInstance(),
             "myTarget", hostServices,
             BuildRequestData.BuildRequestDataFlags.None);
         // Mark your your submission as Pending
         BuildSubmission submission =
              BuildManager.DefaultBuildManager.
              PendBuildRequest(requestData);
         // Register the loggers in BuildLoggers
         if (accessor != null)
         {
               foreach (ILogger logger in BuildLoggers)
               {
                    accessor.RegisterLogger(submission.SubmissionId,
                        logger);
               }
         }
         BuildResult buildResult = submission.Execute();
         return buildResult;
     }
     // Clean up resources
     finally
     {
         if(accessor != null)
         {
             // Unregister the loggers, if necessary.
             accessor.UnregisterLoggers(submission.SubmissionId);
             // Release the UI thread, if used
             if(releaseUIThread)
             {
                  accessor.ReleaseUIThreadForBuild();
             }
             // End the design time build, if used
             if(isDesignTimeBuild)
             {
                  accessor.EndDesignTimeBuild();
             }
         }
     }
}
```
