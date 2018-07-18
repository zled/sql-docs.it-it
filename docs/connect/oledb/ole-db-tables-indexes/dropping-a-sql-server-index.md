---
title: Eliminazione di un indice SQL Server | Documenti Microsoft
description: Eliminazione di un indice di sql server usando il Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-tables-indexes
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
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
ms.openlocfilehash: a790633c129fe1cfb3da9a21a9e4fd9fae3513cd
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/16/2018
ms.locfileid: "35690154"
---
# <a name="dropping-a-sql-server-index"></a>Eliminazione di un indice di SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Il Driver OLE DB per SQL Server espone il **iindexdefinition:: DropIndex** (funzione). Ciò consente ai consumer di rimuovere un indice da un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tabella.  
  
 Il Driver OLE DB per SQL Server espone alcuni [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] i vincoli PRIMARY KEY e UNIQUE come gli indici. Il proprietario della tabella, proprietario del database, alcuni membri del ruolo amministrativo possono modificare un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tabella, eliminazione di un vincolo. Per impostazione predefinita, solo il proprietario della tabella può eliminare un indice. Pertanto, **DropIndex** esito positivo o negativo a seconda dei casi non solo per i diritti di accesso dell'utente dell'applicazione, ma anche sul tipo di indice indicato.  
  
 I consumer specificano il nome della tabella come stringa di caratteri Unicode nel *pwszName* appartenente il *uName* unione nel *pTableID* parametro. Il *eKind* appartenente *pTableID* deve essere DBKIND_NAME.  
  
 I consumer specificano il nome dell'indice come stringa di caratteri Unicode nel *pwszName* appartenente il *uName* unione nel *pIndexID* parametro. Il *eKind* appartenente *pIndexID* deve essere DBKIND_NAME. Il Driver OLE DB per SQL Server non supporta la funzionalità di OLE DB di eliminazione di tutti gli indici in una tabella quando *pIndexID* è null. Se *pIndexID* è null, viene restituito E_INVALIDARG.  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle e indici](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-index-transact-sql.md)  
  
  
