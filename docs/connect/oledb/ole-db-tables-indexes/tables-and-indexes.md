---
title: Tabelle e indici | Documenti Microsoft
description: Creazione, modifica e droping tabelle e gli indici che utilizzano il Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-tables-indexes
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, indexes
- OLE DB, tables
- ITableDefinition interface
- tables [OLE DB]
- IIndexDefinition interface
- OLE DB Driver for SQL Server, tables
- OLE DB Driver for SQL Server, indexes
- indexes [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 821355c800f2b162665b29cfcadd7d9b776a1fc6
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2018
---
# <a name="tables-and-indexes"></a>Tabelle e indici
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il Driver OLE DB per SQL Server espone il **IIndexDefinition** e **ITableDefinition** interfacce, consentendo ai consumer di creare, modificare ed eliminare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tabelle e indici. La validità delle definizioni di tabelle e indici dipende dalla versione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 La possibilità di creare o eliminare tabelle e indici dipende dai diritti di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] di cui dispone l'utente dell'applicazione consumer. L'eliminazione di una tabella può essere vincolata ulteriormente dalla presenza di vincoli di integrità referenziale dichiarativa o da altri fattori.  
  
 La maggior parte delle applicazioni destinate a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzare SQL-DMO anziché queste Driver OLE DB per SQL Server interfacce. SQL-DMO è una raccolta di oggetti di automazione OLE che supportano tutte le funzioni amministrative di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le applicazioni destinate a più provider OLE DB utilizzano queste interfacce OLE DB generiche supportate dai diversi provider OLE DB.  
  
 Nel set di proprietà DBPROPSET_SQLSERVERCOLUMN specifico del provider [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] definisce la proprietà seguente.  
  
|ID proprietà|Description|  
|-----------------|-----------------|  
|SSPROP_COL_COLLATIONNAME|Tipo: VT_BSTR<br /><br /> L/S: Scrittura<br /><br /> Valore predefinito: Null<br /><br /> Descrizione: Questa proprietà viene utilizzata solo in **ITableDefinition**. La stringa specificata in questa proprietà viene utilizzata durante la creazione di un [CREATE TABLE](../../../t-sql/statements/create-table-transact-sql.md)<br /><br /> .|  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Creazione di tabelle di SQL Server](../../oledb/ole-db-tables-indexes/creating-sql-server-tables.md)  
  
-   [Aggiunta di una colonna in una tabella SQL Server](../../oledb/ole-db-tables-indexes/adding-a-column-to-a-sql-server-table.md)  
  
-   [Rimozione di una colonna da una tabella SQL Server](../../oledb/ole-db-tables-indexes/removing-a-column-from-a-sql-server-table.md)  
  
-   [Eliminazione di una tabella SQL Server](../../oledb/ole-db-tables-indexes/dropping-a-sql-server-table.md)  
  
-   [Creazione di indici SQL Server](../../oledb/ole-db-tables-indexes/creating-sql-server-indexes.md)  
  
-   [Eliminazione di un indice SQL Server](../../oledb/ole-db-tables-indexes/dropping-a-sql-server-index.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per SQL Server &#40;OLE DB&#41;](../../oledb/ole-db/oledb-driver-for-sql-server-ole-db.md)   
 [DROP TABLE &#40; Transact-SQL &#41;](../../../t-sql/statements/drop-table-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/create-index-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-index-transact-sql.md)  
  
  
