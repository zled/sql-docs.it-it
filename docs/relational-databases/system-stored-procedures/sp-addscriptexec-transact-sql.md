---
title: sp_addscriptexec (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_addscriptexec
- sp_addscriptexec_TSQL
helpviewer_keywords:
- sp_addscriptexec
ms.assetid: 1627db41-6a80-45b6-b0b9-c0b7f9a1c886
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 8e3122de37c27e8372c2aca77f4dde0b267a8d20
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spaddscriptexec-transact-sql"></a>sp_addscriptexec (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Invia uno script SQL (file con estensione sql) a tutti i Sottoscrittori di una pubblicazione. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_addscriptexec [ @publication = ] publication  
    [ , [ @scriptfile = ] 'scriptfile' ]  
    [ , [ @skiperror = ] 'skiperror' ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=** ] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@scriptfile=** ] **'***scriptfile***'**  
 Percorso completo del file script SQL. *scriptfile* viene **nvarchar(4000**, non prevede alcun valore predefinito.  
  
 [  **@skiperror=** ] **'***skiperror***'**  
 Indica se l'agente di distribuzione o di merge deve essere arrestato in caso di errore durante l'elaborazione dello script. *SkipError* viene **bit**, con un valore predefinito è 0.  
  
 **0** = l'agente verrà arrestato.  
  
 **1** = l'agente continua lo script e ignora l'errore.  
  
 [  **@publisher=** ] **'***publisher***'**  
 Specifica un non -[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione. *server di pubblicazione* viene **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  *server di pubblicazione* non deve essere utilizzato per la pubblicazione da un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_addscriptexec** viene utilizzata nella replica transazionale, replica e di tipo merge.  
  
 **sp_addscriptexec** non viene utilizzato per la replica snapshot.  
  
 Per utilizzare **sp_addscriptexec**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account del servizio deve disporre di lettura e le autorizzazioni di scrittura per le autorizzazioni di lettura e di percorso snapshot alla posizione in cui gli script sono archiviate.  
  
 Il [utilità sqlcmd](../../tools/sqlcmd-utility.md) viene utilizzato per eseguire lo script nel sottoscrittore e lo script viene eseguito nel contesto di sicurezza utilizzato dall'agente di distribuzione o dell'agente di Merge durante la connessione al database di sottoscrizione. Quando l'agente viene eseguito in una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [utilità osql](../../tools/osql-utility.md) viene usata invece di [sqlcmd](../../tools/sqlcmd-utility.md).  
  
 **sp_addscriptexec** è utile per applicare gli script nei Sottoscrittori e utilizza [sqlcmd](../../tools/sqlcmd-utility.md) per applicare il contenuto dello script al sottoscrittore. Tuttavia, poiché le configurazioni dei Sottoscrittori sono soggette a variazioni, gli script testati prima dell'invio al server di pubblicazione potrebbero comunque causare errori in un Sottoscrittore. *SkipError* offre la possibilità di impostare l'agente di distribuzione o dell'agente di Merge ignora gli errori e continua in caso di. Utilizzare [sqlcmd](../../tools/sqlcmd-utility.md) per testare gli script prima dell'esecuzione **sp_addscriptexec**.  
  
> [!NOTE]  
>  Gli errori ignorati vengono comunque registrati nella cronologia dell'agente a titolo di riferimento.  
  
 Utilizzando **sp_addscriptexec** per registrare un file di script per le pubblicazioni utilizzando FTP per il recapito degli snapshot è supportato solo per [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sottoscrittori.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_addscriptexec**.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di script durante la sincronizzazione &#40;programmazione Transact-SQL della replica&#41;](../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)   
 [Sincronizzare i dati](../../relational-databases/replication/synchronize-data.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
