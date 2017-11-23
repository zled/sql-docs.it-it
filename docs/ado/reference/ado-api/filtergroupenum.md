---
title: FilterGroupEnum | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: FilterGroupEnum
helpviewer_keywords: FilterGroupEnum enumeration [ADO]
ms.assetid: b22e725e-84bd-4286-a070-290c278c3783
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 080b0149fcfe0df39e1efbe44a87fe6243424468
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="filtergroupenum"></a>FilterGroupEnum
Specifica il gruppo di record da filtrare un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adFilterAffectedRecords**|2|I filtri per visualizzare solo i record interessati dall'ultima [eliminare](../../../ado/reference/ado-api/delete-method-ado-recordset.md), [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), o [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) chiamare.|  
|**adFilterConflictingRecords**|5|Filtri per la visualizzazione di record che non è l'ultimo aggiornamento batch.|  
|**adFilterFetchedRecords**|3|I filtri per visualizzare i record nella cache corrente, vale a dire i risultati dell'ultima chiamata per recuperare i record dal database.|  
|**adFilterNone**|0|Rimuove il filtro corrente e ripristina tutti i record per la visualizzazione.|  
|**adFilterPendingRecords**|1|I filtri per visualizzare solo i record che sono stati modificati ma non sono ancora stati inviati al server. Applicabile solo per la modalità di aggiornamento batch.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Pacchetto: **com.ms. wfc.**  
  
|Costante|  
|--------------|  
|AdoEnums.FilterGroup.AFFECTEDRECORDS|  
|AdoEnums.FilterGroup.CONFLICTINGRECORDS|  
|AdoEnums.FilterGroup.FETCHEDRECORDS|  
|AdoEnums.FilterGroup.NONE|  
|AdoEnums.FilterGroup.PENDINGRECORDS|  
  
## <a name="applies-to"></a>Si applica a  
 [Proprietà Filter](../../../ado/reference/ado-api/filter-property.md)
