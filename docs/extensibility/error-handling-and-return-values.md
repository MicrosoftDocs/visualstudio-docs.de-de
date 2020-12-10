---
title: Fehlerbehandlung und Rückgabewerte | Microsoft-Dokumentation
description: Erfahren Sie, wie das Visual Studio SDK Interop-Assemblys bereitstellt, um beim Empfang einer Fehler Benachrichtigung umfangreiche Fehlerinformationen aufzuzeichnen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8e8385e0b270cd6e359ef03a3060d5eefb97479
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995849"
---
# <a name="error-handling-and-return-values"></a>Fehlerbehandlung und Rückgabewerte
VSPackages und com verwenden die gleiche Architektur für Fehler. Die `SetErrorInfo` `GetErrorInfo` Funktionen und sind Teil der Win32-API (Application Programming Interface). Jedes VSPackage in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) kann diese globalen Win32-APIs aufzurufen, um umfassende Fehlerinformationen aufzuzeichnen, wenn eine Fehler Benachrichtigung empfangen wird. Stellt Interop-Assemblys [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] bereit, um Fehlerinformationen zu verwalten.

## <a name="interop-methods"></a>Interop-Methoden
 Zur Unterstützung bietet die IDE eine Methode, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> , für die Verwendung statt der Win32-APIs. In verwaltetem Code verwenden <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> . Wenn ein Fehler `HRESULT` auf der Ebene eintrifft, auf der die Fehlermeldung angezeigt werden soll (Dies ist oft das Objekt, das einen <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Befehls Handler implementiert), verwendet die IDE eine andere Methode, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> , um das entsprechende Meldungs Feld anzuzeigen. Verwenden Sie in verwaltetem Code die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> Methode.

 Als VSPackage-Implementierer Implementieren die COM-Objekte normalerweise `ISupportErrorInfo` . Die- `ISupportErrorInfo` Schnittstelle stellt sicher, dass umfangreiche Fehlerinformationen in der Aufrufkette vertikal verschoben werden können. Objekte, die in Prozessen oder Threads verwendet werden können, müssen unterstützen, `ISupportErrorInfo` um sicherzustellen, dass die umfangreichen Fehlerinformationen ordnungsgemäß an den Aufrufer zurück gemarshallt werden.

 Alle Objekte im Zusammenhang mit VSPackages, die an der Erweiterung der IDE beteiligt sind, einschließlich editorfactorys, Editoren, Hierarchien und angebotenen Diensten, sollten umfangreiche Fehlerinformationen unterstützen. Die IDE erfordert, dass diese VSPackage-Objekte nicht implementiert `ISupportErrorInfo` werden, es wird jedoch immer empfohlen.

 Die IDE ist für das Melden von Fehlerinformationen und die Anzeige an einen Benutzer verantwortlich, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Wenn eine `HRESULT` an die IDE weitergegeben wird. Die IDE ist auch der Mechanismus zum Erstellen von `ErrorInfo` Objekten.

## <a name="general-guidelines"></a>Allgemeine Richtlinien
 Mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> -Methode und der-Methode können Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> auch Fehler festlegen und Berichte für Ihre VSPackage-Implementierung melden. Beachten Sie jedoch als allgemeine Regel die folgenden Richtlinien für die Behandlung von Fehlermeldungen in Ihrem VSPackage:

- Implementieren `ISupportErrorInfo` Sie in ihren VSPackage-com-Objekten.

- Erstellen Sie einen Fehler Berichterstattungs Mechanismus, der die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Methode in Objekten aufruft, die implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

- Ermöglicht der IDE das Anzeigen von Fehlern für Benutzer über die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> Methode.

## <a name="error-information-in-the-ide"></a>Fehlerinformationen in der IDE
 Die folgenden Regeln geben an, wie Fehlerinformationen in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE behandelt werden:

- Als Verteidigungsstrategie, um sicherzustellen, dass den Benutzern keine veralteten Fehlerinformationen gemeldet werden, sollten Funktionen, die die-Methode aufruft, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> zuerst die-Methode aufzurufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> . Übergeben `null` Sie, um zwischengespeicherte Fehlermeldungen zu löschen, bevor Sie Elemente aufrufen, die möglicherweise neue Fehlerinformationen festlegen.

- Funktionen, die Fehlermeldungen nicht direkt melden, dürfen nur die-Methode aufzurufen, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Wenn Sie einen Fehler zurückgeben `HRESULT` . Es ist zulässig, die für `ErrorInfo` den Eintrag für eine Funktion oder bei der Rückgabe von zu löschen <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Die einzige Ausnahme von dieser Regel ist, wenn ein-Rückruf einen Fehler zurückgibt `HRESULT` , von dem die empfangende Partei explizit wieder hergestellt oder sicher ignoriert werden kann.

- Jede Partei, die einen Fehler explizit ignoriert, `HRESULT` muss die-Methode mit dem Befehl Abrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Andernfalls kann das `ErrorInfo` Objekt versehentlich verwendet werden, wenn eine andere Partei einen Fehler generiert, ohne eine eigene Partei bereitzustellen `ErrorInfo` .

- Alle Methoden, die einen Fehler erzeugen, `HRESULT` werden empfohlen, die-Methode aufzurufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> , um umfangreiche Fehlerinformationen bereitzustellen. Wenn die zurückgegebene `HRESULT` ein spezieller `FACILITY_ITF` Fehler ist, muss die-Methode ein richtiges-Objekt bereitstellen `ErrorInfo` . Wenn der zurückgegebene Fehler ein Standardsystem Fehler ist (z <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> . b.,,, <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> usw.), ist es zulässig, den Fehlercode zurückzugeben, ohne die-Methode explizit aufrufen zu müssen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> . Wenn Sie einen Fehler (einschließlich Systemfehlern) als eine Verteidigungsstrategie für die Verteidigungsstrategie anwenden, müssen Sie `HRESULT` immer die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Methode anrufen, entweder mit einer `ErrorInfo` ausführlichere Beschreibung des Fehlers oder `null` .

- Alle Funktionen, die einen von einem anderen-Befehl zurückgegebenen Fehler zurückgeben, müssen die Informationen übergeben, die vom fehlgeschlagenen-Befehl in empfangen wurden, `HRESULT` ohne das-Objekt zu ändern `ErrorInfo` .

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- ["Informationen" (Komponenten Automatisierung)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [ISupportErrorInfo-Schnittstelle](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
