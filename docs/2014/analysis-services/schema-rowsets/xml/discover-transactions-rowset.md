---
title: Set di righe DISCOVER_TRANSACTIONS | Documenti Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 85789177-c5df-4336-a90c-c20d69277ab4
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3869d4f8cd3adf96bd006a8669d7d82778b02450
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062759"
---
# <a name="discovertransactions-rowset"></a>Set di righe DISCOVER_TRANSACTIONS
  Restituisce il set corrente di transazioni in sospeso nel sistema.  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_TRANSACTIONS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Description|  
|-----------------|--------------------|-----------------|  
|`TRANSACTION_ID`|`DBTYPE_WSTR`|Identificatore univoco della transazione espresso come GUID.|  
|`TRANSACTION_SESSION_ID`|`DBTYPE_WSTR`|Identificatore univoco della sessione espresso come GUID.|  
|`TRANSACTION_START_TIME`|`DBTYPE_DBTIMESTAMP`|Data e ora UTC del server in cui è stata avviata la transazione.|  
|`TRANSACTION_ELAPSED_TIME_MS`|`DBTYPE_I8`|Tempo trascorso, in millisecondi, dopo l'avvio della transazione.|  
|`TRANSACTION_CPU_TIME_MS`|`DBTYPE_I8`|Tempo di CPU, in millisecondi, utilizzato da tutte le richieste dopo l'inizio della transazione.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DISCOVER_TRANSACTIONS` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|**Nome colonna**|**Indicatore del tipo**|**Stato della restrizione**|  
|---------------------|------------------------|---------------------------|  
|`ID`|`DBTYPE_WSTR`|Facoltativo.|  
|`SESSION_ID`|`DBTYPE_WSTR`|Facoltativo.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|valore|  
|--------------|-----------|  
|GUID|a07ccd28-8148-11d0-87bb-00c04fc33942|  
|String|DISCOVER_TRANSACTIONS|  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](xml-for-analysis-schema-rowsets.md)  
  
  