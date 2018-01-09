---
title: Set di righe MDSCHEMA_DIMENSIONS | Documenti Microsoft
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
apiname: MDSCHEMA_DIMENSIONS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: MDSCHEMA_DIMENSIONS rowset
ms.assetid: a0fd94bb-359a-4df6-93a6-d60d50223944
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5cf0198759485452fc3fd6d82cdd2642df92b440
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="mdschemadimensions-rowset"></a>Set di righe MDSCHEMA_DIMENSIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Descrive le dimensioni condivise e private all'interno di un database.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **MDSCHEMA_DIMENSIONS** set di righe contiene le colonne seguenti:  
  
|Nome colonna|Indicatore del tipo|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Nome del database.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Non supportato.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Nome del cubo.|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**|Nome della dimensione. Se una dimensione appartiene a più cubi o a più gruppi di misure, sarà presente una riga per ogni combinazione univoca di dimensione, gruppo di misure e cubo.|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|Nome univoco della dimensione.|  
|**DIMENSION_GUID**|**DBTYPE_GUID**|Non supportato.|  
|**DIMENSION_CAPTION**|**DBTYPE_WSTR**|Didascalia della dimensione. Deve essere utilizzata durante la visualizzazione del nome della dimensione, ad esempio nell'interfaccia utente o in report.|  
|**DIMENSION_ORDINAL**|**DBTYPE_UI4**|Posizione della dimensione all'interno del cubo.|  
|**DIMENSION_TYPE**|**DBTYPE_I2**|Tipo della dimensione. I valori validi includono:<br /><br /> **MD_DIMTYPE_UNKNOWN** (**0**)<br /><br /> **MD_DIMTYPE_TIME** (**1**)<br /><br /> **MD_DIMTYPE_MEASURE** (**2**)<br /><br /> **MD_DIMTYPE_OTHER** (**3**)<br /><br /> **MD_DIMTYPE_QUANTITATIVE** (**5**)<br /><br /> **MD_DIMTYPE_ACCOUNTS** (**6**)<br /><br /> **MD_DIMTYPE_CUSTOMERS** (**7**)<br /><br /> **MD_DIMTYPE_PRODUCTS** (**8**)<br /><br /> **MD_DIMTYPE_SCENARIO** (**9**)<br /><br /> **MD_DIMTYPE_UTILIY** (**10**)<br /><br /> **MD_DIMTYPE_CURRENCY** (**11**)<br /><br /> **MD_DIMTYPE_RATES** (**12**)<br /><br /> **MD_DIMTYPE_CHANNEL** (**13**)<br /><br /> **MD_DIMTYPE_PROMOTION** (**14**)<br /><br /> **MD_DIMTYPE_ORGANIZATION** (**15**)<br /><br /> **MD_DIMTYPE_BILL_OF_MATERIALS** (**16**)<br /><br /> **MD_DIMTYPE_GEOGRAPHY** (**17**)|  
|**DIMENSION_CARDINALITY**|**DBTYPE_UI4**|Numero di membri nell'attributo chiave.|  
|**DEFAULT_HIERARCHY**|**DBTYPE_WSTR**|Gerarchia della dimensione. Mantenuta per compatibilità con le versioni precedenti.|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Descrizione semplice della dimensione.|  
|**IS_VIRTUAL**|**DBTYPE_BOOL**|Sempre **FALSE**.|  
|**IS_READWRITE**|**DBTYPE_BOOL**|Valore booleano che indica se una dimensione è abilitata per la scrittura.<br /><br /> **TRUE** se la dimensione è abilitata per la scrittura.|  
|**DIMENSION_UNIQUE_SETTINGS**|**DBTYPE_I4**|Bitmap che specifica quali colonne contengono valori univoci, se la dimensione contiene solo membri con nomi univoci. Le costanti del valore bit seguenti sono definite in Msmd.h per questa bitmap:<br /><br /> **MDDIMENSIONS_MEMBER_KEY_UNIQUE**|  
|**DIMENSION_MASTER_UNIQUE_NAME**|**DBTYPE_WSTR**|Sempre **NULL**.|  
|**DIMENSION_IS_VISIBLE**|**DBTYPE_BOOL**|Sempre **TRUE**.<br /><br /> Nota: Una dimensione non è visibile a meno che non sono visibili una o più gerarchie nella dimensione.|  
  
 Il set di righe viene ordinato in base **CATALOG_NAME**, **SCHEMA_NAME**, **CUBE_NAME**, **DIMENSION_NAME**.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **MDSCHEMA_DIMENSIONS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(Facoltativo) Restrizione predefinita è un valore pari a 1. Una bitmap con uno dei valori validi seguenti:<br /><br /> 1 CUBO<br /><br /> 2 DIMENSIONE|  
|**DIMENSION_VISIBILITY**|**DBTYPE_UI2**|(Facoltativo) Restrizione predefinita è un valore pari a 1. Una bitmap con uno dei valori validi seguenti:<br /><br /> 1 Visibile<br /><br /> 2 Non visibile|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
