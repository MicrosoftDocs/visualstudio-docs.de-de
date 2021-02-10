---
title: Disassemblydata | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 49e8f151aa01037a0bc18161fbe94a00488394db
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953837"
---
# <a name="disassemblydata"></a>DisassemblyData
Beschreibt eine disassemblierungsanweisung für die integrierte Entwicklungsumgebung (IDE), die angezeigt werden soll.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagDisassemblyData {
    DISASSEMBLY_STREAM_FIELDS dwFields;
    BSTR                      bstrAddress;
    BSTR                      bstrAddressOffset;
    BSTR                      bstrCodeBytes;
    BSTR                      bstrOpcode;
    BSTR                      bstrOperands;
    BSTR                      bstrSymbol;
    UINT64                    uCodeLocationId;
    TEXT_POSITION             posBeg;
    TEXT_POSITION             posEnd;
    BSTR                      bstrDocumentUrl;
    DWORD                     dwByteOffset;
    DISASSEMBLY_FLAGS         dwFlags;
} DisassemblyData;
```

```csharp
public struct DisassemblyData { 
    public uint          dwFields;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrCodeBytes;
    public string        bstrOpcode;
    public string        bstrOperands;
    public string        bstrSymbol;
    public ulong         uCodeLocationId;
    public TEXT_POSITION posBeg;
    public TEXT_POSITION posEnd;
    public string        bstrDocumentUrl;
    public uint          dwByteOffset;
    public uint          dwFlags;
};
```

## <a name="members"></a>Member
`dwFields`\
Die [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) Konstante, die angibt, welche Felder ausgefüllt werden.

`bstrAddress`\
Die Adresse als Offset von einem Startpunkt (in der Regel der Anfang der zugeordneten Funktion).

`bstrCodeBytes`\
Die Code Bytes für diese Anweisung.

`bstrOpcode`\
Der Opcode für diese Anweisung.

`bstrOperands`\
Die Operanden für diese Anweisung.

`bstrSymbol`\
Der Symbol Name (sofern vorhanden), der der Adresse (öffentliches Symbol, Bezeichnung usw.) zugeordnet ist.

`uCodeLocationId`\
Der Bezeichner des Code Speicher Orts für diese disassemblierte Zeile. Wenn die Code Kontext Adresse einer Zeile größer als die Code Kontext Adresse eines anderen ist, dann ist der disassemblierte Code Speicherort Bezeichner der ersten Zeile größer als der Bezeichner für den Code Speicherort der zweiten.

`posBeg`\
Der [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , der der Position in einem Dokument entspricht, an dem die Disassemblydaten beginnen.

`posEnd`\
Der [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , der der Position in einem Dokument entspricht, an dem die Disassemblydaten enden.

`bstrDocumentUrl`\
Bei Textdokumenten, die als Dateinamen dargestellt werden können, `bstrDocumentUrl` wird das Feld mit dem Dateinamen aufgefüllt, in dem die Quelle gefunden werden kann. dabei wird das Format verwendet `file://file name` .

Für Textdokumente, die nicht als Dateinamen dargestellt werden können, `bstrDocumentUrl` ist ein eindeutiger Bezeichner für das Dokument, und die Debug-Engine muss die [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) -Methode implementieren.

Dieses Feld kann auch zusätzliche Informationen zu Prüfsummen enthalten. Einzelheiten finden Sie in den Hinweisen.

`dwByteOffset`\
Die Anzahl der Bytes, die die Anweisung vom Anfang der Codezeile ist.

`dwFlags`\
Die [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) Konstante, die angibt, welche Flags aktiv sind.

## <a name="remarks"></a>Bemerkungen
Jede `DisassemblyData` Struktur beschreibt eine Anweisung der Disassembly. Ein Array dieser Strukturen wird von der [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) -Methode zurückgegeben.

Die [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur wird nur für Text basierte Dokumente verwendet. Der Quell Code Bereich für diese Anweisung wird nur für die erste Anweisung ausgefüllt, die aus einer Anweisung oder Zeile generiert wird, z `dwByteOffset == 0` . b. wenn.

Bei nicht-Text-Dokumenten kann ein Dokument Kontext aus dem Code abgerufen werden, und das `bstrDocumentUrl` Feld muss ein NULL-Wert sein. Wenn das `bstrDocumentUrl` Feld `bstrDocumentUrl` mit dem Feld im vorherigen Array Element identisch ist `DisassemblyData` , legen `bstrDocumentUrl` Sie den auf einen NULL-Wert fest.

Wenn `dwFlags` für das Feld das `DF_DOCUMENT_CHECKSUM` Flag festgelegt ist, folgen zusätzliche Prüfsummeninformationen der Zeichenfolge, auf die das `bstrDocumentUrl` Feld zeigt. Vor allem folgt nach dem NULL-Zeichen folgen Abschluss Zeichen eine GUID, die den Prüfsummen Algorithmus identifiziert, auf den wiederum ein 4-Byte-Wert folgt, der die Anzahl der Bytes in der Prüfsumme anzeigt, und dass wiederum die Prüfsummen Bytes befolgt werden. Weitere Informationen zum Codieren und Decodieren dieses Felds in finden Sie im Beispiel in diesem Thema [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] .

## <a name="example"></a>Beispiel
`bstrDocumentUrl`Wenn das- `DF_DOCUMENT_CHECKSUM` Flag festgelegt ist, kann das-Feld zusätzliche Informationen enthalten, die keine Zeichenfolge sind. Der Prozess zum Erstellen und Lesen dieser codierten Zeichenfolge ist in unkompliziert [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] . In [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] ist es jedoch eine andere Sache. Für diejenigen, die neugierig sind, zeigt das folgende Beispiel eine Möglichkeit, die codierte Zeichenfolge aus [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] und eine Möglichkeit zum Decodieren der codierten Zeichenfolge in zu erstellen [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] .

```csharp
using System;
using System.Runtime.InteropServices;

namespace MyNamespace
{
    class MyClass
    {
        string EncodeData(string documentString,
                          Guid checksumGuid,
                          byte[] checksumData)
        {
            string returnString = documentString;

            if (checksumGuid == null || checksumData == null)
            {
                // Nothing more to do. Just return the string.
                return returnString;
            }

            returnString += '\0'; // separating null value

            // Add checksum GUID to string.
            byte[] guidDataArray  = checksumGuid.ToByteArray();
            int    guidDataLength = guidDataArray.Length;
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);
            for (int i = 0; i < guidDataLength; i++)
            {
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);
            }
            // Copy guid data bytes to string as wide characters.
            // Assumption: sizeof(char) == 2.
            for (int i = 0; i < guidDataLength / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum count (a 32-bit value).
            Int32 checksumCount = checksumData.Length;
            Marshal.StructureToPtr(checksumCount, pBuffer, true);
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum data.
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);
            for (int i = 0; i < checksumCount; i++)
            {
                Marshal.WriteByte(pBuffer, i, checksumData[i]);
            }
            for (int i = 0; i < checksumCount / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }
            Marshal.FreeCoTaskMem(pBuffer);

            return returnString;
        }

        void DecodeData(    string encodedString,
                        out string documentString,
                        out Guid   checksumGuid,
                        out byte[] checksumData)
        {
            documentString = String.Empty;
            checksumGuid = Guid.Empty;
            checksumData = null;

            IntPtr pBuffer = Marshal.StringToBSTR(encodedString);
            if (null != pBuffer)
            {
                int bufferOffset = 0;

                // Parse string out. String is assumed to be Unicode.
                documentString = Marshal.PtrToStringUni(pBuffer);
                bufferOffset += (documentString.Length + 1) * sizeof(char);

                // Parse Guid out.
                // Read guid bytes from buffer and store in temporary
                // buffer that contains only the guid bytes. Then the
                // Marshal.PtrToStructure() can work properly.
                byte[] guidDataArray  = checksumGuid.ToByteArray();
                int    guidDataLength = guidDataArray.Length;
                IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);
                for (int i = 0; i < guidDataLength; i++)
                {
                    Marshal.WriteByte(pGuidBuffer, i,
                                      Marshal.ReadByte(pBuffer, bufferOffset + i));
                }
                bufferOffset += guidDataLength;
                checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));
                Marshal.FreeCoTaskMem(pGuidBuffer);

                // Parse out the number of checksum data bytes (always 32-bit value).
                int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);
                bufferOffset += sizeof(Int32);

                // Parse out the checksum data.
                checksumData = new byte[dataCount];
                for (int i = 0; i < dataCount; i++)
                {
                    checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
