---
title: IsolationLevelEnum | Documenti Microsoft
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
- IsolationLevelEnum
helpviewer_keywords:
- IsolationLevelEnum enumeration [ADO]
ms.assetid: 8e17a7bc-b8a3-4ae2-b6c9-ce088ad31fdf
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1f6f18a4cd10c70369d2e0aceb226310d7a5f4ae
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="isolationlevelenum"></a>IsolationLevelEnum
Specifica il livello di isolamento delle transazioni per un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adXactUnspecified**|-1|Indica che il provider utilizza un livello di isolamento diverso da quello specificato, ma che non è possibile determinare il livello.|  
|**adXactChaos**|16|Indica che le modifiche da più isolate transazioni in sospeso non può essere sovrascritto.|  
|**adXactBrowse**|256|Indica che da una transazione è possibile visualizzare le modifiche non salvate in altre transazioni.|  
|**adXactReadUncommitted**|256|Uguale a **adXactBrowse**.|  
|**adXactCursorStability**|4096|Indica che da una transazione è possibile visualizzare le modifiche in altre transazioni solo dopo il commit.|  
|**adXactReadCommitted**|4096|Uguale a **adXactCursorStability**.|  
|**adXactRepeatableRead**|65536|Indica che da una transazione non è possibile visualizzare le modifiche apportate in altre transazioni, ma tale ripetizione di query è stato possibile recuperare nuovi **Recordset** oggetti.|  
|**adXactIsolated**|1048576|Indica che le transazioni vengono eseguite in isolamento dalle altre transazioni.|  
|**adXactSerializable**|1048576|Uguale a **adXactIsolated**.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Pacchetto: **com.ms. wfc.**  
  
|Costante|  
|--------------|  
|AdoEnums.IsolationLevel.UNSPECIFIED|  
|AdoEnums.IsolationLevel.CHAOS|  
|AdoEnums.IsolationLevel.BROWSE|  
|AdoEnums.IsolationLevel.READUNCOMMITTED|  
|AdoEnums.IsolationLevel.CURSORSTABILITY|  
|AdoEnums.IsolationLevel.READCOMMITTED|  
|AdoEnums.IsolationLevel.REPEATABLEREAD|  
|AdoEnums.IsolationLevel.ISOLATED|  
|AdoEnums.IsolationLevel.SERIALIZABLE|  
  
## <a name="applies-to"></a>Si applica a  
 [Proprietà IsolationLevel](../../../ado/reference/ado-api/isolationlevel-property.md)

