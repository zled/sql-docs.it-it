---
title: Metodi di spostamento in un Recordset | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MoveNext method [ADO]
- MoveLast method [ADO]
- MoveFirst method [ADO]
- Recordset object [ADO], moving
- MovePrevious method [ADO]
ms.assetid: 9f8cf1b2-3def-453f-a0ff-4646c5f15262
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c3e3f666fd96a1b00d78ba364a8df062fa3f6397
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="more-ways-to-move-in-a-recordset"></a>Metodi di spostamento in un Recordset
I quattro metodi seguenti consentono di spostarsi all'interno o lo scorrimento, il **Recordset**: [MoveFirst, MoveLast, MoveNext e MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md). (Alcuni di questi metodi sono disponibili sui cursori forward-only).  
  
 **MoveFirst** cambia la posizione corrente per il primo record di **Recordset**. **MoveLast** il record corrente posizionare all'ultima modifica il record nel **Recordset**. Per utilizzare **MoveFirst** o **MoveLast**, **Recordset** oggetto deve supportare lo spostamento del cursore con le versioni precedenti o i segnalibri; in caso contrario, la chiamata al metodo genererà un errore.  
  
 **MoveNext** sposta il record corrente posizionare un'unica posizione in avanti. Se si utilizza l'ultimo record quando si chiama **MoveNext**, **EOF** verrà impostato su **True**. **MovePrevious** si sposta un'unica posizione con le versioni precedenti di posizionare il record corrente. Se si utilizza il primo record quando si chiama **MovePrevious**, **BOF** verrà impostato su **True**. È consigliabile controllare il **EOF** e **BOF** proprietà quando si usano questi metodi e a spostare il cursore in un posizione valida del record corrente se si sposta da delle estremità del **Recordset**, come illustrato di seguito:  
  
```  
. . .  
oRs.MoveNext  
If oRs.EOF Then oRs.MoveLast  
. . .   
```  
  
 O, nel caso del **MovePrevious** metodo:  
  
```  
. . .   
oRs.MovePrevious  
If oRs.BOF Then oRs.MoveFirst  
. . .  
```  
  
 Nei casi in cui il **Recordset** filtrate o ordinati e i dati del record corrente viene modificati, può anche cambiare la posizione. In questi casi il **MoveNext** metodo funziona normalmente, ma tenere presente che la posizione viene spostato un record in avanti rispetto la nuova posizione, non il precedente. Modificando, ad esempio, i dati del record corrente, in modo che il record viene spostato alla fine della ordinato **Recordset**, significa che la chiamata **MoveNext** comporta l'impostazione del record corrente il posizione dopo l'ultimo record di **Recordset** (**EOF** = **True**).  
  
 Il comportamento di vari metodi di spostamento di **Recordset** oggetto dipende, in alcuni casi, i dati all'interno di **Recordset**. Nuovi record aggiunti per il **Recordset** vengono inizialmente aggiunti in un ordine specifico viene definito dall'origine dati o in modo esplicito ai dati nel nuovo record. Ad esempio, se un ordinamento o un join viene eseguito all'interno della query che popola la **Recordset**, verrà inserito il nuovo record nella posizione appropriata all'interno di **Recordset**. Se l'ordinamento non viene specificato esplicitamente durante la creazione di **Recordset**, le modifiche apportate nell'implementazione dell'origine dati potrebbero causare l'ordinamento delle righe restituite modificare inavvertitamente. In aggiunta, l'ordinamento, filtro e modifica delle funzioni del **Recordset** può influire sull'ordine e probabilmente saranno visibili le righe nel recordset.  
  
 Pertanto, **MoveNext**, **MovePrevious**, **MoveFirst**, **MoveLast**, e **spostare** sono tutti distinzione ad altre operazioni eseguite nella stessa **Recordset**. ADO tenterà sempre di mantenere la posizione corrente fino a quando non si sposta in modo esplicito, ma in alcuni casi, eventuali modifiche rendono difficile da comprendere gli effetti dello spostamento successive. Ad esempio, se si chiama **MoveFirst** alla posizione della prima riga di un controllo ordinato **Recordset** e si modifica l'ordinamento da crescente a decrescente, che trovano ancora nella stessa riga, ma ora è l'ultima riga nel **Recordset**. **MoveFirst** verrà visualizzata una riga diversa (nuova prima riga).  
  
 Un altro esempio, se si è posizionati in una particolare riga al centro di un **Recordset** e si chiama **eliminare** e quindi chiamare **MoveNext**, trova ora nel record immediatamente dopo il record eliminato. Ma la chiamata **MovePrevious** il record precedente quello eliminato il record corrente, perché il record eliminato non viene più considerato in appartenenza attiva del **Recordset**.  
  
 È particolarmente difficile definire semantica di spostamento coerente in tutti i provider di metodi di spostamento relativo al record corrente, ovvero **MovePrevious**, **MoveNext**, e **spostare** , in caso di modifica dei dati del record corrente. Ad esempio, se si sta usando un ordinati, filtrati **Recordset**e si modificano i dati del record corrente in modo che precedano tutti gli altri record, ma i dati modificati anche non corrispondano al filtro, non è chiaro dove un **MoveNext** dell'esecuzione. La conclusione più sicura è tale spostamento relativo all'interno di un **Recordset** è più rischioso rispetto al movimento assoluto (ad esempio usando **MoveFirst** o **MoveLast**) quando i dati sono la modifica durante la modifica, i record aggiunti o eliminati. Ordinamento e filtro dovrebbe essere basate su una chiave primaria o un ID, poiché questo tipo di valore non deve modificare.
