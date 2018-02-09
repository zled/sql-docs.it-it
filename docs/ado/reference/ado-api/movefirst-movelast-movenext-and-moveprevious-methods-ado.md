---
title: MoveFirst, MoveLast, MoveNext e MovePrevious metodi (ADO) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
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
- Recordset15::MoveLast
- Recordset15::MoveNext
- Recordset15::raw_MoveNext
- Recordset15::raw_MovePrevious
- Recordset15::MoveFirst
- Recordset15::raw_MoveLast
- Recordset15::MovePrevious
- Recordset15::raw_MoveFirst
helpviewer_keywords:
- MoveNext method [ADO]
- MoveLast method [ADO]
- MoveFirst method [ADO]
- MovePrevious method [ADO]
ms.assetid: a61a01a7-5b33-4150-9126-21dfa63654cb
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e6f36322b7e966d48d8ebd7094154646ee51eb20
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="movefirst-movelast-movenext-and-moveprevious-methods-ado"></a>MoveFirst, MoveLast, MoveNext e MovePrevious metodi (ADO)
Sposta il primo, ultimo, successivo o precedente record in un oggetto specificato [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto e imposta tale record come record corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
recordset.{MoveFirst | MoveLast | MoveNext | MovePrevious}  
```  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **MoveFirst** metodo per spostare la posizione corrente del primo record di **Recordset**.  
  
 Utilizzare il **MoveLast** per spostare la posizione corrente all'ultimo record nel **Recordset**. Il **Recordset** oggetto deve supportare lo spostamento del cursore con le versioni precedenti o i segnalibri; in caso contrario, la chiamata al metodo genererà un errore.  
  
 Una chiamata a **MoveFirst** o **MoveLast** quando il **Recordset** è vuoto (entrambi **BOF** e **EOF** sono True) genera un errore.  
  
 Utilizzare il **MoveNext** per spostare il record corrente posizionare un record di inoltro (nella parte inferiore del **Recordset**). Se l'ultimo record è il record corrente e si chiama il **MoveNext** (metodo), ADO imposta il record corrente alla posizione successiva all'ultimo record nel **Recordset** ([EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) è **True**). Tentativo di spostare in avanti quando il **EOF** proprietà è già **True** genera un errore.  
  
 In ADO 2.5 e versioni successiva, quando il **Recordset** sono stati filtrati o ordinati e i dati del record corrente viene modificati, la chiamata di **MoveNext** metodo sposta i record di cursore due inoltrare dal record corrente . Infatti, quando viene modificato il record corrente, il record successivo diventa il nuovo record corrente. La chiamata **MoveNext** dopo la modifica si sposta il cursore al record successivo da nuovo record corrente. Ciò è diverso da quello in ADO 2.1 e versioni precedenti. In queste versioni precedenti, la modifica dei dati di un record corrente nella ordinata o filtrata **Recordset** non modifica la posizione del record corrente, e **MoveNext** sposta il cursore al record successivo immediatamente dopo il record corrente.  
  
 Utilizzare il **MovePrevious** per spostare il record corrente posizionare un record con le versioni precedenti (verso l'alto il **Recordset**). Il **Recordset** oggetto deve supportare lo spostamento del cursore con le versioni precedenti o i segnalibri; in caso contrario, la chiamata al metodo genererà un errore. Se il primo record è il record corrente e si chiama il **MovePrevious** (metodo), ADO imposta il record corrente nella posizione precedente al primo record di **Recordset** ([BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)è **True**). Tenta di spostarsi con le versioni precedenti quando il **BOF** proprietà è già **True** genera un errore. Se il **Recordset** oggetto non supporta i segnalibri o lo spostamento del cursore con le versioni precedenti, il **MovePrevious** metodo genererà un errore.  
  
 Se il **Recordset** è solo in avanti e si desidera supportare lo scorrimento in avanti e indietro, è possibile utilizzare il [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) proprietà per creare una cache di record che supporterà lo spostamento del cursore con le versioni precedenti tramite il [spostare](../../../ado/reference/ado-api/move-method-ado.md) metodo. Poiché i record memorizzati nella cache vengono caricati in memoria, è consigliabile evitare la memorizzazione nella cache più record del necessario. È possibile chiamare il **MoveFirst** metodo forward-only **Recordset** oggetto; tale operazione può causare il provider eseguire nuovamente il comando che ha generato il **Recordset** oggetto .  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [MoveFirst, MoveLast, MoveNext e MovePrevious metodi esempio (VB)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-example-vb.md)   
 [MoveFirst, MoveLast, MoveNext e MovePrevious metodi esempio (VBScript)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-example-vbscript.md)   
 [MoveFirst, MoveLast, MoveNext e MovePrevious metodi esempio (VC + +)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-example-vc.md)   
 [Metodo Move (ADO)](../../../ado/reference/ado-api/move-method-ado.md)   
 [MoveFirst, MoveLast, MoveNext e MovePrevious metodi (RDS)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)   
 [Metodo MoveRecord (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)
