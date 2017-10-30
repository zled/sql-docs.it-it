---
title: "Procedura dettagliata: Configurare SQL Server Integration Services con scalabilità | Documenti Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 685286966599c4dcd3dc2f7029413c77f3ff2689
ms.openlocfilehash: c386b01043764405872365af379cfdedb036b65f
ms.contentlocale: it-it
ms.lasthandoff: 10/20/2017

---
# <a name="walkthrough-set-up-integration-services-scale-out"></a>Procedura dettagliata: Installare il servizio di scalabilità orizzontale di Integration Services
Impostare [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] scalabile, completare le attività seguenti. 

> [!NOTE]
> Se si sta installando orizzontale in un computer, installare le funzionalità di scalabilità Out Master e di scala Out lavoro nello stesso momento. Quando si installano le due funzionalità nello stesso momento, l'endpoint viene generato automaticamente per la connessione al master di scalabilità orizzontale. 

* [Installare il master di scalabilità orizzontale](#InstallMaster)

* [Installare il ruolo di lavoro di scalabilità orizzontale](#InstallWorker)

* [Installare il certificato client del ruolo di lavoro di scalabilità orizzontale](#InstallCert)

* [Aprire la porta del firewall](#Firewall)

* [Avviare i servizi Master di scalabilità orizzontale e Ruolo di lavoro di scalabilità orizzontale di SQL Server](#Start)

* [Abilitare il master di scalabilità orizzontale](#EnableMaster)

* [Abilitare la modalità di autenticazione di SQL Server](#EnableAuth)

* [Abilitare il ruolo di lavoro di scalabilità orizzontale](#EnableWorker)

## <a name="InstallMaster"></a> Installare il master di scalabilità orizzontale

Per abilitare la funzionalità di scalabilità Out Master, è necessario installare servizi motore di Database, [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)]e quando si configura la funzionalità di scalabilità Out Master [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. 

Per informazioni su come installare i servizi del motore di database e [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)], vedere [Installare il motore di database di SQL Server](../../database-engine/install-windows/install-sql-server-database-engine.md) e [Installazione di Integration Services](../install-windows/install-integration-services.md).
> [!NOTE]
> Per utilizzare l'account di autenticazione SQL predefinito per Scale Out della registrazione, selezionare la modalità mista per la modalità di autenticazione nella pagina Configurazione motore di Database durante l'installazione del motore di Database. Vedere [modificare l'account per la registrazione orizzontale](change-logdb-account.md) per ulteriori informazioni.

**Per installare la funzionalità Master di scalabilità orizzontale, usare l'Installazione guidata di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] o il prompt dei comandi.**

- Passaggi dell'Installazione guidata di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]
  1.  Nel **Selezione funzionalità** selezionare **scala Out Master**, presente in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].   
  ![Selezione della funzionalità Master](media/feature-select-master.PNG)
  
  2.  Nella pagina **Configurazione server** selezionare l'account per l'esecuzione del **servizio Master di scalabilità orizzontale di SQL Server Integration Services** e selezionare **Tipo di avvio**.  
  ![Configurazione server](media/server-config.PNG)
  3.  Nella pagina **Configurazione del master di scalabilità orizzontale di Integration Services** specificare il numero di porta che verrà usato dal master per comunicare con il ruolo di lavoro. Il numero di porta predefinito è 8391.  
  ![Configurazione di master](media/master-config.PNG "Master Config")
  4.  Specificare il certificato SSL utilizzato per proteggere la comunicazione tra scala Out Master e di scala Out lavoro effettuando una delle operazioni seguenti.
    * Consentire il processo di installazione di creare un certificato SSL autofirmato predefinito facendo **creare un nuovo certificato SSL**.  Il certificato predefinito viene installato in Autorità di certificazione radice attendibili, Computer locale. È possibile specificare il CN nel certificato. Il nome host dell'endpoint master deve essere incluso in CN. Per impostazione predefinita, sono inclusi il nome del computer e l'ip del nodo principale.
    * Selezionare un durante SSL esistente nel computer locale facendo **usare un certificato SSL esistente** e quindi fare clic su **Sfoglia** per selezionare un certificato. Nella casella di testo viene visualizzata l'identificazione personale del certificato. Facendo clic su **Sfoglia** vengono visualizzati i certificati archiviati in Autorità di certificazione radice attendibili, Computer locale. Il certificato selezionato deve essere archiviato in questo percorso.       
![Configurazione di master 2](media/master-config-2.PNG "Master configurazione 2")
  5.  Completare l'Installazione guidata di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
- Passaggi per il prompt dei comandi

    Seguire le istruzioni riportate in [Installazione di SQL Server dal prompt dei comandi](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md). Impostare i parametri relativi al master di scalabilità orizzontale nel modo seguente:
  1.  Aggiungere IS_Master al parametro /FEATURES
  2.  Configurare scala Out Master specificando i seguenti parametri e i relativi valori: /ISMASTERSVCACCOUNT, /ISMASTERSVCPASSWORD, /ISMASTERSVCSTARTUPTYPE, /ISMASTERSVCPORT, /ISMasterSVCSSLCertCN(optional), /ISMASTERSVCTHUMBPRINT(optional).

> [!Note]
> Se la scala Out Master non è installato insieme al motore di Database e il motore di Database è un'istanza denominata, è necessario configurare SqlServerName nel file di configurazione del servizio di scala Out Master dopo l'installazione. Vedere [scala Out Master](integration-services-ssis-scale-out-master.md) per informazioni dettagliate.

## <a name="InstallWorker"></a> Installare il ruolo di lavoro di scalabilità orizzontale
 
Per abilitare il ruolo di lavoro di scalabilità orizzontale, è necessario installare [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] e la funzionalità Ruolo di lavoro di scalabilità orizzontale durante la procedura di installazione di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].

**Per installare la funzionalità Ruolo di lavoro di scalabilità orizzontale, usare l'Installazione guidata di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] o il prompt dei comandi.**

- Passaggi dell'Installazione guidata di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]
  1.  Nel **Selezione funzionalità** selezionare **scala Out lavoro**, presente in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].   
  ![Selezione della funzionalità Ruolo di lavoro](media/feature-select-worker.PNG)
  2. Nella pagina **Configurazione server** selezionare l'account per l'esecuzione del **servizio Ruolo di lavoro di scalabilità orizzontale di SQL Server Integration Services** e selezionare **Tipo di avvio**.    
  ![Configurazione server 2](media/server-config-2.PNG "configurazione Server 2")
  3. Nella pagina **Configurazione del ruolo di lavoro di scalabilità orizzontale di Integration Services** specificare l'endpoint per la connessione al master di scalabilità orizzontale. 
      > [!Note]
      > È possibile ignorare la configurazione di un nodo di lavoro (passaggio 3 e 4) qui e associare la scala Out lavoro scala Out master con [scala Out Manager](integration-services-ssis-scale-out-manager.md) dopo l'installazione.

    - Per un **un computer** ambiente, l'endpoint viene generato automaticamente quando si scala Out Master e scala Out lavoro vengono installati nello stesso momento. 
    - Per un **più computer** ambiente, l'endpoint è costituito il nome o l'IP del computer con scala Out Master installato e il numero di porta specificato durante l'installazione di scala Out Master.    
   ![Configurazione di lavoro 1](media/worker-config.PNG "lavoro configurazione 1")    

  4. Per un **più computer** ambiente, specificare il certificato client SSL viene utilizzato per convalidare scala Out Master. Per un **un computer** ambiente, non è necessario specificare il certificato SSL del client. 
  
     > [!NOTE]
     > Quando il certificato SSL utilizzato dal scala Out Master è autofirmato, un certificato SSL client corrispondente è necessario installare nel computer con scala il lavoro. Se è fornire il percorso del file per il certificato SSL del client sul **scala Out lavoro configurazione di Integration Services** pagina, il certificato verrà installato automaticamente; in caso contrario, è necessario installare il certificato manualmente in seguito. 
     
     Fare clic su **Sfoglia** per trovare il file del certificato (con estensione cer). Per utilizzare il certificato SSL, selezionare il file SSISScaleOutMaster.cer si trova in \<unità\>: \Programmi\Microsoft SQL Server\140\DTS\Binn nel computer in cui è installato scala Out Master.   
   ![Configurazione di lavoro 2](media/worker-config-2.PNG "configurazione lavoro 2")
  5. Completare l'Installazione guidata di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
- Passaggi per il prompt dei comandi

    Seguire le istruzioni riportate in [Installazione di SQL Server dal prompt dei comandi](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md). Impostare i parametri relativi al ruolo di lavoro di scalabilità orizzontale nel modo seguente:
    1.  Aggiungere IS_Worker al parametro /FEATURES
    2. Configurare scala Out lavoro specificando i seguenti parametri e i relativi valori: /ISWORKERSVCACCOUNT, /ISWORKERSVCPASSWORD, /ISWORKERSVCSTARTUPTYPE, /ISWORKERSVCMASTER(optional), /ISWORKERSVCCERT(optional).

 
## <a name="InstallCert"></a> Installare il certificato client del ruolo di lavoro di scalabilità orizzontale

Durante l'installazione di scala il lavoro, un certificato di lavoro verrà automaticamente creato e installato nel computer. Inoltre, viene installato un certificato client corrispondente, SSISScaleOutWorker.cer, in \<unità\>:\Programmi\Microsoft SQL Server\140\DTS\Binn. Per scala Out Master autenticare lo scala i thread di lavoro, è necessario aggiungere questo certificato client nell'archivio radice del computer locale con scala Out Master.
  
Per aggiungere il certificato client nell'archivio radice, fare doppio clic sul file con estensione cer e quindi fare clic su **Installa certificato** nella finestra di dialogo Certificato. Verrà visualizzata l' **Importazione guidata certificati** .  

## <a name="Firewall"></a> Aprire la porta del firewall

Aprire la porta specificata durante l'installazione di scala Out Master e la porta di SQL Server (1433 per impostazione predefinita), utilizza Windows Firewall nel computer Master Out di scala.
    
## <a name="Start"></a> Avviare i servizi Master di scalabilità orizzontale e Ruolo di lavoro di scalabilità orizzontale di SQL Server

Se il tipo di avvio dei servizi non è impostato su automatico durante l'installazione, avviare i servizi: SQL Server Integration Services scala Out Master 14.0 (SSISScaleOutMaster140) e SQL Server Integration Services scala Out lavoro 14.0 (SSISScaleOutWorker140). 

> [!Note]
> Dopo aver aperto la porta del firewall, è necessario riavviare il servizio di scala il lavoro.
   
## <a name="EnableMaster"></a> Abilitare il master di scalabilità orizzontale

Fare clic su **Abilita questo server come master di scalabilità orizzontale di SSIS** nella finestra di dialogo **Crea catalogo** quando si crea il catalogo SSISDB in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio_md](../../includes/ssmanstudio-md.md)]. In alternativa, scala Out Master può essere abilitata con [scala Out Manager](integration-services-ssis-scale-out-manager.md) dopo la creazione di catalogo.

## <a name="EnableAuth"></a> Abilitare la modalità di autenticazione di SQL Server
Se [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] l'autenticazione non è abilitata durante l'installazione del motore di Database, attivare la modalità di autenticazione di SQL Server il [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] istanza che ospita il catalogo SSISDB. 

Quando l'autenticazione di SQL Server è disabilitata, l'esecuzione dei pacchetti non viene bloccata. Tuttavia, il log di esecuzione non sarà in grado di scrivere in SSISDB.

## <a name="EnableWorker"></a> Abilitare il ruolo di lavoro di scalabilità orizzontale

Scala il lavoro può essere abilitata tramite [scala Out Manager](integration-services-ssis-scale-out-manager.md), che fornisce l'interfaccia utente grafica; o attivata tramite stored procedure, vedere di seguito.

Per abilitare un ruolo di lavoro di scalabilità orizzontale, eseguire la stored procedure *[catalog].[enable_worker_agent]* con **WorkerAgentId** come parametro. 

Dopo la registrazione del ruolo di lavoro di scalabilità orizzontale con il master, viene restituito il valore **WorkerAgentId** dalla vista di database *[catalog].[worker_agents]* in SSISDB. Una volta avviati i servizi Master e Ruolo di lavoro di scalabilità orizzontale, la registrazione richiede alcuni minuti.

#### <a name="example"></a>Esempio
Questo esempio viene abilitato lo scala i thread di lavoro su computerA.
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
L'installazione della funzionalità di scalabilità orizzontale è completata. È ora possibile eseguire pacchetti in orizzontale. Per altre informazioni, vedere [Eseguire pacchetti nel servizio di scalabilità orizzontale di Integration Services (SSIS)](run-packages-in-integration-services-ssis-scale-out.md).

