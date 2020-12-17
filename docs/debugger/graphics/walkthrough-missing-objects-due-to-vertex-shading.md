---
title: 'Exemplarische Vorgehensweise: Fehlende Objekte durch Vertexshading | Microsoft-Dokumentation'
description: Ausführen einer Untersuchung, die einen Vertexshaderfehler findet. Zeigt die Grafikereignisliste, Stufen der Grafikpipeline, den HLSL-Debugger und den Aufrufstapel des Grafikereignisses.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e42b54a0-8092-455c-945b-9ecafb129d93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a7e4c01a990ce4d3fff6769ba016c168b190687f
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994997"
---
# <a name="walkthrough-missing-objects-due-to-vertex-shading"></a>Exemplarische Vorgehensweise: Fehlende Objekte durch Vertex-Shading
Diese exemplarische Vorgehensweise veranschaulicht, wie die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Grafikdiagnosetools zum Untersuchen eines Objekts verwendet werden, das aufgrund eines Fehlers fehlt, der in der Vertexshader-Stufe auftritt.

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben beschrieben:

- Verwenden der **Grafikereignisliste** , um mögliche Quellen des Problems zu suchen.

- Verwenden des Fensters **Grafikpipelinestufen** , um die Wirkung der `DrawIndexed` -Direct3D-API-Aufrufe zu prüfen.

- Verwenden des **HLSL-Debuggers** , um den Vertexshader zu überprüfen.

- Verwenden der **Aufrufliste des Grafikereignisses** , um die Quelle einer falschen HLSL-Konstante zu finden.

## <a name="scenario"></a>Szenario
 Eine der häufigsten Ursachen für ein fehlendes Objekt in einer 3D-App besteht darin, dass der Vertexshader die Scheitelpunkte des Objekts in fehlerhafter oder unerwarteter Weise transformiert – beispielsweise wird das Objekt möglicherweise so skaliert, dass es sehr klein ist, oder so transformiert, dass es nicht vor, sondern hinter der Kamera angezeigt wird.

 In diesem Szenario wird beim Ausführen der App zu Testzwecken der Hintergrund erwartungsgemäß gerendert, eins der Objekte wird jedoch nicht dargestellt. Mithilfe der Grafikdiagnose erfassen Sie das Problem in einer Grafikprotokolldatei, um die App zu debuggen. Das Problem sieht in der App wie folgt aus:

 ![Das Objekt ist nicht sichtbar.](media/gfx_diag_demo_missing_object_shader_problem.png "gfx_diag_demo_missing_object_shader_problem")

## <a name="investigation"></a>Untersuchung
 Mithilfe der Grafikdiagnosetools können Sie die Grafikprotokolldatei laden, um die Frames zu untersuchen, die während des Tests erfasst wurden.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>So überprüfen Sie einen Frame in einem Grafikprotokoll

1. Laden Sie in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]eine Grafikprotokolldatei, die einen Frame enthält, der das fehlende Objekt aufzeigt. Eine neue Grafikprotokoll-Registerkarte wird in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]angezeigt. Ganz oben auf dieser Registerkarte befindet sich die Renderingzielausgabe des ausgewählten Frames. Im unteren Teil befindet sich die **Frameliste**, in der alle aufgezeichneten Frames als Miniaturansichten angezeigt werden.

2. Wählen Sie in der **Frameliste** einen Frame aus, der veranschaulicht, dass das Objekt nicht angezeigt wird. Das Renderziel wird aktualisiert und gibt den ausgewählten Frame wieder. In diesem Szenario sieht die Grafikprotokoll-Registerkarte wie folgt aus:

    ![Das Grafikprotokolldokument in Visual Studio](media/gfx_diag_demo_missing_object_shader_step_1.png "gfx_diag_demo_missing_object_shader_step_1")

   Nachdem Sie einen Frame ausgewählt haben, der das Problem demonstriert, können Sie die **Grafikereignisliste** verwenden, um das Problem zu diagnostizieren. Die **Grafikereignisliste** enthält jeden Direct3D-API-Aufruf, der zum Rendern des aktiven Frames erfolgt ist, z. B. API-Aufrufe zum Einrichten des Gerätestatus, zum Erstellen und Aktualisieren von Puffern und zum Zeichnen von Objekten, die im Frame dargestellt werden. Viele Arten von Aufrufen sind interessant, weil sie häufig (aber nicht immer) mit einer entsprechenden Änderung beim Renderziel einhergehen, wenn die App erwartungsgemäß funktioniert. Dies gilt z. B. für Draw-, Dispatch-, Copy- oder Clear-Aufrufe. Draw-Aufrufe sind besonders interessant, da jeder Aufruf Geometrie darstellt, die von der App gerendert wird (auch Dispatch-Aufrufe können Geometrie rendern).

   Da Sie wissen, dass das fehlende Objekt (in diesem Fall) nicht im Renderziel gezeichnet wird, aber der Rest der Szene erwartungsgemäß gezeichnet wird, können Sie die **Grafikereignisliste** in Kombination mit dem **Grafikpipelinestufen** -Tool verwenden, um den Draw-Aufruf zu bestimmen, der der Geometrie des fehlenden Objekts entspricht. Das Fenster **Grafikpipelinestufen** zeigt die Geometrie an, die an jeden Zeichnen-Befehl gesendet wurde, unabhängig von seiner Wirkung auf das Renderziel. Während Sie sich durch die Draw-Aufrufe bewegen, werden die Pipelinestufen aktualisiert, sodass die Geometrie angezeigt wird, die dem jeweiligen Aufruf zugeordnet ist, und es wird das Renderziel aktualisiert, um den Zustand des Renderziels nach dem Abschluss des Aufrufs anzuzeigen.

#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>So finden Sie den Zeichnen-Befehl für die fehlende Geometrie

1. Öffnen Sie das Fenster **Grafikereignisliste** . Wählen Sie auf der Symbolleiste **Grafikdiagnose** die **Ereignisliste** aus.

2. Öffnen Sie das Fenster **Grafikpipelinestufen** . Wählen Sie auf der Symbolleiste **Grafikdiagnose** die **Pipelinestufen** aus.

3. Suchen Sie beim Navigieren durch die einzelnen Zeichnen-Befehle im Fenster **Grafikereignisliste** im Fenster **Grafikpipelinestufen** nach dem fehlenden Objekt. Zur Vereinfachung können Sie im Feld **Suche** in oberen rechten Ecke des Fensters **Grafikereignisliste** das Wort "Zeichnen" eingeben. Damit wird die Liste gefiltert und enthält nur Ereignisse, die "Zeichnen" im Titel haben.

    Im Fenster **Grafikpipelinestufen** zeigt die **Eingabeassembler** -Stufe die Geometrie des Objekts vor dem Transformieren, und die **Vertexshader** -Stufe zeigt dasselbe Objekt nach dem Transformieren. In diesem Fall wissen Sie, dass Sie das fehlende Objekt gefunden haben, wenn es in der **Eingabeassembler** -Stufe angezeigt wird, und wenn in der **Vertexshader** -Stufe nichts angezeigt wird.

   > [!NOTE]
   > Wenn das Objekt in weiteren Geometriestufen verarbeitet wird – beispielsweise in der Hullshader-, Domainshader- oder Geometryshader-Stufe –, kann die Ursache des Problems in diesen Stufen liegen. Normalerweise hängt das Problem mit der frühesten Stufe zusammen, in der das Ergebnis nicht oder nicht in der erwarteten Weise angezeigt wird.

4. Halten Sie an, wenn Sie den Zeichnen-Befehl erreichen, der dem fehlenden Objekt entspricht. In diesem Szenario zeigt das Fenster **Grafikpipelinestufen** , dass die Geometrie zwar an die GPU übergeben wurde (gekennzeichnet durch die Eingabeassembler-Miniaturansicht), jedoch nicht im Renderziel angezeigt wird, weil auf der Vertexshader-Stufe ein Problem aufgetreten ist (gekennzeichnet durch die Vertexshader-Miniaturansicht):

    ![Ein DrawIndexed-Ereignis und seine Auswirkungen auf die Pipeline](media/gfx_diag_demo_missing_object_shader_step_2.png "gfx_diag_demo_missing_object_shader_step_2")

   Nachdem Sie sich davon überzeugt haben, dass die App einen Draw-Aufruf für die Geometrie des fehlenden Objekts ausgeführt hat und dass das Problem auf der Vertexshader-Stufe aufgetreten ist, können Sie den HLSL-Debugger dazu verwenden, den Vertexshader zu überprüfen und festzustellen, was mit der Objektgeometrie geschehen ist. Mit dem HLSL-Debugger können Sie den Zustand von HLSL-Variablen während der Ausführung feststellen, den HLSL-Code schrittweise durchlaufen sowie Haltepunkte festlegen, um sich die Problemdiagnose zu erleichtern.

#### <a name="to-examine-the-vertex-shader"></a>So überprüfen Sie den Vertexshader

1. Starten Sie das Debuggen der Vertexshader-Stufe. Wählen Sie im Fenster **Grafikpipelinestufen** unter der **Vertexshader** -Stufe die Schaltfläche **Debuggen starten** aus.

2. Da die **Eingabeassembler** -Stufe dem Vertexshader offensichtlich korrekte Daten bereitstellt, aber die **Vertexshader** -Stufe keine Ausgabe erzeugt, müssen Sie die Vertexshader-Ausgabestruktur `output`überprüfen. Während Sie den HLSL-Code durchlaufen, sehen Sie sich die Zeilen genauer an, in denen `output` geändert wird.

3. Bei der ersten Änderung von `output` werden Werte in den Member `worldPos` geschrieben.

    ![Der Wert von „output.worldPos“ erscheint angemessen.](media/gfx_diag_demo_missing_object_shader_step_4.png "gfx_diag_demo_missing_object_shader_step_4")

    Da diese Werte sinnvoll aussehen, durchlaufen Sie den Code weiter bis zur nächsten Zeile, in der `output`geändert wird.

4. Bei der nächsten Änderung von `output` werden Werte in den Member `pos` geschrieben.

    ![Der Wert von „output.pos“ wurde eliminiert.](media/gfx_diag_demo_missing_object_shader_step_5.png "gfx_diag_demo_missing_object_shader_step_5")

    Die Werte des `pos` -Members, nur Nullen, sind allerdings verdächtig. Sie möchten nun herausfinden, warum `output.pos` nur Nullen als Werte hat.

5. Sie stellen fest, dass `output.pos` seine Werte aus einer Variablen namens `temp`erhält. Der vorhergehenden Zeile entnehmen Sie, dass der Wert von `temp` das Ergebnis der Multiplikation seines vorherigen Werts mit der Konstante `projection`ist. Sie vermuten, dass der verdächtige Wert von `temp`das Ergebnis dieser Multiplikation ist. Wenn Sie den Mauszeiger auf `projection`setzen, sehen Sie, dass auch der Wert dieser Konstanten nur aus Nullen besteht.

    ![Die Projektionsmatrix enthält eine ungültige Transformation.](media/gfx_diag_demo_missing_object_shader_step_6.png "gfx_diag_demo_missing_object_shader_step_6")

    In diesem Fall ergibt die Prüfung, dass der verdächtige Wert von `temp`höchstwahrscheinlich aus der Multiplikation mit `projection`resultiert, denn `projection` ist eine Konstante, die eine Projektionsmatrix darstellen soll, weshalb Sie wissen, dass die Konstante nicht nur Nullen enthalten darf.

   Nachdem Sie ermittelt haben, dass wahrscheinlich die HLSL-Konstante `projection`(die von Ihrer App an den Shader übergeben wurde) die Quelle des Problems ist, besteht der nächste Schritt darin, die Stelle im Quellcode der App zu finden, wo der Konstantenpuffer gefüllt wird. Sie können die **Aufrufliste des Grafikereignisses** verwenden, um diese Position zu finden.

#### <a name="to-find-where-the-constant-is-set-in-your-apps-source-code"></a>So finden Sie die Stelle, an der die Konstante im Quellcode Ihrer App festgelegt wird

1. Öffnen Sie das Fenster **Aufrufliste des Grafikereignisses** . Wählen Sie auf der Symbolleiste **Grafikdiagnose** die **Aufrufliste des Grafikereignisses** aus.

2. Navigieren Sie in der Aufrufliste im Quellcode Ihrer App nach oben. Wählen Sie im Fenster **Aufrufliste des Grafikereignisses** den obersten Aufruf aus, um festzustellen, ob der Konstantenpuffer dort gefüllt wird. Ist dies nicht der Fall, durchlaufen Sie die Aufrufliste weiter nach oben, bis Sie die Stelle finden, an der der Konstantenpuffer gefüllt wird. In diesem Fall stellen Sie fest, dass der Konstantenpuffer weiter oben in der Aufrufliste in einer Funktion namens `UpdateSubresource` über einen Aufruf der Direct3D-API `MarbleMaze::Render`gefüllt wird, und dass der Wert des Puffers aus einem Konstantenpufferobjekt namens `m_marbleConstantBufferData`stammt:

    ![Der Code, der den Konstantenpuffer festlegt](media/gfx_diag_demo_missing_object_shader_step_7.png "gfx_diag_demo_missing_object_shader_step_7")

   > [!TIP]
   > Wenn Sie die App gleichzeitig debuggen, können Sie einen Haltepunkt an dieser Position festlegen, der dann erreicht wird, wenn der nächste Frame gerendert wird. Sie können dann die Member von `m_marbleConstantBufferData` überprüfen, um zu bestätigen, dass der Wert des `projection` -Members auf lauter Nullen festgelegt wird, wenn der konstante Puffer gefüllt wird.

   Nachdem Sie die Position, an der der Konstantenpuffer gefüllt wird, gefunden und festgestellt haben, dass dessen Werte aus der Variablen `m_marbleConstantBufferData` stammen, müssen Sie im nächsten Schritt herausfinden, wo der `m_marbleConstantBufferData.projection`-Member mit den Nullen gefüllt wird. Sie können **Alle Verweise suchen** verwenden, um schnell nach Code zu suchen, in dem der Wert von `m_marbleConstantBufferData.projection`geändert wird.

#### <a name="to-find-where-the-projection-member-is-set-in-your-apps-source-code"></a>So ermitteln Sie, wo der Projektionsmember im Quellcode Ihrer App festgelegt wird

1. Suchen Sie nach Verweisen auf `m_marbleConstantBufferData.projection`. Öffnen Sie das Kontextmenü für die Variable `m_marbleConstantBufferData`, und wählen Sie dann **Alle Verweise suchen** aus.

2. Um in der App zu der Quellcodezeile zu navigieren, in der der `projection` -Member geändert wird, wählen Sie diese Zeile im Fenster **Ergebnisse der Symbolsuche** aus. Da das erste Ergebnis, in dem das projection-Member geändert wird, u. U. nicht die Ursache des Problems ist, müssen Sie möglicherweise mehrere Bereiche des Quellcodes Ihrer App überprüfen.

   Nachdem Sie die Zeile gefunden haben, in der `m_marbleConstantBufferData.projection` festgelegt wird, können Sie den umgebenden Quellcode überprüfen, um den Ursprung des falschen Werts zu bestimmen. In diesem Fall ermitteln Sie, dass der Wert von `m_marbleConstantBufferData.projection` auf eine lokale Variable namens `projection` festgelegt wird, bevor diese mit einem Wert initialisiert wurde, der durch den Code `m_camera->GetProjection(&projection);` in der nächsten Zeile angegeben ist.

   ![Die Marmorprojektion wird vor der Initialisierung festgelegt.](media/gfx_diag_demo_missing_object_shader_step_9.png "gfx_diag_demo_missing_object_shader_step_9")

   Um das Problem zu beheben, verschieben Sie die Codezeile, in der der Wert von `m_marbleConstantBufferData.projection` festgelegt wird, hinter die Zeile, in der der Wert der lokalen Variablen `projection`initialisiert wird.

   ![Der korrigierte Quellcode in C&#43;&#43;](media/gfx_diag_demo_missing_object_shader_step_10.png "gfx_diag_demo_missing_object_shader_step_10")

   Nachdem Sie den Code korrigiert haben, können Sie die App erneut erstellen und ausführen, um nun festzustellen, dass das Renderproblem behoben wurde:

   ![Das Objekt wird jetzt angezeigt.](media/gfx_diag_demo_missing_object_shader_resolution.png "gfx_diag_demo_missing_object_shader_resolution")