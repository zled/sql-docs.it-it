---
title: Set di righe DBSCHEMA_TABLES | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 06fc718e4d4bde23bfee4240e89d77bcde3bbf50
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="dbschematables-rowset"></a>Set di righe DBSCHEMA_TABLES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Identifica i gruppi di misure e le dimensioni esposte come tabelle all'interno di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DBSCHEMA_TABLES** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**TABLE_CATALOG**|**DBTYPE_WSTR**|255|Nome del catalogo a cui appartiene l'oggetto.|  
|**TABLE_SCHEMA**|**DBTYPE_WSTR**|255|Nome del cubo a cui appartiene l'oggetto.|  
|**TABLE_NAME**|**DBTYPE_WSTR**|255|Il nome dell'oggetto, se **TABLE_TYPE** è **tabella**.|  
|**TABLE_TYPE**|**DBTYPE_WSTR**||Tipo della tabella.<br /><br /> **TABELLA** indica l'oggetto è un gruppo di misure.<br /><br /> **TABELLA di sistema** indica l'oggetto è una dimensione.|  
|**TABLE_GUID**|**DBTYPE_GUID**||Non supportato.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Descrizione leggibile dell'oggetto.|  
|**TABLE_PROPID**|**DBTYPE_UI4**||Non supportato.|  
|**DATE_CREATED**|**DBTYPE_DBTIMESTAMP**||Non supportato.|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**||Data dell'ultima modifica apportata all'oggetto.|  
|**TABLE_OLAP_TYPE**|**DBTYPE_WSTR**||Tipo OLAP dell'oggetto.<br /><br /> **MEASURE_GROUP** indica l'oggetto è un gruppo di misure.<br /><br /> **CUBE_DIMENSION** indicato l'oggetto è una dimensione.|  
  
 Il set di righe viene ordinato in base **TABLE_TYPE**, **TABLE_CATALOG**, **TABLE_SCHEMA**, e **TABLE_NAME**.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DBSCHEMA_TABLES** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**TABLE_CATALOG**|**DBTYPE_WSTR**|Facoltativo|  
|**TABLE_SCHEMA**|**DBTYPE_WSTR**|Facoltativo|  
|**TABLE_NAME**|**DBTYPE_WSTR**|Facoltativo|  
|**TABLE_TYPE**|**DBTYPE_WSTR**|Facoltativo|  
|**TABLE_OLAP_TYPE**|**DBTYPE_WSTR**|Facoltativo|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello Schema OLE DB](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  
