---
title: '@@MAX_CONNECTIONS (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 1f2630823c6552d5cb450b23cee005a438f32a8c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="x40x40maxconnections-transact-sql"></a>&#x40;&#x40;MAX_CONNECTIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il numero massimo di connessioni utente simultanee consentite in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il numero restituito non corrisponde necessariamente all'impostazione corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
@@MAX_CONNECTIONS  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **integer**  
  
## <a name="remarks"></a>Remarks  
 Il numero effettivo di connessioni utente consentite dipende inoltre dalla versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installata e dalle limitazioni delle applicazioni e dell'hardware in uso.  
  
 Per riconfigurare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per un numero inferiore di connessioni, usare **sp_configure**.  
  
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
  
  
