---
title: Mssccprj. SCC-Datei | Microsoft-Dokumentation
description: Erfahren Sie mehr über Mssccprj. SCC-Datei, bei der es sich um eine lokale, Client seitige Datei handelt, die vom Quellcodeverwaltungs-Plug-in verwendet wird, die mit dem Visual Studio SDK verwendet werden kann.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f55e99d9df10ef2f96761a9436597d227cf0cd93
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886690"
---
# <a name="mssccprjscc-file"></a>Mssccprj. SCC-Datei
Wenn Sie eine Visual Studio-Projekt Mappe oder ein Projekt in der Quell Code Verwaltung mithilfe der IDE platzieren, empfängt die IDE zwei wichtige Informationen. Die Informationen stammen aus dem Quellcodeverwaltungs-Plug-in in Form von Zeichen folgen. Diese Zeichen folgen "", "" "" "" "" "" "" "" "" "" "" "" " Die IDE ruft diese Zeichen folgen in der Regel beim ersten Mal durch Aufrufen von [sccgetprojpath](../extensibility/sccgetprojpath-function.md)ab und speichert Sie dann in der Projekt Mappe oder Projektdatei für zukünftige Aufrufe von [sccopenproject](../extensibility/sccopenproject-function.md). Wenn Sie in die Projekt Mappe und die Projektdateien eingebettet sind, werden die Zeichen folgen "AUXPATH" und "ProjName" nicht automatisch aktualisiert, wenn ein Benutzer Projektmappen und Projektdateien, die sich in der Versionskontrolle befinden, verzweigt, verzweigt oder kopiert. Um sicherzustellen, dass die Projektmappen-und Projektdateien auf Ihren richtigen Speicherort in der Versionskontrolle zeigen, müssen die Benutzer die Zeichen folgen manuell aktualisieren. Da die Zeichen folgen als nicht transparent gemeint sind, ist es möglicherweise nicht immer klar, wie Sie aktualisiert werden sollten.

 Das Quellcodeverwaltungs-Plug-in kann dieses Problem vermeiden, indem die Zeichen folgen "AUXPATH" und "ProjName" in einer speziellen Datei gespeichert werden, die als *Mssccprj. SCC* -Datei bezeichnet wird. Dabei handelt es sich um eine lokale, Client seitige Datei, die im Besitz des Plug-ins ist. Diese Datei wird nie unter Quell Code Verwaltung abgelegt, aber vom Plug-in für jedes Verzeichnis generiert, das Quell Code gesteuerte Dateien enthält. Um zu ermitteln, welche Dateien Visual Studio-Projektmappen-und Projektdateien sind, kann ein Quellcodeverwaltungs-Plug-in die Dateierweiterungen mit einer standardmäßigen oder benutzerdefinierten Liste vergleichen. Sobald die IDE erkennt, dass ein Plug-in die Datei " *Mssccprj. SCC* " unterstützt, werden die Zeichen folgen "AUXPATH" und "ProjName" nicht mehr in Projektmappen-und Projektdateien eingebettet, sondern diese Zeichen folgen werden stattdessen aus der Datei " *Mssccprj. SCC* " gelesen.

 Ein Quellcodeverwaltungs-Plug-in, das die Datei " *Mssccprj. SCC* " unterstützt, muss den folgenden Richtlinien entsprechen:

- Es kann nur eine *Mssccprj. SCC* -Datei pro Verzeichnis vorhanden sein.

- Eine *Mssccprj. SCC* -Datei kann für mehrere Dateien, die sich in einem bestimmten Verzeichnis unter Quell Code Verwaltung befinden, "" "" "" "" "" "" "" "" "" "

- Die ""-Zeichenfolge "" für "" Es darf z. b. in Anführungszeichen eingeschlossen werden (z. b., um eine leere Zeichenfolge anzugeben). Die IDE entfernt alle Anführungszeichen aus der Zeichenfolge "AUXPATH", wenn Sie aus der Datei " *Mssccprj. SCC* " gelesen wird.

- Die Zeichenfolge "ProjName" in *Mssccprj. Die SCC-Datei* muss genau mit der von der Funktion zurückgegebenen Zeichenfolge übereinstimmen `SccGetProjPath` . Wenn die von der Funktion zurückgegebene Zeichenfolge in Anführungszeichen eingeschlossen ist, muss die Zeichenfolge in der *Mssccprj. SCC* -Datei in Anführungszeichen eingeschlossen werden und umgekehrt.

- Eine *Mssccprj. SCC* -Datei wird erstellt oder aktualisiert, wenn eine Datei unter Quell Code Verwaltung platziert wird.

- Wenn eine *Mssccprj. SCC* -Datei gelöscht wird, sollte Sie von einem Anbieter erneut generiert werden, wenn Sie das nächste Mal einen Quell Code Verwaltungsvorgang für dieses Verzeichnis ausführt.

- Eine *Mssccprj. SCC* -Datei muss genau dem definierten Format entsprechen.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Eine Abbildung von Mssccprj. SCC-Dateiformat
 Im folgenden finden Sie ein Beispiel für das Dateiformat *Mssccprj. SCC* (die Zeilennummern werden nur als Leitfaden bereitgestellt und sollten nicht in den Datei Text eingefügt werden):

- [Zeile 1] `SCC = This is a Source Code Control file`

- [Zeile 2]

- [Zeile 3] `[TestApp.sln]`

- [Zeile 4] `SCC_Aux_Path = "\\server\vss\"`

- [Zeile 5] `SCC_Project_Name = "$/TestApp"`

- [Zeile 6]

- [Zeile 7] `[TestApp.csproj]`

- [Zeile 8] `SCC_Aux_Path = "\\server\vss\"`

- [Zeile 9] `SCC_Project_Name = "$/TestApp"`

 Die erste Zeile gibt den Zweck der Datei an und fungiert als Signatur für alle Dateien dieses Typs. Diese Zeile sollte in allen *Mssccprj. SCC* -Dateien genau so aussehen:

 `SCC = This is a Source Code Control file`

 Im folgenden Abschnitt werden die Einstellungen für jede Datei beschrieben, die mit dem Dateinamen in eckigen Klammern gekennzeichnet sind. Dieser Abschnitt wird für jede Datei wiederholt, die nachverfolgt wird. Diese Zeile ist ein Beispiel für einen Dateinamen, nämlich `[TestApp.csproj]` . Die IDE erwartet die folgenden beiden Zeilen. Dabei wird jedoch nicht der Stil der definierten Werte definiert. Die Variablen sind `SCC_Aux_Path` und `SCC_Project_Name` .

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 Es gibt kein endtrennzeichen zu diesem Abschnitt. Der Name der Datei sowie alle Literale, die in der Datei angezeigt werden, werden in der SCC. h-Header Datei definiert. Weitere Informationen finden Sie unter Zeichen folgen, die [als Schlüssel zum Suchen eines Quellcodeverwaltungs-Plug-ins verwendet werden](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)
- [Als Schlüssel für die Suche nach einem Quellcodeverwaltungs-Plug-in verwendete Zeichen folgen](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
