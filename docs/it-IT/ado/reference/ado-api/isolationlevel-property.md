---
title: Proprietà IsolationLevel | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::IsolationLevel
helpviewer_keywords:
- IsolationLevel property
ms.assetid: ea84e4b2-fbf2-4eef-b9ce-796b22e21800
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 326f145da9c2e80b7f4765a0c4bae1a657f4ee25
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="isolationlevel-property"></a>Proprietà IsolationLevel
Indica il livello di isolamento per una [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un [IsolationLevelEnum](../../../ado/reference/ado-api/isolationlevelenum.md) valore. Il valore predefinito è **adXactReadCommitted**.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **IsolationLevel** proprietà per impostare il livello di isolamento un **connessione** oggetto. L'impostazione non ha effetto fino alla chiamata successiva di [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) metodo. Se il livello di isolamento richiesto non è disponibile, il provider può restituire il successivo livello più alto di isolamento senza aggiornare il **IsolationLevel** proprietà.  
  
 Il **IsolationLevel** proprietà è di lettura/scrittura.  
  
> [!NOTE]
>  **Utilizzo del servizio dati remoti** quando viene utilizzata su un lato client **connessione** oggetto, il **IsolationLevel** proprietà può essere impostata solo su **adXactUnspecified**. Poiché gli utenti utilizzano disconnesso **Recordset** oggetti in una cache sul lato client, è possibile riscontrare problemi. Ad esempio, quando due utenti diversi tentano di aggiornare lo stesso record, Remote Data Service semplicemente consente all'utente che ha aggiornato il record prima di "win". Richiesta di aggiornamento del secondo utente avrà esito negativo con un errore.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio IsolationLevel e Mode proprietà (Visual Basic)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vb.md)   
 [Esempio IsolationLevel e Mode proprietà (VC + +)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vc.md)   
