---
title: "Proprietà index | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: Recordset21::Index
helpviewer_keywords: Index property
ms.assetid: 1c79e271-21ec-41a8-8163-c5e89f0001a7
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3fa23448f5942baabf364a0b02f61324d29ec7b3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="index-property"></a>Proprietà index
Indica il nome dell'indice attualmente attivo per un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **stringa** valore, ovvero il nome dell'indice.  
  
## <a name="remarks"></a>Osservazioni  
 L'indice denominato dal **indice** proprietà deve essere già stata dichiarata nella tabella di base sottostante il **Recordset** oggetto. Ovvero, l'indice deve essere stato dichiarato a livello di codice come un ADOX [indice](../../../ado/reference/adox-api/index-object-adox.md) oggetto, oppure quando la tabella di base è stata creata.  
  
 Se l'indice non può essere impostato, si verificherà un errore di run-time. Il **indice** non può essere impostata nelle condizioni seguenti:  
  
-   All'interno di un [WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md) o **RecordsetChangeComplete** gestore dell'evento.  
  
-   Se il **Recordset** è ancora in esecuzione un'operazione (che può essere determinato mediante la [stato](../../../ado/reference/ado-api/state-property-ado.md) proprietà).  
  
-   Se è stato impostato un filtro sul **Recordset** con il [filtro](../../../ado/reference/ado-api/filter-property.md) proprietà.  
  
 Il **indice** può sempre essere impostata correttamente se il **Recordset** è chiuso, ma la **Recordset** non verrà aperto correttamente o l'indice non sarà utilizzabile se il il provider sottostante non supporta gli indici.  
  
 Se l'indice può essere impostato, è possibile modificare la posizione della riga corrente. In questo modo un aggiornamento per il [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) , proprietà e verrà generato il **WillChangeRecordset**, **RecordsetChangeComplete**, [WillMove ](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md), e [MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md) eventi.  
  
 Se l'indice può essere impostato e [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) proprietà **adLockPessimistic** o **adLockOptimistic**, quindi implicita [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) viene eseguita l'operazione. In questo modo i gruppi interessati e correnti. Qualsiasi filtro esistente viene rilasciato e la posizione di riga corrente viene modificata per la prima riga del riordinati **Recordset**.  
  
 Il **indice** proprietà viene utilizzata in combinazione con il [Seek](../../../ado/reference/ado-api/seek-method.md) metodo. Se il provider sottostante non supporta il **indice** proprietà e pertanto il **Seek** (metodo), è consigliabile utilizzare il [trovare](../../../ado/reference/ado-api/find-method-ado.md) metodo invece. Determinare se il **Recordset** oggetto supporta gli indici con il [supporta](../../../ado/reference/ado-api/supports-method.md)**(adIndex)** metodo.  
  
 L'elemento predefinito **indice** proprietà non è correlata all'oggetto dinamico [Ottimizza](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) proprietà, sebbene gestiscano entrambi gli indici.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Seek e esempio di proprietà indice (Visual Basic)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [Oggetto Index (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)   
 [Metodo Seek](../../../ado/reference/ado-api/seek-method.md)
