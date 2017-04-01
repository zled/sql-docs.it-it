---
title: "Pacchetto di Integration Services (SSIS) e i parametri del progetto | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.designer.parameter.f1"
  - "sql13.dts.designer.paramterwindow.f1"
ms.assetid: 9ed9ca8e-8b1e-48d9-907d-285516d6562b
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 22
---
# Pacchetto di Integration Services (SSIS) e i parametri del progetto
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Parametri (SSIS) consentono di assegnare valori alle proprietà dei pacchetti in fase di esecuzione del pacchetto. È possibile creare *parametri di progetto* al livello del progetto e *parametri di pacchetto* al livello del pacchetto. I parametri del progetto vengono utilizzati per fornire input esterno ricevuto dal progetto a uno o più pacchetti nel progetto. I parametri del pacchetto consentono di modificare l'esecuzione del pacchetto senza doverlo modificare e ridistribuire.  
  
 In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] è possibile creare, modificare o eliminare i parametri di progetto utilizzando la finestra **Project.params** . Per creare, modificare ed eliminare i parametri di pacchetto, utilizzare la scheda **Parametri** in Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] . Per associare un parametro nuovo o esistente a una proprietà di un'attività, utilizzare la finestra di dialogo **Imposta parametri** . Per ulteriori informazioni sull'utilizzo della finestra **Project.params** e della scheda **Parametri** , vedere [Create Parameters](../Topic/Create%20Parameters.md). Per ulteriori informazioni sulla finestra di dialogo **Imposta parametri** , vedere [Parameterize Dialog Box](../Topic/Parameterize%20Dialog%20Box.md).  
  
## Parametri e modello di distribuzione del pacchetto  
 In generale, se un pacchetto viene distribuito mediante il relativo modello di distribuzione, è necessario utilizzare le configurazioni anziché i parametri.  
  
 Quando si distribuisce un pacchetto che contiene parametri utilizzando il modello di distribuzione del pacchetto e quindi si esegue il pacchetto, i parametri non vengono chiamati durante l'esecuzione. Se il pacchetto contiene espressioni e parametri di pacchetto all'interno del pacchetto, utilizzare i parametri per applicare i valori risultanti in fase di esecuzione. Se il pacchetto contiene parametri di progetto, è possibile che l'esecuzione del pacchetto non venga completata.  
  
## Parametri e modello di distribuzione del progetto  
 Quando si distribuisce un progetto nel server Integration Services (SSIS), è utilizzare viste, stored procedure e [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] dell'interfaccia utente per gestire i parametri di progetto e del pacchetto. Per ulteriori informazioni, vedere gli argomenti seguenti.  
  
-   [Viste & #40; catalogo di Integration Services & #41;](../integration-services/system-views/views-integration-services-catalog.md)  
  
-   [Stored procedure & #40; catalogo di Integration Services & #41;](../integration-services/system-stored-procedures/stored-procedures-integration-services-catalog.md)  
  
-   [Finestra di dialogo Configura](../integration-services/service/configure-dialog-box.md)  
  
-   [Finestra di dialogo Esecuzione pacchetto](../integration-services/packages/execute-package-dialog-box.md)  
  
### Valori di parametri  
 È possibile assegnare fino a tre tipi diversi di valori a un parametro. Quando viene avviata l'esecuzione di un pacchetto, viene utilizzato un solo valore per il parametro e il parametro viene risolto nel relativo valore letterale finale.  
  
 Nella tabella riportata di seguito sono elencati i tipi di valori.  
  
|Nome del valore|Descrizione|Tipo di valore|  
|----------------|-----------------|-------------------|  
|Valore di esecuzione|Valore assegnato a un'istanza specifica di esecuzione del pacchetto. Questa assegnazione esegue l'override di tutti gli altri valori, tuttavia è applicabile a una sola istanza di esecuzione del pacchetto.|Valore letterale|  
|Valore del server|Valore assegnato al parametro nell'ambito del progetto, dopo la distribuzione del progetto nel server Integration Services. Questo valore esegue l'override del valore predefinito di progettazione.|Valore letterale o riferimento a una variabile di ambiente|  
|Valore di progettazione|Valore assegnato al parametro durante la creazione o modifica del progetto in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Questo valore rimane persistente nel progetto.|Valore letterale|  
  
 È possibile utilizzare un solo parametro per assegnare un valore a più proprietà del pacchetto. A una singola proprietà del pacchetto è possibile assegnare un valore solo da un singolo parametro.  
  
###  <a name="executions"></a> Esecuzioni e valori dei parametri  
 L' *esecuzione* è un oggetto che rappresenta una singola istanza di esecuzione del pacchetto. Quando si crea un'esecuzione, è possibile specificare tutti i dettagli necessari per l'esecuzione di un pacchetto, ad esempio i valori dei parametri di esecuzione. Inoltre, è possibile modificare i valori dei parametri per le esecuzioni esistenti.  
  
 Quando si imposta in modo esplicito un valore del parametro di esecuzione, tale valore è applicabile unicamente a quell'istanza particolare di esecuzione. Anziché un valore del server o un valore di progettazione viene utilizzato un valore di esecuzione. Se non si imposta in modo esplicito un valore di esecuzione ed è stato specificato un valore del server, viene utilizzato quest'ultimo.  
  
 Se un parametro è contrassegnato come obbligatorio, è necessario specificare per tale parametro un valore del server o un valore di esecuzione. In caso contrario, il pacchetto corrispondente non viene eseguito. Sebbene al parametro sia associato un valore predefinito in fase di progettazione, non sarà mai utilizzato dopo la distribuzione del progetto.  
  
#### Variabili di ambiente  
 Se un parametro fa riferimento a una variabile di ambiente, il valore letterale di tale variabile viene risolto attraverso il riferimento all'ambiente specificato e applicato al parametro. Il valore del parametro letterale finale utilizzato per l'esecuzione del pacchetto è definito valore del parametro di esecuzione. Il riferimento all'ambiente per un'esecuzione viene specificato tramite la finestra di dialogo **Esegui** .  
  
 Se un parametro del progetto fa riferimento a una variabile di ambiente e il valore letterale della variabile non può essere risolto in fase di esecuzione, viene utilizzato il valore di progettazione. Il valore del server non viene utilizzato.  
  
 Per visualizzare le variabili di ambiente assegnate ai valori del parametro, eseguire una query sulla vista catalog.object_parameters. Per ulteriori informazioni, vedere [object_parameters & #40; SSISDB #41; & Database](../integration-services/system-views/catalog-object-parameters-ssisdb-database.md).  
  
#### Determinazione dei valori dei parametri di esecuzione  
 Le stored procedure e le viste Transact-SQL seguenti possono essere utilizzate per visualizzare e impostare i valori di parametri.  
  
 [Catalog. execution_parameter_values & #40; SSISDB #41; & Database](../integration-services/system-views/catalog-execution-parameter-values-ssisdb-database.md)(visualizzazione)  
 Consente di visualizzare i valori di parametri effettivi che verranno utilizzati da un'esecuzione specifica  
  
 [Catalog. get_parameter_values & #40; SSISDB #41; & Database](../integration-services/system-stored-procedures/catalog-get-parameter-values-ssisdb-database.md) (stored procedure)  
 Consente di risolvere e visualizzare i valori effettivi per il riferimento all'ambiente e al pacchetto specificato  
  
 [object_parameters & #40; SSISDB #41; & Database](../integration-services/system-views/catalog-object-parameters-ssisdb-database.md) (visualizzazione)  
 Consente di visualizzare i parametri e le proprietà per tutti i pacchetti e i progetti nel catalogo di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], inclusi i valori predefiniti del server e i valori predefiniti di progettazione.  
  
 [Catalog. set_execution_parameter_value & #40; Database SSISDB & #41;](../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)  
 Imposta il valore di un parametro per un'istanza di esecuzione nel catalogo di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 È inoltre possibile utilizzare la finestra di dialogo **Esegui pacchetto** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] per modificare il valore di un parametro. Per ulteriori informazioni, vedere [Execute Package Dialog Box](../integration-services/packages/execute-package-dialog-box.md).  
  
 È inoltre possibile utilizzare il dtexec **/parametro** opzione per modificare un valore di parametro. Per altre informazioni, vedere [dtexec Utility](../integration-services/packages/dtexec-utility.md).  
  
### Convalida dei parametri  
 Se i valori dei parametri non possono essere risolti, il pacchetto corrispondente non viene eseguito. Per evitare errori, è possibile convalidare progetti e pacchetti mediante la finestra di dialogo **Convalida** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Tramite la convalida è possibile confermare che tutti i parametri dispongono dei valori necessari o che possono risolvere i valori necessari con riferimenti all'ambiente specifici. Durante la convalida vengono inoltre verificati altri problemi comuni relativi ai pacchetti.  
  
 Per ulteriori informazioni, vedere [Validate Dialog Box](../integration-services/service/validate-dialog-box.md).  
  
### Esempio di parametro  
 In questo esempio viene descritto un parametro denominato **pkgOptions** utilizzato per specificare opzioni per il pacchetto in cui risiede.  
  
 Durante la fase di progettazione, quando il parametro è stato creato in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], il valore predefinito 1 è stato assegnato al parametro. Questo valore predefinito è noto come valore predefinito di progettazione. Se il progetto è stato distribuito nel catalogo SSISDB e non sono stati assegnati altri valori al parametro, durante l'esecuzione del pacchetto alla proprietà del pacchetto corrispondente al parametro **pkgOptions** verrà assegnato il valore 1. Il valore predefinito di progettazione viene reso persistente nel progetto per tutto il ciclo di vita.  
  
 Durante la preparazione di un'istanza specifica di esecuzione del pacchetto, il valore 5 viene assegnato al parametro **pkgOptions** . A questo valore viene fatto riferimento come valore di esecuzione perché si applica al parametro solo per quell'istanza specifica dell'esecuzione. All'avvio dell'esecuzione, alla proprietà del pacchetto corrispondente al parametro **pkgOptions** viene assegnato il valore 5.  
  
## Attività correlate  
 [Creazione di parametri](../Topic/Create%20Parameters.md)  
  
 [Impostazione dei valori di parametri dopo la distribuzione del progetto](../Topic/Set%20Parameter%20Values%20After%20the%20Project%20Is%20Deployed.md)  
  
## Contenuto correlato  
 Post di blog, [Suggerimento rapido su SSIS: Parametri necessari](http://go.microsoft.com/fwlink/?LinkId=239781), sul sito Web mattmasson.com.  
  
  