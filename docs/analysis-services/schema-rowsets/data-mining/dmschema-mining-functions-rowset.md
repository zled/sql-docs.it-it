---
title: Set di righe DMSCHEMA_MINING_FUNCTIONS | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f92a3028f9397283f8d5820c54d823e40b8fdc3d
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="dmschemaminingfunctions-rowset"></a>Set di righe DMSCHEMA_MINING_FUNCTIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Vengono descritte le funzioni di data mining di dati supportati da algoritmi di data mining disponibili in un server che esegue [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DMSCHEMA_MINING_FUNCTIONS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**SERVICE_NAME**|**DBTYPE_WSTR**||Nome dell'algoritmo.|  
|**NOME_FUNZIONE**|**DBTYPE_WSTR**||Nome della funzione.|  
|**FUNCTION_SIGNATURE**|**DBTYPE_WSTR**||Firma della funzione.|  
|**RETURNS_TABLE**|**DBTYPE_BOOL**||**FALSE** se la funzione restituisce contenuto scalare (ad esempio la lunghezza dell'argomento di tipo carattere); **TRUE** se la funzione restituisce una tabella (ad esempio una tabella dell'istogramma).|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Descrizione intuitiva della funzione.|  
|**HELP_FILE**|**DBTYPE_WSTR**||Nome del file che contiene la documentazione relativa a questa funzione.|  
|**HELP_CONTEXT**|**DBTYPE_I4**||ID di contesto della Guida per questa funzione.|  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DMSCHEMA_MINING_FUNCTIONS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**SERVICE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**NOME_FUNZIONE**|**DBTYPE_WSTR**|Facoltativa.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello Schema di Data Mining](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
