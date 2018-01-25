---
title: Supporto per colonne di tipo sparse (OLE DB) | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 918574b3-c62e-4937-9e5f-37310dedc8f9
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 83781fb2194f5ef94ea7a73a8c32017ceb25424a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="sparse-columns-support-ole-db"></a>Supporto per colonne di tipo sparse (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  In questo argomento vengono fornite informazioni sul supporto OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client per le colonne di tipo sparse. Per ulteriori informazioni sulle colonne di tipo sparse, vedere [supporto per colonne di tipo Sparse in SQL Server Native Client](../../../relational-databases/native-client/features/sparse-columns-support-in-sql-server-native-client.md). Per un esempio, vedere [colonna di visualizzazione e i metadati del catalogo per colonne di tipo Sparse &#40; OLE DB &#41;](../../../relational-databases/native-client-ole-db-how-to/display-column-and-catalog-metadata-for-sparse-columns-ole-db.md).  
  
## <a name="ole-db-statement-metadata"></a>Metadati di istruzione OLE DB  
 A partire da [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], è disponibile un nuovo valore per il flag DBCOLUMNFLAGS, ovvero DBCOLUMNFLAGS_SS_ISCOLUMNSET. Questo valore deve essere impostato per le colonne che sono **column_set** valori. Il flag DBCOLUMNFLAGS può essere recuperato tramite il *dwFlags* parametro IColumnsInfo::GetColumnsInfo e la colonna DBCOLUMN_FLAGS del set di righe restituito da IColumnsRowset::GetColumnsRowset.  
  
## <a name="ole-db-catalog-metadata"></a>Metadati del catalogo OLE DB  
 Due colonne aggiuntive specifiche di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sono state aggiunte a DBSCHEMA_COLUMNS.  
  
|Nome colonna|Tipo di dati|Valore/commenti|  
|-----------------|---------------|---------------------|  
|SS_IS_SPARSE|DBTYPE_BOOL|Se la colonna è una colonna di tipo sparse, il valore di questa colonna è VARIANT_TRUE; in caso contrario, è VARIANT_FALSE.|  
|SS_IS_COLUMN_SET|DBTYPE_BOOL|Se la colonna è di tipo sparse **column_set** colonna, il valore è VARIANT_TRUE; in caso contrario, VARIANT_FALSE.|  
  
 Sono inoltre stati aggiunti altri due set di righe dello schema. Tali set di righe hanno la stessa struttura di DBSCHEMA_COLUMNS ma restituiscono contenuto diverso. DBSCHEMA_COLUMNS_EXTENDED restituisce tutte le colonne indipendentemente **column_set** appartenenza. DBSCHEMA_SPARSE_COLUMN_SET restituisce solo le colonne che sono membri di tipo sparse **column_set**.  
  
## <a name="ole-db-datatypecompatibility-behavior"></a>Comportamento OLE DB di DataTypeCompatibility  
 Comportamento con **DataTypeCompatibility = 80** (nella stringa di connessione) è coerente con un [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] client, come indicato di seguito:  
  
-   I nuovi set di righe dello schema non sono visibili e i set di righe dello schema non includono righe per essi.  
  
-   Le nuove colonne nel set di righe COLUMNS non sono visibili.  
  
-   DBCOLUMNFLAGS_SS_ISCOLUMNSET non è impostato per **column_set** colonne.  
  
-   DBCOMPUTEMODE_NOTCOMPUTED è impostato per **column_set** colonne.  
  
## <a name="ole-db-support-for-sparse-columns"></a>Supporto OLE DB per colonne di tipo sparse  
 Le interfacce OLE DB seguenti sono state modificate in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client per supportare le colonne di tipo sparse:  
  
|Tipo o funzione membro|Description|  
|-----------------------------|-----------------|  
|IColumnsInfo::GetColumnsInfo|Valore DBCOLUMNFLAGS_SS_ISCOLUMNSET è impostato per flag DBCOLUMNFLAGS un nuovo **column_set** colonne *dwFlags*.<br /><br /> DBCOLUMNFLAGS_WRITE è impostato per **column_set** colonne.|  
|IColumsRowset::GetColumnsRowset|Un nuovo valore di un flag DBCOLUMNFLAGS, ovvero DBCOLUMNFLAGS_SS_ISCOLUMNSET, è impostato per **column_set** colonne in DBCOLUMN_FLAGS.<br /><br /> DBCOLUMN_COMPUTEMODE è impostato su dbcomputemode_dynamic per le **column_set** colonne.|  
|IDBSchemaRowset::GetSchemaRowset|DBSCHEMA_COLUMNS restituisce due nuove colonne: SS_IS_COLUMN_SET e SS_IS_SPARSE.<br /><br /> DBSCHEMA_COLUMNS restituisce solo le colonne che non sono membri di un **column_set**.<br /><br /> Sono stati aggiunti due nuovi set di righe dello schema: DBSCHEMA_COLUMNS_EXTENDED restituirà tutte le colonne indipendentemente dal tipo sparse di **column_set** appartenenza. DBSCHEMA_SPARSE_COLUMN_SET restituisce solo le colonne che sono membri di un **column_set**. Questi nuovi set di righe includono le stesse colonne e comportano le stesse restrizioni di DBSCHEMA_COLUMNS.|  
|IDBSchemaRowset::GetSchemas|IDBSchemaRowset:: GetSchemas include i GUID per il nuovo set di righe DBSCHEMA_COLUMNS_EXTENDED e DBSCHEMA_SPARSE_COLUMN_SET nell'elenco di set di righe dello schema disponibili.|  
|ICommand::Execute|Se **selezionare \* da** *tabella* è utilizzata, restituisce tutte le colonne che non sono membri di tipo sparse **column_set**, nonché una colonna XML che contiene i valori di tutte colonne non null che sono membri di tipo sparse **column_set**, se presente.|  
|IOpenRowset::OpenRowset|IOpenRowset::OPENROWSET restituisce un set di righe con le stesse colonne di ICommand::Execute, con un **selezionare \*** query nella stessa tabella.|  
|ITableDefinition|Sussiste alcuna modifica a questa interfaccia per le colonne di tipo sparse o per **column_set** colonne. Le applicazioni che devono apportare modifiche allo schema devono eseguire direttamente l'istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)] appropriata.|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
