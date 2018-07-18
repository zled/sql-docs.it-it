---
title: Amministrazione automatizzata in un'organizzazione | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- enterprise automatic administration [SQL Server]
- multiserver administration [SQL Server]
- SQL Server Agent jobs, multiserver administration
- jobs [SQL Server Agent], multiserver administration
- master servers [SQL Server], about master servers
- target servers [SQL Server], about target servers
- master servers [SQL Server]
- multiple instances of SQL Server
- target servers [SQL Server]
ms.assetid: 44d8365b-42bd-4955-b5b2-74a8a9f4a75f
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: f0245dbc2322c5a0e19fcd18eb5b213422403094
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="automated-administration-across-an-enterprise"></a>Amministrazione automatizzata in un'organizzazione
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

L'automazione dell'amministrazione in più istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] viene definita *amministrazione multiserver*. Utilizzare l'amministrazione multiserver per eseguire le operazioni seguenti:  
  
-   Gestione di due o più server.  
  
-   Pianificazione dei flussi di informazioni tra server aziendali per il data warehousing.  
  
Una soddisfacente configurazione di amministrazione multiserver è costituita da almeno un server master e almeno un server di destinazione. Il server master distribuisce processi ai server di destinazione e riceve eventi da tali server. Nel server master è inoltre archiviata la copia centrale delle definizioni di processo per i processi eseguiti nei server di destinazione. I server di destinazione stabiliscono connessioni periodiche al server master per aggiornare l'elenco dei processi pianificati. Se nel server master è presente un nuovo processo, questo viene scaricato dal server di destinazione. Dopo il completamento del processo, il server di destinazione stabilisce una nuova connessione al server master e trasmette lo stato del processo. Si noti che la definizione del processo deve essere la stessa durante l'esecuzione di qualsiasi attività correlata al database.  
  
Nella figura seguente viene illustrata la relazione tra il server master e quello di destinazione:  
  
![Configurazione dell'amministrazione multiserver](../../ssms/agent/media/multisvr.gif "Configurazione dell'amministrazione multiserver")  
  
Se si amministrano server di reparto in un'azienda di grandi dimensioni, è possibile definire i seguenti elementi:  
  
-   Un processo di backup composto da diversi passaggi.  
  
-   Gli operatori da notificare in caso di errore durante di backup.  
  
-   Una pianificazione dell'esecuzione per il processo di backup.  
  
È possibile creare il processo di backup una sola volta nel server master e quindi integrare ogni server di reparto come server di destinazione. Dal momento dell'integrazione, in tutti i server di reparto verrà eseguito lo stesso processo di backup, anche se il processo sarà stato definito una volta sola.  
  
> [!NOTE]  
> Le caratteristiche di amministrazione multiserver sono riservate ai membri del ruolo sysadmin. Un membro del ruolo sysadmin nel server di destinazione non può tuttavia modificare le operazioni eseguite in tale server dal server master. Questa misura di sicurezza impedisce l'eliminazione accidentale di passaggi del processo ed evita l'interruzione delle operazioni nel server di destinazione.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
[Creazione di un ambiente multiserver](../../ssms/agent/create-a-multiserver-environment.md)  
Contiene informazioni sulla creazione e la gestione di server master e di destinazione.  
  
[Scegliere l'account di servizio SQL Server Agent adatto ad ambienti multiserver](../../ssms/agent/choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)  
Contiene informazioni sull'impatto dell'utilizzo degli account di Windows non amministrativi o dell'account di sistema locale sul servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent negli ambienti multiserver.  
  
[Impostazione delle opzioni di crittografia nei server di destinazione](../../ssms/agent/set-encryption-options-on-target-servers.md)  
Sono incluse informazioni sull'impostazione della sottochiave MsxEncryptChannelOptions del Registro di sistema di[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent nei server di destinazione.  
  
[Gestire i processi in un'azienda](../../ssms/agent/manage-jobs-across-an-enterprise.md)  
Contiene informazioni su verifica dello stato dei processi, modifica dei server di destinazione per i processi, sincronizzazione dei clock dei server e polling dei server master per determinare lo stato attuale dei processi.  
  
[Risolvere i problemi relativi a processi multiserver che utilizzano proxy](../../ssms/agent/troubleshoot-multiserver-jobs-that-use-proxies.md)  
Contiene informazioni sulla risoluzione dei problemi relativi a processi multiserver che utilizzano proxy con esito negativo.  
  
[Polling dei server](../../ssms/agent/poll-servers.md)  
Contiene informazioni su come fare in modo, implicitamente ed esplicitamente, che i server di destinazione eseguano il polling dei server master per sincronizzare le informazioni sui processi.  
  
[Gestione di eventi](../../ssms/agent/manage-events.md)  
Contiene informazioni sull'inoltro di eventi da server di destinazione a server master.  
  
[Ottimizzazione dell'amministrazione automatizzata in un'organizzazione](../../ssms/agent/tune-automated-administration-across-an-enterprise.md)  
Sono incluse informazioni sull'utilizzo ottimale delle caratteristiche di ottimizzazione automatica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]durante l'amministrazione automatizzata in un ambiente multiserver.  
  
## <a name="see-also"></a>Vedere anche  
[Considerazioni sulla compatibilità con le versioni precedenti per l'installazione del motore di database di SQL Server](http://msdn.microsoft.com/en-us/10de5ec6-d3cf-42ef-aa62-1bdf3fbde841)  
[Registrazione di server](http://msdn.microsoft.com/en-us/c2a2513e-fa09-419c-99e7-a12d57c5a0db)  
[sp_add_targetservergroup](http://msdn.microsoft.com/en-us/acb69343-d766-46ff-b771-0c7655c5231a)  
[sp_delete_targetserver](http://msdn.microsoft.com/en-us/cc438701-ad91-419d-9f23-ebc4c548c700)  
[sp_delete_targetservergroup](http://msdn.microsoft.com/en-us/d8dd838e-64aa-419f-9ccb-ff04908cf3e4)  
[sp_help_downloadlist](http://msdn.microsoft.com/en-us/745b265b-86e8-4399-b928-c6969ca1a2c8)  
[sp_help_jobserver](http://msdn.microsoft.com/en-us/57971787-f9f5-4199-9f64-c2b61a308906)  
[sp_help_targetservergroup](http://msdn.microsoft.com/en-us/ec3a4a68-b591-431c-9518-053ede522d0c)  
[sp_resync_targetserver](http://msdn.microsoft.com/en-us/40e44df7-d3e3-44ee-b149-08aba629a21f)  
[sp_update_targetservergroup](http://msdn.microsoft.com/en-us/4ac65ed6-e07e-40e4-a282-13bfd92dfa41)  
[sysjobservers](http://msdn.microsoft.com/en-us/9abcc20f-a421-4591-affb-62674d04575e)  
[syslogins](http://msdn.microsoft.com/en-us/4cb34f17-a4bb-469f-a218-71f074e6308f)  
[systargetservers](http://msdn.microsoft.com/en-us/479d1314-be37-4d19-ac9c-419fc9110e53)  
  
