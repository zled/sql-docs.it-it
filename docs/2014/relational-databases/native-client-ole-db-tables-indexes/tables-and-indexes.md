---
title: Tabelle e indici | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, indexes
- OLE DB, tables
- ITableDefinition interface
- tables [OLE DB]
- IIndexDefinition interface
- SQL Server Native Client OLE DB provider, tables
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: 4217c6d8-8cd2-43dc-b36f-3cfd8a58fabc
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 29940e4ed8e9bb3a0ca7e3e3db419b27e491b1e2
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430982"
---
# <a name="tables-and-indexes"></a>Tabelle e indici
  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client espone il **IIndexDefinition** e **ITableDefinition** interfacce, consentendo ai consumer di creare, modificare ed eliminare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabelle e indici. La validità delle definizioni di tabelle e indici dipende dalla versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La possibilità di creare o eliminare tabelle e indici dipende dai diritti di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di cui dispone l'utente dell'applicazione consumer. L'eliminazione di una tabella può essere vincolata ulteriormente dalla presenza di vincoli di integrità referenziale dichiarativa o da altri fattori.  
  
 La maggior parte delle applicazioni destinate a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usano SQL-DMO anziché queste [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interfacce del provider OLE DB Native Client. SQL-DMO è una raccolta di oggetti di automazione OLE che supportano tutte le funzioni amministrative di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le applicazioni destinate a più provider OLE DB utilizzano queste interfacce OLE DB generiche supportate dai diversi provider OLE DB.  
  
 Nel set di proprietà DBPROPSET_SQLSERVERCOLUMN specifico del provider [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definisce la proprietà seguente.  
  
|ID proprietà|Description|  
|-----------------|-----------------|  
|SSPROP_COL_COLLATIONNAME|Tipo: VT_BSTR<br /><br /> L/S: Scrittura<br /><br /> Valore predefinito: Null<br /><br /> Descrizione: Questa proprietà viene utilizzata solo nella **ITableDefinition**. La stringa specificata in questa proprietà viene utilizzata quando si crea un [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql)<br /><br /> .|  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Creazione di tabelle di SQL Server](../../relational-databases/native-client-ole-db-tables-indexes/creating-sql-server-tables.md)  
  
-   [Aggiunta di una colonna a una tabella di SQL Server](../../relational-databases/native-client-ole-db-tables-indexes/adding-a-column-to-a-sql-server-table.md)  
  
-   [Rimozione di una colonna da una tabella di SQL Server](../../relational-databases/native-client-ole-db-tables-indexes/removing-a-column-from-a-sql-server-table.md)  
  
-   [Eliminazione di una tabella di SQL Server](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-table.md)  
  
-   [Creazione di indici di SQL Server](../../relational-databases/indexes/indexes.md)  
  
-   [Eliminazione di un indice di SQL Server](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-index.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql)   
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)   
 [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
