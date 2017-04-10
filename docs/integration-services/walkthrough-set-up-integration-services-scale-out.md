---
title: "Procedura dettagliata: Installare il servizio di scalabilit&#224; orizzontale di Integration Services | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cabb78a2-f234-46c3-842d-53aa2df8dfb3
caps.latest.revision: 10
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 7
---
# Procedura dettagliata: Installare il servizio di scalabilit&#224; orizzontale di Integration Services

Per installare il servizio di scalabilità orizzontale di [!INCLUDE[ssISnoversion_md](../includes/ssisnoversion-md.md)], completare le attività seguenti. 

> [!NOTE] Se si installa il servizio in un solo computer, è consigliabile installare contemporaneamente le funzionalità Master di scalabilità orizzontale e Ruolo di lavoro di scalabilità orizzontale. Quando si installano le due funzionalità nello stesso momento, l'endpoint viene generato automaticamente per la connessione al master di scalabilità orizzontale. 

* [Installare il master di scalabilità orizzontale](#InstallMaster)

* [Installare il ruolo di lavoro di scalabilità orizzontale](#InstallWorker)

* [Installare il certificato client del ruolo di lavoro di scalabilità orizzontale](#InstallCert)

* [Aprire la porta del firewall](#Firewall)

* [Avviare i servizi Master di scalabilità orizzontale e Ruolo di lavoro di scalabilità orizzontale di SQL Server](#Start)

* [Abilitare il master di scalabilità orizzontale](#EnableMaster)

* [Abilitare la modalità di autenticazione di SQL Server](#EnableAuth)

* [Abilitare il ruolo di lavoro di scalabilità orizzontale](#EnableWorker)

## <a name="a-nameinstallmastera-install-scale-out-master"></a><a name="InstallMaster"></a> Installare il master di scalabilità orizzontale

Per abilitare il master di scalabilità orizzontale, è necessario installare i servizi del motore di database, [!INCLUDE[ssISnoversion_md](../includes/ssisnoversion-md.md)] e la funzionalità Master di scalabilità orizzontale durante la procedura di installazione di [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)]. 

Per informazioni su come installare i servizi del motore di database e [!INCLUDE[ssISnoversion_md](../includes/ssisnoversion-md.md)], vedere [Installare il motore di database di SQL Server](../database-engine/install-windows/install-sql-server-database-engine.md) e [Installazione di Integration Services](../integration-services/install-windows/install-integration-services.md).
> [!NOTE]
> Durante l'installazione del motore di database, selezionare Modalità mista come Modalità di autenticazione nella pagina Configurazione del motore di database. 

**Per installare la funzionalità Master di scalabilità orizzontale, usare l'Installazione guidata di [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] o il prompt dei comandi.**

- Passaggi dell'Installazione guidata di [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)]
  1.  Nella pagina **Selezione funzionalità** selezionare la funzionalità **Master di scalabilità orizzontale**, elencata sotto [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].   
  ![Selezione della funzionalità Master](../integration-services/media/feature-select-master.PNG)
  
  2.  Nella pagina **Configurazione server** selezionare l'account per l'esecuzione del **servizio Master di scalabilità orizzontale di SQL Server Integration Services** e selezionare **Tipo di avvio**.  
  ![Configurazione server](../integration-services/media/server-config.PNG)
  3.  Nella pagina **Configurazione del master di scalabilità orizzontale di Integration Services** specificare il numero di porta che verrà usato dal master per comunicare con il ruolo di lavoro. Il numero di porta predefinito è 8391.  
  ![Master Config](../integration-services/media/master-config.PNG "Master Config")
  4.  Specificare il certificato SSL usato per proteggere le comunicazioni tra il master e il ruolo di lavoro di scalabilità orizzontale effettuando una delle operazioni seguenti.
    * Fare clic su **Crea un nuovo certificato SSL** per creare automaticamente un certificato SSL autofirmato predefinito. Il certificato predefinito viene installato in Autorità di certificazione radice attendibili, Computer locale.
    * Selezionare un certificato SSL esistente nel computer locale facendo clic su **Usa un certificato SSL esistente** e quindi fare clic su **Sfoglia**. Nella casella di testo viene visualizzata l'identificazione personale del certificato. Facendo clic su **Sfoglia** vengono visualizzati i certificati archiviati in Autorità di certificazione radice attendibili, Computer locale. Il certificato selezionato deve essere archiviato in questo percorso.       
![Master Config 2](../integration-services/media/master-config-2.PNG "Master Config 2")
  5.  Completare l'Installazione guidata di [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)].
- Passaggi per il prompt dei comandi

    Seguire le istruzioni riportate in [Installazione di SQL Server dal prompt dei comandi](../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md). Impostare i parametri relativi al master di scalabilità orizzontale nel modo seguente:
  1.  Aggiungere IS_Master al parametro /FEATURES
  2.  Configurare il master di scalabilità orizzontale con i parametri seguenti: /ISMASTERSVCACCOUNT, /ISMASTERSVCPASSWORD, /ISMASTERSVCSTARTUPTYPE, /ISMASTERSVCPORT, /ISMASTERSVCTHUMBPRINT(facoltativp).
  
## <a name="a-nameinstallworkera-install-scale-out-worker"></a><a name="InstallWorker"></a> Installare il ruolo di lavoro di scalabilità orizzontale
 
Per abilitare il ruolo di lavoro di scalabilità orizzontale, è necessario installare [!INCLUDE[ssISnoversion_md](../includes/ssisnoversion-md.md)] e la funzionalità Ruolo di lavoro di scalabilità orizzontale durante la procedura di installazione di [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)].

**Per installare la funzionalità Ruolo di lavoro di scalabilità orizzontale, usare l'Installazione guidata di [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] o il prompt dei comandi.**

- Passaggi dell'Installazione guidata di [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)]
  1.  Nella pagina **Selezione funzionalità** selezionare la funzionalità **Ruolo di lavoro di scalabilità orizzontale**, elencata sotto [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].   
  ![Selezione della funzionalità Ruolo di lavoro](../integration-services/media/feature-select-worker.PNG)
  2. Nella pagina **Configurazione server** selezionare l'account per l'esecuzione del **servizio Ruolo di lavoro di scalabilità orizzontale di SQL Server Integration Services** e selezionare **Tipo di avvio**.    
  ![Server Config 2](../integration-services/media/server-config-2.PNG "Server Config 2")
  3. Nella pagina **Configurazione del ruolo di lavoro di scalabilità orizzontale di Integration Services** specificare l'endpoint per la connessione al master di scalabilità orizzontale. 
    - Per un ambiente con **singolo computer**, l'endpoint viene generato automaticamente quando si installano il master e il ruolo di lavoro di scalabilità orizzontale nello stesso momento. 
    - Per un ambiente con **più computer**, l'endpoint è costituito dal nome o dall'indirizzo IP del computer in cui è installato il master di scalabilità orizzontale e dal numero di porta specificato durante l'installazione del master di scalabilità orizzontale.    
   ![Worker Config 1](../integration-services/media/worker-config-1.PNG "Worker Config 1")
    
  4. Per un ambiente con **più computer**, specificare il certificato SSL client che viene usato per convalidare il master di scalabilità orizzontale. Per un ambiente con **singolo computer**, non è necessario specificare il certificato SSL client. 
  
     > [!NOTE] Quando il certificato SSL usato dal master di scalabilità orizzontale è autofirmato, è necessario installare un certificato SSL client corrispondente nel computer in cui è installato il ruolo di lavoro di scalabilità orizzontale. Se si specifica il percorso di file del certificato SSL client nella pagina **Configurazione del ruolo di lavoro di scalabilità orizzontale di Integration Services**, il certificato verrà installato automaticamente. In caso contrario, sarà necessario installarlo manualmente, in un secondo momento. 
     
     Fare clic su **Sfoglia** per trovare il file del certificato (con estensione cer). Per usare il certificato SSL predefinito, selezionare il file SSISScaleOutMaster.cer in \<unità\>:\Programmi\Microsoft SQL Server\140\DTS\Binn nel computer in cui è installato il master di scalabilità orizzontale.   
   ![Worker Config 2](../integration-services/media/worker-config-2.PNG "Worker Config 2")
  5. Completare l'Installazione guidata di [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)].
- Passaggi per il prompt dei comandi

    Seguire le istruzioni riportate in [Installazione di SQL Server dal prompt dei comandi](../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md). Impostare i parametri relativi al ruolo di lavoro di scalabilità orizzontale nel modo seguente:
    1.  Aggiungere IS_Worker al parametro /FEATURES
    2. Configurare il ruolo di lavoro di scalabilità orizzontale con i parametri seguenti: /ISWORKERSVCACCOUNT, /ISWORKERSVCPASSWORD, /ISWORKERSVCSTARTUPTYPE, /ISWORKERSVCMASTER(facoltativo), /ISWORKERSVCCERT(facoltativo).

 
## <a name="a-nameinstallcerta-install-scale-out-worker-client-certificate"></a><a name="InstallCert"><a/> Installare il certificato client del ruolo di lavoro di scalabilità orizzontale

Durante l'installazione del ruolo di lavoro di scalabilità orizzontale, nel computer viene creato e installato automaticamente un certificato del ruolo di lavoro. Inoltre, viene installato un certificato client corrispondente, SSISScaleOutWorker.cer, in \<unità\>:\Programmi\Microsoft SQL Server\140\DTS\Binn. Per consentire al master di scalabilità orizzontale di autenticare il ruolo di lavoro, è necessario aggiungere questo certificato client nell'archivio radice del computer locale con il master di scalabilità orizzontale.
  
Per aggiungere il certificato client nell'archivio radice, fare doppio clic sul file con estensione cer e quindi fare clic su **Installa certificato** nella finestra di dialogo Certificato. Verrà visualizzata l'**Importazione guidata certificati**.  

## <a name="a-namefirewalla-open-firewall-port"></a><a name="Firewall"><a/> Aprire la porta del firewall

Aprire la porta specificata durante l'installazione del master di scalabilità orizzontale, usando Windows Firewall nel computer in cui è installato il master.
    
## <a name="a-namestarta-start-sql-server-scale-out-master-and-worker-services"></a><a name="Start"></a> Avviare i servizi Master di scalabilità orizzontale e Ruolo di lavoro di scalabilità orizzontale di SQL Server

Se durante l'installazione non è stato specificato il tipo di avvio automatico dei servizi, avviare i servizi: Master di scalabilità orizzontale di SQL Server Integration Services 14.0 (SSISScaleOutMaster140) e Ruolo di lavoro di scalabilità orizzontale di SQL Server Integration Services 14.0 (SSISScaleOutWorker140). 

> [!NOTE]
>Dopo aver aperto la porta del firewall, è necessario riavviare il servizio Ruolo di lavoro di scalabilità orizzontale.
   
## <a name="a-nameenablemastera-enable-scale-out-master"></a><a name="EnableMaster"></a> Abilitare il master di scalabilità orizzontale

Fare clic su **Abilita questo server come master di scalabilità orizzontale di SSIS** nella finestra di dialogo **Crea catalogo** quando si crea il catalogo SSISDB in [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio_md](../includes/ssmanstudio-md.md)].

## <a name="a-nameenableautha-enable-sql-server-authentication-mode"></a><a name="EnableAuth"></a> Abilitare la modalità di autenticazione di SQL Server
Se l'autenticazione [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] non è abilitata durante l'installazione del motore di database, abilitare la modalità di autenticazione di SQL Server sull'istanza di [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] che ospita il catalogo SSISDB. 

Quando l'autenticazione di SQL Server è disabilitata, l'esecuzione dei pacchetti non viene bloccata. Tuttavia, il log di esecuzione non sarà in grado di scrivere in SSISDB.

## <a name="a-nameenableworkera-enable-scale-out-worker"></a><a name="EnableWorker"></a> Abilitare il ruolo di lavoro di scalabilità orizzontale
Per abilitare un ruolo di lavoro di scalabilità orizzontale, eseguire la stored procedure *[catalog].[enable_worker_agent]* con **WorkerAgentId** come parametro. 

Dopo la registrazione del ruolo di lavoro di scalabilità orizzontale con il master, viene restituito il valore **WorkerAgentId** dalla vista di database *[catalog].[worker_agents]* in SSISDB. Una volta avviati i servizi Master e Ruolo di lavoro di scalabilità orizzontale, la registrazione richiede alcuni minuti.

### <a name="example"></a>Esempio
Questo esempio abilita il ruolo di lavoro di scalabilità orizzontale sul computer MachineA.
```tsql
SELECT WorkerAgentId, MachineName FROM [catalog].[worker_agents]
GO
-- Result: --
-- WorkerAgentId                           MachineName --
-- 6583054A-E915-4C2A-80E4-C765E79EF61D    MachineA    --

EXEC [catalog].[enable_worker_agent] '6583054A-E915-4C2A-80E4-C765E79EF61D'
GO 
```
## <a name="next-steps"></a>Passaggi successivi
L'installazione della funzionalità di scalabilità orizzontale è completata. È ora possibile eseguire pacchetti nel servizio di scalabilità orizzontale. Per altre informazioni, vedere [Eseguire pacchetti nel servizio di scalabilità orizzontale di Integration Services (SSIS)](../integration-services/run-packages-in-integration-services-ssis-scale-out.md).

