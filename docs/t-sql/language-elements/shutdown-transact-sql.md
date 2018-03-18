---
title: SHUTDOWN (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SHUTDOWN_TSQL
- SHUTDOWN
dev_langs:
- TSQL
helpviewer_keywords:
- SQL Server, stopping
- shutting down SQL Server
- SHUTDOWN statement
- stopping SQL Server
- immediately stopping SQL Server
ms.assetid: c8b03ff9-688c-4fe8-86e8-bd6bd401c9a4
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: df8ef0a3cfe0ac4adb6f45bddb0bef650fea6ff3
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="shutdown-transact-sql"></a>SHUTDOWN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Arresta immediatamente SQL Server.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SHUTDOWN [ WITH NOWAIT ]   
```  
  
## <a name="arguments"></a>Argomenti  
 WITH NOWAIT  
 Facoltativo. Viene arrestato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] senza eseguire i checkpoint in ogni database. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene chiuso dopo il tentativo di interruzione di tutti i processi degli utenti. All'avvio successivo del server, verrà eseguita una operazione di rollback per le transazioni non completate.  
  
## <a name="remarks"></a>Remarks  
 A meno che non venga usata l'opzione WITHNOWAIT, SHUTDOWN arresta [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eseguendo le operazioni seguenti:  
  
1.  Disabilitazione degli account di accesso, tranne quelli dei membri dei ruoli predefiniti del server **sysadmin** e **serveradmin**.  
  
    > [!NOTE]  
    >  Per visualizzare un elenco di tutti gli utenti correnti, eseguire **sp_who**.  
  
2.  Attesa del completamento delle istruzioni Transact-SQL o delle stored procedure in esecuzione. Per visualizzare un elenco di tutti i processi e i blocchi attivi, eseguire rispettivamente **sp_who** e **sp_lock**.  
  
3.  Inserimento di un checkpoint in ogni database.  
  
 Tramite l'istruzione SHUTDOWN è possibile ridurre la quantità di lavoro per il recupero automatico richiesta quando i membri del ruolo predefinito del server **sysadmin** riavviano [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Per arrestare l'esecuzione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile utilizzare altri strumenti e metodi. Tali strumenti e metodi creano un checkpoint in tutti i database. È possibile scaricare dalla cache dei dati tutti i dati di cui è stato eseguito il commit e arrestare il server:  
  
-   Utilizzando Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Eseguendo **net stop mssqlserver** dal prompt dei comandi per un'istanza predefinita oppure eseguendo **net stop mssql$***instancename* dal prompt dei comandi per un'istanza denominata.  
  
-   Utilizzando Servizi nel Pannello di controllo.  
  
 Se **sqlservr.exe** è stato avviato dal prompt dei comandi, per arrestare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] premere CTRL+C. In questo modo, tuttavia, non viene inserito un checkpoint.  
  
> [!NOTE]  
>  Se si utilizza uno di questi metodi per arrestare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene inviato il messaggio `SERVICE_CONTROL_STOP` a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="permissions"></a>Autorizzazioni  
 Le autorizzazioni per l'istruzione SHUTDOWN vengono assegnate ai membri dei ruoli predefiniti del server **sysadmin** e **serveradmin** e non sono trasferibili.  
  
## <a name="see-also"></a>Vedere anche  
 [CHECKPOINT &#40;Transact-SQL&#41;](../../t-sql/language-elements/checkpoint-transact-sql.md)   
 [sp_lock &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md)   
 [sp_who &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)   
 [Applicazione sqlservr](../../tools/sqlservr-application.md)   
 [Avviare, arrestare, sospendere, riprendere, riavviare il motore di database, SQL Server Agent o SQL Server Browser](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
  
