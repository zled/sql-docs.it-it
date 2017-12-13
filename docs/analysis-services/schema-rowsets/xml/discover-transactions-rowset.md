---
title: Set di righe DISCOVER_TRANSACTIONS | Documenti Microsoft
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
ms.assetid: 85789177-c5df-4336-a90c-c20d69277ab4
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4cc8bdd0f4c3a4b212661e4ac9363ce6bdefb64f
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="discovertransactions-rowset"></a>Set di righe DISCOVER_TRANSACTIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Restituisce il set corrente di transazioni in sospeso nel sistema.  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_TRANSACTIONS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Description|  
|-----------------|--------------------|-----------------|  
|**TRANSACTION_ID**|**DBTYPE_WSTR**|Identificatore univoco della transazione espresso come GUID.|  
|**TRANSACTION_SESSION_ID**|**DBTYPE_WSTR**|Identificatore univoco della sessione espresso come GUID.|  
|**TRANSACTION_START_TIME**|**DBTYPE_DBTIMESTAMP**|Data e ora UTC del server in cui è stata avviata la transazione.|  
|**TRANSACTION_ELAPSED_TIME_MS**|**DBTYPE_I8**|Tempo trascorso, in millisecondi, dopo l'avvio della transazione.|  
|**TRANSACTION_CPU_TIME_MS**|**DBTYPE_I8**|Tempo di CPU, in millisecondi, utilizzato da tutte le richieste dopo l'inizio della transazione.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DISCOVER_TRANSACTIONS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|**Nome colonna**|**Indicatore del tipo**|**Stato della restrizione**|  
|---------------------|------------------------|---------------------------|  
|**ID**|**DBTYPE_WSTR**|Facoltativa.|  
|**SESSION_ID**|**DBTYPE_WSTR**|Facoltativa.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|Valore|  
|--------------|-----------|  
|GUID|a07ccd28-8148-11d0-87bb-00c04fc33942|  
|String|DISCOVER_TRANSACTIONS|  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
