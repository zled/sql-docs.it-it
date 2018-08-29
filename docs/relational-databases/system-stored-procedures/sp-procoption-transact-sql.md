---
title: sp_procoption (Transact-SQL) | Microsoft Docs
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
- sp_procoption
- sp_procoption_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_procoption
ms.assetid: 6f0221bd-70b4-4b04-b15d-722235aceb3c
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3c4c9907c52ad99e1a397b4ad08f9897b6a0c4d5
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43018211"
---
# <a name="spprocoption-transact-sql"></a>sp_procoption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Consente di impostare o di annullare l'esecuzione automatica di una stored procedure. Una stored procedure configurata per l'esecuzione automatica viene eseguita a ogni avvio di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_procoption [ @ProcName = ] 'procedure'   
    , [ @OptionName = ] 'option'   
    , [ @OptionValue = ] 'value'   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@ProcName =** ] **'***procedure***'**  
 È il nome della routine per cui si desidera impostare un'opzione. *routine* viene **nvarchar(776)**, non prevede alcun valore predefinito.  
  
 [  **@OptionName =** ] **'***opzione***'**  
 Nome dell'opzione da impostare. L'unico valore per *opzione* viene **avvio**.  
  
 [  **@OptionValue =** ] **'***valore***'**  
 Indica se attivare l'opzione (**true** o **sul**) o su off (**false** oppure **off**). *valore* viene **varchar(12)**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o numero di errore (esito negativo)  
  
## <a name="remarks"></a>Note  
 Procedure di avvio devono essere il **master** del database e non può contenere parametri INPUT o OUTPUT. L'esecuzione delle stored procedure inizia quando tutti i database sono stati recuperati e il messaggio relativo al completamento del recupero viene registrato all'avvio.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene impostata una routine per esecuzione automatica.  
  
```  
EXEC sp_procoption @ProcName = '<procedure name>'   
    , @OptionName = ] 'startup'   
    , @OptionValue = 'on';   
```  
  
 Nell'esempio seguente viene arrestata l'esecuzione automatica di una routine.  
  
```  
EXEC sp_procoption @ProcName = '<procedure name>'   
    , @OptionValue = 'off';   
```  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire una stored procedure](../../relational-databases/stored-procedures/execute-a-stored-procedure.md)  
  
  
