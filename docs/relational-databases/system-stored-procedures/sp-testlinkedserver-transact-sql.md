---
title: sp_testlinkedserver (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_testlinkedserver
- sp_testlinkedserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_testlinkedserver
ms.assetid: e63ca7d4-47d6-455e-9aac-421f9683dadc
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 51ce322bfd1b3a856bf215be5273cbaf886624b4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sptestlinkedserver-transact-sql"></a>sp_testlinkedserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Consente di testare la connessione a un server collegato. Se il test ha esito negativo, tramite la procedura viene generata un'eccezione con il motivo dell'errore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_testlinkedserver [ @servername ] = servername  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@servername =** ]*servername*  
 Nome del server collegato. *ServerName* viene **sysname**, senza alcun valore predefinito.  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="permissions"></a>Autorizzazioni  
 Le autorizzazioni non vengono controllate, tuttavia il chiamante deve disporre del mapping di account di accesso appropriato.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creato un server collegato denominato `SEATTLESales` e viene quindi testata la connessione.  
  
```  
USE master;  
GO  
EXEC sp_addlinkedserver   
    'SEATTLESales',  
    N'SQL Server';  
GO  
sp_testlinkedserver SEATTLESales;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)  
  
  
