---
title: Supporto per colonne di tipo sparse (OLE DB) | Microsoft Docs
description: Supporto di colonne di tipo sparse (OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: d2f4cd73d4d20d4b54573b300c5006bebd5fb6eb
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/18/2018
ms.locfileid: "39109003"
---
# <a name="sparse-columns-support-ole-db"></a>Supporto per colonne di tipo sparse (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  In questo argomento fornisce informazioni sul Driver OLE DB per il supporto di SQL Server per le colonne di tipo sparse. Per altre informazioni sulle colonne di tipo sparse, vedere [supporto per colonne di tipo Sparse nel Driver OLE DB per SQL Server](../../oledb/features/sparse-columns-support-in-oledb-driver-for-sql-server.md). Per un esempio, vedere [colonne visualizzate e i metadati del catalogo per le colonne di tipo Sparse &#40;OLE DB&#41;](../../oledb/ole-db-how-to/display-column-and-catalog-metadata-for-sparse-columns-ole-db.md).  
  
## <a name="ole-db-statement-metadata"></a>Metadati di istruzione OLE DB  
 A partire da [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], è disponibile un nuovo valore per il flag DBCOLUMNFLAGS, ovvero DBCOLUMNFLAGS_SS_ISCOLUMNSET. Questo valore deve essere impostato per colonne che sono valori **column_set**. Il flag DBCOLUMNFLAGS può essere recuperato tramite il *dwFlags* parametro IColumnsInfo:: e la colonna DBCOLUMN_FLAGS del set di righe restituito da IColumnsRowset::.  
  
## <a name="ole-db-catalog-metadata"></a>Metadati del catalogo OLE DB  
 Due colonne aggiuntive specifiche di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sono state aggiunte a DBSCHEMA_COLUMNS.  
  
|Nome colonna|Tipo di dati|Valore/commenti|  
|-----------------|---------------|---------------------|  
|SS_IS_SPARSE|DBTYPE_BOOL|Se la colonna è una colonna di tipo sparse, il valore di questa colonna è VARIANT_TRUE; in caso contrario, è VARIANT_FALSE.|  
|SS_IS_COLUMN_SET|DBTYPE_BOOL|Se la colonna è la colonna **column_set** di tipo sparse, il relativo valore è VARIANT_TRUE; in caso contrario, è VARIANT_FALSE.|  
  
 Sono inoltre stati aggiunti altri due set di righe dello schema. Tali set di righe hanno la stessa struttura di DBSCHEMA_COLUMNS ma restituiscono contenuto diverso. DBSCHEMA_COLUMNS_EXTENDED restituisce tutte le colonne indipendentemente dall'appartenenza a **column_set**. DBSCHEMA_SPARSE_COLUMN_SET restituisce solo le colonne che sono colonne **column_set** di tipo sparse.  
  
## <a name="ole-db-datatypecompatibility-behavior"></a>Comportamento OLE DB di DataTypeCompatibility  
 Comportamento con **DataTypeCompatibility = 80** (nella stringa di connessione) sia coerente con un [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] client, come indicato di seguito:  
  
-   I nuovi set di righe dello schema non sono visibili e i set di righe dello schema non includono righe per essi.  
  
-   Le nuove colonne nel set di righe COLUMNS non sono visibili.  
  
-   DBCOLUMNFLAGS_SS_ISCOLUMNSET non è impostato per le colonne **column_set**.  
  
-   DBCOMPUTEMODE_NOTCOMPUTED è impostato per le colonne **column_set**.  
  
## <a name="ole-db-support-for-sparse-columns"></a>Supporto OLE DB per colonne di tipo sparse  
 Le interfacce OLE DB seguenti sono state modificate nel Driver OLE DB per SQL Server per supportare colonne di tipo sparse:  
  
|Tipo o funzione membro|Descrizione|  
|-----------------------------|-----------------|  
|IColumnsInfo::|Un nuovo valore del flag DBCOLUMNFLAGS, ovvero DBCOLUMNFLAGS_SS_ISCOLUMNSET, è impostato per le colonne **column_set** in *dwFlags*.<br /><br /> DBCOLUMNFLAGS_WRITE è impostato per le colonne **column_set**.|  
|IColumsRowset::GetColumnsRowset|Un nuovo valore del flag DBCOLUMNFLAGS, ovvero DBCOLUMNFLAGS_SS_ISCOLUMNSET, è impostato per le colonne **column_set** in DBCOLUMN_FLAGS.<br /><br /> DBCOLUMN_COMPUTEMODE è impostato su DBCOMPUTEMODE_DYNAMIC per le colonne **column_set**.|  
|IDBSchemaRowset::GetSchemaRowset|DBSCHEMA_COLUMNS restituisce due nuove colonne: SS_IS_COLUMN_SET e SS_IS_SPARSE.<br /><br /> DBSCHEMA_COLUMNS restituisce solo colonne che non sono membri di **column_set**.<br /><br /> Sono stati aggiunti due nuovi set di righe dello schema: DBSCHEMA_COLUMNS_EXTENDED restituirà tutte le colonne indipendentemente dal fatto che siano o meno di tipo sparse o dall'appartenenza a **column_set**. DBSCHEMA_SPARSE_COLUMN_SET restituisce solo le colonne che sono membri di **column_set**. Questi nuovi set di righe includono le stesse colonne e comportano le stesse restrizioni di DBSCHEMA_COLUMNS.|  
|IDBSchemaRowset:: GetSchemas|IDBSchemaRowset::GetSchemas include i GUID per i nuovi set di righe DBSCHEMA_COLUMNS_EXTENDED e DBSCHEMA_SPARSE_COLUMN_SET nell'elenco dei set di righe dello schema disponibili.|  
|ICommand::Execute|Se si utilizza **select \* from** *table*, vengono restituite tutte le colonne che non sono membri del **column_set** di tipo sparse, nonché una colonna XML che contiene i valori di tutte le colonne non null membri del **column_set** di tipo sparse, se presente.|  
|IOpenRowset::OpenRowset|IOpenRowset:: OPENROWSET restituisce un set di righe con le stesse colonne ICommand:: Execute, con un **selezionate \***  query nella stessa tabella.|  
|ITableDefinition|Non è stata apportata alcuna modifica a questa interfaccia per le colonne di tipo sparse o per le colonne **column_set**. Le applicazioni che devono apportare modifiche allo schema devono eseguire direttamente l'istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)] appropriata.|  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per programmazione con SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
