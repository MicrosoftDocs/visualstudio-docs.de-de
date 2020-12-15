---
title: Die Arbeitsmappe enthält ActiveX-Steuerelemente, die nicht geladen werden können.
description: Erfahren Sie, wie Sie den Fehler beheben können, der auftritt, wenn eine Arbeitsmappe ActiveX-Steuerelemente enthält, die nicht geladen werden können.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: error-reference
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7257e3940af72f344906642adc51a1dd98cb3f25
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524185"
---
# <a name="the-workbook-contains-activex-controls-that-cannot-be-loaded"></a>Die Arbeitsmappe enthält ActiveX-Steuerelemente, die nicht geladen werden können.

  Der Fehler "die zum Erstellen dieses Projekts verwendete Arbeitsmappe enthält ActiveX-Steuerelemente, die vom Designer nicht geladen werden können" wird angezeigt, wenn Sie ein Steuerelement einem Word-Dokument oder einem Excel-Arbeitsblatt Programm gesteuert hinzufügen, das Dokument oder die Arbeitsmappe speichern und dann eine neue Lösung auf Dokument Ebene basierend auf dem Dokument oder der Arbeitsmappe erstellen.

 Informationen über den verwalteten Typ des Steuerelements wird nicht zusammen mit dem Dokument oder der Arbeitsmappe gespeichert. Wenn Sie eine neue Lösung basierend auf diesem Dokument oder dieser Arbeitsmappe erstellen, hat Visual Studio nicht genügend Informationen, um das Steuerelement im Hostelement-Designer zu laden.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Öffnen Sie das Dokument oder die Arbeitsmappe.

2. Entfernen Sie die Steuerelemente, die zur Laufzeit hinzugefügt wurden. Hierzu können Sie diese im Dokument oder **in der Arbeits** Mappe auswählen und die ENTF-Taste drücken.

3. Erstellen Sie eine Lösung auf Dokumentebene basierend auf dem Dokument oder der Arbeitsmappe.

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
