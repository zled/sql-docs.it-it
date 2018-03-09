---
title: xp_cmdshell (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xp_cmdshell
- xp_cmdshell_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_cmdshell
ms.assetid: 18935cf4-b320-4954-b6c1-e007fcefe358
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: bb3fcd3cba2be225c4c45514b2dcbc021683c0db
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="xpcmdshell-transact-sql"></a>xp_cmdshell (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Genera una shell dei comandi di Windows e passa una stringa per l'esecuzione. L'eventuale output viene restituito in forma di righe di testo.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
xp_cmdshell { 'command_string' } [ , no_output ]  
```  
  
## <a name="arguments"></a>Argomenti  
 **'** *command_string* **'**  
 Stringa che contiene un comando da passare al sistema operativo. *command_string* è **varchar(8000)** o **nvarchar (4000)**, non prevede alcun valore predefinito. *command_string* non può contenere più di un set di virgolette doppie. Una singola coppia di virgolette è necessaria se gli spazi sono presenti i percorsi di file o i nomi a cui fa riferimento di programma *command_string*. In caso di problemi nell'utilizzo di spazi incorporati nelle stringhe, valutare l'utilizzo di nomi di file in formato FAT 8.3 come soluzione alternativa.  
  
 **no_output**  
 Parametro facoltativo che indica che non è richiesta la restituzione di output al client.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 L'istruzione `xp_cmdshell` seguente restituisce un elenco dei file con estensione exe contenuti nella directory corrente.  
  
```  
EXEC xp_cmdshell 'dir *.exe';  
GO  
```  
  
 Le righe vengono restituite un **nvarchar (255)** colonna. Se il **no_output** viene utilizzata l'opzione, verranno restituiti solo le operazioni seguenti:  
  
```  
The command(s) completed successfully.  
```  
  
## <a name="remarks"></a>Osservazioni  
 Il processo di Windows generato da **xp_cmdshell** ha gli stessi diritti di sicurezza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account del servizio.  
  
 **xp_cmdshell** opera in modo sincrono. ovvero il controllo viene restituito al chiamante solo dopo il completamento del comando della shell.  
  
 **xp_cmdshell** può essere abilitata e disabilitata tramite la gestione basata su criteri oppure eseguendo **sp_configure**. Per ulteriori informazioni, vedere [Configurazione superficie di attacco](../../relational-databases/security/surface-area-configuration.md) e [opzione di configurazione del Server xp_cmdshell](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).  
  
> [!IMPORTANT]  
>  Se **xp_cmdshell** viene eseguita all'interno di un batch e restituisce un errore, il batch avrà esito negativo. Questa è una differenza funzionale Nelle versioni precedenti di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] batch continuerebbe.  
  
## <a name="xpcmdshell-proxy-account"></a>Account proxy per xp_cmdshell  
 Quando viene chiamato da un utente che non è membro il **sysadmin** ruolo predefinito del server, **xp_cmdshell** si connette a Windows utilizzando il nome account e password archiviati nella credenziale denominata **# # xp_cmdshell_proxy_account # #**. Se questa credenziale proxy non esiste, **xp_cmdshell** avrà esito negativo.  
  
 Le credenziali dell'account proxy possono essere create eseguendo **sp_xp_cmdshell_proxy_account**. Questa stored procedure accetta un nome utente e una password di Windows come argomenti. Il comando seguente, ad esempio, crea una credenziale proxy per l'utente di dominio di Windows `SHIPPING\KobeR` con la password di Windows `sdfh%dkc93vcMt0`.  
  
```  
EXEC sp_xp_cmdshell_proxy_account 'SHIPPING\KobeR','sdfh%dkc93vcMt0';  
```  
  
 Per ulteriori informazioni, vedere [sp_xp_cmdshell_proxy_account &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-xp-cmdshell-proxy-account-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Poiché gli utenti malintenzionati talvolta tentano di elevare i propri privilegi tramite **xp_cmdshell**, **xp_cmdshell** è disabilitato per impostazione predefinita. Utilizzare **sp_configure** o **gestione basata su criteri** per abilitarlo. Per altre informazioni, vedere [Opzione di configurazione del server xp_cmdshell](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).  
  
 Quando si abilita la prima volta, **xp_cmdshell** richiede l'autorizzazione CONTROL SERVER per l'esecuzione e il processo di Windows creato da **xp_cmdshell** ha lo stesso contesto di sicurezza come il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account del servizio. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account del servizio è spesso più autorizzazioni necessarie per il lavoro eseguito dal processo creato da **xp_cmdshell**. Per migliorare la sicurezza, l'accesso a **xp_cmdshell** deve essere limitato agli utenti con privilegi elevati.  
  
 Per consentire a utenti non amministratori di utilizzare **xp_cmdshell**e consentire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per creare processi figlio con il token di sicurezza di un account con privilegi più bassi, seguire questi passaggi:  
  
1.  Creare e personalizzare un account utente locale di Windows o un account di dominio con i privilegi minimi richiesti dai processi.  
  
2.  Utilizzare il **sp_xp_cmdshell_proxy_account** procedure di sistema per configurare **xp_cmdshell** per usare l'account con privilegi minimi.  
  
    > [!NOTE]  
    >  È inoltre possibile configurare questo account proxy utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] facendo **proprietà** sul nome del server in Esplora oggetti e cercando nel **sicurezza** per la scheda di **Server account proxy** sezione.  
  
3.  In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], utilizzando il database master, eseguire il `GRANT exec ON xp_cmdshell TO '<somelogin>'` istruzione per concedere a specifici non**sysadmin** agli utenti la possibilità di eseguire **xp_cmdshell**. L'accesso specificato deve essere mappato a un utente nel database master.  
  
 Ora a utenti non amministratori possono avviare processi del sistema operativo con **xp_cmdshell** ed eseguire i processi con le autorizzazioni dell'account proxy configurato. Gli utenti con autorizzazione CONTROL SERVER (membri del **sysadmin** ruolo predefinito del server) continuerà a ricevere le autorizzazioni del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di servizio per i processi figlio avviati da **xp_cmdshell** .  
  
 Per determinare l'account di Windows utilizzato da **xp_cmdshell** all'avvio dei processi del sistema operativo, eseguire l'istruzione seguente:  
  
```  
xp_cmdshell 'whoami.exe'  
  
```  
  
 Per determinare il contesto di sicurezza per un altro accesso, eseguire gli elementi seguenti:  
  
```  
EXECUTE AS LOGIN = '<other_login>' ;  
GO  
xp_cmdshell 'whoami.exe' ;  
REVERT ;  
  
```  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-a-list-of-executable-files"></a>A. Restituzione di un elenco di file eseguibili  
 Nell'esempio seguente viene mostrato l'utilizzo della stored procedure estesa `xp_cmdshell` per eseguire un comando di directory.  
  
```  
EXEC master..xp_cmdshell 'dir *.exe''  
```  
  
### <a name="b-returning-no-output"></a>B. Esecuzione di un comando senza restituzione dell'output  
 Nell'esempio seguente viene mostrato l'utilizzo di `xp_cmdshell` per eseguire una stringa di comandi senza restituire alcun output al client.  
  
```  
USE master;  
  
EXEC xp_cmdshell 'copy c:\SQLbcks\AdvWorks.bck  
    \\server2\backups\SQLbcks, NO_OUTPUT';  
GO  
```  
  
### <a name="c-using-return-status"></a>C. Restituzione del codice di stato  
 Nell'esempio seguente, il `xp_cmdshell` stored procedure estesa suggerisce di stato restituito. Il valore restituito viene archiviato nella variabile `@result`.  
  
```  
DECLARE @result int;  
EXEC @result = xp_cmdshell 'dir *.exe';  
IF (@result = 0)  
   PRINT 'Success'  
ELSE  
   PRINT 'Failure';  
```  
  
### <a name="d-writing-variable-contents-to-a-file"></a>D. Scrittura del contenuto di una variabile in un file  
 Nell'esempio seguente il contenuto della variabile `@var` viene scritto in un file denominato `var_out.txt` nella directory corrente del server.  
  
```  
DECLARE @cmd sysname, @var sysname;  
SET @var = 'Hello world';  
SET @cmd = 'echo ' + @var + ' > var_out.txt';  
EXEC master..xp_cmdshell @cmd;  
```  
  
### <a name="e-capturing-the-result-of-a-command-to-a-file"></a>E. Memorizzazione del risultato di un comando in un file  
 Nell'esempio seguente il contenuto della directory corrente viene scritto nel file `dir_out.txt` nella directory corrente del server.  
  
```  
DECLARE @cmd sysname, @var sysname;  
SET @var = 'dir/p';  
SET @cmd = @var + ' > dir_out.txt';  
EXEC master..xp_cmdshell @cmd;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Estese generali Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [Opzione di configurazione del Server xp_cmdshell](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md)   
 [Configurazione superficie di attacco](../../relational-databases/security/surface-area-configuration.md)   
 [sp_xp_cmdshell_proxy_account &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-xp-cmdshell-proxy-account-transact-sql.md)  
  
  
