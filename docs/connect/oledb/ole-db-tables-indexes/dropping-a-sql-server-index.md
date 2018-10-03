---
title: Eliminazione di un indice di SQL Server | Microsoft Docs
description: Eliminazione di un indice di sql server usando il Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- OLE DB Driver for SQL Server, indexes
- indexes [OLE DB]
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 990318037a3f1b35e311a983859507a364c52127
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47669169"
---
# <a name="dropping-a-sql-server-index"></a>Eliminazione di un indice di SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Il Driver OLE DB per SQL Server espone il **iindexdefinition:: DropIndex** (funzione). Questo consente ai consumer di rimuovere una colonna da una tabella di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Il Driver OLE DB per SQL Server espone alcuni [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vincoli PRIMARY KEY e UNIQUE come indici. Il proprietario della tabella, il proprietario del database e alcuni membri del ruolo amministrativo possono modificare una tabella di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], eliminando un vincolo. Per impostazione predefinita, solo il proprietario della tabella può eliminare un indice. L'esito positivo o negativo di **DropIndex** dipende quindi non solo dai diritti di accesso dell'utente dell'applicazione, ma anche dal tipo di indice indicato.  
  
 I consumer specificano il nome della tabella come stringa di caratteri Unicode nel membro *pwszName* dell'unione *uName* nel parametro *pTableID*. Il membro *eKind* di*pTableID* deve essere DBKIND_NAME.  
  
 I consumer specificano il nome dell'indice come stringa di caratteri Unicode nel membro *pwszName* dell'unione *uName* nel parametro *pIndexID*. Il membro *eKind* di *pIndexID* deve essere DBKIND_NAME. Il driver OLE DB per SQL Server non supporta la caratteristica OLE DB di eliminazione di tutti gli indici in una tabella quando *pIndexID* è Null. Se *pIndexID* è Null, viene restituito E_INVALIDARG.  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle e indici](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-index-transact-sql.md)  
  
  
