---
title: Set di righe DISCOVER_STORAGE_TABLES | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 13df6f10-8efe-4fe9-83a6-96d108809ed1
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 51b5bd319480be4c7757d4fb642859af54f209a3
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="discoverstoragetables-rowset"></a>Set di righe DISCOVER_STORAGE_TABLES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Consente al client determinare le tabelle in cui sono incluse in un database di Analysis Services in esecuzione in modalità tabulare o SharePoint.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_STORAGE_TABLES** set di righe contiene le colonne seguenti.  
  
|**Nome colonna**|**Indicatore del tipo**|**Length**|**Descrizione**|  
|---------------------|------------------------|----------------|---------------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**||Viene specificato il nome del database contenente le tabelle.<br /><br /> Il **DISCOVER_STORAGE_TABLES** righe può essere limitato tramite questa colonna. Se per limitare il set di righe non viene utilizzata questa colonna, viene utilizzato il database corrente.|  
|**CUBE_NAME**|**DBTYPE_WSTR**||Viene specificato il cubo o il modello contenente le tabelle.<br /><br /> Il **DISCOVER_STORAGE_TABLES** righe può essere limitato tramite questa colonna.|  
|**NOME_GRUPPO_MISURE**|**DBTYPE_WSTR**||Nome del gruppo di misure.|  
|**NOME_PARTIZIONE**|**DBTYPE_WSTR**||Nome della partizione.|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**||Nome della dimensione.|  
|**TABLE_ID**|**DBTYPE_WSTR**||ID della tabella utilizzata per archiviare gli attributi della tabella.|  
|**TABLE_PARTITIONS_COUNT**|**DBTYPE WSTR**||Conteggio della partizione della tabella.|  
|**HINT_TABLE_TYPE**|**DBTYPE WSTR**||Hint del tipo di tabella.|  
|**ROWS_COUNT**|**DBTYPE_UI4**||Numero di righe nella partizione.|  
|**RIVIOLATION_COUNT**|**DBTYPE_UI4**||Numero di righe con violazioni di integrità referenziale.|  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DISCOVER_STORAGE_TABLES** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|**Nome colonna**|**Indicatore del tipo**|**Stato della restrizione**|  
|---------------------|------------------------|---------------------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**NOME_GRUPPO_MISURE**|**DBTYPE_WSTR**|Facoltativo|  
|**NOME_PARTIZIONE**|**DBTYPE_WSTR**|Facoltativo|  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene restituito un elenco delle tabelle di archiviazione e il numero di righe in ognuna, dal database predefinito nella connessione corrente.  
  
```  
SELECT TABLE_ID, ROWS_COUNT  
FROM $system.DISCOVER_STORAGE_TABLES  
ORDER BY TABLE_ID DESC  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema di Analysis Services](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
