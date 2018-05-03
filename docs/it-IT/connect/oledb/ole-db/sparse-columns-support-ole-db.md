---
title: Supporto per colonne di tipo sparse (OLE DB) | Documenti Microsoft
description: Supporto per colonne di tipo sparse (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: f3b840fb808ad9ac1c6fb54772103d5e2275e197
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sparse-columns-support-ole-db"></a>Supporto per colonne di tipo sparse (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  In questo argomento vengono fornite informazioni sui Driver OLE DB per il supporto di SQL Server per le colonne di tipo sparse. Per ulteriori informazioni sulle colonne di tipo sparse, vedere [supporto per colonne di tipo Sparse nel Driver OLE DB per SQL Server](../../oledb/features/sparse-columns-support-in-oledb-driver-for-sql-server.md). Per un esempio, vedere [colonna di visualizzazione e i metadati del catalogo per colonne di tipo Sparse &#40;OLE DB&#41;](../../oledb/ole-db-how-to/display-column-and-catalog-metadata-for-sparse-columns-ole-db.md).  
  
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
 Le interfacce OLE DB seguenti sono state modificate nel Driver OLE DB per SQL Server per supportare colonne di tipo sparse:  
  
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
 [Driver OLE DB per programmazione con SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
