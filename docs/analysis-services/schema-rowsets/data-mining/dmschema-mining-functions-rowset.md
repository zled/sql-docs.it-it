---
title: Set di righe DMSCHEMA_MINING_FUNCTIONS | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
apiname: DMSCHEMA_MINING_FUNCTIONS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DMSCHEMA_MINING_FUNCTIONS rowset
ms.assetid: 9ace7493-a7b1-45ca-93de-3cb2f3597017
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c33bf605db92bae91a0d05c5b4ea8feb6d4542e7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="dmschemaminingfunctions-rowset"></a>Set di righe DMSCHEMA_MINING_FUNCTIONS
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
 [Set di righe dello schema di data mining](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
