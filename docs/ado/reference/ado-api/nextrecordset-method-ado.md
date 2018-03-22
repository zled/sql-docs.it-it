---
title: Firme (ADO) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: article
apitype: COM
f1_keywords:
- NextRecordset
- Recordset15::NextRecordset
- Recordset15::raw_NextRecordset
helpviewer_keywords:
- NextRecordset method [ADO]
ms.assetid: ab1fa449-a695-4987-b1ee-bc68f89418dd
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b4e0e38fc9c01a65916d7979fddfae929d43acf1
ms.sourcegitcommit: ccb05cb5a4cccaf7ffa9e85a4684fa583bab914e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2018
---
# <a name="nextrecordset-method-ado"></a>Firme (ADO)
Cancella il contenuto del [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) dell'oggetto e restituisce il successivo **Recordset** anticipando attraverso una serie di comandi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Set recordset2 = recordset1.NextRecordset(RecordsAffected )  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **Recordset** oggetto. Nel modello di sintassi, *recordset1* e *recordset2* può essere lo stesso **Recordset** oggetto, oppure è possibile utilizzare oggetti separati. Quando si utilizza separato **Recordset** oggetti, la reimpostazione di **ActiveConnection** proprietà originale **Recordset** (*recordset1*) Dopo aver **NextRecordset** è stato chiamato verrà generato un errore.  
  
#### <a name="parameters"></a>Parametri  
 *RecordsAffected*  
 Facoltativa. Oggetto **lungo** variabile in cui il provider restituisce il numero di record interessati dall'operazione corrente.  
  
> [!NOTE]
>  Questo parametro restituisce solo il numero di record interessati da un'operazione. non viene restituito un conteggio di record da un'istruzione select utilizzata per generare il **Recordset**.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **NextRecordset** per restituire i risultati del comando successivo in un'istruzione composta comando o di una stored procedure che restituisce più risultati. Se si apre un **Recordset** oggetto basato su un'istruzione composta comando (ad esempio, "selezionare \* da table1; Selezionare \* da table2 ") utilizzando il [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) metodo su un [comando](../../../ado/reference/ado-api/command-object-ado.md) o [aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md) metodo su un **Recordset**, ADO esegue solo il primo comando e restituisce i risultati in *recordset*. Per accedere ai risultati dei comandi successivi nell'istruzione, chiamare il **NextRecordset** metodo.  
  
 Fino a quando sono presenti altri risultati e **Recordset** contenente le istruzioni composte è disconnessa o sottoposto a marshalling attraverso i limiti di processo, non il **NextRecordset** metodo continuerà a restituire **Recordset** oggetti. Se un comando che restituiscono righe viene eseguito correttamente, ma non restituisce alcun record, l'oggetto restituito **Recordset** oggetto è aperto ma vuoto. Test per questo case verificando che il [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) e [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) siano entrambe **True**. Se un comando non restituiscono righe viene eseguito correttamente, l'oggetto restituito **Recordset** oggetto verrà chiuso, è possibile verificare il [stato](../../../ado/reference/ado-api/state-property-ado.md) proprietà di **Recordset**. Quando non sono presenti più risultati, *recordset* verrà impostato su *nulla*.  
  
 Il **NextRecordset** metodo non è disponibile un disconnesso **Recordset** oggetto, in cui [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) è stata impostata su **nulla**(in Microsoft Visual Basic) o NULL (in altri linguaggi).  
  
 Se una modifica è in corso in modalità di aggiornamento immediato, la chiamata di **NextRecordset** metodo genera un errore, chiamare il [aggiornare](../../../ado/reference/ado-api/update-method.md) o [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) metodo prima.  
  
 Per passare i parametri per più di un comando nell'istruzione composta compilando il [parametri](../../../ado/reference/ado-api/parameters-collection-ado.md) insieme, oppure passando una matrice con l'originale **aprire** o **Execute** chiamata, i parametri devono essere nello stesso ordine nella raccolta o nella matrice dei rispettivi comandi nella serie di comandi. È necessario terminare la lettura di tutti i risultati prima di leggere i valori dei parametri di output.  
  
 Il provider OLE DB determina quando viene eseguito ogni comando in un'istruzione composta. Il [il Provider Microsoft OLE DB per SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), ad esempio, esegue tutti i comandi in un batch dopo aver ricevuto l'istruzione composta. Il valore risultante **recordset** vengono semplicemente restituiti quando si chiama **NextRecordset**.  
  
 Tuttavia, altri provider possono eseguire il comando successivo in un'istruzione solo dopo la chiamata di NextRecordset. Per questi provider, se si chiude in modo esplicito il **Recordset** dell'oggetto prima di scorrere l'intera istruzione di comando, i comandi rimanenti non viene mai eseguito ADO.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di firme (VB)](../../../ado/reference/ado-api/nextrecordset-method-example-vb.md)   
 [Esempio di metodo NextRecordset (VC++)](../../../ado/reference/ado-api/nextrecordset-method-example-vc.md)   
