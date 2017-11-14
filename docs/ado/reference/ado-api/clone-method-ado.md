---
title: Clone (metodo) (ADO) | Documenti Microsoft
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
- Recordset20::Clone
- Recordset20::raw_Clone
helpviewer_keywords:
- Clone method [ADO]
ms.assetid: ad49265f-1c05-4271-9bbf-7c00010ac18c
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9b7586bef017cd4e5f3a89586b8600abfd183f5a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="clone-method-ado"></a>Metodo Clone (ADO)
Crea un duplicato [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto da un oggetto esistente **Recordset** oggetto. Facoltativamente, specifica che il clone è di sola lettura.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Set rstDuplicate = rstOriginal.Clone (LockType)  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **Recordset** riferimento all'oggetto.  
  
#### <a name="parameters"></a>Parametri  
 *rstDuplicate*  
 Una variabile oggetto che identifica il duplicato **Recordset** oggetto da creare.  
  
 *rstOriginal*  
 Una variabile oggetto che identifica il **Recordset** oggetto da duplicare.  
  
 *Tipo di blocco*  
 Facoltativa. Oggetto [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) valore che specifica il tipo di blocco dell'originale **Recordset**, sola lettura o **Recordset**. I valori validi sono **adLockUnspecified** o **adLockReadOnly**.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **Clone** duplicato per creare più **Recordset** oggetti, specialmente se si desidera mantenere più di un record corrente in un determinato set di record. Utilizzando il **Clone** è più efficiente rispetto alla creazione e l'apertura di un nuovo metodo **Recordset** oggetto che utilizza la stessa definizione dell'originale.  
  
 Il [filtro](../../../ado/reference/ado-api/filter-property.md) proprietà dell'originale **Recordset**, se presente, non verranno applicate al clone. Impostare il **filtro** proprietà del nuovo **Recordset** per filtrare i risultati. Il modo più semplice per copiare eventuali **filtro** valore consiste nell'assegnarlo direttamente, come indicato di seguito.  
  
```  
rsNew.Filter = rsOriginal.Filter  
```  
  
 Il record corrente di un clone appena creato è impostato sul primo record.  
  
 Le modifiche apportate a uno **Recordset** oggetto sono visibili in tutti i relativi cloni indipendentemente dal tipo di cursore. Tuttavia, dopo l'esecuzione di [Requery](../../../ado/reference/ado-api/requery-method.md) sull'originale **Recordset**, i cloni non saranno sincronizzati all'originale.  
  
 Chiusura originale **Recordset** non chiudere le copie e neppure la chiusura di chiudere una copia originale o una qualsiasi delle altre copie.  
  
 È possibile duplicare solo un **Recordset** oggetto che supporta i segnalibri. I valori di segnalibro sono intercambiabili; ovvero, un riferimento di segnalibro da un **Recordset** oggetto fa riferimento allo stesso record in uno dei relativi cloni.  
  
 Alcuni **Recordset** anche si verificano eventi che vengono attivati in tutti **Recordset** cloni. Tuttavia, poiché il record corrente può variare tra clonato **recordset**, gli eventi potrebbero non essere validi per il clone. Ad esempio, se si modifica un valore di un campo, un [WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md) evento verrà generato in modificato **Recordset** e in tutti i cloni. Il *campi* parametro il **WillChangeField** evento di un duplicato **Recordset** (in cui la modifica non è stata eseguita) farà riferimento ai campi del record corrente del clone, che può essere un record diverso da quello corrente dell'originale **Recordset** in cui si è verificato durante la modifica.  
  
 Nella tabella seguente fornisce un elenco completo di tutte **Recordset** eventi. Indica se sono validi e attivate per i cloni dei recordset generati utilizzando il **Clone** metodo.  
  
|Evento|Attivato nei cloni|  
|-----------|--------------------------|  
|[EndOfRecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|No|  
|[FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|No|  
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md)|No|  
|[FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Sì|  
|[MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|No|  
|[RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Sì|  
|[RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|No|  
|[WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Sì|  
|[WillChangeRecord](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Sì|  
|[WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|No|  
|[WillMove](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|No|  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio del metodo Clone (VB)](../../../ado/reference/ado-api/clone-method-example-vb.md)   
 [Esempio del metodo Clone (VBScript)](../../../ado/reference/ado-api/clone-method-example-vbscript.md)   
 [Esempio del metodo Clone (VC + +)](../../../ado/reference/ado-api/clone-method-example-vc.md)   

