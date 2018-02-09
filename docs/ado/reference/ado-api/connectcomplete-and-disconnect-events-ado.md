---
title: ConnectComplete e disconnettere eventi (ADO) | Documenti Microsoft
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
- Disconnect
- Connection::ConnectComplete
- ConnectComplete
- Connection::Disconnect
helpviewer_keywords:
- Disconnect event [ADO]
- ConnectComplete event [ADO]
ms.assetid: 568f5252-d069-4d99-a01b-2ada87ad1304
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7ca521c0e850dd7fdacee6cd594b5c9f23a289d3
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="connectcomplete-and-disconnect-events-ado"></a>ConnectComplete e disconnettere eventi (ADO)
Il **ConnectComplete** eventi viene chiamato dopo l'avvio di una connessione. Il **Disconnect** eventi viene chiamato dopo la fine di una connessione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ConnectComplete pError, adStatus, pConnection  
Disconnect adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Parametri  
 *pError*  
 Un [errore](../../../ado/reference/ado-api/error-object.md) oggetto. Viene descritto l'errore che si è verificato se il valore di *adStatus* è **adStatusErrorsOccurred**; in caso contrario non è impostata.  
  
 *adStatus*  
 Un [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) valore indica che è sempre **adStatusOK**.  
  
 Quando **ConnectComplete** viene chiamato, questo parametro è impostato su **adStatusCancel** se un **WillConnect** evento ha richiesto l'annullamento della connessione in sospeso.  
  
 Prima che venga restituito degli eventi, impostare questo parametro su **adStatusUnwantedEvent** per impedire notifiche successive. Tuttavia, chiudere e riaprire il [connessione](../../../ado/reference/ado-api/connection-object-ado.md) fa sì che questi eventi si verifichi nuovamente.  
  
 *pConnection*  
 Il **connessione** dell'oggetto per cui si applica questo evento.  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di modello di eventi ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Riepilogo dei gestori eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)
