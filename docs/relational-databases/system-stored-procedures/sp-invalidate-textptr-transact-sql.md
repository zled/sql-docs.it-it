---
title: sp_invalidate_textptr (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_invalidate_textptr_TSQL
- sp_invalidate_textptr
dev_langs:
- TSQL
helpviewer_keywords:
- sp_invalidate_textptr
ms.assetid: dd9920e1-7064-4c05-93d8-9303103fa1d6
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a3822cc5d7ec4d346c70d717c58d4f0dc391f177
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43019706"
---
# <a name="spinvalidatetextptr-transact-sql"></a>sp_invalidate_textptr (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Viene invalidato il puntatore di testo all'interno di righe specificato oppure tutti i puntatori di testo all'interno di righe nella transazione. **sp_invalidate_textptr** è utilizzabile solo sui puntatori di testo nelle righe. Questi puntatori sono archiviati in tabelle contenenti i **testo nella riga** opzione è abilitata.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_invalidate_textptr [ [ @TextPtrValue = ] textptr_value ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@TextPtrValue=** ] *textptr_value*  
 Puntatore di testo all'interno di righe da invalidare. *textptr_value* viene **varbinary (** 16 **)**, con un valore predefinito è NULL. Se NULL, **sp_invalidate_textptr** invalida tutti i puntatori di testo nelle righe nella transazione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Note  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta un massimo di 1.024 puntatori di testo all'interno di righe validi attivi per ogni transazione di un database. In una transazione che si estende su più database, tuttavia, possono essere inclusi 1.024 puntatori di testo all'interno di righe in ogni database. **sp_invalidate_textptr** consente di invalidare puntatori di testo all'interno di righe e, pertanto, lo spazio disponibile per i puntatori di testo all'interno delle righe aggiuntive.  
  
 Per altre informazioni sull'opzione text in row, vedere [sp_tableoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="see-also"></a>Vedere anche  
 [Motore di database le Stored procedure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_tableoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)   
 [TEXTPTR &#40;Transact-SQL&#41;](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)   
 [TEXTVALID &#40;Transact-SQL&#41;](../../t-sql/functions/text-and-image-functions-textvalid-transact-sql.md)  
  
  
