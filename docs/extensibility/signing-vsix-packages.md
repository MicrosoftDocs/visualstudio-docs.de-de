---
title: Signieren von VSIX-Paketen | Microsoft-Dokumentation
description: Informationen zum Signieren von Erweiterungsassemblys Der VSIX-Installer zeigt eine Meldung an, dass eine VSIX signiert ist, sowie Informationen über die Signatur selbst.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e9152e45b402294dfd0bbb41bfda2c685588f01e
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2020
ms.locfileid: "97716080"
---
# <a name="signing-vsix-packages"></a>Signieren von VSIX-Paketen
Erweiterungsassemblys müssen nicht signiert werden, bevor Sie in Visual Studio ausgeführt werden können. Dies ist jedoch eine bewährte Vorgehensweise.

 Wenn Sie Ihre Erweiterung sichern und sicherstellen möchten, dass Sie nicht manipuliert wurde, können Sie einem VSIX-Paket eine digitale Signatur hinzufügen. Wenn eine VSIX signiert ist, zeigt das VSIX-Installationsprogramm eine Meldung mit dem Hinweis an, dass Sie signiert ist, sowie weitere Informationen zur Signatur selbst. Wenn die Inhalte der VSIX geändert wurden und die VSIX nicht erneut signiert wurde, zeigt das VSIX-Installationsprogramm an, dass die Signatur ungültig ist. Die Installation wird nicht beendet, aber der Benutzer ist gewarnt.

> [!IMPORTANT]
> Ab Visual Studio 2015 werden VSIX-Pakete, die mit anderen als SHA256 Encryption signiert werden, als ungültige Signatur identifiziert. Die VSIX-Installation wird nicht blockiert, aber der Benutzer wird gewarnt.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Signieren einer VSIX mit vsixsigntool
 Es gibt ein SHA256 Encryption-Signatur Tool, das unter " [visualstudioextensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) " unter "nuget.org" unter [vsixsigntool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)verfügbar ist.

#### <a name="to-use-the-vsixsigntool"></a>So verwenden Sie das vsixsigntool

1. Fügen Sie die VSIX einem Projekt hinzu.

2. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf den Projekt Knoten, und wählen **Sie hinzufügen &#124; nuget-Pakete verwalten**  Weitere Informationen zu nuget und zum Hinzufügen von nuget-Paketen finden Sie in den Themen zur [nuget-Dokumentation](/NuGet) und zum [Paket-Manager](/NuGet/Tools/Package-Manager-UI) .

3. Suchen Sie nach vsixsigntool aus visualstudioextensibility, und installieren Sie das nuget-Paket.

4. Sie können jetzt das vsixsigntool aus dem lokalen Paket Speicherort des Projekts ausführen. Informationen zum Signierungs Szenario (VSIXSignTool.exe/?) finden Sie in der Befehlszeilen Hilfe des Tools.

   So können Sie beispielsweise mit einer Kenn Wort geschützten Zertifikatsdatei signieren:

   VSIXSignTool.exe Sign/f \<certfile> /p \<password>\<VSIXfile>

## <a name="see-also"></a>Weitere Informationen
- [Bereitstellen von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)
