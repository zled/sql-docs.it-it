---
title: Set di righe DISCOVER_DB_CONNECTIONS | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_DB_CONNECTIONS rowset
ms.assetid: 12a51a4e-5f3d-4449-9d94-7836fea1bc8b
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: e71d6bcc4a22e95ecb4283946c9ec9c26dd42d93
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
  
  
