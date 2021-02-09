---
title: 'Vorgehensweise: Installieren des Visual Studio-Tools für die weitervertreibbare Office-Laufzeit'
description: Erfahren Sie, wie Sie die weitervertreibbare Microsoft Visual Studio 2010-Tools für Office-Laufzeit installieren.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 75dc5b2f3f207603320a773ebd71f5d6d3f81b8c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918619"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Vorgehensweise: Installieren des Visual Studio-Tools für die weitervertreibbare Office-Laufzeit
  Die Visual Studio 2010-Tools für Office-Laufzeit muss auf jedem Computer installiert sein, auf dem Projektmappen ausgeführt werden, die mithilfe der Microsoft Office Developer Tools in erstellt wurden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Die Laufzeit wird automatisch installiert, wenn Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und Microsoft Office installieren. Weitere Informationen finden Sie unter [Visual Studio-Tools for Office Runtime Installation Szenarios](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

[!include[Add-ins note](includes/addinsnote.md)]

 Sie müssen möglicherweise die Anweisungen zur manuellen Installation weiter unten in den folgenden Situationen befolgen:

- Sie müssen [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] auf einem Server installieren. Sie möchten z. B. die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>-Klasse verwenden, um Lösungen auf Dokumentebene auf einem Server zu verwalten.

- Sie müssen die Laufzeit auf einem Computer installieren, auf dem bereits alle anderen erforderlichen Komponenten für Office-Lösungen installiert wurden.

    > [!NOTE]
    > Sie müssen auf dem Entwicklungscomputer über Administratorrechte verfügen, um .NET Framework und [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zu installieren.

## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>So installieren Sie Visual Studio Tools for Office Runtime

1. Installieren Sie [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher.

    - Informationen zum Herunterladen von finden Sie unter [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [Microsoft .NET Framework 4 (Webinstaller)](https://www.microsoft.com/download/details.aspx?id=17851).

    - Informationen zum Herunterladen von finden Sie unter [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] [Microsoft .NET Framework 4 Client Profile (Webinstaller)](https://www.microsoft.com/download/details.aspx?id=17113).

    - Informationen zum Herunterladen von finden Sie unter [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] [Microsoft .NET Framework 4,5](https://www.microsoft.com/download/details.aspx?id=30653).

2. Führen Sie *vstor_redist.exe* aus, um die zu installieren [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

     Sie können diese Setup Dateien von [Visual Studio 2010 Tools for Office Runtime](https://www.microsoft.com/download/details.aspx?id=56961)herunterladen. Die erforderlichen Komponenten für [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] stimmen mit denen für .NET Framework überein.

     Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] enthält Sprachpakete. Wenn Sie für Windows andere Spracheinstellungen als Englisch festgelegt haben, können Sie Laufzeitmeldungen in der Sprache anzeigen, die Sie für Windows verwenden. Wenn Endbenutzer [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] installieren und dann die Projektmappen auf Windows-Installationen ausführen, die andere Spracheinstellungen als Englisch verwenden, werden Laufzeitmeldungen entsprechend in derselben Sprache wie Windows angezeigt. In einigen Fällen benötigen Sie möglicherweise zusätzliche Language Packs. Beispielsweise können Sie weitere Sprachpakete benötigen, wenn in Ihrer Windows-Version mehr als eine Spracheinstellung verwendet wird, oder wenn Sie auf eine andere Sprache umstellen, nachdem Sie bereits installiert haben [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Sprachpakete finden Sie unter [Microsoft Visual Studio 2010 Tools für das Microsoft Office System (Version 4,0 Runtime) Language Pack](https://www.microsoft.com/download/details.aspx?id=54246).

## <a name="see-also"></a>Weitere Informationen
- [Beginnen Sie &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen](../vsto/configuring-a-computer-to-develop-office-solutions.md)
- [Vorgehensweise: Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Gewusst wie: Installieren von primären Interop-Assemblys in Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Bereitstellen einer Office-Projekt Mappe](../vsto/deploying-an-office-solution.md)
