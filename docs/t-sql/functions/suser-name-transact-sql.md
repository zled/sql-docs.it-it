---
title: SUSER_NAME (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SUSER_NAME
- SUSER_NAME_TSQL
dev_langs: TSQL
helpviewer_keywords:
- security identification names [SQL Server]
- logins [SQL Server], users
- identification names for logins [SQL Server]
- users [SQL Server], logins
- SUSER_NAME function
- logins [SQL Server], names
- names [SQL Server], logins
ms.assetid: ae598d9f-9baa-49b8-b1c1-042854206de4
caps.latest.revision: "29"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: cb236dc3ae7f74ad77ba398e328d4a0bf93a079b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="susername-transact-sql"></a>SUSER_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  Restituisce il nome di identificazione dell'account di accesso dell'utente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SUSER_NAME ( [ server_user_id ] )   
```  
  
## <a name="arguments"></a>Argomenti  
 *server_user_id*  
 Numero di identificazione dell'account di accesso dell'utente. *server_user_id*, che è facoltativo e **int**. *server_user_id* può essere il numero di identificazione di qualsiasi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso o [!INCLUDE[msCoName](../../includes/msconame-md.md)] utente o gruppo che dispone dell'autorizzazione per connettersi a un'istanza di Windows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se *server_user_id* viene omesso, viene restituito il nome di identificazione di account di accesso per l'utente corrente. Se nel parametro è inclusa la parola NULL, verrà restituito NULL.  
  
## <a name="return-types"></a>Tipi restituiti  
 **nvarchar (128)**  
  
## <a name="remarks"></a>Osservazioni  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versione 7.0 l'ID dell'utente del server (SUID) è stato sostituito con l'ID di sicurezza (SID).  
  
 SUSER_NAME restituisce un nome di account di accesso solo per un account di accesso che ha una voce nel **syslogins** tabella di sistema.  
  
 È possibile utilizzare SUSER_NAME in un elenco di selezione, in una clausola WHERE e in qualsiasi posizione in cui è consentita un'espressione. La funzione SUSER_NAME deve essere sempre seguita dalle parentesi, anche se non si specifica alcun parametro.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito il nome di identificazione dell'account di accesso dell'utente il cui numero di identificazione dell'account di accesso è `1`.  
  
```  
SELECT SUSER_NAME(1);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SUSER_ID &#40; Transact-SQL &#41;](../../t-sql/functions/suser-id-transact-sql.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
