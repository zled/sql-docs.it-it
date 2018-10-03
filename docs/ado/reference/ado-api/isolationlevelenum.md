---
title: IsolationLevelEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- IsolationLevelEnum
helpviewer_keywords:
- IsolationLevelEnum enumeration [ADO]
ms.assetid: 8e17a7bc-b8a3-4ae2-b6c9-ce088ad31fdf
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 366892f51207e7d89f643510f9becb664bb098c6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47684199"
---
# <a name="isolationlevelenum"></a>IsolationLevelEnum
Specifica il livello di isolamento delle transazioni per un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto.  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adXactUnspecified**|-1|Indica che il provider utilizza un livello di isolamento diverso rispetto a quanto specificato, ma che non è possibile determinare il livello.|  
|**adXactChaos**|16|Indica che le modifiche da transazioni più isolate in sospeso non può essere sovrascritto.|  
|**adXactBrowse**|256|Indica che da una transazione è possibile visualizzare le modifiche non sottoposte a commit in altre transazioni.|  
|**adXactReadUncommitted**|256|Uguale allo **adXactBrowse**.|  
|**adXactCursorStability**|4096|Indica che da una transazione è possibile visualizzare le modifiche apportate in altre transazioni solo dopo che sono state salvate.|  
|**adXactReadCommitted**|4096|Uguale allo **adXactCursorStability**.|  
|**adXactRepeatableRead**|65536|Indica che da una transazione non è possibile visualizzare le modifiche apportate in altre transazioni, ma tale rieseguendo la query può recuperare nuove **Recordset** oggetti.|  
|**adXactIsolated**|1048576|Indica che le transazioni vengono eseguite in isolamento rispetto alle altre transazioni.|  
|**adXactSerializable**|1048576|Uguale allo **adXactIsolated**.|  
  
## <a name="adowfc-equivalent"></a>Equivalente di ADO o WFC  
 Package: **com.ms.wfc.data**  
  
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
