---
title: ADCPROP_UPDATECRITERIA_ENUM | Documenti Microsoft
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
- ADCPROP_UPDATECRITERIA_ENUM
helpviewer_keywords:
- ADCPROP_UPDATECRITERIA_ENUM [ADO]
ms.assetid: 33fd7b65-2ec8-4f62-91a7-630b5dab1aa2
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7bdd24f437d1bc0712e0e0222a8e99e999b1f3a1
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="adcpropupdatecriteriaenum"></a>ADCPROP_UPDATECRITERIA_ENUM
Specifica i campi che è possono utilizzare per rilevare i conflitti durante un aggiornamento ottimistico di una riga dell'origine dati con un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto.  
  
 Utilizzare queste costanti con il **Recordset** "**criteri di aggiornamento**" proprietà dinamica, che fa riferimento il [ADO Dynamic Property Index](../../../ado/reference/ado-api/ado-dynamic-property-index.md) e documentate nel [ Servizio di cursore per OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) documentazione.  
  
|Costante|Value|Description|  
|--------------|-----------|-----------------|  
|**adCriteriaAllCols**|1|Rileva i conflitti, se è stata modificata alcuna colonna della riga di origine dati.|  
|**adCriteriaKey**|0|Rileva i conflitti se la colonna chiave dei dati di riga di origine è stato modificato, il che significa che la riga è stata eliminata.|  
|**adCriteriaTimeStamp**|3|Rileva i conflitti se il timestamp dei dati di origine di riga è stata modificata, vale a dire che dopo aver eseguita la riga di **Recordset** è stato ottenuto.|  
|**adCriteriaUpdCols**|2|Rileva i conflitti se una o più colonne dell'origine dati della riga che corrispondono ai campi aggiornati del **Recordset** sono state modificate.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.AdcPropUpdateCriteria.ALLCOLS|  
|AdoEnums.AdcPropUpdateCriteria.KEY|  
|AdoEnums.AdcPropUpdateCriteria.TIMESTAMP|  
|AdoEnums.AdcPropUpdateCriteria.UPDCOLS|
