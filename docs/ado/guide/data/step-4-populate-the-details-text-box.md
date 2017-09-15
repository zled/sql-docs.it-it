---
title: 'Passaggio 4: Popolare la casella di testo Details | Documenti Microsoft'
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb4273e2-c907-4a86-a621-3bf110088228
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 512ad22b6529adcf065cacb219d1f0acc025c306
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="step-4-populate-the-details-text-box"></a>Passaggio 4: Popolare la casella di testo Details
Per popolare la casella di testo di dettagli, creare una nuova subroutine denominata **recFields** e inserire il codice seguente:  
  
```  
Sub recFields(r As Record, l As ListBox, t As TextBox)  
    Dim f As Field  
    Dim s As Stream  
    Set s = New Stream  
    Dim str As String  
  
    For Each f In r.Fields  
        l.AddItem f.Name & ": " & f.Value  
    Next  
    t.Text = ""  
    If r!RESOURCE_CONTENTCLASS = "text/plain" Then  
        s.Open r, adModeRead, adOpenStreamFromRecord  
        str = s.ReadText(1)  
        s.Position = 0  
        If Asc(Mid(str, 1, 1)) = 63 Then '//63 = "?"  
            s.Charset = "ascii"  
            s.Type = adTypeText  
        End If  
        t.Text = s.ReadText(adReadAll)  
    End If  
End Sub  
```  
  
 Questo codice popola `lstDetails` con i campi e valori del record semplice passato a `recFields`. Se la risorsa è un file di testo, un flusso di testo viene aperto dal record di risorse. Il codice determina se il set di caratteri ASCII e copia il contenuto di flusso in `txtDetails`.  
  
## <a name="see-also"></a>Vedere anche  
 [Scenario di pubblicazione su Internet](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Passaggio 3: Popolare la casella di riepilogo di campi](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
