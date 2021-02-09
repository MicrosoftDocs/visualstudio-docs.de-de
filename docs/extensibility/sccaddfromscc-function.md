---
title: Sccaddfromscc-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e35ae460d6ceb505bc7ad64a0e522bf2841260f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886612"
---
# <a name="sccaddfromscc-function"></a>Sccaddfromscc-Funktion
Diese Funktion ermöglicht es dem Benutzer, Dateien zu suchen, die sich bereits im Quell Code Verwaltungssystem befinden, und diese Dateien anschließend zu einem Teil des aktuellen Projekts zu machen. Diese Funktion kann z. b. eine gemeinsame Header Datei in das aktuelle Projekt übernehmen, ohne die Datei zu kopieren. Das Rückgabe Array von Dateien, `lplpFileNames` , enthält die Liste der Dateien, die der Benutzer dem IDE-Projekt hinzufügen möchte.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccAddFromScc (
   LPVOID   pvContext,
   HWND     hWnd,
   LPLONG   lpnFiles,
   LPCSTR** lplpFileNames
);
```

### <a name="parameters"></a>Parameter
 pvcontext

in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.

 hWnd

in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.

 lpnfiles

[in, out] Ein Puffer für die Anzahl der Dateien, die in hinzugefügt werden. (Dies ist `NULL` der Wert, wenn der Speicher, auf den verweist, `lplpFileNames` freigegeben werden soll. Weitere Informationen finden Sie in den hinweisen.)

 lplpfile-Namen

[in, out] Ein Array von Zeigern auf alle Dateinamen ohne Verzeichnispfade. Dieses Array wird vom Quellcodeverwaltungs-Plug-in zugeordnet und freigegeben. Wenn `lpnFiles` = 1 und `lplpFileNames` nicht ist `NULL` , enthält der Vorname im Array, auf den verweist, `lplpFileNames` den Zielordner.

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Die Dateien wurden erfolgreich gefunden und dem Projekt hinzugefügt.|
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde ohne Auswirkung abgebrochen.|
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss erneut geladen werden.|

## <a name="remarks"></a>Bemerkungen
 Die IDE ruft diese Funktion auf. Wenn das Quellcodeverwaltungs-Plug-in die Angabe eines lokalen Ziel Ordners unterstützt, übergibt die IDE `lpnFiles` = 1 und übergibt den Namen des lokalen Ordners an `lplpFileNames` .

 Wenn der Rückruf der `SccAddFromScc` Funktion zurückgibt, hat das Plug-in Werte für `lpnFiles` und zugewiesen `lplpFileNames` , wobei der Speicher für das Dateinamen Array nach Bedarf zugewiesen wird (Beachten Sie, dass diese Zuordnung den-Zeiger ersetzt `lplpFileNames` ). Das Quellcodeverwaltungs-Plug-in ist dafür verantwortlich, alle Dateien im Verzeichnis des Benutzers oder im angegebenen Ordner für die Benennung zu platzieren. Die IDE fügt dann die Dateien dem IDE-Projekt hinzu.

 Schließlich ruft die IDE diese Funktion ein zweites Mal auf und übergibt `NULL` für `lpnFiles` . Dies wird vom Quellcodeverwaltungs-Plug-in als besonderes Signal interpretiert, um den Arbeitsspeicher freizugeben, der dem Dateinamen Array in zugewiesen ist. `lplpFileNames``.`

 `lplpFileNames` ist ein- `char ***` Zeiger. Das Quellcodeverwaltungs-Plug-in platziert einen Zeiger auf ein Array von Zeigern auf Dateinamen und übergibt somit die Liste standardmäßig für diese API.

> [!NOTE]
> Anfängliche Versionen der vssci-API bieten keine Möglichkeit, das Ziel Projekt für die hinzugefügten Dateien anzugeben. Um dies zu ermöglichen, wurde die Semantik des `lplpFIleNames` Parameters verbessert, um Sie als einen in/out-Parameter anstelle eines Output-Parameters festzulegen. Wenn nur eine einzelne Datei angegeben ist, d. h. der Wert, auf den durch `lpnFiles` = 1 verwiesen wird, enthält das erste Element von `lplpFileNames` den Zielordner. Um diese neue Semantik zu verwenden, ruft die IDE die-Funktion auf, `SccSetOption` wobei der- `nOption` Parameter auf festgelegt ist `SCC_OPT_SHARESUBPROJ` . Wenn die Semantik von einem Quellcodeverwaltungs-Plug-in nicht unterstützt wird, wird zurückgegeben `SCC_E_OPTNOTSUPPORTED` . Dadurch wird die Verwendung des Features " **aus Quell Code Verwaltung hinzufügen** " deaktiviert. Wenn ein Plug-in das Feature " **aus Quell Code Verwaltung hinzufügen** " () unterstützt `SCC_CAP_ADDFROMSCC` , muss es die neue Semantik unterstützen und zurückgeben `SCC_I_SHARESUBPROJOK` .

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
