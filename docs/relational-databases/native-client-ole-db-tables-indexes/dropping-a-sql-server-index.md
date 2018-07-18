---
title: Eliminazione di un indice di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: add3ba14-10b1-4723-b7c0-3e83689e9fdd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: efb206bda68421a8de81e0f1b03b541d839ef3cc
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37429510"
---
# <a name="dropping-a-sql-server-index"></a>Eliminazione di un indice di SQL Server
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client espone il **iindexdefinition:: DropIndex** (funzione). Ciò consente ai consumer di rimuovere un indice da un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client espone alcuni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vincoli PRIMARY KEY e UNIQUE come indici. Il proprietario della tabella, proprietario del database e alcuni membri del ruolo amministrativo possono modificare un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella, eliminazione di un vincolo. Per impostazione predefinita, solo il proprietario della tabella può eliminare un indice. Pertanto **DropIndex** esito positivo o negativo dipende non solo i diritti di accesso dell'utente dell'applicazione ma anche sul tipo di indice indicato.  
  
 I consumer specificano il nome della tabella come una stringa di caratteri Unicode nel *pwszName* membro delle *uName* union nel *pTableID* parametro. Il *eKind* appartenente *pTableID* deve essere DBKIND_NAME.  
  
 I consumer specificano il nome dell'indice come una stringa di caratteri Unicode nel *pwszName* membro delle *uName* union nel *pIndexID* parametro. Il *eKind* appartenente *pIndexID* deve essere DBKIND_NAME. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non supporta la funzionalità OLE DB di eliminazione di tutti gli indici in una tabella quando *pIndexID* è null. Se *pIndexID* è null, viene restituito E_INVALIDARG.  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle e indici](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-index-transact-sql.md)  
  
  
