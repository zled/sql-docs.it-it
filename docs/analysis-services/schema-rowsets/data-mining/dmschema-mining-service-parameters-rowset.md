---
title: Set di righe DMSCHEMA_MINING_SERVICE_PARAMETERS | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 41554600e77c3055f998d7fa32b6f7330c06de52
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34037495"
---
# <a name="dmschemaminingserviceparameters-rowset"></a>Set di righe DMSCHEMA_MINING_SERVICE_PARAMETERS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [Set di righe dello Schema di Data Mining](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
