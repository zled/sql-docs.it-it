---
title: Eliminazione di un indice di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
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
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 148565f2866e571ba783c58d1ff10413510ef6db
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37422230"
---
# <a name="dropping-a-sql-server-index"></a>Eliminazione di un indice di SQL Server
  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client espone il **iindexdefinition:: DropIndex** (funzione). Ciò consente ai consumer di rimuovere un indice da un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client espone alcuni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vincoli PRIMARY KEY e UNIQUE come indici. Il proprietario della tabella, proprietario del database e alcuni membri del ruolo amministrativo possono modificare un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella, eliminazione di un vincolo. Per impostazione predefinita, solo il proprietario della tabella può eliminare un indice. Pertanto **DropIndex** esito positivo o negativo dipende non solo i diritti di accesso dell'utente dell'applicazione ma anche sul tipo di indice indicato.  
  
 I consumer specificano il nome della tabella come una stringa di caratteri Unicode nel *pwszName* membro delle *uName* union nel *pTableID* parametro. Il *eKind* appartenente *pTableID* deve essere DBKIND_NAME.  
  
 I consumer specificano il nome dell'indice come una stringa di caratteri Unicode nel *pwszName* membro delle *uName* union nel *pIndexID* parametro. Il *eKind* appartenente *pIndexID* deve essere DBKIND_NAME. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non supporta la funzionalità OLE DB di eliminazione di tutti gli indici in una tabella quando *pIndexID* è null. Se *pIndexID* è null, viene restituito E_INVALIDARG.  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle e indici](tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)   
 [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
