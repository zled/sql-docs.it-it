---
title: Set di righe DISCOVER_DB_CONNECTIONS | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3ccdd4496b075c976bfaecb4d7eb9db43560f3c3
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="discoverdbconnections-rowset"></a>Set di righe DISCOVER_DB_CONNECTIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Fornisce informazioni sull'utilizzo delle risorse e sulle attività relative alle connessioni attualmente aperte dal server a un database.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_DB_CONNECTIONS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CONNECTION_CATALOG_NAME**|**DBTYPE_WSTR**||Nome del database attualmente connesso.|  
|**CONNECTION_ID**|**DBTYPE_I4**||Numero univoco che identifica la connessione.|  
|**CONNECTION_IDLE_TIME_MS**|**DBTYPE_I8**||Tempo di inattività, in millisecondi, dopo l'avvio della connessione.|  
|**CONNECTION_IN_USE**|**DBTYPE_I4**||Indica se la connessione è attiva (1) o inattiva (0).|  
|**CONNECTION_LAST_COMMAND_END_TIME**|**DBTYPE_DBTIMESTAMP**||Data e ora UTC del server in cui è terminata l'esecuzione dell'ultimo comando.|  
|**CONNECTION_LAST_COMMAND_START_TIME**|**DBTYPE_DBTIMESTAMP**||Data e ora UTC del server in cui è iniziata l'esecuzione dell'ultimo comando.|  
|**CONNECTION_SERVER_NAME**|**DBTYPE_WSTR**||Nome del server attualmente connesso.|  
|**CONNECTION_SPID**|**DBTYPE_I4**||ID della sessione.|  
|**CONNECTION_START_TIME**|**DBTYPE_DBTIMESTAMP**||Data e ora UTC del server in cui è iniziata la connessione.|  
|**CONNECTION_USAGE_TIME_MS**|**DBTYPE_I8**||Tempo di attività della connessione, in millisecondi, dopo l'avvio della connessione.|  
  
 Questo set di righe dello schema non è ordinato.  
  
> [!IMPORTANT]  
>  Il **DISCOVER_DB_CONNECTIONS** set di righe visualizzerà informazioni solo quando il servizio è connesso alle origini dati relazionali.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DISCOVER_DB_CONNECTIONS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|CONNECTION_ID|DBTYPE_I4|Facoltativa.|  
|CONNECTION_IN_USE|DBTYPE_I4|Facoltativa.|  
|CONNECTION_SERVER_NAME|DBTYPE_WSTR|Facoltativa.|  
|CONNECTION_CATALOG_NAME|DBTYPE_WSTR|Obbligatorio.|  
|CONNECTION_SPID|DBTYPE_I4|Facoltativa.|  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i rowset dello Schema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
