---
title: Erstellen eines Anforderungsebenen-Plug-Ins (Webleistungstests)
description: Lernen Sie, mit Webleistungstest-Plug-Ins einer individuellen Anforderung Code außerhalb der Hauptdeklarationen des Webleistungstests wiederzuverwenden.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- request-level plug-in, creating
- Web performance tests, requests
ms.assetid: d0b5b23c-7e94-4637-be6c-2620a5442d46
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: f546d0433ff5fa3a55f49f559597f1c7a45b1596
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877935"
---
# <a name="how-to-create-a-request-level-plug-in"></a>Vorgehensweise: Erstellen eines Anforderungsebenen-Plug-Ins

*Anforderungen* sind die deklarativen Anweisungen, aus denen Webleistungstests bestehen. Webleistungstest-Plug-Ins ermöglichen Ihnen, Code außerhalb der Hauptdeklarationen des Webleistungstests zu isolieren und wiederzuverwenden. Sie können Plug-Ins erstellen und sie einer individuellen Anforderung sowie dem Webleistungstest hinzufügen, in dem sie enthalten ist. Mit einem benutzerdefinierten *Anforderungs-Plug-In* haben Sie die Möglichkeit, Code aufzurufen, während eine bestimmte Anforderung in einem Webleistungstest ausgeführt wird.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Jedes Webleistungstestanforderungs-Plug-In verfügt über eine PreRequest-Methode und eine PostRequest-Methode. Nachdem Sie ein Anforderungs-Plug-In an eine bestimmte HTTP-Anforderung angefügt haben, wird das PreRequest-Ereignis noch vor Senden der Anforderung ausgelöst und das PostRequest-Ereignis nach dem Empfangen der Antwort.

Sie können ein benutzerdefiniertes Webleistungstestanforderungs-Plug-In erstellen, indem Sie die eigene Klasse von der <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>-Basisklasse ableiten.

Sie können benutzerdefinierte Webleistungstestanforderungs-Plug-Ins mit den aufgezeichneten Webleistungstests verwenden. Durch benutzerdefinierte Webleistungstestanforderungs-Plug-Ins können Sie nur eine minimale Menge Code erstellen, um eine bessere Kontrolle über Ihre Webleistungstests zu erhalten. Sie können die Plug-Ins jedoch auch mit codierten Webleistungstests verwenden. Informationen finden Sie unter [Generate and run a coded web performance test (Generieren und Ausführen eines codierten Webleistungstests)](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="to-create-a-request-level-plug-in"></a>So erstellen Sie ein Anforderungsebenen-Plug-In

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe, wählen Sie **Hinzufügen** aus, und klicken Sie anschließend auf **Neues Projekt**.

2. Erstellen Sie ein neues **Klassenbibliotheksprojekt**.

3. Klicken Sie im **Projektmappen-Explorer** in der neuen Klassenbibliothek mit der rechten Maustaste auf den Ordner **Verweise**, und wählen Sie **Verweis hinzufügen** aus.

     Das Dialogfeld **Verweis hinzufügen** wird angezeigt.

4. Klicken Sie auf die Registerkarte **.NET**, scrollen Sie nach unten, und wählen Sie **Microsoft.VisualStudio.QualityTools.WebTestFramework** aus. Klicken Sie dann auf **OK**.

     Der Verweis auf **Microsoft.VisualStudio.QualityTools.WebTestFramework** wird zum Ordner **Verweise** im **Projektmappen-Explorer** hinzugefügt.

5. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den obersten Knoten des Webleistungs- und Auslastungstestprojekts, das den Auslastungstest enthält, zu dem Sie das Anforderungstest-Plug-In für den Webleistungstest hinzufügen möchten. Klicken Sie auf **Verweis hinzufügen**.

     Das Dialogfeld **Verweis hinzufügen** wird angezeigt.

6. Klicken Sie auf die Registerkarte **Projekte**, wählen Sie das **Klassenbibliotheksprojekt** aus, und klicken Sie anschließend auf **OK**.

7. Schreiben Sie im **Code-Editor** den Code für das Plug-In. Erstellen Sie zunächst eine neue öffentliche Klasse, die von <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin> abgeleitet wird.

8. Implementieren Sie Code innerhalb eines oder beider Ereignishandler <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PreRequest*> und <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PostRequest*>. Beachten Sie hierzu die Beispielimplementierung im folgenden Abschnitt.

9. Nachdem Sie den Code verfasst haben, erstellen Sie das neue Projekt.

10. Öffnen Sie den Webleistungstest, dem Sie das Anforderungs-Plug-In hinzufügen möchten.

11. Klicken Sie mit der rechten Maustaste auf die Anforderung, der Sie das Anforderungs-Plug-In hinzufügen möchten, und wählen Sie **Anforderungs-Plug-In hinzufügen** aus.

     Das Dialogfeld **Webtestanforderungs-Plug-In hinzufügen** wird angezeigt.

12. Wählen Sie unter **Plug-In auswählen** das neue Plug-In aus.

13. Legen Sie im Bereich **Eigenschaften für das ausgewählte Plug-In** die Anfangswerte fest, die das Plug-In zur Laufzeit verwenden soll.

    > [!NOTE]
    > Sie können beliebig viele Plug-In-Eigenschaften verfügbar machen. Die Eigenschaften müssen dazu lediglich öffentlich, festlegbar und von einem Basistyp (z. B. "Integer", "Boolean" oder "String") sein. Sie können die Eigenschaften des Webleistungstest-Plug-Ins auch zu einem späteren Zeitpunkt im Eigenschaftenfenster ändern.

14. Klicken Sie auf **OK**.

     Das Plug-In wird dem Ordner **Anforderungs-Plug-Ins** hinzugefügt, der ein untergeordneter Ordner der HTTP-Anforderung ist.

    > [!WARNING]
    > Möglicherweise erhalten Sie eine Fehlermeldung wie die folgende, wenn Sie einen Webleistungstest oder einen Auslastungstest ausführen, der das Plug-In verwendet:
    >
    > **Fehler bei der Anforderung: Ausnahme im Ereignis \<plug-in>: Die Datei oder Assembly '\<"Plug-in name".dll file>, Version=\<n.n.n.n>, Culture=neutral, PublicKeyToken=null' oder eine ihrer Abhängigkeiten konnte nicht geladen werden. Das System konnte die angegebene Datei nicht finden.**
    >
    > Ein solcher Fehler wird verursacht, wenn Sie an einem der Plug-Ins Codeänderungen vornehmen und eine neue DLL-Version **(Version=0.0.0.0)** erstellen, während das Plug-In weiterhin auf die ursprüngliche Plug-In-Version verweist. Um dieses Problem zu beheben, führen Sie folgende Schritte aus:
    >
    > 1. Im Webleistungs- und Auslastungstestprojekt wird in Verweisen eine Warnung angezeigt. Entfernen Sie den Verweis auf die Plug-In-DLL, und fügen Sie ihn wieder hinzu.
    > 2. Entfernen Sie das Plug-In aus dem Test oder vom entsprechenden Speicherort, und fügen Sie es dann wieder hinzu.

## <a name="example"></a>Beispiel

Sie können mit dem folgenden Code ein benutzerdefiniertes Webleistungstest-Plug-In erstellen, das zwei Dialogfelder anzeigt. In einem Dialogfeld wird die URL angezeigt, die der Anforderung zugeordnet ist, an die Sie das Anforderungs-Add-In anfügen. Das zweite Dialogfeld zeigt den Computernamen für den Agent an.

> [!NOTE]
> Für den folgenden Code müssen Sie einen Verweis auf System.Windows.Forms hinzufügen.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace RequestPluginNamespace
{
    public class MyWebRequestPlugin : WebTestRequestPlugin
    {
        public override void PostRequest(object sender, PostRequestEventArgs e)
        {
            MessageBox.Show(e.WebTest.Context.AgentName);
        }
        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            MessageBox.Show(e.Request.Url);
        }
    }
}
```

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Erstellen von benutzerdefiniertem Code und benutzerdefinierten Plug-Ins für Auslastungstests](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Kodieren einer benutzerdefinierten Extraktionsregel für einen Webleistungstest](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kodieren einer benutzerdefinierten Validierungsregel für einen Webleistungstest](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [How to: Erstellen eines Auslastungstest-Plug-Ins](../test/how-to-create-a-load-test-plug-in.md)
- [Generieren und Ausführen eines codierten Webleistungstests](../test/generate-and-run-a-coded-web-performance-test.md)
