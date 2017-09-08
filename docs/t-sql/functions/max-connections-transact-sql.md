---
title: '@@MAX_CONNECTIONS (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@MAX_CONNECTIONS'
- '@@MAX_CONNECTIONS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- simultaneous connections [SQL Server]
- maximum number of simultaneous user connections
- '@@MAX_CONNECTIONS function'
- connections [SQL Server], simultaneous
- number of simultaneous user connections
ms.assetid: 57eb9f4b-548f-4212-9684-a11d831c4732
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 920bae6fe464d9947ed44236ec13117c55c5cc7d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="maxconnections-transact-sql"></a>@@MAX_CONNECTIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il numero massimo di connessioni utente simultanee consentite in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il numero restituito non corrisponde necessariamente all'impostazione corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
@@MAX_CONNECTIONS  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **integer**  
  
## <a name="remarks"></a>Osservazioni  
 Il numero effettivo di connessioni utente consentite dipende inoltre dalla versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installata e dalle limitazioni delle applicazioni e dell'hardware in uso.  
  
 Per riconfigurare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per le connessioni di un numero inferiore, utilizzare **sp_configure**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito il numero massimo di connessioni utente in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Nell'esempio si presuppone che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non sia stato riconfigurato per un numero inferiore di connessioni utente.  
  
```  
SELECT @@MAX_CONNECTIONS AS 'Max Connections';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Max Connections  
---------------  
32767            
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Funzioni di configurazione](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [Configurare l'opzione di configurazione del server user connections](../../database-engine/configure-windows/configure-the-user-connections-server-configuration-option.md)  
  
  
