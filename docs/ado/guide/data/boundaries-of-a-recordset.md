---
title: I limiti di un oggetto Recordset | Documenti Microsoft
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
helpviewer_keywords:
- EOF property [ADO], boundaries of a Recordset
- Recordset object [ADO], boundaries of a Recordset
- BOF property [ADO], boundaries of a Recordset
ms.assetid: c0dd4a0f-478d-4c5e-b5d5-7535f211d064
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 67a300e30522a5f02bb6c33409a062a3c2434643
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="boundaries-of-a-recordset"></a>Limiti di un Recordset
**Recordset** supporta il **BOF** e **EOF** proprietà per delineare rispettivamente l'inizio e alla fine del set di dati. È possibile considerare **BOF** e **EOF** come record "fantasma" posizionati all'inizio e fine il **Recordset**. Conteggio **BOF** e **EOF**, l'esempio **Recordset** avrà ora un aspetto simile al seguente:  
  
|ProductID|ProductName|UnitPrice|  
|---------------|-----------------|---------------|  
|BOF|||  
|7|Pere secca organici frutta|30.0000|  
|14|Tofu|23.2500|  
|28|Rssle rossi|45.6000|  
|51|Manjimup essiccati mele|53.0000|  
|74|Tofu a lunga conservazione|10.0000|  
|EOF|||  
  
 Quando un cursore viene spostato dopo l'ultimo record, **EOF** è impostato su **True**; in caso contrario, il relativo valore è **False**. Analogamente, quando si sposta il cursore prima del primo record, **BOF** è impostato su **True**; in caso contrario, il relativo valore è **False**. Queste proprietà vengono utilizzate per enumerare i record nel set di dati, come illustrato nel frammento di codice JScript seguente.  
  
```  
while (objRecordset.EOF != true)   
{  
   // Work on the current record.  
   ...  
   // Advance the cursor forward to the next record.  
   objRecordset.MoveNext();  
}  
or  
while (objRecordset.BOF != true)   
{  
   // Work on the current record.  
   ...  
   // Move the cursor to the previous record.  
   objRecordset.MovePrevious();  
}  
```  
  
 Se entrambi **BOF** e **EOF** sono **True**, **Recordset** oggetto è vuoto. Entrambe le proprietà saranno **False** per appena aperto, non vuoto **Recordset** oggetto. È possibile utilizzare il **BOF** e **EOF** insieme per determinare se un **Recordset** oggetto è vuoto o non, come illustrato nel frammento di codice JScript seguente.  
  
```  
if (objRecordset.EOF == true && objRecordset.BOF == true)  
{  
   WScript.Echo("we got an empty dataset.");  
}  
else  
{  
   WScript.Echo("we got a full dataset.");  
}  
```  
  
 Questo schema funziona per tutti i tipi di cursore ed è indipendente da provider sottostanti. Se si tenta di determinare il contenuto di un **Recordset** oggetto controllando se il relativo **RecordCount** valore della proprietà è zero (0) o non, è necessario adottare alcune precauzioni per utilizzare un cursore appropriato e un provider che supporta la restituzione del numero di record nel risultato.  
  
 Se si elimina l'ultimo record rimanente di **Recordset** dell'oggetto, il cursore viene lasciato in uno stato indeterminato. Il **BOF** e **EOF** proprietà restino **False** fino a quando non si tenta di riposizionare il record corrente, in base al provider. Per ulteriori informazioni, vedere [eliminazione record utilizzando il metodo Delete](../../../ado/guide/data/deleting-records-using-the-delete-method.md).
