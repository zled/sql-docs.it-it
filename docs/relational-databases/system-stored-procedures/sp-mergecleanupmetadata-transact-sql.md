---
title: sp_mergecleanupmetadata (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_mergecleanupmetadata_TSQL
- sp_mergecleanupmetadata
helpviewer_keywords: sp_mergecleanupmetadata
ms.assetid: 892f8628-4cbe-4cc3-b959-ed45ffc24064
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7f13d51e68d864410bab57b2723fd2e89cac18dd
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spmergecleanupmetadata-transact-sql"></a>sp_mergecleanupmetadata (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Deve essere utilizzato solo nelle topologie di replica che includono server che eseguono versioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prima di [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Service Pack 1. **sp_mergecleanupmetadata** consente agli amministratori di pulizia dei metadati nel **MSmerge_genhistory**, **MSmerge_contents** e **MSmerge_tombstone** tabelle di sistema. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_mergecleanupmetadata [ [ @publication = ] 'publication' ]  
    [ , [ @reinitialize_subscriber = ] 'reinitialize_subscriber' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication =** ] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* è **sysname**, il valore predefinito è  **%** , che rimuove i metadati per tutte le pubblicazioni. Se viene specificata in modo esplicito, la pubblicazione deve essere esistente.  
  
 [  **@reinitialize_subscriber =** ] **'***sottoscrittore***'**  
 Specifica se reinizializzare il Sottoscrittore. *Sottoscrittore* è **nvarchar (5)**, può essere **TRUE** o **FALSE**, il valore predefinito è **TRUE**. Se **TRUE**, sottoscrizioni vengono contrassegnate per la reinizializzazione. Se **FALSE**, le sottoscrizioni non sono contrassegnate per la reinizializzazione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_mergecleanupmetadata** deve essere utilizzato solo nelle topologie di replica che includono server che eseguono versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prima di [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Service Pack 1. Per le topologie in cui è incluso solo [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Service Pack 1 o versioni successive, è consigliabile utilizzare la pulizia dei metadati basata sulla memorizzazione automatica. Quando si esegue questa stored procedure, è importante tenere presente che le dimensioni del file di log nel computer di esecuzione sono destinate ad aumentare, a volte in modo consistente.  
  
> [!CAUTION]  
>  Dopo aver **sp_mergecleanupmetadata** viene eseguito, per impostazione predefinita, tutte le sottoscrizioni nei Sottoscrittori delle pubblicazioni che includono i metadati archiviati **MSmerge_genhistory**, **MSmerge_contents**  e **MSmerge_tombstone** sono contrassegnati per la reinizializzazione, le modifiche in sospeso nel Sottoscrittore vengono perse, e lo snapshot corrente è contrassegnato come obsoleto.  
  
> [!NOTE]  
>  Se sono presenti più pubblicazioni in un database e uno di tali pubblicazioni viene utilizzato un periodo di memorizzazione infinito (**@retention**=**0**), l'esecuzione  **sp_mergecleanupmetadata** non pulizia delle replica di tipo merge i metadati per il database di rilevamento. È pertanto opportuno utilizzare il periodo di memorizzazione infinito con cautela.  
  
 Quando si esegue questa stored procedure, è possibile scegliere se reinizializzare i sottoscrittori impostando il  **@reinitialize_subscriber**  parametro **TRUE** (impostazione predefinita) o **FALSE**. Se **sp_mergecleanupmetadata** viene eseguita con il  **@reinitialize_subscriber**  parametro impostato su **TRUE**, uno snapshot viene riapplicato nel Sottoscrittore, anche se la sottoscrizione è stata creato senza uno snapshot (ad esempio, se i dati dello snapshot e lo schema sono stati applicati manualmente o esistevano già nel Sottoscrittore) iniziale. Impostazione del parametro su **FALSE** deve essere usata con cautela, poiché se la pubblicazione non viene reinizializzata, è necessario assicurarsi che i dati nel server di pubblicazione e nel Sottoscrittore sono sincronizzati.  
  
 Indipendentemente dal valore di  **@reinitialize_subscriber** , **sp_mergecleanupmetadata** processi che siano tentando di caricare le modifiche in un sottoscrittore di ripubblicazione o di un server di pubblicazione di tipo merge ha esito negativo se sono presenti in corso Quando che viene richiamata la stored procedure.  
  
 **Esecuzione di sp_mergecleanupmetadata con @reinitialize_subscriber = TRUE:**  
  
1.  È consigliabile, ma non richiesto, arrestare tutti gli aggiornamenti nei database di pubblicazione e sottoscrizione. Se l'esecuzione degli aggiornamenti continua, gli aggiornamenti effettuati in un Sottoscrizione dall'ultimo processo di tipo merge andranno perduti quando la pubblicazione viene reinizializzata. Viene tuttavia conservata la convergenza dei dati.  
  
2.  Eseguire un'operazione di merge tramite l'agente di merge. È consigliabile utilizzare il **: convalida** opzione della riga di comando dell'agente in ogni sottoscrittore quando si esegue l'agente di Merge. Se si eseguono operazioni di merge in modalità continua, vedere *considerazioni speciali per unisce in modalità continua* più avanti in questa sezione.  
  
3.  Dopo aver completato tutte le unioni, eseguire **sp_mergecleanupmetadata**.  
  
4.  Eseguire **sp_reinitmergepullsubscription** su tutti i sottoscrittori che utilizzano sottoscrizioni pull denominato o anonimo per garantire la convergenza dei dati.  
  
5.  Se si eseguono operazioni di merge in modalità continua, vedere *considerazioni speciali per unisce in modalità continua* più avanti in questa sezione.  
  
6.  Rigenerare i file di snapshot per tutte le pubblicazioni di tipo merge a tutti i livelli. Se si tenta di eseguire il merge senza rigenerare prima lo snapshot, viene richiesto di rigenerare lo snapshot.  
  
7.  Eseguire il backup del database di pubblicazione. Se non si esegue questa operazione, dopo il ripristino del database di pubblicazione può verificarsi un errore del processo di merge.  
  
 **Esecuzione di sp_mergecleanupmetadata con @reinitialize_subscriber = FALSE:**  
  
1.  Arrestare **tutti** gli aggiornamenti al database di pubblicazione e sottoscrizione.  
  
2.  Eseguire un'operazione di merge tramite l'agente di merge. È consigliabile utilizzare il **: convalida** opzione della riga di comando dell'agente in ogni sottoscrittore quando si esegue l'agente di Merge. Se si eseguono operazioni di merge in modalità continua, vedere *considerazioni speciali per unisce in modalità continua* più avanti in questa sezione.  
  
3.  Dopo aver completato tutte le unioni, eseguire **sp_mergecleanupmetadata**.  
  
4.  Se si eseguono operazioni di merge in modalità continua, vedere *considerazioni speciali per unisce in modalità continua* più avanti in questa sezione.  
  
5.  Rigenerare i file di snapshot per tutte le pubblicazioni di tipo merge a tutti i livelli. Se si tenta di eseguire il merge senza rigenerare prima lo snapshot, viene richiesto di rigenerare lo snapshot.  
  
6.  Eseguire il backup del database di pubblicazione. Se non si esegue questa operazione, dopo il ripristino del database di pubblicazione può verificarsi un errore del processo di merge.  
  
 **Considerazioni speciali per merge in modalità continua**  
  
 In caso di esecuzione di operazioni di merge in modalità continua, è necessario eseguire una delle operazioni seguenti:  
  
-   Arrestare l'agente di Merge e quindi eseguire un'altra operazione di merge senza il **-continua** parametro specificato.  
  
-   Disattivare la pubblicazione con **sp_changemergepublication** per garantire che eventuali operazioni di merge in modalità continua che eseguono il polling dello stato della pubblicazione abbiano esito negativo.  
  
    ```  
    EXEC central..sp_changemergepublication @publication = 'dynpart_pubn', @property = 'status', @value = 'inactive'  
    ```  
  
 Dopo aver completato passaggio 3 dell'esecuzione **sp_mergecleanupmetadata**, riprendere merge in modalità continua in base a come è stata arrestata. Eseguire una delle operazioni seguenti:  
  
-   Aggiungere il **– Continuous** parametro per l'agente di Merge.  
  
-   Riattivare la pubblicazione con **sp_changemergepublication.**  
  
    ```  
    EXEC central..sp_changemergepublication @publication = 'dynpart_pubn', @property = 'status', @value = 'active'  
    ```  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_mergecleanupmetadata**.  
  
 Per utilizzare questa stored procedure, il server di pubblicazione deve eseguire [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. I sottoscrittori devono eseguire [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] o [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0, Service Pack 2.  
  
## <a name="see-also"></a>Vedere anche  
 [MSmerge_genhistory &#40; Transact-SQL &#41;](../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md)   
 [MSmerge_contents &#40; Transact-SQL &#41;](../../relational-databases/system-tables/msmerge-contents-transact-sql.md)   
 [MSmerge_tombstone &#40; Transact-SQL &#41;](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md)  
  
  
