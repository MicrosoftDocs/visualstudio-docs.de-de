---
title: Verwenden einer Eincheck Richtlinie für die Code Analyse
ms.date: 11/04/2016
description: Erfahren Sie, wie Sie eine Eincheck Richtlinie für die Code Analyse verwenden, um zu überprüfen, ob der Code den Vererbung, Klassen Kopplung, Wartbarkeit und Komplexitäts Standards entspricht.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9f061d9d10d66857a0b2506d13d6d6671f7df401
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860039"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Gewusst wie: Erzwingen von wart barem Code mit einer Eincheck Richtlinie für die Code Analyse

Entwickler können das Tool Codemetriken verwenden, um die Komplexität und Verwaltbarkeit Ihres Codes zu messen, aber Sie können keine Codemetriken als Teil einer Eincheck Richtlinie aufrufen. Sie können jedoch Code Analyse Regeln aktivieren, mit denen die Kompatibilität Ihres Codes mit Codemetrikstandards überprüft wird, und die Regeln mithilfe von Eincheck Richtlinien erzwingen. Weitere Informationen zu Codemetriken finden Sie unter [codemetrikwerte](../code-quality/code-metrics-values.md).

Sie können die Tiefe von Vererbung, Klassen Kopplung, verwaltbarkeitsindex und Komplexitäts Regeln aktivieren, um verwaltbaren Code durch eine Eincheck Richtlinie für die Code Analyse zu erzwingen. Alle vier dieser Regeln finden Sie unter der Kategorie "wart barkeits Regeln" im Code Analyse Richtlinien-Editor.

Administratoren der Versionskontrolle für Team Foundation können den Check-in-Richtlinien Anforderungen die wart barkeits Regeln für die Code Analyse hinzufügen. Diese Eincheck Richtlinien erfordern, dass Entwickler die Code Analyse auf der Grundlage dieser Regeländerungen ausführen, bevor Sie einen Eincheck Vorgang einleiten.

## <a name="to-open-the-code-analysis-policy-editor"></a>So öffnen Sie den Code Analyse Richtlinien-Editor

1. Klicken Sie in **Team Explorer** mit der rechten Maustaste auf das Projekt, klicken Sie auf **Projekteinstellungen** und dann auf **Quell** Code Verwaltung.

     Das Dialogfeld **Quell** Code Verwaltung wird angezeigt.

2. Klicken Sie auf der Registerkarte **Check-in-Richtlinie** auf **Hinzufügen**.

     Das Dialogfeld " **Eincheck Richtlinie hinzufügen** " wird angezeigt.

3. Aktivieren Sie in der Liste **Eincheck Richtlinie** das Kontrollkästchen **Code Analyse** , und klicken Sie dann auf **OK**.

     Das Dialogfeld Editor für die **Code Analyse Richtlinie** wird angezeigt.

## <a name="to-enable-code-analysis-maintainability-rules"></a>So aktivieren Sie die wart barkeits Regeln für die Code Analyse

1. Erweitern Sie im Dialogfeld Editor für die **Code Analyse Richtlinien** unter **Regel Einstellungen** den Knoten **wart barkeits Regeln** .

2. Aktivieren Sie die Kontrollkästchen für die folgenden Regeln:

   - Vererbungs Tiefe: **CA1501 avoidexcessiveinvererance** -Threshold: Warnung auf mehr als 5 Ebenen tief

   - Komplexität: **CA1502 avoidexcessivekomplexitäts** Schwellenwert: Warnung bei mehr als 25

   - Wart barkeits Index: **CA1505 vermeidunwart ablecode** -Threshold: Warnung bei weniger als 20

   - Klassen Kopplung: **CA1506 AvoidExcessiveClassCoupling** -Threshold: Warnung bei mehr als 80 für eine Klasse und mehr als 30 für eine Methode

     Wenn Sie außerdem eine Regelverletzung für einen erfolgreichen Build verhindern möchten, aktivieren Sie neben der Regel Beschreibung das Kontrollkästchen **Warnung als Fehler behandeln** .

3. Klicken Sie auf **OK**. Die neue Eincheck Richtlinie gilt jetzt für künftige Eincheck Vorgänge.

## <a name="see-also"></a>Weitere Informationen

- [Codemetrikwerte](../code-quality/code-metrics-values.md)
- [Erstellen und Verwenden von Eincheck Richtlinien für die Code Analyse](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)
