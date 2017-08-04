---
title: Creare un flusso di lavoro personalizzato (Master Data Services) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 8e4403e9-595c-4b6b-9d0c-f6ae1b2bc99d
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: dacc515af7f4d05fc2bad2fd43535bc27c13ea76
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="create-a-custom-workflow-master-data-services"></a>Creare un flusso di lavoro personalizzato (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] vengono utilizzate le regole business per creare soluzioni di base per il flusso di lavoro, come l'aggiornamento e la convalida automatici dei dati e l'invio di notifiche mediante posta elettronica in base alle condizioni specificate. Quando è necessaria un'elaborazione più complessa di quella fornita dalle azioni predefinite del flusso di lavoro, utilizzare un flusso di lavoro personalizzato. Un flusso di lavoro personalizzato è un assembly .NET che viene creato. Quando viene chiamato l'assembly del flusso di lavoro, il codice può eseguire qualsiasi azione richiesta dalla situazione. Se ad esempio il flusso di lavoro richiede l'elaborazione di eventi complessi, come le approvazioni multilivello o gli alberi delle decisioni complessi, è possibile configurare [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] in modo da avviare un flusso di lavoro personalizzato che analizza i dati e determina dove inviarli per l'approvazione.  
  
## <a name="how-custom-workflows-are-processed"></a>Elaborazione di flussi di lavoro personalizzati  
 Per l'elaborazione dei flussi di lavoro personalizzati sono necessari tre componenti principali: applicazione Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], SQL Server MDS Workflow Integration Service e assembly del gestore del flusso di lavoro. Di seguito è riportata la procedura di elaborazione di un flusso di lavoro personalizzato mediante tali componenti:  
  
1.  Utilizzare [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] per convalidare un'entità che avvia un flusso di lavoro.  
  
2.  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] invia i membri che soddisfano le condizioni delle regole business a una coda di Service Broker nel database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
3.  A intervalli regolari SQL Server MDS Workflow Integration Service chiama una stored procedure nel database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
4.  Quando questa stored procedure trova i record nella coda di Service Broker, li restituisce a SQL Server MDS Workflow Integration Service.  
  
5.  SQL Server MDS Workflow Integration Service instrada i dati all'assembly del gestore del flusso di lavoro.  
  
> [!NOTE]  
>  Nota: SQL Server MDS Workflow Integration Service deve attivare processi semplici. Se il codice personalizzato richiede un'elaborazione complessa, completare l'elaborazione in un thread separato o all'esterno del processo del flusso di lavoro.  
  
## <a name="configure-master-data-services-for-custom-workflows"></a>Configurare Master Data Services per i flussi di lavoro personalizzati  
 Per creare di un flusso di lavoro personalizzato, è necessario scrivere codice personalizzato e configurare [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] in modo da passare i dati del flusso di lavoro al gestore del flusso di lavoro. Per consentire l'elaborazione del flusso di lavoro personalizzato, effettuare i passaggi seguenti:  
  
1.  Creare un assembly .NET che implementi <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender>.  
  
2.  Configurare SQL Server MDS Workflow Integration Service per la connessione al database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] e per associare un tag al gestore del flusso di lavoro.  
  
3.  Avviare SQL Server MDS Workflow Integration Service.  
  
4.  Creare una regola business in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] per avviare un flusso di lavoro contrassegnato con il nome del gestore del flusso di lavoro.  
  
5.  Applicare la regola business a un membro che attiva il flusso di lavoro personalizzato.  
  
### <a name="create-the-workflow-handler-assembly"></a>Creare l'assembly del gestore del flusso di lavoro  
 Un flusso di lavoro personalizzato è un assembly della libreria di classi .NET che implementa l'interfaccia <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender>. SQL Server MDS Workflow Integration Service chiama il metodo <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> per eseguire il codice. Ad esempio di codice che implementa <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A>, vedere [personalizzato del flusso di lavoro esempio &#40; Master Data Services &#41; ](../../master-data-services/develop/create-a-custom-workflow-example.md).  
  
 Per creare con Visual Studio 2010 un assembly che SQL Server MDS Workflow Integration Service può chiamare per gestire un flusso di lavoro personalizzato, effettuare i passaggi seguenti:  
  
1.  In Visual Studio 2010, creare un nuovo **libreria di classi** progetto che utilizza il linguaggio di propria scelta. Per creare una libreria di classi c#, selezionare il **Visual C# \Windows** tipi di progetto e selezionare il **libreria di classi** modello. Immettere un nome per il progetto, ad esempio **MDSWorkflowTest**, fare clic su **OK**.  
  
2.  Aggiungere un riferimento a Microsoft.MasterDataServices.WorkflowTypeExtender.dll. Questo assembly è reperibile \<la cartella di installazione > \Master Data Services\WebApplication\bin.  
  
3.  Aggiungere ‘using Microsoft.MasterDataServices.Core.Workflow;’ al file del codice C#.  
  
4.  Ereditare da <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender> nella dichiarazione di classe. La dichiarazione di classe deve essere simile a: ‘public class WorkflowTester : IWorkflowTypeExtender’.  
  
5.  Implementare l'interfaccia <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender>. Viene chiamato il metodo <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> da SQL Server MDS Workflow Integration Service per avviare il flusso di lavoro.  
  
6.  Copiare l'assembly nel percorso di SQL Server MDS Workflow Integration eseguibile del servizio, denominato Microsoft.MasterDataServices.Workflow.exe, in \<la cartella di installazione > \Master Data Services\WebApplication\bin.  
  
### <a name="configure-sql-server-mds-workflow-integration-service"></a>Configurare SQL Server MDS Workflow Integration Service  
 Per modificare il file di configurazione di [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] in modo da includere le informazioni di connessione per il database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] e associare un tag all'assembly del gestore del flusso di lavoro, effettuare i passaggi seguenti:  
  
1.  Individuare Microsoft.masterdataservices.workflow.exe in \<la cartella di installazione > \Master Data Services\WebApplication\bin.  
  
2.  Aggiungere le informazioni di connessione al database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] all'impostazione "ConnectionString". Se nell'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono utilizzate regole di confronto con distinzione tra maiuscole e minuscole, il nome del database deve essere immesso nella stessa combinazione di maiuscole e minuscole del database. Il tag di impostazione completo, ad esempio, potrebbe essere analogo al seguente:  
  
    ```xml  
    <setting name="ConnectionString" serializeAs="String">  
        <value>Server=myServer;Database=myDatabase;Integrated Security=True</value>  
    </setting>  
    ```  
  
3.  Sotto l'impostazione "ConnectionString" aggiungere l'impostazione "WorkflowTypeExtenders" per associare il nome di un tag all'assembly del gestore del flusso di lavoro. Esempio:  
  
    ```xml  
    <setting name="WorkflowTypeExtenders" serializeAs="String">  
        <value>TEST=MDSWorkflowTestLib.WorkflowTester, MDSWorkflowTestLib</value>  
    </setting>  
    ```  
  
     Il testo interno del \<valore > è sotto forma di tag \<tag del flusso di lavoro > =\<nome del tipo qualificato dall'assembly del flusso di lavoro >. \<Tag del flusso di lavoro > è il nome utilizzato per identificare l'assembly del gestore del flusso di lavoro quando si crea una regola business in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]. \<nome del tipo qualificato dall'assembly del flusso di lavoro > è il nome completo dello spazio dei nomi della classe di flusso di lavoro, seguito da una virgola, seguito dal nome visualizzato dell'assembly. Se il nome dell'assembly è sicuro, è necessario includere anche le informazioni sulla versione e l'oggetto PublicKeyToken. È possibile includere più \<impostazione > tag se sono stati creati più gestori del flusso di lavoro per diversi tipi di flussi di lavoro.  
  
> [!NOTE]  
>  A seconda della configurazione del server, è possibile che venga visualizzato l'errore "Accesso negato" quando si tenta di salvare il file Microsoft.MasterDataServices.Workflow.exe.config. In tal caso, disabilitare temporaneamente la funzionalità Controllo dell'account utente nel server. A tale scopo, aprire il pannello di controllo, fare clic su **sistema e sicurezza**. In **centro operativo**, fare clic su **impostazioni di controllo Account utente di modifica**. Nel **le impostazioni di controllo Account utente** finestra di dialogo, far scorrere la barra verso il basso in modo che non si sono mai una notifica. Riavviare il computer e ripetere i passaggi precedenti per modificare il file di configurazione. Dopo avere salvato il file, reimpostare le impostazioni del Controllo dell'account utente sul livello predefinito.  
  
### <a name="start-sql-server-mds-workflow-integration-service"></a>Avviare SQL Server MDS Workflow Integration Service  
 Per impostazione predefinita, SQL Server MDS Workflow Integration Service non è installato. Per poter utilizzare il servizio, è necessario prima installarlo. Per una maggiore sicurezza, creare un utente locale per il servizio e concedere all'utente solo le autorizzazioni necessarie per eseguire le operazioni del flusso di lavoro. Per creare un utente e per installare e avviare il servizio, effettuare i passaggi seguenti:  
  
1.  Utilizzare Utenti e gruppi locali per creare un utente locale denominato, ad esempio, mds_workflow_service.  
  
2.  Utilizzare SQL Server Management Studio per concedere all'utente mds_workflow_service l'autorizzazione per eseguire la stored procedure [mdm].[udpExternalActionsGet]. A tale scopo, creare un nuovo account di accesso per l'account mds_workflow_service, creare un nuovo utente nel database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], eseguire il mapping di questo utente all'account di accesso mds_workflow_service e concedere all'utente l'autorizzazione EXECUTE per la stored procedure [mdm].[udpExternalActionsGet].  
  
3.  Concedere all'utente mds_workflow_service l'autorizzazione per eseguire l'assembly del gestore del flusso di lavoro. A tale scopo, aggiungere l'utente mds_workflow_service al **sicurezza** scheda della finestra di **proprietà** del flusso di lavoro assembly del gestore e concedere all'utente mds_workflow_service l'autorizzazione READ ed EXECUTE.  
  
4.  Concedere all'utente mds_workflow_service l'autorizzazione per eseguire l'eseguibile di SQL Server MDS Workflow Integration Service. A tale scopo, aggiungere l'utente mds_workflow_service al **sicurezza** scheda della finestra il **proprietà** di Microsoft.MasterDataServices.Workflow.exe, in \<la cartella di installazione > \Master Data Services\WebApplication\bin e concedere all'utente mds_workflow_service l'autorizzazione READ ed EXECUTE.  
  
5.  Installare SQL Server MDS Workflow Integration Service mediante l'utilità di installazione .NET, denominata InstallUtil.exe. InstallUtil.exe è reperibile nella cartella di installazione .NET, ad esempio C:\Windows\Microsoft.NET\Framework\v4.0.30319\\. Installare SQL Server MDS Workflow Integration Service immettendo in un prompt dei comandi con privilegi elevati il comando seguente:  
  
    ```  
    C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil Microsoft.MasterDataServices.Workflow.exe  
    ```  
  
     Quando richiesto durante l'installazione, specificare l'utente mds_workflow_service.  
  
6.  Avviare SQL Server MDS Workflow Integration Service mediante lo snap-in Servizi. A tale scopo, individuare SQL Server MDS Workflow Integration Service nello snap-in servizi, selezionarlo e fare clic su di **avviare** collegamento.  
  
### <a name="create-a-workflow-business-rule"></a>Creare una regola business del flusso di lavoro  
 Utilizzare [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] per creare e pubblicare una regola business che, quando applicata, consente di avviare il flusso di lavoro. È necessario assicurarsi che la regola business contenga le azioni che modificano i valori dell'attributo, in modo tale che una volta applicata la regola restituisca false. Ad esempio, la regola business potrebbe restituire true quando un valore dell'attributo Price è maggiore di 500 e il valore dell'attributo Approved è vuoto. La regola può includere quindi due azioni: una per impostare il valore dell'attributo Approved su Pending e l'altra per avviare il flusso di lavoro. In alternativa, è possibile creare una regola che utilizzi la condizione “has changed” e aggiungere gli attributi ai gruppi rilevamento modifiche. Per ulteriori informazioni sulle regole di business, vedere [regole Business &#40; Master Data Services &#41; ](../../master-data-services/business-rules-master-data-services.md).  
  
 Per creare una regola business che avvia un flusso di lavoro personalizzato in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], effettuare i passaggi seguenti:  
  
1.  Nell'editor delle regole di business di [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], dopo aver specificato le condizioni della regola business, trascinare il **Avvia flusso di lavoro** azione il **azioni esterne** elenco il **quindi** del riquadro **azione** etichetta.  
  
2.  Nel **Modifica azione** riquadro, nel **tipo flusso di lavoro** , digitare il tag che identifica l'assembly del gestore del flusso di lavoro. Si tratta del tag specificato nel file di configurazione per l'assembly, ad esempio TEST.  
  
3.  Facoltativamente, selezionare il **Includi dati membro** casella di controllo. Questa opzione consente di includere i nomi e i valori degli attributi nel codice XML passato al gestore del flusso di lavoro.  
  
4.  Nel **sito flusso di lavoro** , digitare il nome di un sito Web. Questa opzione potrebbe non essere valida per il flusso di lavoro personalizzato, ma può essere utilizzata per il contesto aggiunto.  
  
5.  Nel **nome flusso di lavoro** , digitare il nome del flusso di lavoro di Visual Studio. Questa opzione potrebbe non essere valida per il flusso di lavoro personalizzato, ma può essere utilizzata per il contesto aggiunto.  
  
6.  Salvare e pubblicare la regola business.  
  
### <a name="apply-business-rules-to-start-a-workflow"></a>Applicare le regole business per avviare un flusso di lavoro  
 Applicare la regola business ai dati per avviare il flusso di lavoro. A tale scopo, utilizzare [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] per modificare l'entità che contiene i membri che di desidera convalidare. Fare clic su **applicare regole business**. In risposta alla regola business, in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] viene popolata la coda di Service Broker del database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]. Quando SQL Server MDS Workflow Integration Service controlla la coda, invia i dati all'assembly del gestore del flusso di lavoro specificato e cancella la coda. L'assembly del gestore del flusso di lavoro esegue qualsiasi azione in esso codificata.  
  
## <a name="troubleshoot-custom-workflows"></a>Risolvere i problemi relativi ai flussi di lavoro personalizzati  
 Se l'assembly del gestore del flusso di lavoro non riceve dati, è possibile provare a eseguire il debug di SQL Server MDS Workflow Integration Service o a visualizzare la coda di Service Broker.  
  
### <a name="debug-sql-server-mds-workflow-integration-service"></a>Eseguire il debug di SQL Server MDS Workflow Integration Service  
 Per eseguire il debug di SQL Server Workflow Integration Service, effettuare i passaggi seguenti:  
  
1.  Utilizzare lo snap-in Servizi per arrestare il servizio.  
  
2.  Aprire un prompt dei comandi, passare al percorso del servizio ed eseguire il servizio in modalità console immettendo Microsoft.MasterDataServices.Workflow.exe -console.  
  
3.  In [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] aggiornare il membro e applicare di nuovo le regole business. I log dettagliati vengono visualizzati nella finestra della console.  
  
### <a name="view-the-service-broker-queue"></a>Visualizzare la coda di Service Broker  
 La coda di Service Broker che contiene i dati master passati come parte del flusso di lavoro è mdm.microsoft/mdm/queue/externalaction. Le code sono reperibili il **Esplora oggetti** di SQL Management Studio, sotto il nodo di Service Broker del [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database. Tenere presente che, se il servizio ha cancellato correttamente la coda, questa sarà vuota.  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di flusso di lavoro personalizzato &#40; Master Data Services &#41;](../../master-data-services/develop/create-a-custom-workflow-example.md)   
 [Descrizione XML del flusso di lavoro personalizzato &#40; Master Data Services &#41;](../../master-data-services/develop/create-a-custom-workflow-xml-description.md)  
  
  
