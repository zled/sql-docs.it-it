---
title: "Abilitare la registrazione per l&#39;esecuzione di pacchetti nel server SSIS | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SQL13.SSIS.SSMS.ISMANAGECUSTOMIZEDLOGGINGLEVEL.F1"
ms.assetid: 8930c63c-bc6f-46c2-b428-b3c29ee89a7d
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 19
---
# Abilitare la registrazione per l&#39;esecuzione di pacchetti nel server SSIS
  Questo argomento descrive come impostare o modificare il livello di registrazione per un pacchetto quando si esegue un pacchetto che è stato distribuito nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Il livello di registrazione impostato quando si esegue il pacchetto sostituisce il livello di registrazione del pacchetto configurato in fase di progettazione in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Vedere [Abilitare la registrazione di pacchetti in SQL Server Data Tools](../../integration-services/performance/enable-package-logging-in-sql-server-data-tools.md) per altre informazioni.  
  
 In **Proprietà server** di SQL Server, nella proprietà **Server logging level** (Livello di registrazione del server), è possibile selezionare un livello di registrazione predefinito per l'intero server. È possibile scegliere uno dei livelli di registrazione predefiniti descritti in questo argomento oppure è possibile selezionare un livello di registrazione personalizzato esistente. Il livello di registrazione selezionato viene applicato per impostazione predefinita a tutti i pacchetti distribuiti nel catalogo SSIS. Si applica anche per impostazione predefinita a un passaggio del processo di SQL Agent che esegue un pacchetto SSIS.  
  
 È anche possibile specificare il livello di registrazione per un singolo pacchetto con uno dei metodi indicati di seguito. In questo argomento viene illustrato il primo metodo.  
  
-   Configurazione di un'istanza di esecuzione di un pacchetto tramite la finestra di dialogo Esegui pacchetto  
  
-   Impostazione dei parametri per un'istanza di esecuzione usando il valore [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)  
  
-   Configurazione di un processo di SQL Server Agent per l'esecuzione di un pacchetto tramite la finestra di dialogo Nuovo passaggio di processo.  
  
## Per impostare il livello di registrazione per un pacchetto mediante la finestra di dialogo Esegui pacchetto  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], passare al pacchetto in Esplora oggetti.  
  
2.  Fare clic con il pulsante destro del mouse sul pacchetto e selezionare **Esegui**.  
  
3.  Selezionare la scheda **Avanzate** nella finestra di dialogo **Esecuzione pacchetto**.  
  
4.  In **Livello di registrazione**, selezionare il livello di registrazione. Questo argomento contiene una descrizione dei valori disponibili.  
  
5.  Completare le eventuali altre configurazione pacchetto, quindi fare clic su **OK** per eseguire il pacchetto.  
  
## Selezionare un livello di registrazione  
 Sono disponibili i livelli di registrazione predefiniti seguenti. È anche possibile selezionare un livello di registrazione personalizzato esistente. Questo argomento contiene una descrizione dei livelli di registrazione personalizzati.  
  
|Livello di registrazione|Description|  
|-------------------|-----------------|  
|Nessuno|La registrazione è disabilitata. Solo lo stato dell'esecuzione del pacchetto viene registrato.|  
|Basic|Tutti gli eventi sono registrati, ad eccezione di eventi personalizzati e di diagnostica. Si tratta del valore predefinito.|  
|RuntimeLineage|Raccoglie i dati necessari a tenere traccia delle informazioni di derivazione nel flusso di dati. È possibile analizzare queste informazioni di derivazione per mappare la relazione di derivazione tra attività. Gli ISV e sviluppatori possono creare strumenti personalizzati di mapping della derivazione con queste informazioni.|  
|Prestazioni|Vengono registrati solo le statistiche sulle prestazioni e gli eventi OnError e OnWarning.<br /><br /> Nel report **Prestazioni di esecuzione** vengono visualizzati il tempo di attività e il tempo totale per i componenti flusso di dati del pacchetto. Queste informazioni sono disponibili se il livello di registrazione dell'ultima esecuzione del pacchetto è stato impostato su **Prestazioni** o **Dettagliato**. Per altre informazioni, vedere [Report per il server Integration Services](../../integration-services/performance/reports-for-the-integration-services-server.md).<br /><br /> La vista [catalog.execution_component_phases](../../integration-services/system-views/catalog-execution-component-phases.md) visualizza le ore di inizio e di fine per i componenti flusso di dati, per ogni fase di esecuzione. In questa vista vengono visualizzate le informazioni per i componenti solo quando il livello di registrazione dell'esecuzione del pacchetto è impostato su **Prestazioni** o **Dettagliato**.|  
|Dettagliato|Tutti gli eventi vengono registrati, inclusi gli eventi personalizzati e di diagnostica.<br /><br /> Gli eventi personalizzati includono quelli registrati dalle attività di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Per altre informazioni sugli eventi personalizzati, vedere [Messaggi personalizzati per la registrazione](../../integration-services/performance/custom-messages-for-logging.md).<br /><br /> L'evento **DiagnosticEx** rappresenta un esempio di un evento di diagnostica. Ogni volta che un'attività Esegui pacchetto esegue un pacchetto figlio, l'evento acquisisce i valori dei parametri passati ai pacchetti figlio.<br /><br /> L'evento **DiagnosticEx** consente inoltre di ottenere i nomi delle colonne in cui si verificano errori a livello di riga. Questo evento scrive una mappa di derivazione del flusso di dati nel log. È quindi possibile cercare il nome della colonna in questa mappa di derivazione usando l'identificatore della colonna acquisito da un output degli errori.  Per ulteriori informazioni, vedere [Error Handling in Data](../../integration-services/data-flow/error-handling-in-data.md).<br /><br /> Il valore della colonna di messaggio per **DiagnosticEx** è testo XML. Per visualizzare il testo del messaggio per l'esecuzione del pacchetto, eseguire una query nella vista [catalog.operation_messages &#40;database SSISDB&#41;](../../integration-services/system-views/catalog-operation-messages-ssisdb-database.md). Notare che l'evento **DiagnosticEx** non mantiene gli spazi vuoti nel relativo output XML per ridurre le dimensioni del log. Per migliorare la leggibilità, copiare il log in un editor XML come Visual Studio, che supporta la formattazione XML e l'evidenziazione della sintassi.<br /><br /> Nella vista [catalog.execution_data_statistics](../../integration-services/system-views/catalog-execution-data-statistics.md) viene visualizzata una riga ogni volta che un componente flusso di dati invia dati a un componente downstream, per l'esecuzione di un pacchetto. Il livello di registrazione deve essere impostato su **Dettagliato** per acquisire queste informazioni nella vista.|  
  
## Creare e gestire i livelli di registrazione personalizzati con la finestra di dialogo Gestione del livello di registrazione personalizzato  
 È possibile creare livelli di registrazione personalizzati che raccolgono solo le statistiche e gli eventi desiderati. Facoltativamente, è anche possibile acquisire il contesto degli eventi, che include i valori delle variabili, le stringhe di connessione e le proprietà del componente. Quando si esegue un pacchetto, è possibile selezionare un livello di registrazione personalizzato in tutti i casi in cui è possibile selezionare un livello di registrazione predefinito.  
  
> [!TIP]  
>  Per acquisire i valori delle variabili del pacchetto, la proprietà **IncludeInDebugDump** delle variabili deve essere impostata su **True**.  
  
1.  Per creare e gestire i livelli di registrazione personalizzati, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] fare clic con il pulsante destro del mouse sul database SSISDB e scegliere**Livello di registrazione personalizzato** per aprire la finestra di dialogo **Gestione del livello di registrazione personalizzato**. L'elenco **Livelli di registrazione personalizzati** contiene tutti i livelli di registrazione personalizzati esistenti.  
  
2.  Per **creare** un nuovo livello di registrazione personalizzato, fare clic su **Crea**, quindi specificare un nome e una descrizione. Nelle schede **Statistiche** ed **Eventi** selezionare le statistiche e gli eventi da raccogliere. Nella scheda **Eventi** selezionare facoltativamente **Includi contesto** per singoli eventi. Fare quindi clic su **Salva**.  
  
3.  Per **aggiornare** un livello di registrazione personalizzato esistente, selezionarlo nell'elenco, riconfigurarlo, quindi fare clic su **Salva**.  
  
4.  Per **eliminare** un livello di registrazione personalizzato esistente, selezionarlo nell'elenco, quindi fare clic su **Elimina**.  
  
 **Autorizzazioni per i livelli di registrazione personalizzati.**  
  
-   Tutti gli utenti del database SSISDB possono visualizzare i livelli di registrazione personalizzati e selezionare un livello di registrazione personalizzato quando eseguono i pacchetti.  
  
-   Solo gli utenti nel ruolo ssis_admin o sysadmin possono creare, aggiornare o eliminare i livelli di registrazione personalizzati.  
  
## Vedere anche  
 [Registrazione di Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md)   
 [Abilitare la registrazione di pacchetti in SQL Server Data Tools](../../integration-services/performance/enable-package-logging-in-sql-server-data-tools.md)  
  
  