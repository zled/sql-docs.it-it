---
title: Record corrente e le dimensioni dell'oggetto Recordset | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- record location [ADO]
- current record [ADO]
ms.assetid: e63ff331-8655-4be7-82c6-e6cd6cc9d16d
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: d6b4bab8061c7343d303dcd322ae2ae7fef2fd42
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="current-record-and-size-of-recordset"></a>Record corrente e le dimensioni di Recordset
In questa sezione viene descritto come individuare la posizione corrente del cursore nell'esempio **Recordset** in [esempio di codice JScript per restituire un Recordset](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md).  
  
## <a name="current-record"></a>Record corrente  
 Il record corrente nel set di dati corrisponde a che la posizione del cursore di cui punta il **Recordset** oggetto. Quando un **Recordset** oggetto viene restituito dall'origine dati come risultato della chiamata **Open**, **Command. Execute**, o **Connection**  (inclusi **Connection.NamedCommand** e **Connection.StoredProcedure**), il cursore viene impostato in modo da indicare il primo record. Nel set di dati di esempio, il record corrente è "Frutta la organici pere" elemento.  
  
## <a name="size-of-recordset"></a>Dimensioni dell'oggetto Recordset  
 Per trovare la dimensione di un **Recordset** oggetto, ottenere il valore della **Recordset.RecordCount** proprietà. Questo valore è un valore long integer che indica il numero di record di **Recordset**. Se il set di dati viene restituita dal Provider OLE DB per Microsoft SQL Server, questo valore restituisce il numero di righe restituite. Lettura di **RecordCount** proprietà in una classe chiusa **Recordset** causa un errore.  
  
 Se non è possibile determinare il numero di record, il valore della proprietà è -1.  
  
 Il valore di **RecordCount** proprietà dipende anche dalle funzionalità del provider e il tipo di cursore utilizzato. Per un cursore forward-only, il valore è -1. Per un cursore statico o keyset, il valore è il numero effettivo di record restituiti nella **Recordset** oggetto. Per un cursore dinamico, il valore è -1 o il numero effettivo di record, a seconda dell'origine dati.  
  
 Un cursore che supporta **Recordcount** deve lavoro più complessa e pertanto richiede maggiore potenza di elaborazione, di un cursore non supporta **Recordcount**. Se è necessario conoscere il numero di record, utilizzando il tipo di cursore diverso potrebbe migliorare le prestazioni dell'applicazione, soprattutto se è necessario gestire un ampio set di dati.  
  
 In alcuni casi, un cursore o il provider non è in grado di determinare il **RecordCount** valore senza prima recuperare tutti i record dall'origine dati. Per garantire l'accuratezza del conteggio, chiamare il **Recordset**. **MoveLast** metodo prima di chiamare **Recordset.RecordCount**.  
  
 L'esempio **Recordset** oggetto ottenuto utilizzando il [esempio di codice JScript](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md) utilizza un cursore forward-only, pertanto la chiamata di **RecordCount** su questo oggetto comporta sempre -1. Se si modifica la riga di codice che chiama il **Recordset**. **Aprire** metodo come illustrato nell'esempio seguente, il **RecordCount** proprietà restituirà il numero effettivo di record recuperati.  
  
```  
oRs.Open sSQL, sCnStr, adOpenStatic, adLockOptimistic, adCmdText   
```  
  
 In questo modo statico cursori con il [il Provider Microsoft OLE DB per SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) supporta **RecordCount**. In questo esempio, sono disponibili cinque record e quindi **RecordCount** deve produrre il valore di 5.  
  
 In questa sezione contiene l'argomento seguente.  
  
 [Limiti di un recordset](../../../ado/guide/data/boundaries-of-a-recordset.md)
