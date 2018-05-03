---
title: Eliminazione di un indice SQL Server | Documenti Microsoft
description: Eliminazione di un indice di sql server usando il Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-tables-indexes
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- OLE DB Driver for SQL Server, indexes
- indexes [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: fcca3d266ae8ec5415e0affb29f64b085bdb2829
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="dropping-a-sql-server-index"></a>Eliminazione di un indice di SQL Server

  Il Driver OLE DB per SQL Server espone il **iindexdefinition:: DropIndex** (funzione). Questo consente ai consumer di rimuovere un indice da un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tabella.  
  
 Il Driver OLE DB per SQL Server espone alcuni [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] i vincoli PRIMARY KEY e UNIQUE come gli indici. Il proprietario della tabella, proprietario del database, alcuni membri del ruolo amministrativo possono modificare un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tabella, l'eliminazione di un vincolo. Per impostazione predefinita, solo il proprietario della tabella può eliminare un indice. Pertanto, **DropIndex** esito positivo o negativo dipende non solo i diritti di accesso dell'utente dell'applicazione ma anche sul tipo di indice indicato.  
  
 I consumer specificano il nome della tabella come stringa di caratteri Unicode nel *pwszName* appartenente il *uName* unione nel *pTableID* parametro. Il *eKind* membro di *pTableID* deve essere DBKIND_NAME.  
  
 I consumer specificano il nome dell'indice come stringa di caratteri Unicode nel *pwszName* appartenente il *uName* unione nel *pIndexID* parametro. Il *eKind* membro di *pIndexID* deve essere DBKIND_NAME. Il Driver OLE DB per SQL Server non supporta la funzionalità di OLE DB di eliminazione di tutti gli indici in una tabella quando *pIndexID* è null. Se *pIndexID* è null, viene restituito E_INVALIDARG.  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle e indici](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-index-transact-sql.md)  
  
  
