---
title: sp_certify_removable (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_certify_removable_TSQL
- sp_certify_removable
dev_langs:
- TSQL
helpviewer_keywords:
- sp_certify_removable
ms.assetid: ca12767f-0ae5-4652-b523-c23473f100a1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1d2586f1ad5f7be9b5916caea7699ca9c90f22db
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47691409"
---
# <a name="spcertifyremovable-transact-sql"></a>sp_certify_removable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Verifica che un database sia configurato correttamente per la distribuzione su supporti rimovibili e segnala eventuali problemi.  
  
> **IMPORTANTE** [! INCLUDERE[ssNoteDepFutureAvoid](../../t-sql/statements/create-database-sql-server-transact-sql.md) invece.  
  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_certify_removable [ @dbname= ] 'dbname'  
     [ , [ @autofix = ] 'auto' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@dbname=**] **'***dbname***'**  
 Viene specificato il database da verificare. *dbname* viene **sysname**.  
  
 [  **@autofix=**] **'auto'**  
 Viene assegnata la proprietà del database e di tutti i relativi oggetti all'amministratore di sistema e vengono eliminati tutti gli utenti del database creati dall'utente e tutte le autorizzazioni non predefinite. *Auto* viene **nvarchar(4)**, con un valore predefinito è NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Note  
 Se il database è configurato correttamente, **sp_certify_removable** esegue le operazioni seguenti:  
  
-   Imposta il database offline per consentire la copia dei file.  
  
-   Aggiorna i dati statistici di tutte le tabelle e segnala gli eventuali problemi relativi alla proprietà o a un utente.  
  
-   Contrassegna i filegroup di dati come filegroup di sola lettura per consentire la copia dei file su supporti di sola lettura.  
  
 L'amministratore di sistema deve essere il proprietario del database e di tutti i relativi oggetti. L'amministratore di sistema è un utente noto presente in tutti i server che eseguono [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e può essere necessario che esista quando il database viene distribuito e installato in un secondo momento.  
  
 Se si esegue **sp_certify_removable** senza il **automatico** valore e restituisce informazioni su una delle condizioni seguenti:  
  
-   L'amministratore di sistema non è il proprietario del database.  
  
-   Esistono utenti creati da un altro utente.  
  
-   L'amministratore di sistema non è il proprietario di tutti gli oggetti del database.  
  
-   Sono state concesse autorizzazioni non predefinite.  
  
 È possibile correggere queste condizioni come indicato di seguito:  
  
-   Uso [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gli strumenti e le procedure e quindi eseguire **sp_certify_removable** nuovamente.  
  
-   Eseguire semplicemente **sp_certify_removable** con il **automatico** valore.  
  
 Si noti che questa stored procedure controlla solo gli utenti e le autorizzazioni degli utenti. È consentito aggiungere gruppi al database e concedere autorizzazioni a tali gruppi. Per altre informazioni, vedere [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Eseguire le autorizzazioni sono limitate ai membri del **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene confermato che il database `inventory` è pronto per la rimozione.  
  
```  
EXEC sp_certify_removable inventory, AUTO;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Collegamento e scollegamento di un database &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [sp_create_removable &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-removable-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sp_dbremove &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbremove-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
