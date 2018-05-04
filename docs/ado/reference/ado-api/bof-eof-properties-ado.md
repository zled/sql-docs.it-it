---
title: BOF, proprietà EOF (ADO) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::BOF
- Recordset15::EOF
helpviewer_keywords:
- EOF property [ADO]
- BOF property [ADO]
ms.assetid: 36c31ab2-f3b6-4281-89b6-db7e04e38fd2
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 369d6a3b4d069ed67ccc4c4d217aa257c20c79b1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="bof-eof-properties-ado"></a>BOF, proprietà EOF (ADO)
-   **BOF** indica che la posizione del record corrente è precedente al primo record in un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto.  
  
-   **EOF** indica che la posizione del record corrente è successiva all'ultimo record in un **Recordset** oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Il **BOF** e **EOF** restituiscono **booleano** valori.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **BOF** e **EOF** le proprietà per determinare se un **Recordset** oggetto contiene record o se sono stati superati i limiti di un **Recordset**  dell'oggetto quando si sposta da un record a altro.  
  
 Il **BOF** restituisce proprietà **True** (-1) se la posizione del record corrente è precedente al primo record e **False** (0) se la posizione del record corrente è il o dopo il primo record.  
  
 Il **EOF** restituisce proprietà **True** se la posizione del record corrente è successiva all'ultimo record e **False** se la posizione del record corrente è il o prima dell'ultimo record.  
  
 Se il valore di **BOF** o **EOF** proprietà **True**, nessun record corrente.  
  
 Se si apre un **Recordset** oggetto che non contiene record, il **BOF** e **EOF** sono impostate su **True** (vedere il [ RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md) proprietà per ulteriori informazioni su questo stato di un **Recordset**). Quando si apre un **Recordset** oggetto che contiene almeno un record, il primo record è il record corrente e **BOF** e **EOF** sono proprietà **False** .  
  
 Se si elimina l'ultimo record rimanente di **Recordset** oggetto, il **BOF** e **EOF** proprietà restino **False** finché non si tentativo di riposizionare il record corrente.  
  
 Questa tabella mostra che **spostare** metodi sono consentiti con diverse combinazioni del **BOF** e **EOF** proprietà.  
  
||MoveFirst,<br /><br /> MoveLast|MovePrevious,<br /><br /> Spostare < 0|Spostare 0|MoveNext,<br /><br /> Spostare > 0|  
|------|-----------------------------|---------------------------------|------------|-----------------------------|  
|**BOF**=**True**, **EOF**=**False**|Allowed|Errore|Errore|Allowed|  
|**BOF**=**False**, **EOF**=**True**|Allowed|Allowed|Errore|Errore|  
|Entrambi **True**|Errore|Errore|Errore|Errore|  
|Entrambi **False**|Allowed|Allowed|Allowed|Allowed|  
  
 Consentendo un **spostare** (metodo) non garantisce che il metodo individuerà correttamente un record; significa solo che la chiamata a specificato **spostare** metodo non genererà un errore.  
  
 Nella tabella seguente mostra cosa accade al **BOF** e **EOF** le impostazioni delle proprietà quando si chiama vari **spostare** metodi ma non sono possibile individuare correttamente un record.  
  
||BOF|EOF|  
|------|---------|---------|  
|**MoveFirst**, **MoveLast**|Impostare su **True**|Impostare su **True**|  
|**Spostare** 0|Nessuna modifica|Nessuna modifica|  
|**MovePrevious**, **spostare** < 0|Impostare su **True**|Nessuna modifica|  
|**MoveNext**, **spostare** > 0|Nessuna modifica|Impostare su **True**|  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà di segnalibro (VB), EOF e BOF](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vb.md)   
 [Esempio di proprietà di segnalibro (VC + +), EOF e BOF](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vc.md)   
