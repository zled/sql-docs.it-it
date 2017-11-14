---
title: "Proprietà AbsolutePage (ADO) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::AbsolutePage
helpviewer_keywords:
- AbsolutePage property [ADO]
ms.assetid: ddb58a35-ec3a-423c-a504-3c65e62c23d4
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 54d429f0920da7f68bcea54b72077b96d6d198f7
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="absolutepage-property-ado"></a>Proprietà AbsolutePage (ADO)
Indica la pagina in cui risiede il record corrente.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Per il codice a 32 bit, imposta o restituisce un **lungo** valore compreso tra 1 e il numero di pagine nel [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto ([PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)), oppure restituisce uno del [PositionEnum ](../../../ado/reference/ado-api/positionenum.md) valori.  
  
 Per il codice a 64 bit, utilizzare un tipo di dati che fornisce per l'archiviazione di un valore a 64 bit. Ad esempio, è possibile utilizzare **lungo** o un altro valore che può essere di lunghezza a 64 bit, ad esempio DBORDINAL. Non utilizzare **PositionEnum** valori perché sono limitati alla lunghezza di 32 bit.  
  
## <a name="remarks"></a>Osservazioni  
 Questa proprietà può essere utilizzata per identificare il numero di pagina in cui si trova il record corrente. Usa il [PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md) proprietà per suddividere logicamente il numero totale di righe del **Recordset** oggetto in una serie di pagine, ognuna delle quali è il numero di record è uguale a **PageSize** (ad eccezione dell'ultima pagina, che può contenere un numero minore di record). Il provider deve supportare le funzionalità appropriate per questa proprietà sia disponibile.  
  
-   Per ottenere o impostare il **AbsolutePage** proprietà, viene utilizzato ADO la [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) proprietà e [PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md) insieme come segue:  
  
-   Per ottenere il **AbsolutePage**, ADO recupera innanzitutto il **AbsolutePosition**e quindi diviso per il **PageSize**.  
  
-   Per impostare il **AbsolutePage**, ADO sposta la **AbsolutePosition** come indicato di seguito: vengono moltiplicati i **PageSize** dalla nuova **AbsolutePage** il valore e quindi aggiunge 1 al valore. Di conseguenza, la posizione corrente di **Recordset** dopo aver impostato correttamente **AbsolutePage** è il primo record in tale pagina.  
  
 Ad esempio il **AbsolutePosition** proprietà, **AbsolutePage** è basata su 1 ed è uguale a 1 quando il record corrente è il primo record di **Recordset**. Impostare questa proprietà per passare al primo record di una pagina specifica. Ottenere il numero totale di pagine dal **PageCount** proprietà.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà PageSize (VB), PageCount e AbsolutePage](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [Esempio di proprietà PageSize (VC + +), AbsolutePage e PageCount](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [Proprietà AbsolutePosition (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)   
 [Proprietà PageCount (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)   
 [Proprietà PageSize (ADO)](../../../ado/reference/ado-api/pagesize-property-ado.md)

