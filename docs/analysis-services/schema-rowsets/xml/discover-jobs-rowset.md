---
title: Set di righe DISCOVER_JOBS | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_JOBS rowset
ms.assetid: b4d83bb6-aed3-4513-b516-cefadf95dad2
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e1f7ac112f3fcae70751f02038d0257231600b56
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="discoverjobs-rowset"></a>Set di righe DISCOVER_JOBS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Vengono fornite informazioni sui processi attivi in esecuzione nel server. Un processo fa parte di un comando che esegue un'attività specifica per conto del comando.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_JOBS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**JOB_CREATION_TIME**|**DBTYPE_DBTIMESTAMP**||Data e ora UTC del server in cui è stato creato il processo.|  
|**JOB_DESCRIPTION**|**DBTYPE_WSTR**||Descrizione del processo assegnata dal servizio del server.|  
|**JOB_EXECUTION_TIME_MS**|**DBTYPE_I8**||Tempo di attività, in millisecondi, del processo.|  
|**JOB_ID**|**DBTYPE_I4**||Identificatore univoco del processo.|  
|**JOB_START_TIME**|**DBTYPE_DBTIMESTAMP**||Data e ora UTC del server in cui è stato avviato il processo.|  
|**JOB_THREADPOOL_ID**|**DBTYPE_I4**||Pool di thread dal quale è stato avviato il processo corrente.|  
|**JOB_TOTAL_TIME_MS**|**DBTYPE_I8**||Tempo trascorso, in millisecondi, dopo l'avvio del processo.|  
|**SPID**|**DBTYPE_I4**||ID della sessione.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DISCOVER_JOBS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|SPID|DBTYPE_I4|Facoltativa.|  
|JOB_ID|DBTYPE_I4|Facoltativa.|  
|JOB_DESCRIPTION|DBTYPE_WSTR|Facoltativa.|  
|JOB_THREADPOOL_ID|DBTYPE_I4|Facoltativa.|  
|JOB_MIN TOTAL_TIME_MS|DBTYPE_I8|Facoltativa.|  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
