---
title: "Distribuzione guidata Integration Services | Microsoft Docs"
ms.custom: ""
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.deploymentwizard.f1"
ms.assetid: f3d93e13-2d85-47ff-a913-cda4046491c4
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 14
---
# Distribuzione guidata Integration Services
  La **Distribuzione guidata Integration Services** supporta due modelli di distribuzione:
   - Modello di distribuzione del progetto
   - Modello di distribuzione del pacchetto 
   
 Il **modello di distribuzione del progetto** consente di distribuire un progetto di SQL Server Integration Services (SSIS) come una singola unità nel catalogo SSIS.
 
 Il **modello di distribuzione del pacchetto** consente di distribuire i pacchetti che sono stati aggiornati nel catalogo SSIS senza dover distribuire l'intero progetto. 
 
 > **NOTA:** il modello di distribuzione del progetto è il modello predefinito della procedura guidata.  
  
## Avviare la procedura guidata
Avviare la procedura guidata in uno dei due modi seguenti:

 - Digitare **"Distribuzione guidata di SQL Server"** in Windows Search 

**OPPURE**

 - Cercare il file eseguibile **ISDeploymentWizard.exe** nella cartella di installazione di SQL Server; ad esempio: "C:\Programmi (x86) \Microsoft SQL Server\130\DTS\Binn". 
 
 > **NOTA:** se viene visualizzata la pagina **Introduzione**, fare clic su **Avanti** per passare alla pagina **Seleziona origine**. 
 
 Le impostazioni in questa pagina sono diverse per ogni modello di distribuzione. Seguire la procedura nella sezione [Project Deployment Model](../../integration-services/packages/integration-services-deployment-wizard.md#ProjectModel) o nella sezione [Package Deployment Model](../../integration-services/packages/integration-services-deployment-wizard.md#PackageModel) in base al modello selezionato in questa pagina.  
  
##  <a name="ProjectModel"></a> Modello di distribuzione del progetto  
  
### Seleziona origine  
 Per distribuire un file di distribuzione del progetto creato, selezionare **File distribuzione progetto** e immettere il percorso al file con estensione ispac. Per distribuire un progetto che si trova nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , selezionare **Catalogo di Integration Services**, quindi immettere il nome del server e il percorso del progetto nel catalogo. Fare clic su **Avanti** per visualizzare la pagina **Seleziona destinazione** .  
  
### Seleziona destinazione  
 Per selezionare la cartella di destinazione per il progetto nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , immettere l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o fare clic su **Sfoglia** per effettuare una selezione da un elenco di server. Immettere il percorso del progetto in SSISDB o fare clic su **Sfoglia** per selezionarlo. Fare clic su **Avanti** per visualizzare la pagina **Verifica** .  
  
### Verifica (e distribuisci)  
 La pagina consente di controllare le impostazioni selezionate. È possibile modificare le selezioni facendo clic su **Indietro**o selezionando un qualsiasi passaggio nel riquadro sinistro. Fare clic su **Distribuisci** per avviare il processo di distribuzione.  
  
### Risultati  
 Al termine del processo di distribuzione, verrà visualizzata la pagina **Risultati** . Questa pagina consente di visualizzare l'esito positivo o negativo di ogni azione. Se l'azione non viene completata correttamente, fare clic su **Non riuscito** nella colonna **Risultato** per visualizzare una spiegazione dell'errore. Fare clic su **Salva report...** per salvare i risultati in un file XML oppure su **Chiudi** per uscire dalla procedura guidata.  
  
##  <a name="PackageModel"></a> Modello di distribuzione del pacchetto  
  
### Seleziona origine  
 La pagina **Seleziona origine** in **Distribuzione guidata Integration Services** mostra le impostazioni specifiche per il modello di distribuzione del pacchetto al momento della selezione dell'opzione **Distribuzione di pacchetti** per il **modello di distribuzione**.  
  
 Per selezionare i pacchetti di origine, fare clic sul pulsante **Sfoglia…** per selezionare la **cartella** that contains the packages or type the cartella path in the **Packages cartella path** e fare clic sul pulsante **Aggiorna** nella parte inferiore della pagina. A questo punto, tutti i pacchetti dovrebbero essere visualizzati nella cartella specificata nella casella di riepilogo. Per impostazione predefinita, tutti i pacchetti sono selezionati. Fare clic sulla **casella di controllo** nella prima colonna per scegliere i pacchetti da distribuire nel server.  
  
 Fare riferimento alle colonne **Stato** e **Messaggio** per verificare lo stato del pacchetto. Se lo stato è impostato su **Pronto** o **Avviso**, la distribuzione guidata non blocca il processo di distribuzione. Al contrario, se lo stato è impostato su **Errore**, la procedura guidata interrompe la distribuzione dei pacchetti selezionati. Per visualizzare il dettaglio dei messaggi di avviso/errore, fare clic sul collegamento nella colonna **Messaggio**.  
  
 Se i dati sensibili o i dati del pacchetto sono crittografati con una password, digitarla nella colonna **Password** e fare clic sul pulsante **Aggiorna** per verificare che venga accettata. Se la password è corretta, lo stato verrà modificato in **Pronto** e il messaggio di avviso non verrà più visualizzato. Se sono presenti più pacchetti con la stessa password, selezionare quelli con la stessa password di crittografia, digitarla nella casella di testo **Password** e fare clic sul pulsante **Applica** . La password viene applicata ai pacchetti selezionati.  
  
 Se lo stato di tutti i pacchetti selezionati non è impostato su **Errore**, verrà abilitato il pulsante **Avanti** per proseguire con il processo di distribuzione dei pacchetti.  
  
### Seleziona destinazione  
 Dopo aver selezionato le origini dei pacchetti, fare clic sul pulsante **Avanti** per passare alla pagina **Seleziona destinazione** . I pacchetti devono essere distribuiti in un progetto nel catalogo SSIS (SSISDB). Prima di distribuirli, verificare quindi che il progetto di destinazione esista già nel catalogo SSIS. In caso contrario, creare un progetto vuoto. Nella pagina **Seleziona destinazione** digitare il nome del server nella casella di testo **Nome server** oppure fare clic sul pulsante **Sfoglia…** per selezionare un'istanza del server. Quindi fare clic sul pulsante **Sfoglia…** accanto alla casella di testo **Percorso** per specificare il progetto di destinazione. Se il progetto non esiste, fare clic su **Nuovo progetto…** per creare un progetto vuoto come progetto di destinazione. Il progetto **DEVE** essere creato in una cartella.  
  
### Verifica e distribuisci  
 Fare clic su **Avanti** nella pagina **Seleziona destinazione** per passare alla pagina **Verifica** nella **Distribuzione guidata Integration Services**. Nella pagina della verifica rivedere il report di riepilogo sull'azione di distribuzione. Dopo la verifica, fare clic sul pulsante **Distribuisci** per eseguire l'azione di distribuzione.  
  
### Risultati  
 Al termine del processo di distribuzione, verrà visualizzata la pagina **Risultati** . Nella pagina **Risultati** esaminare i risultati di ogni passaggio nel processo di distribuzione. Nella pagina **Risultati** fare clic su **Salva report** per salvare il report di distribuzione o su **Chiudi** per chiudere la procedura guidata.  
  
## Vedere anche  
 [Distribuire progetti nel server Integration Services](../../integration-services/packages/deploy-projects-to-integration-services-server.md)   
 [Distribuzione di progetti e pacchetti](https://msdn.microsoft.com/library/hh213290.aspx)  
  
  