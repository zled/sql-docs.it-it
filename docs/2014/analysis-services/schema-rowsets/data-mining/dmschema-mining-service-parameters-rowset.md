---
title: Set di righe DMSCHEMA_MINING_SERVICE_PARAMETERS | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DMSCHEMA_MINING_SERVICE_PARAMETERS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_SERVICE_PARAMETERS rowset
ms.assetid: 5994e66b-84d0-4279-9f50-d92fd829dd83
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e7203b2f717ec7605fcc52c1387472779488ae4c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224471"
---
# <a name="dmschemaminingserviceparameters-rowset"></a>Set di righe DMSCHEMA_MINING_SERVICE_PARAMETERS
  Descrive i parametri per gli algoritmi nel server.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DMSCHEMA_MINING_SERVICE_PARAMETERS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`||Nome dell'algoritmo.|  
|`PARAMETER_NAME`|`DBTYPE_WSTR`||Nome del parametro.|  
|`PARAMETER_TYPE`|`DBTYPE_WSTR`||Tipo del parametro.|  
|`IS_REQUIRED`|`DBTYPE_BOOL`||Valore booleano che restituisce `TRUE` se il parametro è obbligatorio.|  
|`PARAMETER_FLAGS`|`DBTYPE_UI4`||Maschera di bit che descrive le caratteristiche del parametro:<br /><br /> -   `DM_PARAMETER_TRAINING` (`0x0000001`) indica il parametro viene utilizzato per il training<br />-   `DM_PARAMETER_PREDICTION` (`0x00000002`) indica il parametro viene utilizzato per la stima<br />-   `DM_PARAMETER_CONTENT` (`0x00000003`) indica il parametro viene utilizzato per la restrizione di contenuto|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Descrizione intuitiva del parametro.|  
|`DEFAULT_VALUE`|`DBTYPE_WSTR`||Valore predefinito del parametro. Restituisce `NULL` se il valore predefinito non è un tipo di dati semplice.|  
|`VALUE_ENUMERATION`|`DBTYPE_WSTR`||Enumeratore di possibili valori per il parametro.|  
|`HELP_FILE`|`DBTYPE_WSTR`||Nome del file che contiene la documentazione relativa a questo parametro.|  
|`HELP_CONTEXT`|`DBTYPE_I4`||ID di contesto della Guida per questa funzione.|  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DMSCHEMA_MINING_SERVICE_PARAMETERS` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`PARAMETER_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema di data mining](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
