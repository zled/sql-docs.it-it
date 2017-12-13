---
title: Set di righe MDSCHEMA_MEASURES | Documenti Microsoft
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
apiname: MDSCHEMA_MEASURES
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: MDSCHEMA_MEASURES rowset
ms.assetid: 6ff5bd1a-aad0-49b8-9f8d-7df2637caacf
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f25b46b4a8d5ab61a848febb9f1322759ba4cc83
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="mdschemameasures-rowset"></a>Set di righe MDSCHEMA_MEASURES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Descrive ogni misura all'interno di un cubo.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **MDSCHEMA_MEASURES** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||Nome del catalogo a cui appartiene questa misura. **NULL** se il provider non supporta i cataloghi.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||Nome dello schema a cui appartiene questa misura. **NULL** se il provider non supporta gli schemi.|  
|**CUBE_NAME**|**DBTYPE_WSTR**||Nome del cubo a cui appartiene questa misura.|  
|**MEASURE_NAME**|**DBTYPE_WSTR**||Nome della misura.|  
|**MEASURE_UNIQUE_NAME**|**DBTYPE_WSTR**||Nome univoco della misura. Per i provider che generano nomi univoci tramite qualificazione, i singoli componenti di tale nome sono delimitati.|  
|**MEASURE_CAPTION**|**DBTYPE_WSTR**||Etichetta o didascalia associata alla misura. Utilizzata principalmente a scopo di visualizzazione. Se non esiste una didascalia, **MEASURE_NAME** viene restituito.|  
|**MEASURE_GUID**|**DBTYPE_GUID**||Non supportato.|  
|**MEASURE_AGGREGATOR**|**DBTYPE_I4**||Enumerazione tramite cui viene identificata la modalità di derivazione di una misura. I possibili valori sono i seguenti:<br /><br /> **MDMEASURE_AGGR_SUM** (**1**) indicato che la misura viene aggregata da **somma**.<br /><br /> **MDMEASURE_AGGR_COUNT** (**2**) indicato che la misura viene aggregata da **conteggio**.<br /><br /> **MDMEASURE_AGGR_MIN** (**3**) indicato che la misura viene aggregata da **MIN**.<br /><br /> **MDMEASURE_AGGR_MAX** (**4**) indicato che la misura viene aggregata da **MAX**.<br /><br /> **MDMEASURE_AGGR_AVG** (**5**) indicato che la misura viene aggregata da **AVG**.<br /><br /> **MDMEASURE_AGGR_VAR** (**6**) indicato che la misura viene aggregata da **VAR**.<br /><br /> **MDMEASURE_AGGR_STD** (**7**) indicato che la misura viene aggregata da **STDEV**.<br /><br /> **MDMEASURE_AGGR_DST** (**8**) indicato che la misura viene aggregata da **DISTINCT COUNT**.<br /><br /> **MDMEASURE_AGGR_NONE** (**9**) indicato che la misura viene aggregata da **Nessuno**.<br /><br /> **MDMEASURE_AGGR_AVGCHILDREN** (**10**) indicato che la misura viene aggregata da **AVERAGEOFCHILDREN**.<br /><br /> **MDMEASURE_AGGR_FIRSTCHILD** (**11**) indicato che la misura viene aggregata da **FIRSTCHILD**.<br /><br /> **MDMEASURE_AGGR_LASTCHILD** (**12**) indicato che la misura viene aggregata da **LASTCHILD**.<br /><br /> **MDMEASURE_AGGR_FIRSTNONEMPTY** (**13**) indicato che la misura viene aggregata da **FIRSTNONEMPTY**,<br /><br /> **MDMEASURE_AGGR_LASTNONEMPTY** (**14**) indicato che la misura viene aggregata da **LASTNONEMPTY**.<br /><br /> **MDMEASURE_AGGR_BYACCOUNT** (**15**) indicato che la misura viene aggregata da **BYACCOUNT**.<br /><br /> **MDMEASURE_AGGR_CALCULATED** (**127**) indica che la misura è stata derivata da una formula che non era qualsiasi singola funzione precedente.<br /><br /> **MDMEASURE_AGGR_UNKNOWN** (**0**) indica che la misura è stata derivata da una funzione di aggregazione sconosciuto o la formula.|  
|**DATA_TYPE**|**DBTYPE_UI2**||Tipo di dati della misura.|  
|**NUMERIC_PRECISION**|**DBTYPE_UI2**||Precisione massima della proprietà se il tipo di dati dell'oggetto misura è un valore numerico esatto. **NULL** per tutti gli altri tipi di proprietà.|  
|**NUMERIC_SCALE**|**DBTYPE_I2**||Il numero di cifre a destra del separatore decimale se l'indicatore del tipo dell'oggetto misura è **DBTYPE_NUMERIC** o **DBTYPE_DECIMAL**. In caso contrario, questo valore è **NULL**.|  
|**MEASURE_UNITS**|**DBTYPE_WSTR**||Non supportato|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Descrizione leggibile della misura. **NULL** se è presente alcuna descrizione.|  
|**ESPRESSIONE**|**DBTYPE_WSTR**||Espressione per il membro.|  
|**MEASURE_IS_VISIBLE**|**DBTYPE_BOOL**||Valore booleano che restituisce sempre True. Se la misura non è visibile, non verrà inclusa nel set di righe dello schema.|  
|**LEVELS_LIST**|**DBTYPE_WSTR**||Stringa che restituisce sempre **NULL**.|  
|**MEASURE_NAME_SQL_COLUMN_NAME**|**DBTYPE_WSTR**||Nome della colonna nella query SQL che corrisponde al nome della misura.|  
|**MEASURE_UNQUALIFIED_CAPTION**|**DBTYPE_WSTR**||Nome della misura, non qualificato con il nome del gruppo di misure.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**||Nome del gruppo di misure a cui appartiene la misura.|  
|**MEASURE_DISPLAY_FOLDER**|**DBTYPE_WSTR**||Il percorso da utilizzare durante la visualizzazione della misura nell'interfaccia utente. I nomi delle cartelle saranno separati da un punto e virgola. Cartelle nidificate sono indicate da una barra rovesciata (\\).|  
|**DEFAULT_FORMAT_STRING**|**DBTYPE_WSTR**||La stringa di formato predefinita per la misura.|  
  
 Il set di righe viene ordinato in base **CATALOG_NAME**, **SCHEMA_NAME**, **CUBE_NAME**, **MEASURE_NAME**.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **MDSCHEMA_MEASURES** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**MEASURE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**MEASURE_UNIQUE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(Facoltativo) Restrizione predefinita è un valore pari a 1. Una bitmap con uno dei valori validi seguenti:<br /><br /> 1 CUBO<br /><br /> 2 DIMENSIONE|  
|**MEASURE_VISIBILITY**|**DBTYPE_UI2**|(Facoltativo) Restrizione predefinita è un valore pari a 1. Una bitmap con uno dei valori validi seguenti:<br /><br /> 1 Visibile<br /><br /> 2 Non visibile|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
