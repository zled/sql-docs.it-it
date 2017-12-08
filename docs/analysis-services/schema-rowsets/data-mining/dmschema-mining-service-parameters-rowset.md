---
title: Set di righe DMSCHEMA_MINING_SERVICE_PARAMETERS | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DMSCHEMA_MINING_SERVICE_PARAMETERS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DMSCHEMA_MINING_SERVICE_PARAMETERS rowset
ms.assetid: 5994e66b-84d0-4279-9f50-d92fd829dd83
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c84d263a312318be40c65c37a168bf11fdc97cfc
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="dmschemaminingserviceparameters-rowset"></a>Set di righe DMSCHEMA_MINING_SERVICE_PARAMETERS
  Descrive i parametri per gli algoritmi nel server.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DMSCHEMA_MINING_SERVICE_PARAMETERS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Description|  
|-----------------|--------------------|-----------------|  
|**SERVICE_NAME**|**DBTYPE_WSTR**|Nome dell'algoritmo.|  
|**PARAMETER_NAME**|**DBTYPE_WSTR**|Nome del parametro.|  
|**TIPO_PARAMETRO**|**DBTYPE_WSTR**|Tipo del parametro.|  
|**IS_REQUIRED**|**DBTYPE_BOOL**|Valore booleano che restituisce **TRUE** se il parametro è obbligatorio.|  
|**PARAMETER_FLAGS**|**DBTYPE_UI4**|Maschera di bit che descrive le caratteristiche del parametro:<br /><br /> **DM_PARAMETER_TRAINING** (**0x0000001**) indica il parametro viene utilizzato per il training<br /><br /> **DM_PARAMETER_PREDICTION** (**0x00000002**) indica il parametro viene utilizzato per la stima<br /><br /> **DM_PARAMETER_CONTENT** (**0x00000003**) indica il parametro viene utilizzato per la restrizione di contenuto|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Descrizione intuitiva del parametro.|  
|**VALORE PREDEFINITO**|**DBTYPE_WSTR**|Valore predefinito del parametro. Restituisce **NULL** se il valore predefinito non è un tipo di dati semplice.|  
|**VALUE_ENUMERATION**|**DBTYPE_WSTR**|Enumeratore di possibili valori per il parametro.|  
|**HELP_FILE**|**DBTYPE_WSTR**|Nome del file che contiene la documentazione relativa a questo parametro.|  
|**HELP_CONTEXT**|**DBTYPE_I4**|ID di contesto della Guida per questa funzione.|  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DMSCHEMA_MINING_SERVICE_PARAMETERS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**SERVICE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**PARAMETER_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema di data mining](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
