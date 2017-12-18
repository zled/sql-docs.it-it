---
title: 'Procedura dettagliata: installare SQL Server Integration Services Scale Out | Microsoft Docs'
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ec9744a1efb0e78aca55e85e7f9f3eca007de5a2
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="walkthrough-set-up-integration-services-scale-out"></a>Procedura dettagliata: Installare il servizio di scalabilità orizzontale di Integration Services
Installare [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] Scale Out completando le attività seguenti. 

> [!NOTE]
> Se si installa Scale Out in un solo computer, installare contemporaneamente le funzionalità Scale Out Master e Scale Out Worker. Quando si installano le due funzionalità nello stesso momento, l'endpoint viene generato automaticamente per la connessione al master di scalabilità orizzontale. 

* [Installare il master di scalabilità orizzontale](#InstallMaster)

* [Installare il ruolo di lavoro di scalabilità orizzontale](#InstallWorker)

* [Installare il certificato client del ruolo di lavoro di scalabilità orizzontale](#InstallCert)

* [Aprire la porta del firewall](#Firewall)

* [Avviare i servizi Master di scalabilità orizzontale e Ruolo di lavoro di scalabilità orizzontale di SQL Server](#Start)

* [Abilitare il master di scalabilità orizzontale](#EnableMaster)

* [Abilitare la modalità di autenticazione di SQL Server](#EnableAuth)

* [Abilitare il ruolo di lavoro di scalabilità orizzontale](#EnableWorker)

## <a name="InstallMaster"></a> Installare il master di scalabilità orizzontale

Per abilitare Scale Out Master, è necessario installare i servizi del motore di database, [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] e la funzionalità Scale Out Master durante l'installazione di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. 

Per informazioni su come installare i servizi del motore di database e [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)], vedere [Installare il motore di database di SQL Server](../../database-engine/install-windows/install-sql-server-database-engine.md) e [Installazione di Integration Services](../install-windows/install-integration-services.md).
> [!NOTE]
> Per usare l'account di autenticazione SQL predefinito per la registrazione di Scale Out, selezionare Modalità mista come modalità di autenticazione nella pagina Configurazione del motore di database durante l'installazione del motore di database. Per altre informazioni, vedere [Modificare l'account per la registrazione di Scale Out](change-logdb-account.md).

**Per installare la funzionalità Master di scalabilità orizzontale, usare l'Installazione guidata di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] o il prompt dei comandi.**

- Passaggi dell'Installazione guidata di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]
  1.  Nella pagina **Selezione funzionalità** selezionare la funzionalità **Scale Out Master** elencata sotto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].   
  ![Selezione della funzionalità Master](media/feature-select-master.PNG)
  
  2.  Nella pagina **Configurazione server** selezionare l'account per l'esecuzione del **servizio Master di scalabilità orizzontale di SQL Server Integration Services** e selezionare **Tipo di avvio**.  
  ![Configurazione server](media/server-config.PNG)
  3.  Nella pagina **Configurazione del master di scalabilità orizzontale di Integration Services** specificare il numero di porta che verrà usato dal master per comunicare con il ruolo di lavoro. Il numero di porta predefinito è 8391.  
  ![Configurazione Master](media/master-config.PNG "Configurazione Master")
  4.  Specificare il certificato SSL usato per proteggere la comunicazione tra Scale Out Master e Scale Out Worker eseguendo una delle operazioni seguenti.
    * Fare clic su **Crea un nuovo certificato SSL** per creare automaticamente un certificato SSL autofirmato predefinito.  Il certificato predefinito viene installato in Autorità di certificazione radice attendibili, Computer locale. In questo certificato è possibile specificare i nomi comuni (CN). Il nome host dell'endpoint master deve essere incluso nei nomi comuni. Per impostazione predefinita, sono inclusi il nome del computer e l'IP del nodo master.
    * Selezionare un certificato SSL esistente nel computer locale facendo clic su **Usa un certificato SSL esistente** e poi su **Sfoglia** per selezionare un certificato. Nella casella di testo viene visualizzata l'identificazione personale del certificato. Facendo clic su **Sfoglia** vengono visualizzati i certificati archiviati in Autorità di certificazione radice attendibili, Computer locale. Il certificato selezionato deve essere archiviato in questo percorso.       
![Configurazione Master 2](media/master-config-2.PNG "Configurazione Master 2")
  5.  Completare l'Installazione guidata di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
- Passaggi per il prompt dei comandi

    Seguire le istruzioni riportate in [Installazione di SQL Server dal prompt dei comandi](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md). Impostare i parametri relativi al master di scalabilità orizzontale nel modo seguente:
  1.  Aggiungere IS_Master al parametro /FEATURES
  2.  Configurare Scale Out Master specificando i parametri e i valori seguenti: /ISMASTERSVCACCOUNT, /ISMASTERSVCPASSWORD, /ISMASTERSVCSTARTUPTYPE, /ISMASTERSVCPORT, /ISMasterSVCSSLCertCN (facoltativo), /ISMASTERSVCTHUMBPRINT (facoltativo).

> [!Note]
> Se Scale Out Master non è installato insieme al motore di database e il motore di database è un'istanza denominata, è necessario configurare SqlServerName nel file di configurazione del servizio di Scale Out Master dopo l'installazione. Per informazioni dettagliate, vedere [Scale Out Master](integration-services-ssis-scale-out-master.md).

## <a name="InstallWorker"></a> Installare il ruolo di lavoro di scalabilità orizzontale
 
Per abilitare il ruolo di lavoro di scalabilità orizzontale, è necessario installare [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] e la funzionalità Ruolo di lavoro di scalabilità orizzontale durante la procedura di installazione di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].

**Per installare la funzionalità Ruolo di lavoro di scalabilità orizzontale, usare l'Installazione guidata di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] o il prompt dei comandi.**

- Passaggi dell'Installazione guidata di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]
  1.  Nella pagina **Selezione funzionalità** selezionare la funzionalità **Scale Out Worker** elencata sotto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].   
  ![Selezione della funzionalità Ruolo di lavoro](media/feature-select-worker.PNG)
  2. Nella pagina **Configurazione server** selezionare l'account per l'esecuzione del **servizio Ruolo di lavoro di scalabilità orizzontale di SQL Server Integration Services** e selezionare **Tipo di avvio**.    
  ![Configurazione server 2](media/server-config-2.PNG "Configurazione Server 2")
  3. Nella pagina **Configurazione del ruolo di lavoro di scalabilità orizzontale di Integration Services** specificare l'endpoint per la connessione al master di scalabilità orizzontale. 
      > [!Note]
      > È possibile ignorare la configurazione del nodo di lavoro (passaggio 3 e 4) e associare l'istanza di Scale Out Worker a Scale Out Master usando [Scale Out Manager](integration-services-ssis-scale-out-manager.md) dopo l'installazione.

    - Per un ambiente con **computer singolo**, l'endpoint viene generato automaticamente quando Scale Out Master e Scale Out Worker vengono installati contemporaneamente. 
    - Per un ambiente con **più computer**, l'endpoint è costituito dal nome o dall'IP del computer in cui è installato Scale Out Master e dal numero di porta specificato durante l'installazione di Scale Out Master.    
   ![Configurazione Worker 1](media/worker-config.PNG "Configurazione Worker 1")    

  4. Per un ambiente con **più computer**, specificare il certificato SSL client che viene usato per convalidare Scale Out Master. Per un ambiente con **computer singolo**, non è necessario specificare il certificato SSL client. 
  
     > [!NOTE]
     > Quando il certificato SSL usato da Scale Out Master è autofirmato, è necessario installare un certificato SSL client corrispondente nel computer in cui è installato Scale Out Worker. Se si specifica il percorso di file del certificato SSL client nella pagina **Configurazione di Integration Services Scale Out Worker**, il certificato verrà installato automaticamente. In caso contrario, sarà poi necessario installarlo manualmente. 
     
     Fare clic su **Sfoglia** per trovare il file del certificato (con estensione cer). Per usare il certificato SSL predefinito, selezionare il file SSISScaleOutMaster.cer in \<unità\>:\Programmi\Microsoft SQL Server\140\DTS\Binn nel computer in cui è installato Scale Out Master.   
   ![Configurazione Worker 2](media/worker-config-2.PNG "Configurazione Worker 2")
  5. Completare l'Installazione guidata di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
- Passaggi per il prompt dei comandi

    Seguire le istruzioni riportate in [Installazione di SQL Server dal prompt dei comandi](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md). Impostare i parametri relativi al ruolo di lavoro di scalabilità orizzontale nel modo seguente:
    1.  Aggiungere IS_Worker al parametro /FEATURES
    2. Configurare Scale Out Worker specificando i parametri e i valori seguenti: /ISWORKERSVCACCOUNT, /ISWORKERSVCPASSWORD, /ISWORKERSVCSTARTUPTYPE, /ISWORKERSVCMASTER (facoltativo), /ISWORKERSVCCERT(facoltativo).

 
## <a name="InstallCert"></a> Installare il certificato client del ruolo di lavoro di scalabilità orizzontale

Durante l'installazione di Scale Out Worker, nel computer viene creato e installato automaticamente un certificato del ruolo di lavoro. Inoltre, viene installato un certificato client corrispondente, SSISScaleOutWorker.cer, in \<unità\>:\Programmi\Microsoft SQL Server\140\DTS\Binn. Per consentire a Scale Out Master di autenticare l'istanza di Scale Out Worker, è necessario aggiungere questo certificato client all'archivio Radice del computer locale in cui è installato Scale Out Master.
  
Per aggiungere il certificato client nell'archivio radice, fare doppio clic sul file con estensione cer e quindi fare clic su **Installa certificato** nella finestra di dialogo Certificato. Verrà visualizzata l' **Importazione guidata certificati** .  

## <a name="Firewall"></a> Aprire la porta del firewall

Aprire la porta specificata durante l'installazione dell'istanza di Scale Out Master e la porta di SQL Server (1433 per impostazione predefinita) usando Windows Firewall nel computer con Scale Out Master.
    
## <a name="Start"></a> Avviare i servizi Master di scalabilità orizzontale e Ruolo di lavoro di scalabilità orizzontale di SQL Server

Se durante l'installazione non è stato specificato il tipo di avvio automatico dei servizi, avviare i servizi: SQL Server Integration Services Scale Out Master 14.0 (SSISScaleOutMaster140) e SQL Server Integration Services Scale Out Worker 14.0 (SSISScaleOutWorker140). 

> [!Note]
> Dopo aver aperto la porta del firewall, è anche necessario riavviare il servizio Scale Out Worker.
   
## <a name="EnableMaster"></a> Abilitare il master di scalabilità orizzontale

Fare clic su **Abilita questo server come master di scalabilità orizzontale di SSIS** nella finestra di dialogo **Crea catalogo** quando si crea il catalogo SSISDB in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio_md](../../includes/ssmanstudio-md.md)]. In alternativa, è possibile abilitare Scale Out Master usando [Scale Out Manager](integration-services-ssis-scale-out-manager.md) dopo che il catalogo è stato creato.

## <a name="EnableAuth"></a> Abilitare la modalità di autenticazione di SQL Server
Se l'autenticazione [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] non è abilitata durante l'installazione del motore di database, abilitare la modalità di autenticazione di SQL Server nell'istanza di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] che ospita il catalogo SSISDB. 

Quando l'autenticazione di SQL Server è disabilitata, l'esecuzione dei pacchetti non viene bloccata. Tuttavia, il log di esecuzione non sarà in grado di scrivere in SSISDB.

## <a name="EnableWorker"></a> Abilitare il ruolo di lavoro di scalabilità orizzontale

Scale Out Worker può essere abilitato tramite [Scale Out Manager](integration-services-ssis-scale-out-manager.md), che specifica l'interfaccia utente grafica oppure tramite stored procedure (vedere di seguito).

Per abilitare un ruolo di lavoro di scalabilità orizzontale, eseguire la stored procedure *[catalog].[enable_worker_agent]* con **WorkerAgentId** come parametro. 

Dopo la registrazione del ruolo di lavoro di scalabilità orizzontale con il master, viene restituito il valore **WorkerAgentId** dalla vista di database *[catalog].[worker_agents]* in SSISDB. Una volta avviati i servizi Master e Ruolo di lavoro di scalabilità orizzontale, la registrazione richiede alcuni minuti.

#### <a name="example"></a>Esempio
Questo esempio abilita l'istanza di Scale Out Worker in computerA.
```sql
SELECT WorkerAgentId, MachineName FROM [catalog].[worker_agents]
GO
-- Result: --
-- WorkerAgentId                           MachineName  --
-- 6583054A-E915-4C2A-80E4-C765E79EF61D    computerA    --

EXEC [catalog].[enable_worker_agent] '6583054A-E915-4C2A-80E4-C765E79EF61D'
GO 
```
## <a name="next-steps"></a>Passaggi successivi
L'installazione della funzionalità di scalabilità orizzontale è completata. È ora possibile eseguire in pacchetti in Scale Out. Per altre informazioni, vedere [Eseguire pacchetti nel servizio di scalabilità orizzontale di Integration Services (SSIS)](run-packages-in-integration-services-ssis-scale-out.md).
