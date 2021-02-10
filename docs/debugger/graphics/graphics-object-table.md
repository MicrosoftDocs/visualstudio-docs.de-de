---
title: Grafikobjekttabelle | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die Grafikobjekttabelle. Damit können Sie in Visual Studio-Grafikanalyse die Direct3D-Objekte erkennen, die einen Frame eines Spiels oder einer App unterstützen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.datavisualizer
- vs.graphics.objecttable
- vs.graphics.bufferviewer
ms.assetid: f48f62d9-16ff-4a2e-8c01-5cbe99513788
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 095828e711f860662432edd767b19493b73c56c0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887574"
---
# <a name="graphics-object-table"></a>Grafikobjekttabelle
Mit der Grafikobjekttabelle in Visual Studio-Grafikanalyse können Sie die Direct3D-Objekte erkennen, die einen Frame Ihres Spiels oder Ihrer App unterstützen.

 Dies ist die Objekttabelle:

 ![Direct3D-Objekte, die von einer App erstellt wurden.](media/gfx_diag_demo_object_table_orientation.png "gfx_diag_demo_object_table_orientation")

## <a name="understanding-the-graphics-object-table"></a>Die Grafikobjekttabelle verstehen
 Mit der Objekttabelle können Sie Direct3D-Objekte analysieren, die das Rendern eines bestimmten Frames unterstützen. Sie können ein Renderingproblem auf ein bestimmtes Objekt zurückführen, indem Sie die Eigenschaften und Daten untersuchen. (Mit anderen Grafikdiagnosetools können Sie früher in der Diagnose die Liste der Objekte einschränken, die möglicherweise nicht Ihren Erwartungen entsprechen.) Wenn Sie das problemauslösende Objekt gefunden haben, können Sie eine typspezifische Visualisierung verwenden, um das Objekt zu untersuchen. So können Sie beispielsweise die Bildbearbeitung einsetzen, um Texturen anzusehen, oder die *Puffer-Schnellansicht* verwenden, um Pufferinhalte anzuzeigen.

 Die Objekttabelle unterstützt das Kopieren und Einfügen, sodass Sie ein anderes Tool, wie etwa Microsoft Excel, zum Überprüfen des Inhalts verwenden können.

 Darüber hinaus können Sie in der linken oberen Ecke über die Dropdownliste **Typ** die Anzeige von Objekten eines der Typen **Puffer**, **Shader** oder **Texturen** oder aller dieser Elemente gleichzeitig umschalten.  Sie können auch das Suchfeld in der rechten oberen Ecke verwenden, um in allen dargestellten Daten nach bestimmten Zeilen zu suchen.  Sie können dort beispielsweise nach *D32_FLOAT* suchen, um alle Instanzen von Objekten dieses Formats in der Liste zu finden.

### <a name="graphics-object-table-format"></a>Format der Grafikobjekttabelle
 Die Objekttabelle zeigt die Direct3D-Objekte und die Ressourcen an, die den Frame unterstützen, der mit dem ausgewählten Ereignis verknüpft ist, beispielsweise Zustandsobjekte, Puffer, Shader, Texturen und andere Ressourcen. Nicht in die Objekttabelle aufgenommen werden Objekte, die in einem vorherigen Frame erstellt wurden und während des aufgezeichneten Frames nicht verwendet werden. Objekte, die während des aufgezeichneten Frames durch vorherige Ereignisse zerstört wurden, werden in den folgenden Ereignissen weggelassen. Objekte, die nicht auf D3D10Device oder D3D11DeviceContext festgelegt wurden, werden in grauer Schrift angezeigt. Objekte werden in einem Tabellenformat angezeigt.

|Spalte|Beschreibung|
|------------|-----------------|
|**Bezeichner**|Die Objekt-ID.|
|**Name**|Anwendungsspezifische Informationen, die für das Objekt mit der Direct3D-Funktion `SetPrivateData` festgelegt wurden (normalerweise zur Bereitstellung zusätzlicher Informationen über das Objekt).|
|**Type**|Der Objekttyp.|
|**Active**|Zeigt "*" für ein Objekt an, das während des aufgezeichneten Frames auf D3D10Device oder D3D11DeviceContext festgelegt wurde.<br /><br /> Dies entspricht den Objekten, die in grauer Schrift angezeigt werden, stellt aber einen Spalteneintrag bereit, mit dem Sie die Objekttabelle sortieren können.|
|**Size**|Die Größe des Objekts in Bytes.|
|**Format**|Das Format des Objekts. Beispielsweise das Format eines Texturobjekts oder das Shadermodell eines Shaderobjekts.|
|**Width**|Die Breite eines Texturobjekts. Gilt nicht für andere Objekttypen.|
|**Height**|Die Höhe eines Texturobjekts. Gilt nicht für andere Objekttypen.|
|**Depth**|Die Tiefe eines 3D-Texturobjekts. Wenn eine Textur nicht 3D ist, ist der Wert 0. Gilt nicht für andere Objekttypen.|
|**Mips**|Die Anzahl von MIP-Ebenen eines Texturobjekts. Gilt nicht für andere Objekttypen.|
|**ArraySize**|Die Anzahl von Texturen in einem Texturarray. Der Bereich liegt zwischen 1 und einer von der aktuellen Funktionsebene definierten Obergrenze. Für eine Cubemap beträgt dieser Wert 6 mal die Anzahl der Cubemaps im Array.|
|**Beispiele**|Die Anzahl der Mehrfachabtastungen pro Pixel.|

## <a name="graphics-object-viewers"></a>Grafikobjekt-Viewer
 Um Informationen zu einem Objekt anzuzeigen, öffnen Sie es, indem Sie seinen Namen in der Objekttabelle auswählen. Details über das Objekt werden in verschiedenen Formaten angezeigt, je nach Typ des Objekts. Texturen werden beispielsweise unter Verwendung des Textur-Viewers und Gerätestatus angezeigt, z. B. wird Gerätekontext D3D11 als formatierte Liste angezeigt. Unterschiedliche Versionen von Direct3D verwenden unterschiedliche Objekte, und es gibt häufig spezifische Schnellansichten für die wichtigsten Objekte der einzelnen Versionen.

 Hier ist der Textur-Viewer mit dem Inhalt der Pipelinestufe „Ausgabemerge“.

 ![Die Texturvorschau mit Anzeige des Ausgabemergers](media/gfx_diag_texture_preview.png "gfx_diag_texture_preview")

### <a name="d3d12-command-list"></a>D3D12-Befehlsliste
 In Direct3D 12 ist eine Befehlsliste ein Objekt, von dem Befehle in einer Befehlszuweisung aufgezeichnet werden, damit sie an die GPU als eine einzelne Anforderung gesendet werden können. Befehlslisten führen in der Regel eine Reihe von Statuseinstellungen aus, zeichnen, deaktivieren und kopieren Befehle. Sie sind besonders wichtig, da sie die bevorzugte Methode für das Rendern in Direct3D 12 sind und zwischen den Frames zur Leistungsoptimierung erneut verwendet werden können. Details zur Befehlsliste werden mit Informationen zu den einzelnen Pipelinestufen auf einer eigenen Registerkarte in einem neuen Dokumentfenster angezeigt.

### <a name="d3d12-pipeline-state-object-pso"></a>D3D12-Pipelinestatusobjekt (PSO)
 In Direct3D 12 stellt ein Pipelinestatusobjekt einen erheblichen Teil der GPU-Status dar, einschließlich aller derzeit festgelegten Shader und bestimmter Statusobjekte mit festen Funktionen. Nach der Erstellung ist ein Pipelinestatusobjekt unveränderlich – eine Anwendung kann die Konfiguration der Pipeline nur durch die Bindung eines anderen Pipelinestatusobjekts ändern. PSO-Details werden in einem neuen Dokumentfenster angezeigt, wobei die Details der Pipelinekonfiguration hierarchisch angeordnet sind.

### <a name="d3d12-root-signature"></a>D3D12-Stammsignatur
 In Direct3D 12 definiert die Stammsignatur alle Ressourcen, die an eine Grafik- oder Computepipeline gebunden sind und verknüpft Befehlslisten mit für den Shader erforderlichen Ressourcen. In der Regel gibt es in einer App eine Stammsignatur für Grafiken und eine für Compute. Stammsignaturdetails werden in einem neuen Dokumentfenster angezeigt, wobei die Details der Stammsignatur hierarchisch angeordnet sind.

### <a name="d3d12-resources"></a>D3D12-Ressourcen
 In Direct3D-12 sind Ressourcen Catchall-Objekte, die Daten für die Renderingpipeline bereitstellen. Dies steht im Gegensatz zu Direct3D11, wo viele spezifische Objekte für verschiedene Arten und Dimensionen von Ressourcen definiert werden. Eine Direct3D 12-Ressource kann Texturdaten, Scheitelpunktdaten, Shaderdaten und mehr enthalten – sie kann sogar Renderziele, z. B. Tiefenpuffer, darstellen. Einzelheiten über eine Direct3D 12-Ressource werden in einem neuen Dokumentfenster angezeigt. Die Grafikanalyse verwendet den entsprechenden Viewer für den Inhalt des Ressourcenobjekts, wenn dessen Typ bestimmt werden kann. Beispielsweise wird ein Ressourcenobjekt mit Texturdaten mit dem Textur-Viewer angezeigt, wie bei einem D3D11 Texture2D-Objekt.

### <a name="device-context-object"></a>Gerätekontextobjekt
 In Direct3D 11 und Direct3D 10 ist das Gerätekontextobjekt (**D3D11-Gerätekontext** oder **D3D10-Gerät**) besonders wichtig, da es die wichtigsten Zustandsinformationen enthält und auf andere Zustandsobjekte verweist, die momentan festgelegt sind. Gerätekontextdetails werden in einem neuen Dokumentfenster angezeigt, und jede Kategorie von Informationen wird dort auf einer eigenen Registerkarte angezeigt. Der Gerätekontext ändert sich, wenn ein neues Ereignis ausgewählt wird, um den aktuellen Gerätezustand wiederzugeben.

### <a name="buffer-object"></a>Pufferobjekt
 Pufferobjektdetails (D3D11-Puffer oder D3D10-Puffer) werden in einem neuen Dokumentfenster angezeigt, das den Pufferinhalt in einer Tabelle darstellt und eine Schnittstelle bereitstellt, um die Art und Weise, wie Pufferinhalt angezeigt wird, zu ändern. Die Tabelle **Pufferdaten** unterstützt das Kopieren und Einfügen, sodass Sie ein anderes Tool, wie etwa Microsoft Excel, zum Überprüfen des Inhalts verwenden können. Der Inhalt des Puffers wird gemäß dem Wert des Kombinationsfelds **Format** interpretiert, das sich oberhalb der Tabelle **Pufferdaten** befindet. Im Feld können Sie ein zusammengesetztes Datenformat eingeben, das aus den Datentypen besteht, die in der folgenden Tabelle aufgelistet sind. Beispielsweise zeigt "float int" eine Liste von Strukturen an, die einen 32-Bit-Gleitkommawert enthalten, dem ein 32-Bit-Ganzzahlwert mit Vorzeichen folgt. Zusammengesetzte Datenformate, die Sie angegeben haben, werden dem Kombinationsfeld zur späteren Verwendung hinzugefügt.

 Sie können auch das Kontrollkästchen **Offsets anzeigen** umschalten, um Offsets der einzelnen Elemente im Puffer ein- oder auszublenden.

|Typ|Beschreibung|
|----------|-----------------|
|**float**|Ein 32-Bit-Gleitkommawert.|
|**float2**|Ein Vektor, der zwei 32-Bit-Gleitkommawerte enthält.|
|**float3**|Ein Vektor, der drei 32-Bit-Gleitkommawerte enthält.|
|**float4**|Ein Vektor, der vier 32-Bit-Gleitkommawerte enthält.|
|**byte**|Ein 8-Bit-Ganzzahlwert mit Vorzeichen|
|**2byte**|Ein 16-Bit-Ganzzahlwert mit Vorzeichen.|
|**4byte**|Ein 32-Bit-Ganzzahlwert mit Vorzeichen. Identisch mit **int**.|
|**8byte**|Ein 64-Bit-Ganzzahlwert mit Vorzeichen. Identisch mit **int64**.|
|**xbyte**|Ein 8-Bit-Hexadezimalwert|
|**x2byte**|Ein 16-Bit-Hexadezimalwert|
|**x4byte**|Ein 32-Bit-Hexadezimalwert Identisch mit **xint**.|
|**x8byte**|Ein 64-Bit-Hexadezimalwert Identisch mit **xint64**.|
|**ubyte**|Ein 8-Bit-Ganzzahlwert ohne Vorzeichen.|
|**u2byte**|Ein 16-Bit-Ganzzahlwert ohne Vorzeichen.|
|**u4byte**|Ein 32-Bit-Ganzzahlwert ohne Vorzeichen. Identisch mit **uint**.|
|**u8byte**|Ein 64-Bit-Ganzzahlwert ohne Vorzeichen. Identisch mit **uint64**.|
|**half**|Ein 16-Bit-Gleitkommawert.|
|**half2**|Ein Vektor, der zwei 16-Bit-Gleitkommawerte enthält.|
|**half3**|Ein Vektor, der drei 16-Bit-Gleitkommawerte enthält.|
|**half4**|Ein Vektor, der vier 16-Bit-Gleitkommawerte enthält.|
|**double**|Ein 64-Bit-Gleitkommawert.|
|**int**|Ein 32-Bit-Ganzzahlwert mit Vorzeichen. Identisch mit **4byte**.|
|**int64**|Ein 64-Bit-Ganzzahlwert mit Vorzeichen. Identisch mit **8byte**.|
|**xint**|Ein 32-Bit-Hexadezimalwert Identisch mit **x4byte**.|
|**xint64**|Ein 64-Bit-Hexadezimalwert Identisch mit **x8byte**.|
|**uint**|Ein 32-Bit-Ganzzahlwert ohne Vorzeichen. Identisch mit **u4byte**.|
|**uint64**|Ein 64-Bit-Ganzzahlwert ohne Vorzeichen. Identisch mit **u8byte**.|
|**bool**|Ein boolescher Wert (`true` oder `false`) Jeder boolesche Wert wird durch einen 32-Bit-Wert dargestellt.|

## <a name="see-also"></a>Siehe auch
- [Grafikdiagnose (Debuggen von DirectX-Grafiken)](visual-studio-graphics-diagnostics.md)
- [Exemplarische Vorgehensweise: Fehlende Objekte durch Gerätestatus](walkthrough-missing-objects-due-to-device-state.md)