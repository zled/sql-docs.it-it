---
title: FilterGroupEnum | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FilterGroupEnum
helpviewer_keywords:
- FilterGroupEnum enumeration [ADO]
ms.assetid: b22e725e-84bd-4286-a070-290c278c3783
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dd0af463cf9ebc5bad28665cad32fc49fce5fb5b
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35278650"
---
# <a name="filtergroupenum"></a>FilterGroupEnum
Specifica il gruppo di record da filtrare un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adFilterAffectedRecords**|2|I filtri per visualizzare solo i record interessati dall'ultima [eliminare](../../../ado/reference/ado-api/delete-method-ado-recordset.md), [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), o [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) chiamare.|  
|**adFilterConflictingRecords**|5|Filtri per la visualizzazione di record che non è l'ultimo aggiornamento batch.|  
|**adFilterFetchedRecords**|3|I filtri per visualizzare i record nella cache corrente, vale a dire i risultati dell'ultima chiamata per recuperare i record dal database.|  
|**adFilterNone**|0|Rimuove il filtro corrente e ripristina tutti i record per la visualizzazione.|  
|**adFilterPendingRecords**|1|I filtri per visualizzare solo i record che sono stati modificati ma non sono ancora stati inviati al server. Applicabile solo per la modalità di aggiornamento batch.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.FilterGroup.AFFECTEDRECORDS|  
|AdoEnums.FilterGroup.CONFLICTINGRECORDS|  
|AdoEnums.FilterGroup.FETCHEDRECORDS|  
|AdoEnums.FilterGroup.NONE|  
|AdoEnums.FilterGroup.PENDINGRECORDS|  
  
## <a name="applies-to"></a>Si applica a  
 [Proprietà Filter](../../../ado/reference/ado-api/filter-property.md)
