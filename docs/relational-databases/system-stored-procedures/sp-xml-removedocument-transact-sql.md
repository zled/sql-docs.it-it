---
title: sp_xml_removedocument (Transact-SQL) | Documenti Microsoft
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
- sp_xml_removedocument_TSQL
- sp_xml_removedocument
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xml_removedocument
ms.assetid: f9dca50a-8baf-4170-90bc-e72783ce5b73
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6b031f1fc058ba51407ff748a6b7ef779edf1e6a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="spxmlremovedocument-transact-sql"></a>sp_xml_removedocument (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove la rappresentazione interna del documento XML specificato dall'handle di documento, che viene quindi reso non valido.  
  
> [!NOTE]  
>  Un documento analizzato viene archiviato nella cache interna di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il parser MSXML utilizza un ottavo della memoria totale disponibile per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per evitare di esaurire la memoria, eseguire **sp_xml_removedocument** per liberare la memoria.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_xml_removedocument hdoc  
```  
  
## <a name="arguments"></a>Argomenti  
 *hdoc*  
 Handle del nuovo documento. Se non è un valore valido, viene restituito un errore. *hdoc* è un numero intero.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o >0 (esito negativo)  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene rimossa la rappresentazione interna di un documento XML. L'handle del documento viene fornito come input.  
  
```  
EXEC sp_xml_removedocument @hdoc;  
```  
  
## <a name="see-also"></a>Vedere anche      
 <br>[Stored procedure (Transact-SQL) di sistema](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)
 <br>[XML Stored procedure (Transact-SQL)](../../relational-databases/system-stored-procedures/xml-stored-procedures-transact-sql.md)
 <br>[Sys.dm_exec_xml_handles (Transact-SQL)](../system-dynamic-management-views/sys-dm-exec-xml-handles-transact-sql.md)
 <br>[sp_xml_preparedocument(Transact-SQL)](../../relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql.md)
 <br>[OPENXML (Transact-SQL)](../../t-sql/functions/openxml-transact-sql.md)
  
  
