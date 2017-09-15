---
title: Move (metodo) (ADO) | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::Move
- Recordset15::raw_Move
helpviewer_keywords:
- Move method [ADO]
ms.assetid: 13fe9381-d00b-4f4a-9162-83c3f21b3837
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 69f3ce38f87be4670bcb08f80db076ce88d37212
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="move-method-ado"></a>Metodo Move (ADO)
Sposta la posizione del record corrente in un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
recordset.Move NumRecords, Start  
```  
  
#### <a name="parameters"></a>Parametri  
 *NumRecords*  
 Con un segno **lungo** espressione che specifica il numero di record che si sposta la posizione del record corrente.  
  
 *Inizio*  
 Facoltativa. Oggetto **stringa** valore o **Variant** che restituisca un segnalibro. È inoltre possibile utilizzare un [BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md) valore.  
  
## <a name="remarks"></a>Osservazioni  
 Il **spostare** metodo è supportato in tutti **Recordset** oggetti.  
  
 Se il *NumRecords* argomento è maggiore di zero, la posizione del record corrente viene spostata in avanti (verso la fine del **Recordset**). Se *NumRecords* è minore di zero, la posizione corrente si sposta all'indietro (verso l'inizio del **Recordset**).  
  
 Se il **spostare** chiamata Sposta la posizione corrente a un punto prima del primo record, ADO imposta il record corrente nella posizione precedente al primo record del recordset ([BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) è **True **). Tenta di spostarsi con le versioni precedenti quando il **BOF** proprietà è già **True** genera un errore.  
  
 Se il **spostare** chiamata Sposta la posizione corrente a un punto successivo all'ultimo record, ADO imposta il record corrente alla posizione successiva all'ultimo record del recordset ([EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) è **True **). Tentativo di spostare in avanti quando il **EOF** proprietà è già **True** genera un errore.  
  
 La chiamata di **spostare** metodo da un oggetto vuoto **Recordset** oggetto genera un errore.  
  
 Se si passa il *avviare* argomento, lo spostamento è relativo al record con il segnalibro, supponendo che il **Recordset** oggetto supporta i segnalibri. Se non specificato, lo spostamento è relativo al record corrente.  
  
 Se si utilizza il [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) proprietà da memorizzare localmente i record dal provider, passando un *NumRecords* argomento che sposta la posizione corrente all'esterno del gruppo corrente di record memorizzati nella cache ADO viene forzato a recuperare un nuovo gruppo di record, a partire dal record di destinazione. Il **CacheSize** proprietà determina le dimensioni del gruppo appena recuperato e il record di destinazione è il primo record recuperato.  
  
 Se il **Recordset** oggetto è forward-only, è comunque possibile passare un *NumRecords* argomento è minore di zero, purché la destinazione all'interno del set corrente di record memorizzati nella cache. Se il **spostare** chiamata Sposta la posizione corrente a un record prima del primo record memorizzati nella cache, si verificherà un errore. Di conseguenza, è possibile utilizzare una cache di record che supporta lo scorrimento bidirezionale su un provider che supporta lo scorrimento solo in avanti. Poiché i record memorizzati nella cache vengono caricati in memoria, è consigliabile evitare la memorizzazione nella cache più record di quelli necessari. Anche se forward-only **Recordset** supporta l'oggetto con le versioni precedenti consente di spostare in questo modo, la chiamata di [MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) metodo su qualsiasi forward-only **Recordset** oggetto verrà comunque Genera un errore.  
  
> [!NOTE]
>  Supporto per lo spostamento all'indietro nella forward-only **Recordset** non è prevedibile, a seconda del provider. Se il record corrente è stato posizionato dopo l'ultimo record di **Recordset**, **spostare** con le versioni precedenti non può generare la posizione corrente corretta.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio del metodo Move (VB)](../../../ado/reference/ado-api/move-method-example-vb.md)   
 [Esempio del metodo Move (VBScript)](../../../ado/reference/ado-api/move-method-example-vbscript.md)   
 [Esempio del metodo Move (VC + +)](../../../ado/reference/ado-api/move-method-example-vc.md)   
 [MoveFirst, MoveLast, MoveNext e MovePrevious metodi (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [MoveFirst, MoveLast, MoveNext e MovePrevious metodi (RDS)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)   
 [Metodo MoveRecord (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)

