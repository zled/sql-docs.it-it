---
title: sysmail_start_sp (Transact-SQL) | Microsoft Docs
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
- sysmail_start_sp
- sysmail_start_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_start_sp
ms.assetid: 25fd7bb6-cfdd-463f-bea8-c6fcb805d3f5
caps.latest.revision: 32
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2fa805836387ae94cca2cba189eb4a9a9b20d8a3
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43024180"
---
# <a name="sysmailstartsp-transact-sql"></a>sysmail_start_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Avvia l'esecuzione di Posta elettronica database mediante l'avvio degli oggetti di [!INCLUDE[ssSB](../../includes/sssb-md.md)] utilizzati dal programma esterno.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sysmail_start_sp  
```  
  
## <a name="arguments"></a>Argomenti  
 None  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
 None  
  
## <a name="remarks"></a>Note  
 Posta elettronica database non è abilitato o installata al momento[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installazione. Per abilitare e installare oggetti di Posta elettronica database, utilizzare la Configurazione guidata posta elettronica database.  
  
 Questa stored procedure è nel **msdb** database. Questa stored procedure avvia la coda di Posta elettronica database contenente le richieste dei messaggi in uscita e abilita l'attivazione di [!INCLUDE[ssSB](../../includes/sssb-md.md)] per il programma esterno.  
  
 Se le code vengono avviate, il programma esterno Posta elettronica database elabora i messaggi. Questa procedura consente di riavviare le code dopo le code sono state arrestate con il **sysmail_stop_sp** stored procedure.  
  
> [!NOTE]  
>  Questa stored procedure avvia solo le code di Posta elettronica database e non attiva il recapito dei messaggi di [!INCLUDE[ssSB](../../includes/sssb-md.md)] nel database.  
  
## <a name="permissions"></a>Permissions  
 Le autorizzazioni per questa routine per impostazione predefinita ai membri di esecuzione per il **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente illustra a partire da posta elettronica Database di **msdb** database. Nell'esempio si presuppone che il programma esterno Posta elettronica database sia stato abilitato.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sysmail_start_sp ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Posta elettronica database](../../relational-databases/database-mail/database-mail.md)   
 [Opzione di configurazione Server database Mail XPs](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md)   
 [sysmail_stop_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-stop-sp-transact-sql.md)   
 [Stored procedure di posta elettronica database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
