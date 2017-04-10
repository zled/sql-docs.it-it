---
title: "Ruoli Integration Services (servizio SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sicurezza [Integration Services], ruoli"
  - "ruolo db_ssisoperator"
  - "ruolo db_ssisadmin"
  - "ruoli predefiniti dei database [Integration Services]"
  - "pacchetti [Integration Services], sicurezza"
  - "ruoli [Integration Services]"
  - "ruolo db_ssisltduser"
ms.assetid: 9702e90c-fada-4978-a473-1b1423017d80
caps.latest.revision: 50
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 50
---
# Ruoli Integration Services (servizio SSIS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] fornisce alcuni ruoli predefiniti a livello di database per consentire l'accesso sicuro ai pacchetti archiviati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. I ruoli disponibili sono diversi a seconda di dove si salvano i pacchetti, nel database del catalogo SSIS (SSISDB) o nel database msdb.  
  
## Ruoli nel database del catalogo SSIS (SSISDB)  
 Il database del catalogo SSIS (SSISDB) fornisce i seguenti ruoli predefiniti a livello di database per proteggere l'accesso ai pacchetti e alle relative informazioni.  
  
-   **ssis_admin**. Questo ruolo fornisce l'accesso amministrativo completo al database del catalogo SSIS.  
  
-   **ssis_logreader** Questo ruolo fornisce le autorizzazioni per accedere a tutte le viste correlate ai log operativi di SSISDB.  
  
     L'elenco delle viste include: [catalog].[projects], [catalog].[packages], [catalog].[operations], [catalog].[extended_operation_info], [catalog].[operation_messages], [catalog].[event_messages], [catalog].[execution_data_statistics], [catalog].[execution_component_phases], [catalog].[execution_data_taps], [catalog].[event_message_context], [catalog].[executions], [catalog].[executables], [catalog].[executable_statistics], [catalog].[validations], [catalog].[execution_parameter_values] e [catalog].[execution_property_override_values].  
  
## Ruoli all'interno del database msdb  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] include i tre ruoli predefiniti a livello di database, **db_ssisadmin**, **db_ssisltduser** e **db_ssisoperator**, per il controllo dell'accesso ai pacchetti salvati nel database **msdb**. I ruoli vengono assegnati a un pacchetto in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Le assegnazioni dei ruoli vengono salvate nel database **msdb** .  
  
### Azioni di lettura e scrittura  
 La tabella seguente descrive le azioni di lettura e scrittura di Windows e i ruoli predefiniti del database in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Ruolo|Azione di lettura|Azione di scrittura|  
|----------|-----------------|------------------|  
|**db_ssisadmin**<br /><br /> o<br /><br /> **sysadmin**|Enumerazione dei propri pacchetti.<br /><br /> Enumerazione di tutti i pacchetti.<br /><br /> Visualizzazione dei propri pacchetti.<br /><br /> Visualizzazione di tutti i pacchetti.<br /><br /> Esecuzione dei propri pacchetti.<br /><br /> Esecuzione di tutti i pacchetti.<br /><br /> Esportazione dei propri pacchetti.<br /><br /> Esportazione di tutti i pacchetti.<br /><br /> Esecuzione di tutti i pacchetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.|Importazione di pacchetti.<br /><br /> Eliminazione dei propri pacchetti.<br /><br /> Eliminazione di tutti i pacchetti.<br /><br /> Modifica dei propri ruoli di pacchetto.<br /><br /> Modifica di tutti i ruoli di pacchetto.<br /><br /> <br /><br /> **\*\* Avviso \*\***I membri dei ruoli db_ssisadmin e dc_admin possono essere in grado di elevare i privilegi a sysadmin. Questa elevazione dei privilegi può verificarsi perché tali ruoli possono modificare i pacchetti [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e i pacchetti [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] possono essere eseguiti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando il contesto di sicurezza sysadmin di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Per impedire questa elevazione dei privilegi durante l'esecuzione dei piani di manutenzione, set di raccolta dati e altri pacchetti [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], configurare i processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent che eseguono pacchetti in modo da utilizzare un account proxy con privilegi limitati o aggiungere solo i membri sysadmin ai ruoli db_ssisadmin e dc_admin.|  
|**db_ssisltduser**|Enumerazione dei propri pacchetti.<br /><br /> Enumerazione di tutti i pacchetti.<br /><br /> Visualizzazione dei propri pacchetti.<br /><br /> Esecuzione dei propri pacchetti.<br /><br /> Esportazione dei propri pacchetti.|Importazione di pacchetti.<br /><br /> Eliminazione dei propri pacchetti.<br /><br /> Modifica dei propri ruoli di pacchetto.|  
|**db_ssisoperator**|Enumerazione di tutti i pacchetti.<br /><br /> Visualizzazione di tutti i pacchetti.<br /><br /> Esecuzione di tutti i pacchetti.<br /><br /> Esportazione di tutti i pacchetti.<br /><br /> Esecuzione di tutti i pacchetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.|Nessuno|  
|**Amministratori di Windows**|Visualizzazione delle informazioni di esecuzione di tutti i pacchetti in esecuzione.|Arresto di tutti i pacchetti in esecuzione.|  
  
### Tabella Sysssispackages  
 La tabella **sysssispackages** del database **msdb** include i pacchetti che sono stati salvati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [sysssispackages &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysssispackages-transact-sql.md).  
  
 Le colonne della tabella **sysssispackages** contengono informazioni sui ruoli assegnati ai pacchetti.  
  
-   Nella colonna **readerrole** è indicato il ruolo con accesso in lettura al pacchetto.  
  
-   Nella colonna **writerrole** è indicato il ruolo con accesso in scrittura al pacchetto.  
  
-   La colonna **ownersid** include l'ID di sicurezza (SID) univoco dell'utente che ha creato il pacchetto. Questa colonna definisce pertanto il proprietario del pacchetto.  
  
### Permissions  
 Per impostazione predefinita, le autorizzazioni dei ruoli predefiniti a livello di database **db_ssisadmin** e **db_ssisoperator** e l'ID di sicurezza univoco dell'utente che ha creato il pacchetto si applicano al ruolo lettura per il pacchetto, mentre le autorizzazioni del ruolo **db_ssisadmin** e l'ID di sicurezza univoco dell'utente che ha creato il pacchetto si applicano al ruolo scrittura. Per disporre dell'accesso in lettura per il pacchetto, l'utente deve essere membro del ruolo **db_ssisadmin**, **db_ssisltduser** o **db_ssisoperator**. Per disporre dell'accesso in scrittura, l'utente deve essere membro del ruolo **db_ssisadmin**.  
  
### Accesso ai pacchetti  
 I ruoli predefiniti del database funzionano congiuntamente ai ruoli definiti dall'utente, ovvero i ruoli creati dall'utente in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e usati per l'assegnazione di autorizzazioni ai pacchetti. Per poter accedere a un pacchetto, un utente deve essere membro del ruolo definito dall'utente e del ruolo predefinito del database di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] appropriato. Se, ad esempio, gli utenti sono membri del ruolo definito dall'utente **AuditUsers** assegnato a un pacchetto, per poter accedere in lettura al pacchetto devono essere membri anche del ruolo **db_ssisadmin**, **db_ssisltduser** o **db_ssisoperator**.  
  
 Se non si assegna alcun ruolo definito dall'utente ai pacchetti, l'accesso verrà determinato dai ruoli predefiniti a livello di database.  
  
 Per poter assegnare i ruoli definiti dall'utente ai pacchetti, è prima necessario aggiungerli al database **msdb**. È possibile creare nuovi ruoli del database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 I ruoli a livello di database di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] concedono diritti per le tabelle di sistema di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] nel database msdb.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Per poter eseguire la connessione al Motore di database e accedere al database **msdb**, è necessario che si stato avviato il servizio MSSQLSERVER.  
  
 Per assegnare ruoli ai pacchetti, è necessario completare le attività seguenti.  
  
-   **Aprire Esplora oggetti e connettersi a Integration Services**  
  
     Per poter assegnare ruoli ai pacchetti in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], è necessario aprire Esplora oggetti in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e connettersi a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
     Per poter eseguire la connessione a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , è necessario che il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]sia stato avviato.  
  
-   **Assegnazione dei ruoli lettura e scrittura ai pacchetti**  
  
     È possibile assegnare un ruolo lettura o scrittura a ogni pacchetto.  
  
## Attività correlate  
  
-   [Assegnazione di un ruolo lettura e scrittura a un pacchetto](../../integration-services/service/assign-a-reader-and-writer-role-to-a-package.md)  
  
-   [Creazione di un ruolo definito dall'utente](../../integration-services/service/create-a-user-defined-role.md)  
  
-   [Connessione a Integration Services](../../integration-services/service/connect-to-integration-services.md)  
  
  