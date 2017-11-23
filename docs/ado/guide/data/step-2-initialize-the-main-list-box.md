---
title: 'Passaggio 2: Inizializzare la casella di riepilogo principale | Documenti Microsoft'
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1454493-1c86-46c2-ada8-d3c6fcdaf3c1
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e84bc73bd63d90b43b4192208690fe3bca272de6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="step-2-initialize-the-main-list-box"></a>Passaggio 2: Inizializzare la casella di riepilogo principale
Per dichiarare gli oggetti globali Record e Recordset, inserire il codice seguente (generale) (dichiarazioni) relativo a Form1:  
  
```  
Option Explicit  
Dim grec As Record  
Dim grs As Recordset  
```  
  
 Questo codice dichiara riferimenti a oggetti globali per Record e gli oggetti Recordset che verranno utilizzati più avanti in questo scenario.  
  
## <a name="to-connect-to-a-url-and-populate-lstmain"></a>Per connettersi a un URL e popolare lstMain  
 Inserire il codice seguente nel gestore eventi Load modulo relativo a Form1:  
  
```  
Private Sub Form_Load()  
    Set grec = New Record  
    Set grs = New Recordset  
    grec.Open "", "URL=http://servername/foldername/", , _  
        adOpenIfExists Or adCreateCollection  
    Set grs = grec.GetChildren  
    While Not grs.EOF  
        lstMain.AddItem grs(0)  
        grs.MoveNext  
    Wend  
End Sub  
```  
  
 Questo codice crea un'istanza di oggetti globali Record e Recordset. Oggetto Record `grec`, viene aperto con un URL specificato come ActiveConnection. Se non esiste, l'URL viene aperto. Se non esiste già, viene creato. Si noti che è necessario sostituire "http://servername/foldername/" con un URL valido dall'ambiente in uso.  
  
 L'oggetto Recordset, `grs`, viene aperto sugli elementi figlio del Record, `grec`. Quindi `lstMain` viene popolato con i nomi dei file delle risorse pubblicate per l'URL.  
  
## <a name="see-also"></a>Vedere anche  
 [Scenario di pubblicazione su Internet](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Passaggio 1: Configurare il progetto di Visual Basic](../../../ado/guide/data/step-1-set-up-the-visual-basic-project.md)   
 [Passaggio 3: Popolare la casella di riepilogo Fields](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
