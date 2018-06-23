---
title: Eliminazione di un indice SQL Server | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
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
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 38e103cd19950846dd9c88d0b4bdc0d5d385ba1f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065136"
---
# <a name="dropping-a-sql-server-index"></a>Eliminazione di un indice di SQL Server
  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client espone il **iindexdefinition:: DropIndex** (funzione). Ciò consente ai consumer di rimuovere un indice da un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client espone alcuni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i vincoli PRIMARY KEY e UNIQUE come gli indici. Il proprietario della tabella, proprietario del database, alcuni membri del ruolo amministrativo possono modificare un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella, eliminazione di un vincolo. Per impostazione predefinita, solo il proprietario della tabella può eliminare un indice. Pertanto, **DropIndex** esito positivo o negativo a seconda dei casi non solo per i diritti di accesso dell'utente dell'applicazione, ma anche sul tipo di indice indicato.  
  
 I consumer specificano il nome della tabella come stringa di caratteri Unicode nel *pwszName* appartenente il *uName* unione nel *pTableID* parametro. Il *eKind* appartenente *pTableID* deve essere DBKIND_NAME.  
  
 I consumer specificano il nome dell'indice come stringa di caratteri Unicode nel *pwszName* appartenente il *uName* unione nel *pIndexID* parametro. Il *eKind* appartenente *pIndexID* deve essere DBKIND_NAME. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non supporta la funzionalità di OLE DB di eliminazione di tutti gli indici in una tabella quando *pIndexID* è null. Se *pIndexID* è null, viene restituito E_INVALIDARG.  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle e indici](tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)   
 [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
